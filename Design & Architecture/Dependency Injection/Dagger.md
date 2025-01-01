## Dagger
**Dagger**는 **DI**를 도와주는 **DI Framework** 의미

## Dagger 5가지 필수 개념
+ Inject
+ Component
+ SubComponent
+ Module
+ Scope

## Inject
**Inject**는 ```필드```, ```생성자```, ```메서드```에 붙여 **Component**로 부터 의존성 객체를 주입 요청하는 **annotation**이다.

```@Inject```로 의존성 주입을 요청하면 연결된 ```Component```가 ```Module```로부터 객체를 생성하여 넘겨준다.
```Component```는 ```@Inject``` 어노테이션을 의존성 주입할 멤버변수와 생성자에 달아줌으로 DI 대상을 확인할 수 있다.

### Inject 생산자에 의존성 주입 방식
```kotlin
class AA()

class BB(val aa: AA)

// 생성자에 @Inject를 사용해서 CC Type의 인스턴스를 주입하는 방식
class CC @Inject constructor(val aa: AA, val bb: BB)
```
### Inject 필드에 의존성 주입 방식
```kotlin
@Inject
lateinit var aa: AA	// @Inject로 필드에 의존성 주입을 하는 방식

@Inject
lateinit var bb: BB

@Inject
lateinit var cc: CC
```

 ### Inject를 붙일 수 없는 경우는 다음과 같다

1. Interface는 생성자 개념이 없으므로 불가능하다
2. 서드파티 라이브러리 등의 클래스는 참조가 불가능하여 annotation프로세싱이 불가능하다

## Module

**Component**에 연결되어 의존성 객체를 생성하는 역할이다. 생성 후 Scope에 따라 객체를 관리도 한다.

```@Module```은 클래스에만 붙이고,```@Provides```는 반드시 **Module** 클래스에 선언된 메서드에만 사용한다.

**Module 클래스**는 의존성 주입에 필요한 객체들을```@Provide```, ```@Binds``` 메서드를 통해 관리한다.

```kotlin
@Module
class Module_A {
    @Provides
    fun provideAA() : AA = AA()	// AA 객체(인스턴스)를 Component에게 제공

    @Provides
    fun provideBB(aa: AA) : BB = BB(aa) // 필요한 인자(AA)를 Component로 부터 전달받아 BB 객체를 생성해서 Component에게 제공
}
```
## Component

## SubComponent

## Scope