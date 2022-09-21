### 날짜 : 2022-09-20
### 주제 : 
----
### 정리
Json 
장점
- readable: 텍스트로 되어 있어 언제든지 일을수 있다.
- extensible: Json은 확장이 쉽다.
단정
- expensive: 직렬화, 역직렬화 시 비용이 클 수 있다.
- unclear types: 텍스트로 이루어 져있어 타입이 불분명 하다.
- massive: 필요한 데이터의 크기에 비해 크기가 크다

Protobuf
- schema를 미리 선언해두고 이 객체로 인코더와 디코더를 하여 proto 파일을 가져올 수 있다. 그래서 데이터를 보낼 때 Json처럼 데이터의 네이밍이 필요하지 않다. 추가적으로 schema를 선언할 때 타입도 선언 가능하다.

### 참고
- [[Json 및 Protobuf]](https://www.youtube.com/watch?v=uGYZn6xk-hA)
- [protobuf-gradle-plugin](https://github.com/google/protobuf-gradle-plugin)

### 연결된 메모
- 