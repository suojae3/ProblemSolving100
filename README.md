

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

//Swift도 파이썬과 마찬가지로 half_even이기 때문에 0.5를 더해준다
let ave = round(Double(a.reduce(0, +)) / Double(n) + 0.1)
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
a=list( map(int, input().split()) )
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

#

### 08. 뒤집은 소수

N개의 자연수가 입력되면 각 자연수를 뒤집은 후 그 뒤집은 수가 소수이면 그 수를 출력하는 프로그램을 작성하세요.<br/>
예를 들어 32를 뒤집으면 23이고, 23은 소수이다. 그러면 23을 출력 한다.<br/>
단 910를 뒤집으면 19로 숫자화 해야 한다. 첫 자리부터의 연속된 0은 무시한다.<br/>
뒤집는 함수인 def reverse(x) 와 소수인지를 확인하는 함수 def isPrime(x)를 반드시 작성하 여 프로그래밍 한다.<br/>

▣ 입력설명<br/>
첫 줄에 자연수의 개수 N(3<=N<=100)이 주어지고, 그 다음 줄에 N개의 자연수가 주어진다.<br/>
각 자연수의 크기는 100,000를 넘지 않는다.<br/>

▣ 출력설명<br/>
첫 줄에 뒤집은 소수를 출력합니다. 출력순서는 입력된 순서대로 출력합니다.<br/>

▣ 입력예제<br/>
5<br/>
32 55 62 3700 250<br/>

▣ 출력예제<br/>
23 73 <br/>

```python
import sys
n=int(input())
a=list(map(int, input().split()))

def reverse(x):
    res=0
    while x>0:
        t=x%10
        res=res*10+t
        x=x//10
    return res

def isPrime(x):
    if x==1:
        return False
    for i in range(2, x//2+1): #절반까지만 돌아도 소수 판별 가능
        if x%i==0:
            return False
    else:
        return True    
            

for x in a:
    tmp=reverse(x)
    if isPrime(tmp):
        print(tmp, end=' ')
```
```Swift
import Foundation

let n = Int(readLine()!)!
let a = readLine()!.split(separator: " ").map { Int($0)! }

func reverse(_ x: Int) -> Int {
    var x = x
    var res = 0
    while x > 0 {
        let t = x % 10
        res = res * 10 + t
        x /= 10
    }
    return res
}

func isPrime(_ x: Int) -> Bool {
    if x == 1 {
        return false
    }
    for i in 2...x/2 {
        if x % i == 0 {
            return false
        }
    }
    return true
}

for x in a {
    let tmp = reverse(x)
    if isPrime(tmp) {
        print(tmp, terminator: " ")
    }
}
```

#

### 09. 주사위 게임

1에서부터 6까지의 눈을 가진 3개의 주사위를 던져서 다음과 같은 규칙에 따라 상금을 받는 게 임이 있다.<br/>
규칙(1) 같은 눈이 3개가 나오면 10,000원+(같은 눈)*1,000원의 상금을 받게 된다. <br/>
규칙(2) 같은 눈이 2개만 나오는 경우에는 1,000원+(같은 눈)*100원의 상금을 받게 된다. <br/>
규칙(3) 모두 다른 눈이 나오는 경우에는 (그 중 가장 큰 눈)*100원의 상금을 받게 된다.<br/>
예를 들어, 3개의 눈 3, 3, 6이 주어지면 상금은 1,000+3*100으로 계산되어 1,300원을 받게 된 다. <br/>
또 3개의 눈이 2, 2, 2로 주어지면 10,000+2*1,000 으로 계산되어 12,000원을 받게 된다. <br/>
3개의 눈이 6, 2, 5로 주어지면 그 중 가장 큰 값이 6이므로 6*100으로 계산되어 600원을 상금 으로 받게 된다.<br/>
N 명이 주사위 게임에 참여하였을 때, 가장 많은 상금을 받은 사람의 상금을 출력하는 프로그램 을 작성하시오<br/>

▣ 입력설명<br/>
첫째 줄에는 참여하는 사람 수 N(2<=N<=1,000)이 주어지고 <br/>
그 다음 줄부터 N개의 줄에 사람 들이 주사위를 던진 3개의 눈이 빈칸을 사이에 두고 각각 주어진다.<br/>

▣ 출력설명<br/>
첫째 줄에 가장 많은 상금을 받은 사람의 상금을 출력한다.<br/>

▣ 입력예제<br/>
3<br/>
3 3 6<br/>
2 2 2<br/> 
6 2 5<br/>

▣ 출력예제<br/>
12000<br/>

```python
import sys
n=int(input())
res=0
for i in range(n):
    tmp=input().split()
    tmp=sort()
    a, b, c=map(int, tmp)
    print(a, b, c)

    #if문을 작성할 때는 가장 좁은 범위부터
    if  a==b and b==c:
        money=10000+a*1000
    elif a==b or a==c:
        money=1000+(a*100)
    elif b==c:
        money=1000+(b*100)
    else:
        money=c*100
    if money>res:
        res=money
print(res)
```
```Swift
import Foundation

let n = Int(readLine()!)!
var res = 0

for _ in 0..<n {
    let tmp = readLine()!.split(separator: " ").map { Int($0)! }.sorted()
    let (a, b, c) = (tmp[0], tmp[1], tmp[2])
    
    var money: Int
    if a == b && b == c {
        money = 10000 + a * 1000
    } else if a == b || a == c {
        money = 1000 + a * 100
    } else if b == c {
        money = 1000 + b * 100
    } else {
        money = c * 100
    }
    
    if money > res {
        res = money
    }
}

print(res)
```



#

### 10. 점수계산

