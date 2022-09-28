### 날짜 : 2022-09-28
### 주제 : #DI #Dagger
----
### 정리
먼저 Module코드를 살펴보면 Integer를 삽입하면서 print를 찍어주는 동작을 수 행하여 언제 동작이 수행하게 되는지 알 수 있다.
```Java
  @Module
   final class CounterModule {
     int next = 100;

      @Provides Integer provideInteger() {
       System.out.println("computing...");
       return next++;
     }
   }
 
```

다음으로 `CounterModuel`을 사용하는 class를 만들어 보겠습니다. print함수를 이용해서 Module의 생성 시간과 print메서드의 호출 타이밍을 확인해보겠습니다.
```Java
 final class DirectCounter {
      @Inject Integer value;

     void print() {
       System.out.println("printing...");
       System.out.println(value);
       System.out.println(value);
       System.out.println(value);
     }
   }
```
```
 결과
 computing...
   printing...
   100
   100
   100
```

Module이 먼저 생성되고 printing메서드가 호출 되는걸 확인 할 수 있습니다. 결과적으로 문제는 안돼지만 경우에 따라서는 class시작시가 아닌 Module을 사용하기 전에 생성하고 사용하고 싶을 수 있습니다. 그럴때는 `Provider`, `Lazy`를 고려해 볼 수 있습니다.

Provider를 사용하게 되면  `.get()`으로 가져올수 있습니다. 결과를 확인해 보면 `.get()`으로 가져올때마다 객체가 새로 생성되는 것 을 확인해볼 수 있습니다.
```Java
   final class ProviderCounter {
      @Inject Provider<Integer> provider;

     void print() {
       System.out.println("printing...");
       System.out.println(provider.get().value);
       System.out.println(provider.get().value);
       System.out.println(provider.get().value);
     }
   }
```
```
   printing...
   computing...
   100
   computing...
   101
   computing...
   102
```

Lazt를 사용하게 되면 Provider와 사용방법은 같지만 동작 방식에서 차이를 볼 수 있습니다. 결과를 확인해 보면 `.get()`을 사용할때 생성하지만 이후에 사용할때는 객체를 다시 생성하지 않는것을 볼수 있다.
```Java
   final class LazyCounter {
      @Inject Lazy<Integer> lazy;

     void print() {
       System.out.println("printing...");
       System.out.println(lazy.get());
       System.out.println(lazy.get());
       System.out.println(lazy.get());
     }
   }
```
```
   printing...
   computing...
   100
   100
   100
```

하지만 여기서 헷갈리면 안돼는것이 하나 있다. lazy로 생성된 객체를 계속 사용하지만 Singleton은 아니라는 점이다. Lazy로 같은 객체를 두개 주입 받게 되면 두개는 다른 객체이다.

### 참고 자료
- [dagger.dev](https://dagger.dev/api/2.13/dagger/Lazy.html)

### 연관된 기술
- [[Dagger]]
