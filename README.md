# ProblemSolving100

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=250&section=header&text=Problem%20Solving%20100&fontSize=40&animation=fadeIn&fontAlign=25&fontAlignY=40)


<br/>

---

### 01. K번째 약수

&nbsp;&nbsp;&nbsp;&nbsp;<image src="img/1.png" width="400" height="200"><br/>

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


```

#

### 02. 