OX 문제는 맞거나 틀린 두 경우의 답을 가지는 문제를 말한다. <br/>
여러 개의 OX 문제로 만들어진 시험에서 연속적으로 답을 맞히는 경우에는 가산점을 주기 위해서 다음과 같이 점수 계산을 하기 로 하였다.<br/>
1번 문제가 맞는 경우에는 1점으로 계산한다. 앞의 문제에 대해서는 답을 틀리다가 답이 맞는 처음 문제는 1점으로 계산한다. <br/>
또한, 연속으로 문제의 답이 맞는 경우에서 두 번째 문제는 2점, 세 번째 문제는 3점, ..., K번째 문제는 K점으로 계산한다. <br/>
틀린 문제는 0점으로 계 산한다.<br/>
예를 들어, 아래와 같이 10 개의 OX 문제에서 답이 맞은 문제의 경우에는 1로 표시하고,<br/>
틀린 경 우에는 0으로 표시하였을 때, 점수 계산은 아래 표와 같이 계산되어, <br/>
총 점수는 1+1+2+3+1+2=10 점이다.<br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/001.png" width="400" height="200"><br/>

시험문제의 채점 결과가 주어졌을 때, 총 점수를 계산하는 프로그램을 작성하시오.<br/>

▣ 입력설명<br/>
첫째 줄에 문제의 개수 N (1 ≤ N ≤ 100)이 주어진다.<br/>
둘째 줄에는 N개 문제의 채점 결과를 나 타내는 0 혹은 1이 빈 칸을 사이에 두고 주어진다.<br/>
0은 문제의 답이 틀린 경우이고, 1은 문제의 답이 맞는 경우이다.<br/>

▣ 출력설명<br/>
첫째 줄에 입력에서 주어진 채점 결과에 대하여 가산점을 고려한 총 점수를 출력한다.<br/>

▣ 입력예제<br/>
10<br/>
1 0 1 1 1 0 0 1 1 0<br/>

▣ 출력예제<br/>
10<br/>

```python
import sys

n=int(input())
a=list(map(int, input().split()))
sum=0
cnt=0
for x in a:
    if x==1:
        cnt+=1
        sum+=cnt
    else:
        cnt=0
print(sum)
```
```swift
import Foundation

let n = Int(readLine()!)!
let a = readLine()!.split(separator: " ").map { Int($0)! }

var sum = 0
var cnt = 0

for x in a {
    if x == 1 {
        cnt += 1
        sum += cnt
    } else {
        cnt = 0
    }
}

print(sum)
```
#

### 11. 회문 문자열 검사

N개의 문자열 데이터를 입력받아 앞에서 읽을 때나 뒤에서 읽을 때나 같은 경우 <br/>
(회문 문자열) 이면 YES를 출력하고 회문 문자열이 아니면 NO를 출력하는 프로그램을 작성한다. <br/>
단 회문을 검사할 때 대소문자를 구분하지 않습니다. <br/>

▣ 입력설명 <br/>
첫 줄에 정수 N(1<=N<=20)이 주어지고, 그 다음 줄부터 N개의 단어가 입력된다.<br/>
각 단어의 길이는 100을 넘지 않는다.<br/>

▣ 출력설명 <br/>
각 줄에 해당 문자열의 결과를 YES 또는 NO로 출력한다. <br/>

▣ 입력예제 <br/>
5 <br/>
level <br/>
moon <br/>
abcba <br/> 
soon <br/> 
gooG <br/>

▣ 출력예제 <br/>
#1 YES <br/>
#2 NO <br/>
#3 YES <br/>
#4 NO <br/>
#5 YES <br/>

```python
import sys

n=int(input())
for i in range(n):
    s=input()
    s=s.upper()
    size=len(s[-1])

    for j in range(size//2):
        if s[j]!=s[-1-j]:
            print("#%d NO" %(i+1))
            break
    else:
        print("#%d YES" %(i+1))
```
```swift
import Foundation

let n = Int(readLine()!)!
for i in 1...n {
    let s = readLine()!.uppercased()
    let reversedS = String(s.reversed())
    
    if s == reversedS {
        print("#\(i) YES")
    } else {
        print("#\(i) NO")
    }
}
```

#

### 12. 숫자만 추출

문자와 숫자가 섞여있는 문자열이 주어지면 그 중 숫자만 추출하여 그 순서대로 자연수를 만 듭니다.<br/>
만들어진 자연수와 그 자연수의 약수 개수를 출력합니다.<br/>
만약 “t0e0a1c2h0er”에서 숫자만 추출하면 0, 0, 1, 2, 0이고 이것을 자연수를 만들면 120이 됩니다.<br/>
즉첫자리0은자연수화할때무시합니다. 출력은 120를출력하고,다음줄에 120 의 약수의 개수를 출력하면 됩니다.<br/>
추출하여 만들어지는 자연수는 100,000,000을 넘지 않습니다.<br/>

▣ 입력설명<br/>
첫 줄에 숫자가 썩인 문자열이 주어집니다.<br/>
문자열의 길이는 50을 넘지 않습니다.<br/>

▣ 출력설명<br/>
첫 줄에 자연수를 출력하고, 두 번째 줄에 약수의 개수를 출력합니다.<br/>

▣ 입력예제<br/>
g0en2Ts8eSoft<br/>

▣ 출력예제<br/>
28<br/>
6<br/>

```python
import sys
s=input()
res=0

for x in s:
    if x.isDecimal():
        res=res*10+int(x)
print(res)
cnt = 0
for i in range(1, res+1):
    if res%i==0:
        cnt+=1
print(cnt)
```
```Swift
import Foundation

let s = readLine()!
var res = 0

for char in s {
    if let num = Int(String(char)) {
        res = res * 10 + num
    }
}

print(res)

var cnt = 0
for i in 1...res {
    if res % i == 0 {
        cnt += 1
    }
}

print(cnt)
```

