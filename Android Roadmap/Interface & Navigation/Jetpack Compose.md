## Jetpack Compose
Jetpack Compose는 네이티브 Android UI를 구축하기 위한 툴킷(toolkit)
+ Kotlin API로 Android에서의 UI 개발을 간소화하고 가속화하여 앱에 생동감을 더해준다

## 사용해야 하는 이유
1. 간단한 코드
2. 직관적임
3. 빠른 개발 과정
4. 강력한 성능

## 예제
```kotlin
@Composable <- 이렇게 @Composable을 써줘야 한다.
fun SignUp1(
    modifier: Modifier = Modifier
) {
    Column(
        modifier = modifier
            .fillMaxSize()
            .background(Color.White),
    )
```