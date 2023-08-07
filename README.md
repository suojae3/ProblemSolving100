# ProblemSolving100

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=250&section=header&text=Problem%20Solving%20100&fontSize=60&animation=fadeIn&fontAlign=35&fontAlignY=35)


<br/>

---

### 04. [백준 1920번] 수찾기

#### 문제
첫째 줄에 자연수 N(1 ≤ N ≤ 100,000)이 주어진다.<br/> 
다음 줄에는 N개의 정수 A[1], A[2], …, A[N]이 주어진다. 다음 줄에는 M(1 ≤ M ≤ 100,000)이 주어진다.<br/>
다음 줄에는 M개의 수들이 주어지는데, 이 수들이 A안에 존재하는지 알아내면 된다. 모든 정수의 범위는 -231 보다 크거나 같고 231보다 작다.<br/>

<br/>

#

#### 나의 풀이 로직 
1. 2,4번째 입력값을 받을 배열과 정답 배열 객체를 만들어준다
2. 체크리스트를 for-in 반복을 돌려 값하나씩 체크하고 true면 정답배열에 1, false면 정답배열에 0을 담는다.
3. 정답배열을 for-in문을 돌려 출력한다

```dart
import 'dart:io';

void main() {
  stdin.readLineSync(); 

  List<int> inputList = stdin.readLineSync()!.split(" ").map((str) => int.parse(str)).toList();
  stdin.readLineSync();

  List<int> checkList = stdin.readLineSync()!.split(" ").map((str) => int.parse(str)).toList();
  List<int> answerList = []; 

  for (int checkValue in checkList) {
    if (inputList.contains(checkValue)) {
      answerList.add(1); 
    } else {
      answerList.add(0); 
    }
  }

  // Output the answerList
  for (int answer in answerList) {
    print(answer);
  }
}
```

```swift
import Foundation

_ = readLine()
let inputList = readLine()!.split(separator: " ").map { Int(String($0))! }
_ = readLine()
let checkList = readLine()!.split(separator: " ").map { Int(String($0))! }

var answerList: [Int] = []


for checkValue in checkList {
    if inputList.contains(checkValue) {
        answerList.append(1)
    } else {
        answerList.append(0)
    }
}

for answer in answerList {
    print(answer)
}
```


<br/>

#

#### 결과: 시간 초과가 뜬다. 
1. `contain()`의 시간복잡도가 n이기 때문에 for문안에서 돌아 최종적인 시간복잡도는 O(n^2)이 되어버린다
2. 비교할 배열을 Set으로 답안을 다시 풀어보기 (Set은 비교할 때 시간복잡도가 O(1)이기 때문에)
```dart
import 'dart:io';

void main() {
  stdin.readLineSync();
  Set<int> inputSet = stdin.readLineSync()!.split(' ').map(int.parse).toSet();
  stdin.readLineSync();
  List<int> checkList = stdin.readLineSync()!.split(' ').map(int.parse).toList();

  for (int checkValue in checkList) {
    if (inputSet.contains(checkValue)) {
      print(1); // If the value is in the set, print 1
    } else {
      print(0); // If the value is not in the set, print 0
    }
  }
}
```
```swift
import Foundation

let n = Int(readLine()!)!

let array = Set(readLine()!.split(separator: " ").map { Int($0)! })

let m = Int(readLine()!)!

let x_values = readLine()!.split(separator: " ").map { Int($0)! }

for x in x_values {
    print(array.contains(x) ? 1 : 0)
}
```

<br/>

---

### 05. [백준 4195번] 친구 네트워크  

#### 문제
민혁이는 소셜 네트워크 사이트에서 친구를 만드는 것을 좋아하는 친구이다. 우표를 모으는 취미가 있듯이, 민혁이는 소셜 네트워크 사이트에서 친구를 모으는 것이 취미이다.<br/>

어떤 사이트의 친구 관계가 생긴 순서대로 주어졌을 때, 두 사람의 친구 네트워크에 몇 명이 있는지 구하는 프로그램을 작성하시오.<br/>

친구 네트워크란 친구 관계만으로 이동할 수 있는 사이를 말한다.<br/>

<br/>

#

#### 나의 풀이 로직 

1. 첫번째 입력값은 버린다
2. 두번째 입력값을 n에 넣는다
3. n개의 비어있는 Set을 만든다
4. 각 Set에 입력값을 저장한다
5. 먼저 첫번째 Set의 내용물의 개수를 print한다
6. 첫번째 Set과 두번째 Set을 비교한다. 하나가 겹친다면 3 나머지 경우는 2 를 출력한다.
7. 비교한뒤에 첫번째 Set과 두번째 Set을 합친다.
8. 이를 n개의 Set까지 반복한다