#

### 13. 카드 역배치

1부터 20까지 숫자가 하나씩 쓰인 20장의 카드가 아래 그림과 같이 오름차순으로 한 줄로 놓 여있다. <br/>
각 카드의 위치는 카드 위에 적힌 숫자와 같이 1부터 20까지로 나타낸다. <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/2.png" width="400" height="200"><br/>

이제 여러분은 다음과 같은 규칙으로 카드의 위치를 바꾼다: <br/>
구간 [a, b] (단, 1 ≤ a ≤ b ≤ 20)가 주어지면 위치 a부터 위치 b까지의 카드를 현재의 역순으로 놓는다. <br/>
예를 들어, 현재 카드가 놓인 순서가 위의 그림과 같고 구간이 [5, 10]으로 주어진다면, <br/>
위치 5부터 위치 10까지의 카드 5, 6, 7, 8, 9, 10을 역순으로 하여 10, 9, 8, 7, 6, 5로 놓는다. <br/>
이제 전체 카드가 놓인 순서는 아래 그림과 같다.<br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/3.png" width="400" height="200"><br/>

이 상태에서 구간 [9, 13]이 다시 주어진다면, 위치 9부터 위치 13까지의 카드 6, 5, 11, 12, 13을 역순으로 하여 <br/>
13, 12, 11, 5, 6으로 놓는다. 이제 전체 카드가 놓인 순서는 아래 그림 과 같다. <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/4.png" width="400" height="200"><br/>

오름차순으로 한 줄로 놓여있는 20장의 카드에 대해 10개의 구간이 주어지면, <br/>
주어진 구간의 순서대로 위의 규칙에 따라 순서를 뒤집는 작업을 연속해서 처리한 뒤 <br/>
마지막 카드들의 배치 를 구하는 프로그램을 작성하시오. <br/>

▣ 입력설명 <br/>
총 10개의 줄에 걸쳐 한 줄에 하나씩 10개의 구간이 주어진다. <br/>
i번째 줄에는 i번째 구간의 시 작 위치 ai와 끝 위치 bi가 차례대로 주어진다.<br/>
이때 두 값의 범위는 1 ≤ ai ≤ bi ≤ 20이다. <br/>

▣ 출력설명 <br/>
1부터 20까지 오름차순으로 놓인 카드들에 대해, <br/>
입력으로 주어진 10개의 구간 순서대로 뒤집 는 작업을 했을 때 마지막 카드들의 배치를 한 줄에 출력한다. <br/>

▣ 입력예제 <br/>
5 10 <br/>
9 13 <br/>
1 2 <br/>
3 4 <br/>
5 6 <br/>
1 2 <br/>
3 4 <br/>
5 6 <br/> 
1 20 <br/>
1 20 <br/>

▣ 출력예제 <br/>
1 2 3 4 10 9 8 7 13 12 11 5 6 14 15 16 17 18 19 20 <br/>

```python
import sys

a=list(range(21))
for _ in range(10):
    s, e=map(int, input().split())
    for i in range((e-s+1)//2):
        a[s+i], a[e-i]=a[e-i], a[s+i]

a.pop(0)
for x in a:
    print(x, end= ' ')
print(a)
```
```Swift
import Foundation

var cards = Array(0...20)  

for _ in 0..<10 {
    let range = readLine()!.split(separator: " ").map { Int($0)! }
    let (start, end) = (range[0], range[1])
    
    var i = 0
    while i < (end - start + 1) / 2 {
        cards.swapAt(start + i, end - i)
        i += 1
    }
}

cards.remove(at: 0)
for card in cards {
    print(card, terminator: " ")
}
```

#

### 14. 두 리스트 합치기

오름차순으로 정렬이 된 두 리스트가 주어지면 두 리스트를 오름차순으로 합쳐 출력하는 프로 그램을 작성하세요. <br/>

▣ 입력설명 <br/>
첫 번째 줄에 첫 번째 리스트의 크기 N(1<=N<=100)이 주어집니다. <br/>
두 번째 줄에 N개의 리스트 원소가 오름차순으로 주어집니다. <br/>
세 번째 줄에 두 번째 리스트의 크기 M(1<=M<=100)이 주어집니다.  <br/>
네 번째 줄에 M개의 리스트 원소가 오름차순으로 주어집니다. <br/>
각 리스트의 원소는 int형 변수의 크기를 넘지 않습니다. <br/>
(sort함수를 사용하는 것보다 시간복잡도를 더 줄일 것) <br/>

▣ 출력설명 <br/>
오름차순으로 정렬된 리스트를 출력합니다. <br/>

▣ 입력예제 <br/>
3 <br/>
1 3 5 <br/>
5 <br/>
2 3 6 7 9 <br/>

▣ 출력예제 <br/>
1 2 3 3 5 6 7 9 <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/5.png" width="400" height="200"><br/>


```python
import sys

n=int(input())
a=list(map(int, input().split()))
m=int(input())
b=list(map(int, input().split()))
p1=p2=0
c=[]
while p1<n and p2<m:
    if a[p1]<=b[p2]:
        c.append(a[p1])
        p1+=1
    else:
        c.append(b[p2])
        p2+=1
if p1<n:
    c=c+a[p1:]
if p2<m:
    c=c+b[p2:]

for x in c:
    print(x, end=' ')
```
```Swift
import Foundation

let n = Int(readLine()!)!
let a = readLine()!.split(separator: " ").map { Int($0)! }

let m = Int(readLine()!)!
let b = readLine()!.split(separator: " ").map { Int($0)! }

var p1 = 0
var p2 = 0
var c: [Int] = []

while p1 < n && p2 < m {
    if a[p1] <= b[p2] {
        c.append(a[p1])
        p1 += 1
    } else {
        c.append(b[p2])
        p2 += 1
    }
}

if p1 < n {
    c += a[p1...]
}

if p2 < m {
    c += b[p2...]
}

for x in c {
    print(x, terminator: " ")
}
```

