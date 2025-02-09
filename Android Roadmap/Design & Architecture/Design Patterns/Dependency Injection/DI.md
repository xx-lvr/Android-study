## DI
클래스 또는 객체가 필요로 하는 의존성(Dependency)을 직접 생성하거나 관리하는 대신, 외부로부터 제공받는 디자인 패턴
+ 핵심은 **의존성을 주입받는다는 것**이다. 객체가 스스로 의존성을 만들거나 찾지 않고, 외부에서 제공받는다.
+ DI는 **SOLID 원칙 중 D (Dependency Inversion Principle, 의존성 역전 원칙)** 를 따르는 디자인 패턴이다.

## DI 사용 장점
+ 코드의 재사용 및 의존성 분리 -> 클래스 간의 결합도를 줄임
+ 리팩토링이 수월함
+ 테스트 편의성 -> 클래스가 의존성을 관리하지 않으므로 테스트를 더 쉽게 수행할 수 있음

## Android Di 실행 방법
+ Constructor Injection(생성자 주입)
+ Field Injection(필드 주입)
+ Method Injection(메소드 주입) -> Compose에서는 사용 빈도가 낮음

## 예시
```kotlin
class Car(private val engine: Engine) { // 생성자를 통해 Engine 객체 주입
    fun start() {
        engine.start()
    }
}

fun main(args: Array<String>) {
    val engine = Engine() // Engine 객체 생성
    val car = Car(engine) // Car 객체 생성 시 Engine 객체 주입
    car.start() // Car 객체의 start() 메서드 호출
}
// Constructor Injection(생성자 주입)
// Car 클래스는 생성자를 통해 Engine 객체를 주입받는다
```

## DI 라이브러리(DI 컨테이너)
+ Dagger/Hilt: 컴파일 시점에 의존성 그래프를 생성하여 런타임 성능이 우수하다. Hilt는 Dagger를 Android 환경에 맞춰 더 쉽게 사용할 수 있도록 Google에서 제공하는 라이브러리이다. Compose UI에서 Hilt를 사용하려면 hiltViewModel() 함수를 활용한다.
+ Koin: Kotlin으로 작성된 경량 DI 프레임워크로, DSL을 사용하여 의존성을 정의하고 주입한다. Compose UI에서 Koin을 사용하려면 getViewModel() 함수를 활용한다.