### 날짜 : 2022-08-12
### 주제 : #Flutter #StateManagment #Provider
----
### 정리
Provider란  Flutter의 상태 관리 방법이다.
라이브러리 설치 방법
```shell
$ flutter pub add provider
```
```yaml
dependencies:
  provider: ^6.0.3
```

Flutter에서 Provider를 사용하기 위해서는 먼저 `ChangeNotifier`를 확장하는 class를 생성해야한다. 생성한 클래스에서 관찰할 데이터와 데이터를 변경시키는 함수도 구현하여 View에서 데이터를변경, 옵저빙하여 화면을 다시 그릴 수 있도록 구현해야 한다. 예제로 카운트와 카운트를 증가시키는 동작을 구현 하였다. 추가적으로 데이터가 변경 되었다면 `notifyListeners()`를 호출하여 데이터 변경 되었음을 구독자에게 알려 주어야 한다.

```Dart
class ViewModel extendsChangeNotifier{
	int _count = 0;

	int get count => _count;

	void countUp() {
	    _count++;
		notifyListeners();
	}
}
```

### 참고
- [Pub.dev](https://pub.dev/packages/provider)

### 연결된 메모
- [[Flutter Provider Selector]]