### 날짜 : 2022-08-18
### 주제 : #Android #LayoutInspector
----
### 정리
앱을 개발하다보면 xml의 뷰를 런타임에 계층의 구조 layout들의 상태 영역의 크기등 다양한 정보를 확인 하고 싶을때가 있다. Android Studio에 Layout Inspector기능에 대해 한번 살펴보면 런타임의 뷰를 디버깅 해볼 수 있다.

LayouInspector를 사용 하며 런타임에 레이아웃 정보를 확인 할 수 있으며 런타임 이휴에 생성되는 UI들에 대해서 검토, 디버깅을 할 수 있다. 
Component Tree를 통해  레이아웃의 뷰 계층 구조, id, View의 종류또한 바로 알 수 있다.

![[스크린샷 2022-08-18 오후 6.46.44.png]]
![[스크린샷 2022-08-18 오후 7.05.20.png]]
복잡한 뷰에서 원하는 뷰의 트리를 보싶은면 마우스 우측 클릭후 **Show Only Subtree** 기능을 이용할 수 있다.
Go To Declaration을 통해 해당 View Xml코드로 바로 이동할 수 있다.

아이템들을 개별적으로 확인할때에는 Attributes탭을 사용 하면 선택한 뷰의 레이아웃 세부 정보들을 확인 할 수 있다.
![[스크린샷 2022-08-18 오후 6.56.51.png]]
**Experimental** 설정에서 **Enable Live Layout Inspector** ![[스크린샷 2022-08-18 오후 6.59.32.png]]기능을 활성화 하면 하면이 변경 될때 마다 **Component Tree**와 **Layout Display**가 바로 업데이트 되며 기능이 불필요하다면 **Refresh layout** ![[스크린샷 2022-08-18 오후 6.59.47.png]]의로 화면을 업데이트 할 수 있다.

Layout들의 계층도 확인할 수 있는 ![[스크린샷 2022-08-19 오후 7.25.02.png]] 3D 기능도 지원하고 있다.


### 참고
- [Layout Inspector 및 Layout Validation으로 레이아웃 디버깅](https://developer.android.com/studio/debug/layout-inspector?hl=ko)

### 연결된 메모
- 