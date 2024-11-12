## MVP
MVP는 Model View Presenter의 약자로 MVC패턴을 패턴을 기반으로 하는 아키텍쳐
+ 요약: MVC패턴에서 View와 Model의 의존성을 없애고 단위 테스트가 어려웠던 문제점을 해결하기 위해 등장하게된 패턴

### Model
앱에 사용되는 데이터를 관리 담당하는 역할을 합니다. 흔히 '비즈니스 로직'이리고 부르는 부분이다. 모델에는 network API, 데이터 캐싱, 데이터베이스 등이 포함되고 Repository pattern을 사용하는 경우 Repository도 포함된다.

### View
사용자 인터페이스 영역이며, Activity, Fragment 등이 포함되고 데이터를 표시하는 역할만 합니다. 오직 Presenter를 통해서 데이터를 요청하고 전달 받기때문에 Presenter에 의존적이다.

### Presenter
View와 Model 사이 중개자 역할을 담당합니다. View에서 사용자 이벤트를 전달 받아 Model에 데이터를 요청하고 전달받은 데이터를 View에 그대로 전달 합니다. ( MVVM의 ViewModel과 비교했을때 ViewModel은 View를 알지 못하고 View에 대한 참조를 가지고 있지 않다. 하지만 Presenter는 View와 Model 모두 참조 하고있다)