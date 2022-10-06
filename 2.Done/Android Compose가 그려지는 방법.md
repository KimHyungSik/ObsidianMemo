### 날짜 : 2022-08-11
### 주제 : #Android #Compose 
----
### 정리
1. Composition: Compose의 구성 가능한 함수를 실행 하고 다음 두가지 작업을 준비 
   @Compsable 함수의 상태 값이 변경되면 Recomposer는 상태값을 모두 읽어 함수를 재실행합니다.
   이때 콘텐츠가 동일하게 유지된다면 이후의 단계를 건너뛸 수 있습니다.
2. Layout: UI를 배치할 위치를 측정하고 배치 합니다. 레이아웃 트리에 있는 모든 레이아웃의 레이아웃 요소 및 하위 요소를 2D 좌료를 측정 배치 합니다.  측정 단계에서는 LayoutModifier 인터페이스의 `MeasureScope.measure` 메서드가 실행 되고 배치 단계에서 `Modifier.offset{}` 람다 블록이 실행됩니다. 이러한 과정에 영향을 주어 ComposeUI를 변경하는 것 도 가능합니다.
4. Draw: UI를 기기의 화면 캔버스에 그립니다. `Canvas()`, `Modifier.drawBehind`, `Modifier.drawWithContent` 등이 Draw 단계에 영향을 줄 수 있습니다.

![[이미지 2022. 8. 11. 오전 8.57.jpg]]

>Compose는 이전 결과를 재사용할 수 있으면 구성 가능한 함수 실행을 [건너뛰고](https://developer.android.com/jetpack/compose/mental-model?hl=ko#skips) Compose UI는 꼭 필요한 경우가 아니라면 전체 트리를 다시 배치하거나 다시 그리는 작업을 하지 않습니다. Compose는 UI를 업데이트하는 데 필요한 최소한의 작업만 실행합니다. 이러한 최적화가 가능한 이유는 Compose가 여러 단계 내에서 상태 읽기를 추적하기 때문입니다.


### 참고
- [Jetpack Compose 단계](https://developer.android.com/jetpack/compose/phases?hl=ko)

### 연결된 메모
- [[Android JetPack Compose 정의]]