#

### 15. 수들의 합

N개의 수로 된 수열 A[1], A[2], ..., A[N] 이 있다. <br/>
이 수열의 i번째 수부터 j번째 수까지의 합 A[i]+A[i+1]+...+A[j-1]+A[j]가 M이 되는 경우의 수를 구하는 프로그램을 작성하시오. <br/>

▣ 입력설명<br/>
첫째 줄에 N(1≤N≤10,000), M(1≤M≤300,000,000)이 주어진다. <br/>
다음 줄에는 A[1], A[2], ..., A[N]이 공백으로 분리되어 주어진다. <br/>
각각의 A[x]는 30,000을 넘지 않는 자연수이다.<br/>

▣ 출력설명<br/>
첫째 줄에 경우의 수를 출력한다.<br/>

▣ 입력예제<br/>
8 3 <br/> 
1 2 1 3 1 1 1 2 <br/> 

▣ 출력예제<br/> 
5<br/> 

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/6.png" width="400" height="200"><br/>

```python
import sys

n, m=map(int, input().split())
a=list(map(int, input().split()))
lt=0
rt=1
tot=a[0]
cnt=0
while True:
    if tot<m:
        if rt<n:
            tot+=a[rt]
            rt+=1
        else:
            break
    elif tot==m:
        cnt+=1
        tot-=a[lt]
        lt+=1
    else:
        tot-=a[lt]
        lt+=1
print(cnt)
```
```swift
let nm = readLine()!.split(separator: " ").map { Int($0)! }
let (n, m) = (nm[0], nm[1])

let a = readLine()!.split(separator: " ").map { Int($0)! }

var lt = 0
var rt = 1
var tot = a[0]
var cnt = 0

while true {
    if tot < m {
        if rt < n {
            tot += a[rt]
            rt += 1
        } else {
            break
        }
    } else if tot == m {
        cnt += 1
        tot -= a[lt]
        lt += 1
    } else {
        tot -= a[lt]
        lt += 1
    }
}

print(cnt)
```

#

### 16. 격자판 최대합

N*N의 격자판이 주어지면 각 행의 합, 각 열의 합, 두 대각선의 합 중 가 장 큰 합을 출력합니다.<br/>

▣ 입력설명<br/>
첫 줄에 자연수 N이 주어진다.(1<=N<=50) <br/>
두 번째 줄부터 N줄에 걸쳐 각 줄에 N개의 자연수가 주어진다.<br/>
각 자연수는 100을 넘지 않는다. <br/>

▣ 출력설명 <br/>
최대합을 출력합니다. <br/>

▣ 입력예제<br/>
5 <br/>
10 13 10 12 15 <br/>
12 39 30 23 11 <br/>
11 25 50 53 15 <br/>
19 27 29 37 27 <br/>
19 13 30 13 19 <br/>

▣ 출력예제 <br/>
155<br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/7.png" width="400" height="200"><br/>

```python
import sys
sys.stdin = open("input.txt", 'r')
n=int(input())
a=[list(map(int, input().split())) for _ in range(n)]
largest=-2147000000
for i in range(n):
    sum1=sum2=0
    for j in range(n):
        sum1+=a[i][j]
        sum2+=a[j][i]
    if sum1>largest:
        largest=sum1
    if sum2>largest:
        largest=sum2
sum1=sum2=0
for i in range(n):
    sum1+=a[i][i]
    sum2+=a[i][n-i-1]
if sum1>largest:
    largest=sum1
if sum2>largest:
    largest=sum2
print(largest)
```
```Swift
import Foundation

let n = Int(readLine()!)!
var a: [[Int]] = []

for _ in 0..<n {
    let row = readLine()!.split(separator: " ").map { Int($0)! }
    a.append(row)
}

var largest = Int.min

for i in 0..<n {
    var sum1 = 0
    var sum2 = 0
    for j in 0..<n {
        sum1 += a[i][j]
        sum2 += a[j][i]
    }
    largest = max(largest, sum1, sum2)
}

var sum1 = 0
var sum2 = 0
for i in 0..<n {
    sum1 += a[i][i]
    sum2 += a[i][n-i-1]
}

largest = max(largest, sum1, sum2)
print(largest)
```

#

### 17. 사과나무 (다이아몬드)

현수의 농장은 N*N 격자판으로 이루어져 있으며, 각 격자안에는 한 그루의 사과나무가 심어저 있다. <br/>
N의 크기는 항상 홀수이다. 가을이 되어 사과를 수확해야 하는데 현수는 격자판안의 사과를 수확할 때 <br/>
다이아몬드 모양의 격자판만 수확하고 나머지 격자안의 사과는 새들을 위해서 남겨놓는다. <br/>
현수과 수확하는 사과의 총 개수를 출력하세요. <br/>

▣ 입력설명 <br/>
첫 줄에 자연수 N(홀수)이 주어진다.(3<=N<=20) <br/>
두 번째 줄부터 N줄에 걸쳐 각 줄에 N개의 자연수가 주어진다. <br/>
이 자연수는 각 격자안에 있는 사과나무에 열린 사과의 개수이다. <br/>
각 격자안의 사과의 개수는 100을 넘지 않는다. <br/>

▣ 출력설명 <br/>
수확한 사과의 총 개수를 출력합니다. <br/>

▣ 입력예제 <br/>
5 <br/>
10 13 10 12 15 <br/>
12 39 30 23 11 <br/> 
11 25 50 53 15 <br/>
19 27 29 37 27 <br/>
19 13 30 13 19 <br/>

▣ 출력예제 <br/>
379 <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/8.png" width="400" height="200"><br/>

