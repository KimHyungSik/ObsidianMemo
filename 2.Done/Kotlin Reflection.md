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
    println(isAbstract)  // abstract인지 확인
    println(isCompanion) // compaion인지 확인
    println(isOpen)      // open class 인지 확인
    println(isData)      // data class 인지 확인
    println(isFinal)     // Finnal로 선언되었는지 확인
    println(isInner)     // inner class인지 확인
    println(isSealed)    // sealed class 인지 확인

	println(primaryConstructor) // 주생성자 정보
	println(constructors)  //모든 생성자 정보
	constructors  
	    .first()  
	    .parameters        // 생성자 파라미터 정보
		    .forEach {  
			    println(it.name + " : " + it.type)  
			}

	println(declaredMemberProperties)         // 확장 프로퍼티를 제외한 클래스에 선언된 모든 프로퍼티
	println(memberProperties)                 // 확장 프로퍼티를 제외한 클래스와 상위 클래스의 모든 프로퍼티
	println(declaredMemberExtensionProperties)// 클래스에 선언된 확장 프로퍼티
	
	println(declaredFunctions)                // 확장 함수를 제외한 클래스에 선언된 함수 정보
	println(memberFunctions)                  // 확장 함수를 제외한 클래스와 상위 클래스에 정의된 함수
	println(declaredMemberExtensionFunctions) // 확장 함수 정보
}
```

## Class Properties 분석
```Kotlin
data::class.memberProperties  
    .first()  
    .apply {  
        println(name)               // property 이름
        println(returnType)         // property 타입
        println(isAccessible)       // property public 여부
        if(!isAccessible) isAccessible = true  
        println(getter.call(data))  // property value
        println(annotations)        // property의 어노테이션
    }
```
여기서 프로퍼티의 어노테이션을 알아 낼 수 있기 때문에 어노테이션 사용 시 Reflection을 이용하여 어노테이션 별 동작을 구현할 수 있다.

### 참고
- 

### 연결된 메모
- [[Android Annotations]]