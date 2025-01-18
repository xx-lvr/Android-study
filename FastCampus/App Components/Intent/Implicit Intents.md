## Implicit Intent (암시적 인텐트)
암시적 인텐트는 호출할 대상이 명확하지 않을 때 사용되며, 시스템이 인텐트의 의도에 맞는 적절한 Activity를 찾아 실행한다.\
 이는 앱 간 상호작용을 가능하게 하며, 다양한 상황에서 활용된다.

### 특징⚠️
+ 호출할 대상이 명확하지 않을 때 사용!
+ Action, Data, Category, Extras 등을 통해 작업의 목적과 관련 데이터를 전달
+ 시스템이 적합한 컴포넌트를 선택해 Activity를 실행

### 사용 예시
- 웹 페이지 열기
- 연락처 불러오기
- 사진 찍기
- 이메일 전송
### 주요 속성
+ Action: 수행하려는 작업을 정의\
```예: Intent.ACTION_VIEW, Intent.ACTION_SEND```

+ Data: 작업을 수행할 데이터 ```(예: URI 형식으로 웹 주소, 전화번호 등)```
```예: Uri.parse("tel:123456789")```

+ Category: 추가적인 분류 정보
```예: Intent.CATEGORY_DEFAULT```

+ Extras: 인텐트에 추가 데이터를 담을 수 있는 옵션