```python
import sys
sys.stdin = open("input.txt", 'r')
n=int(input())
a=[list(map(int, input().split())) for _ in range(n)]
res=0
s=e=n//2
for i in range(n):
    for j in range(s, e+1):
        res+=a[i][j]
    if i<n//2:
        s-=1
        e+=1
    else:
        s+=1
        e-=1
print(res)
```
```swift
let n = Int(readLine()!)!
var a: [[Int]] = []

for _ in 0..<n {
    let row = readLine()!.split(separator: " ").map { Int($0)! }
    a.append(row)
}

var res = 0
var s = n / 2
var e = n / 2

for i in 0..<n {
    for j in s...e {
        res += a[i][j]
    }

    //좁혀졌다가
    if i < n / 2 {
        s -= 1
        e += 1
    } else {
        //넓혀졌다가
        s += 1
        e -= 1
    }
}

print(res)
```

#

### 18. 곳감 (모래시계)

현수는 곳감을 만들기 위해 감을 깍아 마당에 말리고 있습니다. 현수의 마당은 N*N 격자판으 로 이루어져 있으며,  <br/>
현수는 각 격자단위로 말리는 감의 수를 정합니다.<br/>
그런데 해의 위치에 따라 특정위치의 감은 잘 마르지 않습니다. 그래서 현수는 격자의 행을 기준으로 왼쪽,  <br/>
또는 오른쪽으로 회전시켜 위치를 변경해 모든 감이 잘 마르게 합니다.<br/>
만약 회전명령 정보가 2 0 3이면 2번째 행을 왼쪽으로 3만큼 아래 그림처럼 회전시키는 명령 입니다.<br/>

첫 번째 수는 행번호, 두 번째 수는 방향인데 0이면 왼쪽, 1이면 오른쪽이고, 세 번째 수는 회 전하는 격자의 수입니다.<br/>
M개의 회전명령을 실행하고 난 후 아래와 같이 마당의 모래시계 모양의 영역에는 <br/>
감이 총 몇 개가 있는지 출력하는 프로그램을 작성하세요.<br/>

▣ 입력설명 <br/>
첫 줄에 자연수 N(3<=N<=20) 이 주어며, N은 홀수입니다.<br/>
두 번째 줄부터 N줄에 걸쳐 각 줄에 N개의 자연수가 주어진다.<br/>
이 자연수는 각 격자안에 있는 감의 개수이며, 각 격자안의 감의 개수는 100을 넘지 않는다. <br/>
그 다음 줄에 회전명령의 개수인 M(1<=M<=10)이 주어지고, <br/>
그 다음 줄부터 M개의 회전명령 정보가 M줄에 걸쳐 주어집니다. <br/>

▣ 출력설명 <br/>
총 감의 개수를 출력합니다. <br/>

▣ 입력예제 <br/>
5 <br/>
10 13 10 12 15 <br/>
12 39 30 23 11 <br/>
11 25 50 53 15 <br/>
19 27 29 37 27 <br/>
19 13 30 13 19 <br/>
3 <br/>
2 0 3 <br/>
5 1 2 <br/>
3 1 4 <br/>

▣ 출력예제 <br/>
362 <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/9.png" width="400" height="200"><br/>

```python
import sys
n=int(input())
a=[list(map(int, input().split())) for _ in range(n)]
m=int(input())
for i in range(m):
    h, t, k=map(int, input().split())
    if(t==0):
        for _ in range(k):
            a[h-1].append(a[h-1].pop(0))
    else:
        for _ in range(k):
            a[h-1].insert(0, a[h-1].pop())

res=0
s=0
e=n-1
for i in range(n):
    for j in range(s, e+1):
        res+=a[i][j]
    if i<n//2:
        s+=1
        e-=1
    else:
        s-=1
        e+=1
print(res)
```
```swift
import Foundation

let n = Int(readLine()!)!
var a: [[Int]] = []

for _ in 0..<n {
    let row = readLine()!.split(separator: " ").map { Int($0)! }
    a.append(row)
}

let m = Int(readLine()!)!

for _ in 0..<m {
    let commands = readLine()!.split(separator: " ").map { Int($0)! }
    let (h, t, k) = (commands[0], commands[1], commands[2])
    
    if t == 0 {
        for _ in 0..<k {
            let first = a[h-1].removeFirst()
            a[h-1].append(first)
        }
    } else {
        for _ in 0..<k {
            let last = a[h-1].removeLast()
            a[h-1].insert(last, at: 0)
        }
    }
}

var res = 0
var s = 0
var e = n - 1

for i in 0..<n {
    for j in s...e {
        res += a[i][j]
    }
    if i < n / 2 {
        s += 1
        e -= 1
    } else {
        s -= 1
        e += 1
    }
}

print(res)
```

#

### 19. 봉우리 

지도 정보가 N*N 격자판에 주어집니다. 각 격자에는 그 지역의 높이가 쓰여있습니다. <br/>
각 격자 판의 숫자 중 자신의 상하좌우 숫자보다 큰 숫자는 봉우리 지역입니다. <br/>
봉우리 지역이 몇 개 있는 지 알아내는 프로그램을 작성하세요. <br/>
격자의 가장자리는 0으로 초기화 되었다고 가정한다. <br/>
만약 N=5 이고, 격자판의 숫자가 다음과 같다면 봉우리의 개수는 10개입니다. <br/>

▣ 입력설명 <br/>
첫 줄에 자연수 N이 주어진다.(1<=N<=50) <br/>
두 번째 줄부터 N줄에 걸쳐 각 줄에 N개의 자연수가 주어진다. <br/>
각 자연수는 100을 넘지 않는다. <br/>

▣ 출력설명 <br/>
봉우리의 개수를 출력하세요. <br/>

