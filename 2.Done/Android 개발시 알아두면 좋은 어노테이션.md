### 날짜 : 2022-11-01
### 주제 : #Android #Annotations
----
### 정리
### Resource annotations
Annotaion Resource Type에 맞지 않는 Resource Type이 들어올 경우 경고를 통해 알려주기에 개발자가 실수를 줄일 수 있습니다.
-   @AnyRes: R 타입의 리소스(모든 타입의 리소스)
-   @AnimationRes : animator 리소스 참조
-   @AnimRes : anim 리소스 참조
-   @ArrayRes : 배열 타입의 리소스 참조
-   @AttrRes : attribute 리소스 참조
-   @BoolRes : boolean 리소스 참조
-   @ColorRes : color 리소스 참조
-   @DimenRes : dimen 리소스 참조
-   @DrawableRes : drawable 리소스 참조
-   @FontRes : font 리소스 참조
-   @IdRes : id 리소스 참조
-   @IntegerRes : integer 리소스 참조
-   @IntegerpolatorRes : interpolator 리소스 참조
-   @LayoutRes : layout 리소스 참조
-   @MenuRes : menu 리소스 참조
-   @NavigationRes : navigation 리소스 참조
-   @PluralRes : plurals(개수에 따른 문자열 표현) 리소스 참조
-   @RawRes : raw(원본 리소스 : txt, 음악 파일 등) 리소스 참조
-   @StringRes : string 리소스 참조
-   @StyleRes : style 리소스 참조
-   @TransitionRes : transition(전환 애니메이션 효과) 리소스 참조
-   @XmlRes : XML 리소스 참조

### Thread annotations
thread annotation이 클래스에 붙는다면 해당 클래스의 모든 메소드들은 해당 스레드에서만 호출할 수 있습니다.
-   @MainThread : 메소드는 main thread 에서만 호출이 가능합니다.
-   @UiThread : 메소드나 생성자는 ui thread 에서만 호출이 가능합니다.
-   @WorkerThread : 메소드는 worker thread 에서만 호출이 가능합니다.
-   @BinderThread : 메소드는 binder thread 에서만 호출이 가능합니다.
-   @AnyTherad : 메소드는 모든 thread 에서 호출이 가능합니다.

### Value constraint annotations
사용자가 범위를 잘못 알 수 있는 파라미터에 적용할 때 유용합니다.
-   @IntRange : integer, long 타입의 변수의 값을 특정한 범위로 제한합니다.
	- @IntRange(from = 0) : 0 보다 크면 된다.
-   @FloatRange : float, double 타입의 변수의 값을 특정한 범위로 제한합니다.
-   @Size : 문자열의 길이 또는 collection, array의 크기를 해당 어노테이션에 지정된 값으로 제한합니다. 즉, 연결된요소가 주어진 크기 또는 길이를 가져야 함을 나타냅니다.

### Return value annotations
-  @CheckResult : 해당 어노테이션이 붙은 메소드가 리턴한 결과를 개발자가 사용하지 않았으면 경고를 나타냅니다.

- @CallSuper : 이 어노테이션이 붙은 메서드를 하위 클래스에서 오버라이드 할 땐 반드시 상위 클래스의 메서드를 호출하도록 강제함을 나타냅니다. 

@Supperss : 해당하는 린트검사를 무시 한다.

### 참고 자료
- [개발에 도움을 주는 어노테이션](https://velog.io/@changhee09/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-%EC%96%B4%EB%85%B8%ED%85%8C%EC%9D%B4%EC%85%98-%EC%82%AC%EC%9A%A9)

### 연관된 기술
- [[Android Annotations]]