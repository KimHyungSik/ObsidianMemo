### 날짜 : 2024-05-02
### 주제 : #Dart #part
----
### 정리
Dart 에서 파일을 분리할때 사용한다. 
기준이 되는 파일을 library로 설정하고 분활되는 파일들에 library 파일명으로 part of(이 파일의 분리된 것) 선언한다. part 로 기존의 파일에서 호출하여 사용하다.

```dart
// main.dart

void partOne(){
	print("part One");
}

void partTwo(){
	print("part Two");
}

void main(){
	partOne();
	partTwo();
}
```

```dart
// part1.dart
part of main;

void partOne(){
	print("part One");
}

// part2.dart
part of main;

void partTwo(){
	print("part Two");
}

// main.dart
library main;

part 'part1.dart';
part 'part2.dart';

void main(){
	partOne();
	partTwo();
}

```
### 참고
- 

### 연결된 메모
- 