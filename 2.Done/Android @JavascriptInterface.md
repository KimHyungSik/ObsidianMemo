### 날짜 : 2022-10-05
### 주제 : #Android #WebView
----
### 정리
WebView를 이용할때 사용할때 JavaScript에서 메서드를 호출할 수 있도록 노출시켜주는 어노테이션 입니다.
```kotlin
class WebAppInterface(private val mContext: Context) {

	@JavascriptInterface // 어노테이션을 추가하여 Webview의 JavaScript에서 호출 가능
	fun showToast(toast: String) {
		Toast.makeText(mContext, toast, Toast.LENGTH_SHORT).show()
	}
}
```
`WebAppInterface` class를 JavaScript에 연결하여 사용하기 위해 methods에 `@JavascriptInterface` 어노테이션을 추가하여 `showToast(Stirng)`메서드를 사용할 수 있게 만듭니다.
```kotlin
  webView.addJavascriptInterface(WebAppInterface(this), "ProtocalName")
```
`addJavascriptInterface`에 `WebAppInterface`객체를 추가하고, 정의한 호출할 네임("ProtocalName")을 추가하여 JavaScript에서 사용가능하게 합니다.
```javascript
function showAndroidToast(toast) {
	ProtocalName.showToast(toast);
}
```
JavaScript에서는 정의한 네임으로 메서드를 호출하면 사용 가능합니다
### 참고 자료
- [앱과-웹뷰간의-통신-예제-Android-JavascriptInterface-사용법](https://velog.io/@limsaehyun/%EC%95%B1%EA%B3%BC-%EC%9B%B9%EB%B7%B0%EA%B0%84%EC%9D%98-%ED%86%B5%EC%8B%A0-%EC%98%88%EC%A0%9C-Android-JavascriptInterface-%EC%82%AC%EC%9A%A9%EB%B2%95)

### 연관된 기술
- 