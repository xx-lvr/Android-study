## Repository Pattern
Data의 출처에 관계 없이 동일한 인터페이스로 데이터에 접근할 수 있도록 하는 패턴. 즉, **DataSource를 캡슐화 시킨다**

[text](<Repository Pattern.md>)
ViewModel에서 직접 Data에 접근하여 데이터를 가져오는 것이 아니라, **ViewModel에서는 Repository만 접근** 을 하게 된다.
Repository에서 Remote Data인지 Local Data인지 필요한 데이터를 가져와 ViewModel에게 전달한다.

즉, Data Layer가 캡슐화가 되고 ViewModel이 포함되어 있는 Presentation Layer에서 Data Layer를 직접 호출하지 않고 Repository를 통해서만 접근이 가능하게 되는 것**Data Layer를 캡슐화 시키는 것이 Repository 패턴의 주된 목적**
## 캡슐화를 통해 얻을 수 있는 장점
+ Data Layer에 대한 의존성을 줄일 수 있다. 즉, Data Layer와 Presentation Layer 간의 Coupling이 줄어든다.
+ Presentation Layer에서 Data Layer에 직접 접근하지 않으므로, 새로운 Data의 추가가 쉽다.
+ Presentation Layer에서는 Repository에 데이터 요청만 하면 되므로, 일관된 인터페이스로 데이터를 요청할 수 있다.
+ Unit Test를 통한 검증하기가 쉬워진다.