▣ 입력예제 <br/>
5 <br/>
5 3 7 2 3 <br/>
3 7 1 6 1 <br/>
7 2 5 3 4 <br/>
4 3 6 4 1 <br/>
8 7 3 5 2<br/>

▣ 출력예제 <br/>
10 <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/10.png" width="400" height="200"><br/>

```python
import sys
dx=[-1, 0, 1, 0]
dy=[0, 1, 0, -1]
n=int(input())
a=[list(map(int, input().split())) for _ in range(n)]
a.insert(0, [0]*n)
a.append([0]*n)
for x in a:
    x.insert(0, 0)
    x.append(0)

cnt=0
for i in range(1, n+1):
    for j in range(1, n+1):
        if all(a[i][j]>a[i+dx[k]][j+dy[k]] for k in range(4)):
            cnt+=1
print(cnt)
```
```swift
import Foundation

//상하좌우 탐색
let dx = [-1, 0, 1, 0]
let dy = [0, 1, 0, -1]

let n = Int(readLine()!)!
var a: [[Int]] = []

// Read the input and pad with zeros on all sides
for _ in 0..<n {
    let row = [0] + readLine()!.split(separator: " ").map { Int($0)! } + [0]
    a.append(row)
}
a.insert([Int](repeating: 0, count: n + 2), at: 0)
a.append([Int](repeating: 0, count: n + 2))

var cnt = 0

for i in 1...n {
    for j in 1...n {
        if (0..<4).allSatisfy({ a[i][j] > a[i + dx[$0]][j + dy[$0]] }) {
            cnt += 1
        }
    }
}

print(cnt)
```

#

### 20. 스도쿠 검사

스도쿠는 매우 간단한 숫자 퍼즐이다. 9×9 크기의 보드가 있을 때, <br/>
각 행과 각 열, 그리고 9 개의 3×3 크기의 보드에 1부터 9까지의 숫자가 중복 없이 나타나도록 보드를 채우면 된다. <br/>
예를 들어 다음을 보자.

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/11.png" width="400" height="400"><br/>

위 그림은 스도쿠를 정확하게 푼 경우이다. 각 행에 1부터 9까지의 숫자가 중복 없이 나오 고,  <br/>
각 열에 1부터 9까지의 숫자가 중복 없이 나오고,  <br/>
각 3×3짜리 사각형(9개이며, 위에서 색 깔로 표시되었다)에 1부터 9까지의 숫자가 중복 없이 나오기 때문이다.  <br/>
완성된 9×9 크기의 수도쿠가 주어지면 정확하게 풀었으면 “YES", 잘 못 풀었으면 ”NO"를 출 력하는 프로그램을 작성하세요.  <br/>

▣ 입력설명  <br/>
첫 번째 줄에 완성된 9×9 스도쿠가 주어집니다. <br/>

▣ 출력설명  <br/>
첫째 줄에 “YES" 또는 ”NO"를 출력하세요.  <br/>

▣ 입력예제  <br/>
1 4 3 6 2 8 5 7 9  <br/>
5 7 2 1 3 9 4 6 8  <br/>
9 8 6 7 5 4 2 3 1  <br/>
3 9 1 5 4 2 7 8 6  <br/>
4 6 8 9 1 7 3 5 2  <br/>
7 2 5 8 6 3 9 1 4  <br/>
2 3 7 4 8 1 6 9 5  <br/>
6 1 9 2 7 5 8 4 3  <br/>
8 5 4 3 9 6 1 2 7  <br/>

▣ 출력예제  <br/>
YES  <br/>

▣ 풀이로직 
- 행 / 열 / 3x3 박스 (그룹탐색)의 중복 숫자를 체크한다
- `a[i][j]`를 ch 배열에 넣어서 중복체크한다
- 그룹탐색은 4중 for 문을 돌리게 된다

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/12.png" width="400" height="400"><br/>

```python
import sys
sys.stdin=open("input.txt", "r")
def check(a):

    for i in range(9):

        # 행 / 열 체크
        ch1=[0]*10
        ch2=[0]*10
        for j in range(9):
            ch1[a[i][j]]=1
            ch2[a[j][i]]=1
        if sum(ch1)!=9 or sum(ch2)!=9:
            return False

    # 그룹탐색은 4중 for문으로 체크
    for i in range(3):
        for j in range(3):
            ch3=[0]*10
            for k in range(3):
                for s in range(3):
                    ch3[a[i*3+k][j*3+s]]=1
            if sum(ch3)!=9:
                return False
    return True

b=[list(map(int, input().split())) for _ in range(9)]
if check(b):
    print("YES")
else:
    print("NO")
```
```Swift
import Foundation

func check(_ a: [[Int]]) -> Bool {
    
    for i in 0..<9 {
        var ch1 = Array(repeating: 0, count: 10)
        var ch2 = Array(repeating: 0, count: 10)
        for j in 0..<9 {
            ch1[a[i][j]] = 1
            ch2[a[j][i]] = 1
        }
        if ch1.reduce(0, +) != 9 || ch2.reduce(0, +) != 9 {
            return false
        }
    }

    for i in 0..<3 {
        for j in 0..<3 {
            var ch3 = Array(repeating: 0, count: 10)
            for k in 0..<3 {
                for s in 0..<3 {
                    ch3[a[i*3 + k][j*3 + s]] = 1
                }
            }
            if ch3.reduce(0, +) != 9 {
                return false
            }
        }
    }
    return true
}

var board: [[Int]] = []
for _ in 0..<9 {
    if let line = readLine()?.split(separator: " ").map({ Int($0)! }) {
        board.append(line)
    }
}

if check(board) {
    print("YES")
} else {
    print("NO")
}
```

#

