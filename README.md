# ProblemSolving100

![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=250&section=header&text=Problem%20Solving%20100&fontSize=60&animation=fadeIn&fontAlign=35&fontAlignY=35)


<br/>

---

### 04. [백준 1920] 수찾기


&nbsp;&nbsp;&nbsp;&nbsp;<img src="image/01.png" width="400" height="200"><br/>



```dart
import 'dart:io';

void main() {
  stdin.readLineSync(); // Discard the first line

  // Parse the second line into a list of integers
  List<int> inputList = stdin.readLineSync()!.split(" ").map((str) => int.parse(str)).toList();
  stdin.readLineSync(); // Discard the third line

  // Parse the fourth line into a list of integers
  List<int> checkList = stdin.readLineSync()!.split(" ").map((str) => int.parse(str)).toList();
  List<int> answerList = []; // This will hold your answers

  // Compare each element of checkList to the elements of inputList
  for (int checkValue in checkList) {
    if (inputList.contains(checkValue)) {
      answerList.add(1); // If the value is in the list, add 1 to the answerList
    } else {
      answerList.add(0); // If the value is not in the list, add 0 to the answerList
    }
  }

  // Output the answerList
  for (int answer in answerList) {
    print(answer);
  }
}
```

```swift

```
- 풀이 로직 <br/>
1. 
