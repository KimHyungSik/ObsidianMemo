### 날짜 : 2024-05-02
### 주제 : #Dart #part
----
### 정리
Dart 에서 파일을 분리할때 사용한다

```dart
// main.dart

void partOne(){
	print("part One")
}

void partTwo(){
	print("part Two")
}

void main(){
	partOne()
	partTwo()
}
```

```dart
// part1.dart
void partOne(){
	print("part One")
}

// part2.dart
void partTwo(){
	print("part Two")
}

// main.dart


void main(){
	partOne()
	partTwo()
}

```
### 참고
- 

### 연결된 메모
- 