### 21. 격자판 회문수
1부터 9까지의 자연수로 채워진 7*7 격자판이 주어지면 격자판 위에서 가로방향 또는 세로방향으로 <br/>
길이 5자리 회문수가 몇 개 있는지 구하는 프로그램을 작성하세요. <br/>
회문수란 121과 같이 앞에서부터 읽으나 뒤에서부터 읽으나 같은 수를 말합니다.<br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/13.png" width="400" height="400"><br/>

빨간색처럼 구부러진 경우(87178)는 회문수로 간주하지 않습니다.<br/>

▣ 입력설명<br/>
1부터 9까지의 자연수로 채워진 7*7격자판이 주어집니다.<br/>

▣ 출력설명<br/>
5자리 회문수의 개수를 출력합니다<br/>

▣ 입력예제<br/>
2 4 1 5 3 2 6 <br/>
3 5 1 8 7 1 7 <br/>
8 3 2 7 1 3 8 <br/>
6 1 2 3 2 1 1 <br/>
1 3 1 3 5 3 2 <br/>
1 1 2 5 6 5 2 <br/>
1 2 2 2 2 1 5 <br/>

▣ 출력예제<br/>
3 <br/>

▣ 풀이로직 <br/>
5개를 보면 되기 때문에 0,1,2까지만 돌면 되는 부분 <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/14.png" width="400" height="400"><br/>


```python
import sys
sys.stdin=open("input.txt", "r")
board=[list(map(int, input().split())) for _ in range(7)]
cnt=0
for i in range(3):
    for j in range(7):
        tmp=board[j][i:i+5]
        if tmp==tmp[::-1]:
            cnt+=1
        for k in range(2):
            if board[i+k][j]!=board[i+5-k-1][j]:
                break;
        else:
            cnt+=1
        
print(cnt)
```
```swift
import Foundation

let board: [[Int]] = (0..<7).map { _ in readLine()!.split(separator: " ").map { Int($0)! } }
var cnt = 0

for i in 0..<3 {
    for j in 0..<7 {
        let tmp = Array(board[j][i..<i+5])
        if tmp == tmp.reversed() {
            cnt += 1
        }

        //5개 이기 때문에 양쪽 두 개만 비교하면 된다!
        for k in 0..<2 {
            if board[i+k][j] != board[i+5-k-1][j] {
                break
            } else {
                cnt += 1
            }
        }
    }
}

print(cnt)
```

#

### 22. 이분검색

임의의 N개의 숫자가 입력으로 주어집니다. <br/>
N개의 수를 오름차순으로 정렬한 다음 N개의 수 중 한 개의 수인 M이 주어지면 이분검색으로 M이 정렬된 상태에서 <br/>
몇 번째에 있는지 구하는 프로그램을 작성하세요. 단 중복값은 존재하지 않습니다. <br/>

▣ 입력설명 <br/>
첫 줄에 한 줄에 자연수 N(3<=N<=1,000,000)과 M이 주어집니다.<br/>
두 번째 줄에 N개의 수가 공백을 사이에 두고 주어집니다.<br/>

▣ 출력설명 <br/>
첫 줄에 정렬 후 M의 값의 위치 번호를 출력한다. <br/>

▣ 입력예제 <br/>
8 32 <br/>
23 87 65 12 57 32 99 81 <br/>

▣ 출력예제 <br/>
3

```python
import sys
sys.stdin=open("input.txt", "r")
n, m=map(int, input().split())
a=list(map(int, input().split()))
a.sort()
lt=0
rt=n-1
while lt<=rt:
    mid=(lt+rt)//2
    if a[mid]==m:
        print(mid+1)
        break
    elif a[mid]>m:
        rt=mid-1
    else:
        lt=mid+1
```
```Swift
import Foundation

let inputs = readLine()!.split(separator: " ").map { Int($0)! }
let n = inputs[0]
let m = inputs[1]

var a = readLine()!.split(separator: " ").map { Int($0)! }
a.sort()

var lt = 0
var rt = n - 1

while lt <= rt {
    let mid = (lt + rt) / 2
    if a[mid] == m {
        print(mid + 1)
        break
    } else if a[mid] > m {
        rt = mid - 1
    } else {
        lt = mid + 1
    }
}
```

#

### 23. 랜선 자르기 (결정 알고리즘)

엘리트 학원은 자체적으로 K개의 랜선을 가지고 있다. <br/>
그러나 K개의 랜선은 길이가 제각각이다. 선생님은 랜선을 모두 N개의 같은 길이의 랜선으로 만들고 싶었기 때문에 <br/>
K개의 랜선을 잘라서 만들어야 한다. <br/>
예를 들어 300cm 짜리 랜선에서 140cm 짜리 랜선을 두 개 잘라내면 20cm 은 버려야 한다. <br/>
(이미 자른 랜선은 붙일 수 없다.) <br/>
편의를 위해 랜선을 자를때 손실되는 길이는 없다고 가정하며, <br/>
기존의 K개의 랜선으로 N개의 랜선을 만들 수 없는 경우는 없다고 가정하자. <br/>
그리고 자를 때는 항상 센티미터 단위로 정수 길이만큼 자른다고 가정하자. <br/>
N개보다 많이 만드는 것도 N개를 만드는 것에 포함된다. <br/>
이때 만들 수 있는 최대 랜선의 길이를 구하는 프로그램을 작성하시오.<br/>

▣ 입력설명 <br/>
첫째 줄에는 엘리트학원이 이미 가지고 있는 랜선의 개수 K, 그리고 필요한 랜선의 개수 N이 입력된다. <br/>
K는 1이상 10,000이하의 정수이고, N은 1이상 1,000,000이하의 정수이다. 그리고 항상 K ≦ N 이다. <br/>
그 후 K줄에 걸쳐 이미 가지고 있는 각 랜선의 길이가 센티미터 단위의 2^31-1이하의 자연수로 주어진다. <br/>

