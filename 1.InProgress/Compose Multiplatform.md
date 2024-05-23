### 날짜 : 2024-05-21
### 주제 :
----
### 정리
 [Kotlin Multiplatform wizard](https://kmp.jetbrains.com/?_gl=1*1myn6e7*_ga*MjA1NDg5MDI2OC4xNjYzNTE3Mzc2*_ga_9J976DJZ68*MTcxNjI5MjE5OS4xNi4xLjE3MTYyOTMwOTQuNTQuMC4w&_ga=2.102840132.597063886.1716292199-2054890268.1663517376).
 
- _composeApp_ is a Kotlin module that contains the logic shared among the Android, desktop, iOS, and web applications – the code you use for all the platforms. It uses [Gradle](https://kotlinlang.org/docs/gradle.html) as the build system that helps you automate your build process.
    
- _iosApp_ is an Xcode project that builds into an iOS application. It depends on and uses the shared module as an iOS framework.

### 참고
- https://www.jetbrains.com/help/kotlin-multiplatform-dev/compose-multiplatform-create-first-app.html#examine-the-project-structure
- coil: https://velog.io/@mraz3068/How-to-load-Network-Image-by-Coil-in-Compose-Multiplatform

### 연결된 메모
- 