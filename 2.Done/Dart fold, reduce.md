### 날짜 : 2022-08-18
### 주제 : #Dart #List #Map
----
### 정리
flod의 사용 법
```dart
_productsInCart.values.fold(0, (accumulator, value){
	return accumulator + value;
});
```
flod(시작할 값, 이전에 리턴한 값, 이번 값)

reduce에서는 0이 생략 가능 하다

reduce의 경우에는 리스트의 타입만 반환 가능하며 fold의 경우 원하는 타입으로 반환이 가능 하다.
### 참고


### 연결된 메모
- 