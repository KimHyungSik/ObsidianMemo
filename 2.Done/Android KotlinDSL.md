### 날짜 : 2022-09-27
### 주제 : #Android #gradle #buildSrc #DSL
----
### 정리
Kotlin DSL
- 장점
	- IDE가 지원하는 언어 환경, Kotlin의 경우 IDE가 지원하여 코드 탐색, 자동완성, 편한 변수 사용이 가능하다
	- 멀티모듈 사용시 의존성 관리가 편해진다
- 단점
	- Groovy DSL보다 느림
	- 새로운 라이브러리 및 안드로이드 프레임워크 도입시 불편하거나 미지원
buildSrc
>Gradle이 수행되면 buildSrc 디렉터리가 존재하는지 체크한다.  
이 경우 Gradle은 자동적으로 코드를 컴파일하고 테스트한 뒤 당신의 빌드 스크립트의 classpath에 넣는다.  
이 방법은 유지 보수, 리팩터링 및 코드 테스트가 더 쉽다.

KotlinDSL사용해보기
Android Directory에 buildSrc 파일을 생성하고 build.gradle.kts파일을 생성한다. build.gradle.kts파일에  kotlinDSL을 사용 할 것을 작성하면 Gradle이 buildSrc의 buildgradle.kts 파일을 검사하여 스크립트를 생성한다. 
```kotlin
plugins {
    `kotlin-dsl`

repositories {
    google()
    mavenCentral()
}
```
파일 생성이 끝났다면 gradle Sncy하면 Gradle이 동작하면서 buildSrc파일에 추가로 필요한 파일을 생성한다.(`build`, `.gradle` 등) 파일 생성이 완료 되었다면 의존성 및 안드로이드 설정을 관리할 파일을 만들어 준다. build/src/main/kotlin/ Directory에 정의 한다.
```Kotlin
object Dependency {  
    object Kotlin{  
        const val SDK = "org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.6.10"  
    }  
    object AndroidX{  
        const val activityCompose = "androidx.activity:activity-compose:1.3.1"  
        const val lifecycle = "androidx.lifecycle:lifecycle-runtime-ktx:2.3.1"  
        object Compose{  
            const val version = "1.1.0"  
            const val ui = "androidx.compose.ui:ui:$version"  
            const val material = "androidx.compose.material:material:$version"  
            const val preview = "androidx.compose.ui:ui-tooling-preview:$version"  
        }  
    }    object KTX{  
        const val core = "androidx.core:core-ktx:1.7.0"  
    }  
    object Test{  
        const val junit = "junit:junit:4.13.2"  
        const val ext = "androidx.test.ext:junit:1.1.3"  
        const val espresso = "androidx.test.espresso:espresso-core:3.4.0"  
        object Compose{  
            const val uiTestJunit4 = "androidx.compose.ui:ui-test-junit4:$version"  
            const val uiTooling = "androidx.compose.ui:ui-tooling:$version"  
            const val uiTestManifest = "androidx.compose.ui:ui-test-manifest:$version"  
        }  
    }
}
```

Module수준의 build.gradle을 build.gradle.kts로 변경하고 위에서 정의한 내용과 함께 Kotlin스럽게 변경한다.  '의 경우 "로 변경하고 =추가 ()를 추가하는 등의 변화가 있다.
```Kotlin
plugins {  
    id ("com.android.application")  
    id ("org.jetbrains.kotlin.android")  
}  
  
android {  
    compileSdk = Android.compileSdk  
  
    defaultConfig {  
        applicationId = "com.example.catdogapp"  
        minSdk = Android.midSdk  
        targetSdk = Android.targetSdk  
        versionCode = Android.versionCode  
        versionName = Android.versionName  
  
        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"  
  
    }  
  
    buildTypes {  
        getByName("release") {  
            isMinifyEnabled = false  
            proguardFiles(getDefaultProguardFile("proguard-android.txt"), "proguard-rules.pro")  
        }    }    compileOptions {  
        sourceCompatibility = JavaVersion.VERSION_1_8  
        targetCompatibility = JavaVersion.VERSION_1_8  
    }    kotlinOptions {  
        jvmTarget = "1.8"  
    }  
    buildFeatures {  
        compose = true  
    }  
    composeOptions {  
        kotlinCompilerExtensionVersion = Dependency.AndroidX.Compose.version  
    }  
}  
  
dependencies {  
  
    implementation(Dependency.Kotlin.SDK)  
    implementation(Dependency.KTX.core)  
    implementation(Dependency.AndroidX.Compose.ui)  
    implementation(Dependency.AndroidX.Compose.material)  
    implementation(Dependency.AndroidX.Compose.preview)  
    implementation(Dependency.AndroidX.activityCompose)  
    implementation(Dependency.AndroidX.lifecycle)  
  
    testImplementation(Dependency.Test.junit)  
    androidTestImplementation(Dependency.Test.ext)  
    androidTestImplementation(Dependency.Test.espresso)  
  
    androidTestImplementation(Dependency.Test.Compose.uiTestJunit4)  
    debugImplementation(Dependency.Test.Compose.uiTooling)  
    debugImplementation(Dependency.Test.Compose.uiTestManifest)  
}
```
### 참고
- [Kotlin DSL + buildSrc으로 의존성 관리](https://beomseok95.tistory.com/367)
- [# [Android] 멀티모듈에서 buildSrc + Kotlin DSL로 Dependency 관리하기](https://velog.io/@yuuuzzzin/Android-buildSrc-Kotlin-DSL%EB%A1%9C-Dependency-%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0)
- [Gradle](https://docs.gradle.org/current/userguide/migrating_from_groovy_to_kotlin_dsl.html)
- [Android Developer](https://docs.gradle.org/current/userguide/migrating_from_groovy_to_kotlin_dsl.html)
### 연결된 메모
- 