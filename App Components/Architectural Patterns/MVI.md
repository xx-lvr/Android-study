## MVI
MVI는 Model-View-Intent의 약자로서 안드로이드를 위한 최신 아키텍처 패턴 중 하나이다.
+ Model — 모델은 상태를 나타낸다. MVI의 모델은 아키텍쳐의 다른 레이어와의 단방향 데이터 흐름을 보장하기 위해 변경이 불가능해야 한다.

+ View — View를 나타내며 하나 이상의 Activity나 Fragment로 구현된다.

+ Intent — 사용자 또는 앱내 발생하는 Action을 나타낸다. 모든 Action에 대해 View는 Intent를 수신한다. Presenter는 Intent를 관찰하고 Model은 새로운 상태로 변환한다.

