## 코루틴
코루틴은 비동기적으로 실행되는 코드를 간소화하기 위해 Android에서 사용할 수 있는 동시 실행 설계 패턴이다.

## 기능
+ **경량**: 코루틴을 실행 중인 스레드를 차단하지 않는 정지를 지원하므로 단일 스레드에서 많은 코루틴을 실행할 수 있다. 정지는 많은 동시 작업을 지원하면서도 차단보다 메모리를 절약한다.

+ **메모리 누수 감소**: 구조화된 동시 실행 범위 내에서 작업을 실행할 수 있다.

+ **내장된 취소 지원**: 취소 실행 중인 코루틴 계층 구조를 통해 자동으로 전파된다.

+ **Jetpack 통합**: 많은 Jetpack 라이브러리에 코루틴을 완전히 지원하는 확장 프로그램이 포함되어 있다. 일부 라이브러리는 구조화된 동시 실행에 사용할 수 있는 자체 코루틴 범위도 제공한다.

### 종속 항목
코루틴을 사용하려면 앱의 build.gradle 파일에 종속 항목을 추가해야한다.
```kotlin
dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.3.9")
} 
```
## 코루틴 동작 과정
​
코루틴은 비동기 작업을 '일시 중단'과 '재개'라는 간단한 원리로 처리한다.
​
-   suspend 함수: suspend 키워드가 붙은 함수는 코루틴 내에서만 호출 가능하며, 코루틴을 일시 중단시킬 수 있다. 네트워크 요청 등 시간이 걸리는 작업은 보통 suspend 함수로 제공된다.
-   코루틴 빌더: 코루틴을 시작하는 방법이다. launch는 결과를 반환하지 않는 코루틴을, async는 결과를 반환하는 코루틴을 실행한다.
    
    ```
    // launch 사용 예시
    fun fetchData() = runBlocking {
    launch {
        // 네트워크 요청
        delay(2000) // 2초 대기 시뮬레이션
        println("데이터 요청 완료")
        }
    }
    ```
-   코루틴 스코프: 코루틴을 관리하는 영역이다. 코루틴 스코프를 사용하면 코루틴의 생명주기를 쉽게 관리하고, 메모리 누수를 방지할 수 있다.  
+  ex) 안드로이드에서는 ViewModelScope를 이용하여 뷰모델의 생명주기에 맞춰 코루틴을 관리할 수 있다.

## 코루틴 예외 처리
코루틴에서 발생하는 에러는 ```try-catch``` 블록으로 처리할 수 있다. 코루틴 스코프의``` CoroutineExceptionHandler```를 사용하면 모든 코루틴에서 발생하는 예외를 한 번에 처리할 수도 있다.
```kotlin
class LoginViewModel(
    private val loginRepository: LoginRepository
): ViewModel() {

    fun login(username: String, token: String) {
        viewModelScope.launch {
            val jsonBody = "{ username: \"$username\", token: \"$token\"}"
            val result = try {
                loginRepository.makeLoginRequest(jsonBody)
            } catch(e: Exception) {
                Result.Error(Exception("Network request failed"))
            }
            when (result) {
                is Result.Success<LoginResponse> -> // Happy path
                else -> // Show error in UI
            }
        }
    }
}
```

## 코루틴 사용시 주의점

-   무분별한 코루틴 생성은 성능 저하를 유발할 수 있다.
-   코루틴 스코프를 적절히 사용하여 메모리 누수를 방지해야 한다.
-   UI 스레드에서 시간이 오래 걸리는 작업을 실행하지 않도록 주의해야 한다.