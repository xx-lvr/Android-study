## Hilt
Hilt는 Dagger를 기반으로 빌드되어 Dagger를 Android 애플리케이션에 통합하는 표준 방법을 제공한다.

안드로이드 컴포넌트 생명주기에 맞게 인스턴스를 관리하는 방법을 제공한다.

안드로이드에서 종속성 주입에는 **Hilt를 사용하도록 권고**한다.

### Dagger과 관련해서 Hilt의 목표?
1. Android 앱을 위한 Dagger 관련 인프라 간소화
2. 앱 간의 설정, 가독성 및 코드 공유를 용이하게 하기 위한 표준 구성요소 및 범위 세트 생성
3. 테스트, 디버그 또는 출시와 같은 다양한 빌드 유형에 서로 다른 결합을 프로비저닝하는 쉬운 방법 제공하는 것

### Hilt가 자동으로 생성하고 제공하는 것
+ 수동으로 생성해야 하는 Dagger와 Android 프레임워크 클래스를 통합하기 위한 **구성요소**
+ Hilt가 자동으로 생성하는 구성요소와 함께 사용할 **범위 주석**
+ Application 또는 Activity와 같은 Android 클래스를 나타내는 **사전 정의된 결합**
+ ```@ApplicationContext``` 및 ```@ActivityContext```를 나타내는 **사전 정의된 한정자**

## Hilt 종속 항목 추가
```kotlin
buildscript {
    ...
    dependencies {
        ...
        classpath 'com.google.dagger:hilt-android-gradle-plugin:2.38.1'
    }
}
```
hilt-android-gradle-plugin 플러그인을 **프로젝트의 루트(프로젝트 레벨) build.gradle 파일에 추가**
```
...
plugins {
  id 'kotlin-kapt'
  id 'dagger.hilt.android.plugin'
}

android {
    ...
}

dependencies {
    implementation "com.google.dagger:hilt-android:2.38.1"
    kapt "com.google.dagger:hilt-compiler:2.38.1"
}
```
 app 레벨에서 또한 종속성을 추가