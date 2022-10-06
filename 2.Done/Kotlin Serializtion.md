### 날짜 : 2022-10-07
### 주제 : #Kotlin #Serializtion
----
### 정리
기존에는 Java의 Serialization또는 , Gson, Moshi 등을 사용하여 직렬화 또는 역직렬화를 사용해 왔다. 하지만 이모두 Java 언어로 개발되어있어 Kotlin환경에서는 완벽하게 호환되지 않는다. 예를 들어 Kotlin data class를 사용할 때 기본값을 정해 줄 수 있다. 하지만 Java에서는이 동작을 지원하지 않고 있기 때문에 Gson이나 Moshi를 통해 직렬화 하게 된다면 호환되지 않는걸 확인할 수 있다.
```Kotlin
data class User (
    val name: String,
    val email: String,
    val age: Int = 25 // default value
)

fun main() {
    val jsonString = """
            {
                "name" : "KimHyoungSik",
                "email" : "Sikham@socar.com"
            }
        """.trimIndent()
 
    val user = Gson().fromJson(jsonString, User::class.java)
 
    println(user)
}

// 결과 User(name=KimHyoungSik, email=Sikham@socar.com, age=0) age가 25로 초기화 되지 않음
```

Kotlin에서 공식적으로 지원하는 Kotlin Serializtion을 사용한다면이 문제를 해결할 수 있습니다.
Json, Protocol buffers, CBOR등 다양한 직렬화 라이버리를 지원하고 있습니다.
Kotlin Serializtion을 사용하기 위해서먼저 Dependencies를 선언해야합니다.
```Groovy
build.gradle(Project)
plugins { 
	id 'org.jetbrains.kotlin.jvm' version '1.7.20' 
	id 'org.jetbrains.kotlin.plugin.serialization' version '1.7.20' 
}

build.gradle(Module)
dependencies { 
	// Json을 사용하기 위해 json lib를 설치 하였다
	implementation 'org.jetbrains.kotlinx:kotlinx-serialization-json:1.4.0' 
}
```

이후 직렬화할 객체에 `@Serializable` 어노테이션을 등록하여 사용할 수 있다.`Json.encodeToString()` 메서드를 통해서 객체를 Json형태의 String으로 직렬화 할 수 있다. 반대로는 `decondeFromString<T>()`메서드를 통해 String형태의 Json을 다시 객체로 변화 가능하다.
```Kotlin
import kotlinx.serialization.Serializable 

@Serializable 
data class Data(val a: Int, val b: String)

fun main() {
   val json = Json.encodeToString(Data(42, "str"))
   val dataList = listOf(Data(42, "str"), Data(12, "test")) 
   val jsonList = Json.encodeToString(dataList)
}

val obj = Json.decodeFromString<Data>("""{"a":42, "b": "str"}""")

```
### 참고
- [Kotlin](https://kotlinlang.org/docs/serialization.html)

### 연결된 메모
- 