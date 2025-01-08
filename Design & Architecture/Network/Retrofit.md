## Retrofit
**서버와 클라이언트 간 http 통신**을 위한 라이브러리이다. OkHttp 라이브러리를 기반으로 한다.

Retrofit을 사용하면 REST 기반의 웹 서비스를 통해 JSON 구조의 데이터를 쉽게 가져오고 업로드 가능하다.

## Retrofit을 사용하기 위한 세 가지 클래스
+ **Data class**
+ Http를 정의하는 **Interface**
+ Retrofit.Builder를 선언하는 **Obejct**

## @Field, @Body, @Query, @Path

+ ```@Field``` : @FormUrlEncoded 어노테이션을 사용해서 파라미터를 전달하는데, key=value&key=value의 형태로 전달된다
+ ```@Body``` : JSON 형태의 하나의 객체만 제공한다(key: value, key: value)
+ ```@Query``` : Query Parameter를 명시한다
+ ```@Path``` : Path Parameter를 명시한다

## Query Parameter
URL 뒤에 전달되어야 하는 key-value 형식의 파라미터이다\
 URL 끝에는 '?'가 추가되는데, ? 기호는 경로 및 Query parameter를 구분하는 기준이 된다.\
 여러개의 Query parameter를 추가를 해야하면 '&' 기호를 파라미터 사이에 배치한다.
```kotlin
GET /users?id=1234&pw=***
```
```kotlin
 // @Query 어노테이션 사용
@GET("user")
fun getUserOuth(
    @Query("id") user_id: String,
    @Query("pw") user_pw: String
):Call<UserCredentail>
```