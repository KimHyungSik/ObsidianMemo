### 날짜 : 2022-10-12
### 주제 : #WeakRefernce #SoftReference #Memory
----
### 정리
GC가 메모리를 확보하기 위해 쓰레기 취급하는 우선 순위

WeakReference > SoftReference > StrongReference

WeakReference, SoftReference 사용 방법
```Kotlin
data class A(  
    val a : String  
)  
  
fun main() {  
    val aSoft = SoftReference(A("abc"))  
    val aWeak = WeakReference(A("abc"))  

	// get()으로 가져오고 GC에 의해 처리되었을 수 도있기 때문에 nullable하다
    println(aSoft.get()?.a)  
    println(aWeak.get()?.a)  
}
```

### WeakReference
-   GC가 언제든지 쓰레기 취급 할 수 있는 Reference
-   WeakReference(Object())

### SoftReference
-   GC가 OOM 직전 일 경우, 쓰레기 취급해버리는 Reference
-   SoftReference(Object())
- 
### StrongReference
-   GC가 처리 하지 않는 Reference
-   null 처리로 GC에 알려주는 게 메모리 누수 좋음
-   New Object()

### 참고 자료
- [Medium](https://medium.com/@logishudson0218/weakreference-softreference-strongreference-c4dee86317c)
- [stack overflow](https://stackoverflow.com/questions/299659/whats-the-difference-between-softreference-and-weakreference-in-java)

### 연관된 기술
- 