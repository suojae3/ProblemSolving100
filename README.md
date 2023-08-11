# ProblemSolving100

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=250&section=header&text=Problem%20Solving%20100&fontSize=40&animation=fadeIn&fontAlign=25&fontAlignY=40)


<br/>

---

### 01. K번째 약수

두 개의 자연수 N과 K가 주어졌을 때, N의 약수들 중 K번째로 작은 수를 출력하는 프로그램을 작성하시오.

▣ 입력설명
첫째 줄에 N과 K가 빈칸을 사이에 두고 주어진다. N은 1 이상 10,000 이하이다. K는 1 이상 N 이하이다.

▣ 출력설명
첫째 줄에 N의 약수들 중 K번째로 작은 수를 출력한다. 만일 N의 약수의 개수가 K개보다 적어서 K번째 약수가 존재하지 않을 경우에는 -1을 출력하시오.

▣ 입력예제 6 3
▣ 출력예제 3

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

// Read the input values
let input = readLine()!.split(separator: " ").map { Int($0)! }
let (n, k) = (input[0], input[1])

var cnt = 0

for i in 1...n {
    if n % i == 0 {
        cnt += 1
    }
    if cnt == k {
        print(i)
        exit(0)  // Exit the program once the kth divisor is found
    }
}

// If the loop completes without finding the kth divisor, print -1
print(-1)
```

#

### 02. 


