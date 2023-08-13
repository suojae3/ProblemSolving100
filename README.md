

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=250&section=header&text=Problem%20Solving%20100&fontSize=40&animation=fadeIn&fontAlign=25&fontAlignY=40)


<br/>

---

### 01. K번째 약수

두 개의 자연수 N과 K가 주어졌을 때, N의 약수들 중 K번째로 작은 수를 출력하는 프로그램을 작성하시오.

▣ 입력설명
첫째 줄에 N과 K가 빈칸을 사이에 두고 주어진다. N은 1 이상 10,000 이하이다. K는 1 이상 N 이하이다.

▣ 출력설명
첫째 줄에 N의 약수들 중 K번째로 작은 수를 출력한다. 만일 N의 약수의 개수가 K개보다 적어서 K번째 약수가 존재하지 않을 경우에는 -1을 출력하시오.

▣ 입력예제<br/> 6 3

▣ 출력예제<br/> 3

```python
import sys

n, k=map(int, input().split())
cnt=0
for i in range(1, n+1):
    if n%i==0:
        cnt+=1
    if cnt==k:
        print(i)
        break
else: 
    print(-1)
```
```swift
import Foundation

let input = readLine()!.split(separator: " ").map { Int($0)! }
let (n, k) = (input[0], input[1])

var cnt = 0

for i in 1...n {
    if n % i == 0 {
        cnt += 1
    }
    if cnt == k {
        print(i)
        exit(0) 
    }
}

print(-1)
```

#

### 02. K번째 수

N개의 숫자로 이루어진 숫자열이 주어지면 해당 숫자열중에서 s번째부터 e번째 까지의 수를 오름 차순 정렬했을 때 k번째로 나타나는 숫자를 출력하는 프로그램을 작성하세요.

▣ 입력설명
첫 번째 줄에 테스트 케이스 T(1<=T<=10)이 주어집니다.
각 케이스별
첫 번째 줄은 자연수 N(5<=N<=500), s, e, k가 차례로 주어진다. 두 번째 줄에 N개의 숫자가 차례로 주어진다.

▣ 출력설명
각 케이스별 k번째 수를 아래 출력예제와 같이 출력하세요.

▣ 입력예제<br/>
2<br/>
6 2 5 3<br/>
5 2 7 3 8 9<br/>
15 3 10 3<br/>
4 15 8 16 6 6 17 3 10 11 18 7 14 7 15 <br/>

▣ 출력예제<br/>
#1 7 <br/>
#2 6

```python
import sys

T=int(input())
for t in range(T):
    n, s, e, k=map(int, input().split())
    a=list(map(int, input().split()))
    a=a[s-1:e]
    a.sort()
    print("#%d %d" %(t+1, a[k-1])) 
```
```swift
import Foundation

let T = Int(readLine()!)!

for t in 1...T {
    let inputs = readLine()!.split(separator: " ").map { Int($0)! }
    var (n, s, e, k) = (inputs[0], inputs[1], inputs[2], inputs[3])
    
    var a = readLine()!.split(separator: " ").map { Int($0)! }
    a = Array(a[s-1..<e])
    a.sort()
    
    print("#\(t) \(a[k-1])")
}

```

#

### 03. K번째 큰 수

현수는 1부터 100사이의 자연수가 적힌 N장의 카드를 가지고 있습니다. 같은 숫자의 카드가 여러장 있을 수 있습니다. 현수는 이 중 3장을 뽑아 각 카드에 적힌 수를 합한 값을 기록하려 고 합니다. 3장을 뽑을 수 있는 모든 경우를 기록합니다. 기록한 값 중 K번째로 큰 수를 출력 하는 프로그램을 작성하세요.

만약 큰 수부터 만들어진 수가 25 25 23 23 22 20 19......이고 K값이 3이라면 K번째 큰 값 은 22입니다.

▣ 입력설명
첫 줄에 자연수 N(3<=N<=100)과 K(1<=K<=50) 입력되고, 그 다음 줄에 N개의 카드값이 입력 된다.

▣ 출력설명
첫 줄에 K번째 수를 출력합니다. K번째 수는 반드시 존재합니다.

▣ 입력예제 <br/>
1<br/>
10 3<br/>
13 15 34 23 45 65 33 11 26 42<br/>


▣ 출력예제 <br/>
1 <br/>
143<br/>

