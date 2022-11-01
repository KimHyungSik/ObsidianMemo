### 날짜 : 2022-11-01
### 주제 : #Reflection #Annotations 
----
### 정리
리플렉션이란 런타임에 클래스의 구조를 조사, 분석하는 방법을 이야기 한다. Java와 다르게 Kotlin에서는 리플렉션을 위한 라이브러리가 필요하다. 

```gradle
implementation "org.jetbrains.kotlin:kotlin-reflect:<version>"
```

런타임에 Kotlin의 class를 분석하기 위해서는 `KClass<*>` 로 class를 표현하여 사용해야한다. `KClass<*>`로 캐스팅하는 방법은 'ClassNam::class'로 표현 가능하다.

### class 분석
```Kotlin
data::class.apply {  
    println(isAbstract)  
    println(isCompanion)  
    println(isOpen)  
    println(isData)  
    println(isFinal)  
    println(isInner)  
    println(isSealed)  
}
```

### 참고
- 

### 연결된 메모
- [[Android Annotations]]