▣ 출력설명 <br/>
첫째 줄에 N개를 만들 수 있는 랜선의 최대 길이를 센티미터 단위의 정수로 출력한다. <br/>

▣ 입력예제 <br/>
4 11  <br/>
802 <br/>
743 <br/>
457 <br/>
539 <br/>

▣ 출력예제 <br/>
200 <br/>

▣ 풀이로직 <br/>
결정알고리즘의 특징은 답이 몇부터 몇사이까지 범위가 있다는 것을 알 수 있다.<br/>
범위를 알기때문에 중앙값을 설정할 수 있고 이분탐색이 가능해짐 <br/>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/15.png" width="400" height="400"><br/>

```python
import sys
sys.stdin=open("input.txt", "r")
def Count(len):
    cnt=0
    for x in Line:
        cnt+=(x//len)
    return cnt

k, n=map(int, input().split())
Line=[]
res=0
largest=0
for i in range(k):
    tmp=int(input())
    Line.append(tmp)
    largest=max(largest, tmp)
lt=1
rt=largest
while lt<=rt:
    mid=(lt+rt)//2
    if Count(mid)>=n:
        res=mid
        lt=mid+1
    else:
        rt=mid-1
print(res)
```
```swift
import Foundation

func count(_ len: Int, _ lines: [Int]) -> Int {
    var cnt = 0
    for line in lines {
        cnt += line / len
    }
    return cnt
}

let inputs = readLine()!.split(separator: " ").map { Int($0)! }
let k = inputs[0]
let n = inputs[1]

var lines: [Int] = []
var largest = 0

for _ in 0..<k {
    let length = Int(readLine()!)!
    lines.append(length)
    largest = max(largest, length)
}

var lt = 1
var rt = largest
var res = 0

while lt <= rt {
    let mid = (lt + rt) / 2
    if count(mid, lines) >= n {
        res = mid
        lt = mid + 1
    } else {
        rt = mid - 1
    }
}

print(res)
```

#

### 24. 뮤직비디오 (결정 알고리즘)

지니레코드에서는 불세출의 가수 조영필의 라이브 동영상을 DVD로 만들어 판매하려 한다. <br/>
DVD에는 총 N개의 곡이 들어가는데, DVD에 녹화할 때에는 라이브에서의 순서가 그대로 유지 되어야 한다. <br/>
순서가 바뀌는 것을 우리의 가수 조영필씨가 매우 싫어한다.<br/>
즉, 1번 노래와 5번 노래를 같은 DVD에 녹화하기 위해서는 
1번과 5번 사이의 모든 노래도 같은 DVD에 녹화해야 한다. <br/>
또한 한 노래를 쪼개서 두 개의 DVD에 녹화하면 안된다. <br/>
지니레코드 입장에서는 이 DVD가 팔릴 것인지 확신할 수 없기 때문에 <br/>
이 사업에 낭비되는 DVD를 가급적 줄이려고 한다. <br/>
고민 끝에 지니레코드는 M개의 DVD에 모든 동영상을 녹화하기 로 하였다. <br/>
이 때 DVD의 크기(녹화 가능한 길이)를 최소로 하려고 한다. <br/> 
그리고 M개의 DVD는 모두 같은 크기여야 제조원가가 적게 들기 때문에 꼭 같은 크기로 해야 한다. <br/>

▣ 입력설명 <br/>
첫째 줄에 자연수 N(1≤N≤1,000), M(1≤M≤N)이 주어진다. <br/>
다음 줄에는 조영필이 라이브에서 부른 순서대로 부른 곡의 길이가 분 단위로(자연수) 주어진다.  <br/>
부른 곡의 길이는 10,000분을 넘지 않는다고 가정하자. <br/>

▣ 출력설명 <br/>
첫 번째 줄부터 DVD의 최소 용량 크기를 출력하세요. <br/>
3개의 DVD용량이 17분짜리이면 (1, 2, 3, 4, 5) (6, 7), (8, 9) 이렇게 3개의 DVD로 녹음을 할 수 있다. <br/> 
17분 용량보다 작은 용량으로는 3개의 DVD에 모든 영상을 녹화할 수 없다. <br/>

▣ 입력예제 <br/>
93 <br/>
1 2 3 4 5 6 7 8 9 <br/>

▣ 출력예제 <br/>
17 <br/>

```python
import sys
sys.stdin=open("input.txt", "r")
def Count(capacity):
    cnt=1
    sum=0
    for x in Music:
        if sum+x>capacity:
            cnt+=1
            sum=x
        else:
            sum+=x
    return cnt

n, m=map(int, input().split())
Music=list(map(int, input().split()))
maxx=max(Music)
lt=1
rt=sum(Music)
res=0
while lt<=rt:
    mid=(lt+rt)//2
    if mid>=maxx and Count(mid)<=m:
        res=mid
        rt=mid-1
    else:
        lt=mid+1
print(res)
```
```Swift
import Foundation

func count(_ capacity: Int, _ music: [Int]) -> Int {
    var cnt = 1
    var sum = 0
    for length in music {
        if sum + length > capacity {
            cnt += 1
            sum = length
        } else {
            sum += length
        }
    }
    return cnt
}

let inputs = readLine()!.split(separator: " ").map { Int($0)! }
let n = inputs[0]
let m = inputs[1]

let music = readLine()!.split(separator: " ").map { Int($0)! }
let maxx = music.max() ?? 0
var lt = 1
var rt = music.reduce(0, +)
var res = 0

while lt <= rt {
    let mid = (lt + rt) / 2
    if mid >= maxx && count(mid, music) <= m {
        res = mid
        rt = mid - 1
    } else {
        lt = mid + 1
    }
}

print(res)
```