```Dart
import 'dart:io';

void main() {
  stdin.readLineSync(); 
  int t = int.parse(stdin.readLineSync()!);
  for (int i = 0; i < t; i++) {
    int f = int.parse(stdin.readLineSync()!);
    var friends = <String, Set<String>>{};
    for (int j = 0; j < f; j++) {
      var pair = stdin.readLineSync()!.split(' ');
      var set1 = friends[pair[0]];
      var set2 = friends[pair[1]];
      if (set1 == null && set2 == null) {
        set1 = {pair[0], pair[1]};
        friends[pair[0]] = set1;
        friends[pair[1]] = set1;
      } else if (set1 == null) {
        set2!.add(pair[0]);
        friends[pair[0]] = set2;
      } else if (set2 == null) {
        set1.add(pair[1]);
        friends[pair[1]] = set1;
      } else if (set1 != set2) {
        set1.addAll(set2);
        for (var person in set2) {
          friends[person] = set1;
        }
        for (var person in set1) {
          friends[person] = set1;
        }
      }
      print(friends[pair[0]]!.length);
    }
  }
}

```
```Swift
import Foundation

let t = Int(readLine()!)!
for _ in 0..<t {
    let f = Int(readLine()!)!
    var friends = [String: Set<String>]()
    for _ in 0..<f {
        let pair = readLine()!.split(separator: " ").map(String.init)
        var set1 = friends[pair[0]]
        var set2 = friends[pair[1]]
        if set1 == nil && set2 == nil {
            set1 = [pair[0], pair[1]]
            friends[pair[0]] = set1
            friends[pair[1]] = set1
        } else if set1 == nil {
            set2!.insert(pair[0])
            friends[pair[0]] = set2
        } else if set2 == nil {
            set1!.insert(pair[1])
            friends[pair[1]] = set1
        } else if set1 != set2 {
            set1!.formUnion(set2!)
            for person in set2! {
                friends[person] = set1
            }
            for person in set1! {
                friends[person] = set1
            }
        }
        print(friends[pair[0]]!.count)
    }
}
```

<br/>

#

#### 결과: 시간 초과가 뜬다. 


```dart
import 'dart:io';

// Define the 'find' function
String find(String x, Map<String, String> parent) {
  // If 'x' is its own parent, then 'x' is the representative of its set
  if (parent[x] == x) {
    return x;
  } else {
    // If 'x' is not its own parent, then find the representative of 'x's parent
    String p = find(parent[x]!, parent);
    // Update the parent of 'x' to its representative to achieve path compression
    parent[x] = p;
    // Return the representative
    return p;
  }
}

// Define the 'union' function
void union(String x, String y, Map<String, String> parent, Map<String, int> size) {
  // Find the representative of 'x'
  String xRoot = find(x, parent);
  // Find the representative of 'y'
  String yRoot = find(y, parent);
  
  // If 'x' and 'y' are not already in the same set
  if (xRoot != yRoot) {
    // Make the representative of 'x' the parent of the representative of 'y'
    parent[yRoot] = xRoot;
    // Update the size of 'x's set
    size[xRoot] = (size[xRoot] ?? 1) + (size[yRoot] ?? 1);
  }
}

void main() {
  // Define the number of test cases
  int testCases = int.parse(stdin.readLineSync()!);

  // Process each test case
  for (int _ = 0; _ < testCases; _++) {
    // Read the number of friendships
    int friendships = int.parse(stdin.readLineSync()!);
    // Initialize the parent and size dictionaries
    Map<String, String> parent = {};
    Map<String, int> size = {};
    
    // Process each friendship
    for (int _ = 0; _ < friendships; _++) {
      // Read the names of the two friends
      List<String> line = stdin.readLineSync()!.split(" ");
      String x = line[0], y = line[1];
      
      // If 'x' is not already in the parent dictionary, add it
      if (!parent.containsKey(x)) {
        parent[x] = x;
        size[x] = 1;
      }
      
      // If 'y' is not already in the parent dictionary, add it
      if (!parent.containsKey(y)) {
        parent[y] = y;
        size[y] = 1;
      }
      
      // Merge the sets of 'x' and 'y'
      union(x, y, parent, size);
      
      // Print the size of the set that 'x' belongs to
      print(size[find(x, parent)]!);
    }
  }
}

```

```swift
import Foundation

// Define the 'find' function
func find(_ x: String, _ parent: inout [String: String]) -> String {
    // If 'x' is its own parent, then 'x' is the representative of its set
    if parent[x] == x {
        return x
    } else {
        // If 'x' is not its own parent, then find the representative of 'x's parent
        let p = find(parent[x]!, &parent)
        // Update the parent of 'x' to its representative to achieve path compression
        parent[x] = p
        // Return the representative
        return p
    }
}

// Define the 'union' function
func union(_ x: String, _ y: String, _ parent: inout [String: String], _ size: inout [String: Int]) {
    // Find the representative of 'x'
    let xRoot = find(x, &parent)
    // Find the representative of 'y'
    let yRoot = find(y, &parent)
    
    // If 'x' and 'y' are not already in the same set
    if xRoot != yRoot {
        // Make the representative of 'x' the parent of the representative of 'y'
        parent[yRoot] = xRoot
        // Update the size of 'x's set
        size[xRoot] = (size[xRoot] ?? 1) + (size[yRoot] ?? 1)
    }
}

// Define the number of test cases
let testCases = Int(readLine()!)!

// Process each test case
for _ in 1...testCases {
    // Read the number of friendships
    let friendships = Int(readLine()!)!
    // Initialize the parent and size dictionaries
    var parent = [String: String]()
    var size = [String: Int]()
    
    // Process each friendship
    for _ in 1...friendships {
        // Read the names of the two friends
        let line = readLine()!.split(separator: " ").map { String($0) }
        let x = line[0], y = line[1]
        
        // If 'x' is not already in the parent dictionary, add it
        if parent[x] == nil {
            parent[x] = x
            size[x] = 1
        }
        
        // If 'y' is not already in the parent dictionary, add it
        if parent[y] == nil {
            parent[y] = y
            size[y] = 1
        }
        
        // Merge the sets of 'x' and 'y'
        union(x, y, &parent, &size)
        
        // Print the size of the set that 'x' belongs to
        print(size[find(x, &parent)]!)
    }
}
```
