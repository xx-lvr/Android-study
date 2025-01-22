## DataStore
Kotlin 코루틴 및 Flow를 사용하여 비동기적이고 일관된 트랜잭션 방식으로 데이터를 저장한다.

## 종속 항목 선언
DataStore의 종속 항목을 추가하려면 프로젝트에 Google Maven 저장소를 추가 해야 한다.

DataStore는 Preferences DataStore과 Proto DataStore 두 가지 방식을 통해 구현이 가능하다.

## Preferences DataStore
 키를 사용하여 데이터를 저장하고 데이터에 액세스한다. 구현은 유형 안전성을 제공하지 않으며 사전 정의된 스키마가 필요하지 않다.
```Kotlin
 // Preferences DataStore (SharedPreferences like APIs)
    dependencie"? bgt6ts {
        implementation("androidx.datastore:datastore-preferences:1.1.1")

        // optional - RxJava2 support
        implementation("androidx.datastore:datastore-preferences-rxjava2:1.1.1")

        // optional - RxJava3 support
        implementation("androidx.datastore:datastore-preferences-rxjava3:1.1.1")
    }

    // Alternatively - use the following artifact without an Android dependency.
    dependencies {
        implementation("androidx.datastore:datastore-preferences-core:1.1.1")
    }
```

## Proto DataStore
맞춤 데이터 유형의 인스턴스로 데이터를 저장한다. 이 구현은 유형 안전성을 제공하며 프로토콜 버퍼를 사용하여 스키마를 정의해야 한다
```Kotlin
    // Typed DataStore (Typed API surface, such as Proto)
    dependencies {
        implementation("androidx.datastore:datastore:1.1.1")

        // optional - RxJava2 support
        implementation("androidx.datastore:datastore-rxjava2:1.1.1")

        // optional - RxJava3 support
        implementation("androidx.datastore:datastore-rxjava3:1.1.1")
    }

    // Alternatively - use the following artifact without an Android dependency.
    dependencies {
        implementation("androidx.datastore:datastore-core:1.1.1")
    }
```

## DataStore 올바르게 사용하는 규칙
1. 같은 프로세스에서 특정 파일의 DataStore 인스턴스를 두 개 이상 만들지 않는다.
2. DataStore의 일반 유형은 변경 불가능해야 한다.
3. 동일한 파일에서 ```SingleProcessDataStore```와 ```MultiProcessDataStore```를 함께 사용하지 않는다.
+ 두개 이상의 프로세스에서 DataStore에 엑세스 하려면 ```MultiProcessDataStore```를 사용해라