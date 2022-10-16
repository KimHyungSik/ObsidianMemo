### 날짜 : 2022-10-07
### 주제 : #Android #MethodCount #Dex #MultiDex
----
### 정리
안드로이드 프로젝트가 커지면서 메소드가 많아지게 되고 하나의 Dex파일의 용량(65,536개)을 초과하게되고 method count와 관련된 에러 메시지를 만날 수 있게된다. 메소드 갯수가 많이지고 하나의 Dex파일로 처리가 불과하게 되면 Dex파일을 로드할 수 있도록 Multi Dex설정을 해야한다.

### Android 5.0 미만 멀티덱스 설정
Android 5.0(API 수준 21) 이전의 플랫폼 버전에서는 앱 코드 실행을 위해 Dalvik 런타임을 사용합니다. Dalvik에서는 APK당 하나의 `classes.dex` 바이트 코드 파일로 앱을 제한합니다.  멀티덱스 라이브러리를 모듈 수준 `build.gradle` 파일에 추가할 수 있습니다.

```Kotlin 
dependencies {    
val multidex_version = "2.0.1"    implementation("androidx.multidex:multidex:$multidex_version")  

//AndroidX를 사용하지 않는 경우 다음의 지원 중단된 지원 라이브러리 종속 항목을 대신 추가합니다.
implementation("com.android.support:multidex:1.0.3")
}
```


### Android 5.0 이상에서 멀티덱스 지원
Android 5.0(API 수준 21) 이상에서는 ART라는 런타임을 사용합니다. APK 파일에서 여러 개의 DEX 파일을 로드하는 것을 지원합니다. `minSdkVersion`이 21 이상이라면 멀티덱스가 기본적으로 사용 설정되며 멀티덱스 라이브러리가 필요하지 않습니다.

### 참고
- [Android Developrt](https://developer.android.com/studio/build/multidex?hl=ko)

### 연결된 메모
- 