```python
import sys

n,k=map(int, input().split())
a=list(map(int, input().split()))
res=set()
for i in range(n):
    for j in range(i+1, n):
        for m in range(j+1, n):
            res.add(a[i]+a[j]+a[m])

res=list(res)
res.sort(reverse=True)
print(res[k-1])
```
```Swift
import Foundation

// Read input
let t = Int(readline()!)!
let nk = readLine()!.split(separator: " ").map { Int($0)! }
let n = nk[0]
let k = nk[1]

let a = readLine()!.split(separator: " ").map { Int($0)! }

var res = Set<Int>()

for i in 0..<n {
    for j in (i+1)..<n {
        for m in (j+1)..<n {
            res.insert(a[i] + a[j] + a[m])
        }
    }
}

let sortedRes = res.sorted(by: >)
print(sortedRes[k-1])
```
#

### (Tip) 최솟값 구하기

```Python
arr = [5, 3, 7, 9, 2, 5, 2, 6]
arrMin = float('inf') #최댓값 할당
for i in range(len(arr)):
    if arr[i]<arrMin:
        arrMin=arr[i]
```
```Swift
let arr = [5, 3, 7, 9, 2, 5, 2, 6]
var arrMin = Int.max  

for i in 0..<arr.count {
    if arr[i] < arrMin {
        arrMin = arr[i]
    }
}
print(arrMin)

//하지만 Swift는 최솟값 함수 찾기가 빌트인으로 선언되어있다
let arr = [5, 3, 7, 9, 2, 5, 2, 6]
if let arrMin = arr.min() {
    print(arrMin)
}
```

#

### 04. 대표값

N명의 학생의 수학점수가 주어집니다. N명의 학생들의 평균(소수 첫째자리 반올림)을 구하고, N명의 학생 중 평균에 가장 가까운 학생은 몇 번째 학생인지 출력하는 프로그램을 작성하세요. <br/>
평균과 가장 가까운 점수가 여러 개일 경우 먼저 점수가 높은 학생의 번호를 답으로 하고, 높은 점수를 가진 학생이 여러 명일 경우 그 중 학생번호가 빠른 학생의 번호를 답으로 합니다. <br/>

▣ 입력설명 <br/>
첫줄에 자연수 N(5<=N<=100)이 주어지고, 두 번째 줄에는 각 학생의 수학점수인 N개의 자연 수가 주어집니다. 학생의 번호는 앞에서부터 1로 시작해서 N까지이다.

▣ 출력설명 <br/>
첫줄에 평균과 평균에 가장 가까운 학생의 번호를 출력한다. 평균은 소수 첫째 자리에서 반올림합니다.

▣ 입력 예제 <br/>
10 <br/>
45 73 66 87 92 67 75 79 75 80 <br/>

▣ 출력 예제 <br/>
1 7 <br/>

```python
import sys

n= int(input())
a=list(map(int, input().split()))

# round()는 반홀림함수 일반적으로 half_up방식 (1.5면 2로 뱉음)
# 파이썬의 roundsms half_even 방식 택함(1.5면 1로 뱉음) 그래서 +0.5
ave=round(sum(a)/n+0.5)
min=21470000000 # 4바이트에서 가장 큰 값

for idx, x in enumerate(a):
    tmp=abs(x-ave) # 절댓값 함수 abs()
    if tmp<min:
        min=tmp
        score=x
        res=idx+1

    #답이 두 개 이상인 경우 점수가 높은 사람 우선순위
    # 점수가 같으면 앞번호 유지
    elif tmp==min:
        if x>score:
            score=x
            res=idx+1

print(ave, res)
```
```Swift
import Foundation

let n = Int(readLine()!)!
let a = readLine()!.split(separator: " ").map { Int($0)! }

//Swift도 파이썬과 마찬가지로 half_evne이기 때문에 0.5를 더해준다
let ave = round(Double(a.reduce(0, +)) / Double(n) + 0.5)
var minDistance = Double(Int.max)
var score = -1
var res = -1

for (idx, x) in a.enumerated() {
    let tmp = abs(Double(x) - ave)
    
    if tmp < minDistance {
        minDistance = tmp
        score = x
        res = idx + 1
    } else if tmp == minDistance {
        if x > score {
            score = x
            res = idx + 1
        }
    }
}

print(Int(ave), res)
```

#

### 05. 정다면체

두 개의 정 N면체와 정 M면체의 두 개의 주사위를 던져서 나올 수 있는 눈의 합 중 가장 확 률이 높은 숫자를 출력하는 프로그램을 작성하세요.<br/>

정답이 여러 개일 경우 오름차순으로 출력합니다.<br/>

▣ 입력설명<br/>
첫 번째 줄에는 자연수 N과 M이 주어집니다. N과 M은 4, 6, 8, 12, 20 중의 하나입니다.<br/>

▣ 출력설명<br/>
첫 번째 줄에 답을 출력합니다.<br/>

▣ 입력예제<br/>
4 6<br/>

▣ 출력예제<br/>
5 6 7<br/>

