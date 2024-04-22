### 날짜 : 2024-04-22
### 주제 : 
----
### 정리
```dart
class A {
	void a() {}
}
class A2 {}

mixin A3 {}
mixin A3on {}
mixin A4 on A2 {}

class B extends A with A3,A3on {}
class C implements A, A2 {
	@override
	void a() {}
}
class D extends A with A3 implements A2 {}
class E extends A2 with A4 {}
```
dart에서는 extends을 통한 다중상속을 지원하지 않는다. 
extends - 상속
implements - 상속, 내부요소를 모두 override 해야한다.
mixin - 생성자가 없는 class 로 만들어 주며 with 를 통해 다중 상속이 가능하다록 한다.
on - mixin A on B 처럼 작성하면 A를 상속하기 위해서는 반드시 B를 상속해야한다.

### 연결된 메모
- 