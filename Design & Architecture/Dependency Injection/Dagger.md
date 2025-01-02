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

@Component는 ```Interface``` 또는 ```abstract class```에만 사용이 가능\
컴파일 타임에 접두어 **'Dagger'**와 **Component** 클래스 이름이 합쳐진 **Dagger**클래스 자동생성\
(ex : ```@Component interface MyComponent``` -> ```DaggerMyComponent``` 클래스 생성)

연결된 **Module**을 이용하여 의존성 객체를 생성하고, **Inject**로 요청받은 인스턴스에 생성한 객체를 전달(주입)합니다

의존성을 요청받고 전달(주입)하는 **Dagger**의 주된 역할을 수행하는 부분

## SubComponent

```SubComponent```는 말 그대로 부모 **Component**가 있는 자식 **Component**라고 보면 된다. 

**Inject**로 의존성 주입을 요청받으면 **SubComponent**에서 먼저 ```의존성```을 검색하고, 없으면 부모로 올라가면서 검색한다

**SubComponent**는 **Component**와 달리 코드 생성은 부모 ```Component```에서 이루어 진다다.

**SubComponent**는 **Component**와 마찬가지로 **interface** 또는 **abstract class**에 **@SubComponent** 에노테이션으로 생성

## Scope

**Component**   별로 ```@Scope``` **annotation**으로 주입되는 객체들을 관리한다

생성된 객체의 ```Lifecycle``` 범위. 안드로이드는 주로 **PerActivity**, **PerFragment** 등으로 하면의 생명주기와 맞춰서 사용한다.