```python
import sys
n, m=map(int, input().split())

# max값을 이후에 지속적으로 넣어주어야하기 때문에 가장 작은 값 할당
max = -214700000

#눈의 합은 n+m까지 나오겠지만 혹시모르니 +3으로 넉넉하게 잡아주기
cnt=[0]*(n+m+3)

#1부터 n까지 for문 돌리기
for i in range(1, n+1):
    for j in range(1, m+1):
        cnt[i+j]+=1

# +1을 해야 n+m까지 돔
for i in range(n+m+1):
    if cnt[i]>max:
        max=cnt[i]

for i in range(n+m+1):
    if cnt[i]==max:
        print(i, end=' ')
```
```swift
import Foundation

let nm = readLine()!.split(separator: " ").map { Int($0)! }
let (n, m) = (nm[0], nm[1])

// Initialize an array to count occurrences of each sum
var cnt = [Int](repeating: 0, count: n + m + 3)

// Set an initial value for the maximum occurrence
var maxOccurrence = Int.min

// Iterate over all possible dice rolls and count the occurrences of each sum
for i in 1...n {
    for j in 1...m {
        cnt[i + j] += 1
    }
}

// Find the maximum occurrence
for i in 0...(n + m) {
    if cnt[i] > maxOccurrence {
        maxOccurrence = cnt[i]
    }
}

// Print the sums that occurred the maximum number of times
for i in 0...(n + m) {
    if cnt[i] == maxOccurrence {
        print(i, terminator: " ")
    }
}
```
#

### 06. 자릿수의 합

N개의 자연수가 입력되면 각 자연수의 자릿수의 합을 구하고, 그 합이 최대인 자연수를 출력 하는 프로그램을 작성하세요.<br/>
각 자연수의 자릿수의 합을 구하는 함수를 def digit_sum(x)를 꼭 작성해서 프로그래밍 하세요. <br/>

▣ 입력설명<br/>
첫 줄에 자연수의 개수 N(3<=N<=100)이 주어지고, 그 다음 줄에 N개의 자연수가 주어진다. 각 자연수의 크기는 10,000,000를 넘지 않는다.<br/>

▣ 출력설명<br/>
자릿수의 합이 최대인 자연수를 출력한다. 자릿수의 합이 같을 경우 입력순으로 먼저인 숫자 를 출력합니다.<br/>

▣ 입력예제<br/> 
3<br/>
125 15232 97<br/>

▣ 출력예제<br/> 
97<br/>

```python
import sys
n=int(input())
a=list(map(int, input().split()))
max=-214700000

def digit_sum(x):
    sum=0

    # x 각 자릿수 합을 sum에 누적하기
    while x>0:
        sum+=x%10
        x=x//10

for x in a:
    tot=digit_sums(x)
    if tot>max:
        max=tot
        res=x
print(res)


```
```Swift
import Foundation

let n = Int(readLine()!)!
let a = readLine()!.split(separator: " ").map { Int($0)! }

var maxSum = Int.min
var res = 0

func digitSum(_ x: Int) -> Int {
    var sum = 0
    var num = x
    
    while num > 0 {
        sum += num % 10
        num /= 10
    }
    return sum
}

for x in a {
    let tot = digitSum(x)
    if tot > maxSum {
        maxSum = tot
        res = x
    }
}

print(res)
```

#

### 07. 소수(에라토스테네스 체)

자연수 N이 입력되면 1부터 N까지의 소수의 개수를 출력하는 프로그램을 작성하세요.<br/> 
만약 20이 입력되면 1부터 20까지의 소수는 2, 3, 5, 7, 11, 13, 17, 19로 총 8개입니다. 제한시간은 1초입니다.<br/>

▣ 입력설명<br/>
첫 줄에 자연수의 개수 N(2<=N<=200,000)이 주어집니다.<br/>

▣ 출력설명<br/>
첫 줄에 소수의 개수를 출력합니다.<br/>

▣ 입력예제<br/>
20<br/>

▣ 출력예제 <br/>
8 <br/>

```Python
import sys
n=int(input())
ch=[0]*(n+1)
cnt=0

# 소수는 2부터 시작
for i in range(2, n+1):
    if ch[i]==0:
        cnt+=1

        # i부터 시작해서 i씩 n까지 증가
        for j in range(i, n+1, i):
            ch[j]=1

print(cnt)
```
```Swift
import Foundation

let n = Int(readLine()!)!
var ch = [Int](repeating: 0, count: n + 1)
var cnt = 0

for i in 2...n {
    if ch[i] == 0 {
        cnt += 1
        for j in stride(from: i, through: n, by: i) {
            ch[j] = 1
        }
    }
}

print(cnt)
```






