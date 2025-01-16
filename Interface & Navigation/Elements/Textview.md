## Textview
Android View 시스템의 ```TextView```는 Compose 에서 ```Text```로 쓰여진다

## 예제코드
+ xml에서의 코드
```kotlin
 <TextView
        android:id="@+id/textView6"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="TextView" />
```
+ Compose에서의 코드
```kotlin
 Text(
        text = "TextView",
        style = TextStyle(
         fontSize = 16.sp,
         fontWeight = FontWeight(700),
        color = Color(0xFFFFFFFF),
        )
 )
```

+ 개인적으로 Compose가 더 좋은 듯