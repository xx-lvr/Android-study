## MVI
MVI는 Model-View-Intent의 약자로서 안드로이드를 위한 최신 아키텍처 패턴 중 하나이다.\
MVI는 먼 친척인 MVC, MVP 또는 MVVM과 매우 다른 방식으로 작동
+ **Model** — 모델은 상태를 나타낸다. MVI의 모델은 아키텍쳐의 다른 레이어와의 단방향 데이터 흐름을 보장하기 위해 변경이 불가능해야 한다.

+ **View** — View를 나타내며 하나 이상의 Activity나 Fragment로 구현된다.

+ **Intent** — 사용자 또는 앱내 발생하는 Action을 나타낸다. 모든 Action에 대해 View는 Intent를 수신한다. Presenter는 Intent를 관찰하고 Model은 새로운 상태로 변환한다.

## MVI 장점과 단점
**Model-View-Intent** 는 유지 관리가 용이하고 확장 가능한 앱을 만들수 있도록 도와준다

**주요장점**
+ 데이터가 단방향으로 순환한다.
+ View의 생명주기 동안 일관성 있는 상태를 갖는다.
+ 불변 Model은 큰 앱에서 멀티 스레드 안정성과 안정적인 동작을 제공한다.