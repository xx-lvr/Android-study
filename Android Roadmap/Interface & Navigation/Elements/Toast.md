## Toast
사용자를 위한 간단한 메시지를 담은 뷰

사용자에게 뷰가 표시되면 애플리케이션 위에 떠 있는 뷰로 나타난다.

```kotlin
Toast(Context context)
// 빈 Toast 객체를 생성합니다.
```

```kotlin
//Toast 위젯 상속
class CustomToast(context: Context) : Toast(context) {

}

//객체 생성
Toast(context).apply { 
	view = toastLayout
    setGravity(Gravity.CENTER,0,0)
}
```