<h2>flex box</h2>

```display: flex``` 는 부모 박스 요소에 적용해, 자식 박스의 방향과 크기를 결정하는 레이아웃 구성 방법

flex box를 만들때 주의할 것은 부모요소에 적용할 것(정렬관련)과 자식요소에 설정할 것(차지하는공간관련)을 구분해야함<br>

**부모요소에 설정해야 할 것들**
  1. ```flex-direction``` 속성은 부모 요소에 설정해주는 속성으로 자식 요소들을 정렬할 정렬 축을 정한다. (기본값은 가로 정렬)
   - row/ column/ row-reverse/ column-reverse
  2. ```flex-wrap``` 속성은 하위 요소들의 크기가 상위 요소의 크기를 넘으면 자동 줄 바꿈을 할 것인지 정합니다. (기본값 : 줄바꿈x)
   - no wrap/ wrap/ wrap-reverse
  3. ```justify-content```자식 요소들을 축의 수평 방향으로 어떻게 정렬할 것인지 정함.
   - flex-start / flex-end/ center/ space-between/ space-around
  4. ```align-items``` 속성은 자식 요소들을 축의 수직 방향으로 어떻게 정렬할 것인지 정합니다.
   - stretch / flex-start / flex-end / center / baseline
 
**자식요소에 설정해야 할 것들**

  1. flex:   <grow(팽창 지수)>    <shrink(수축 지수)>    <basis(기본 크기)>
  
    - 기본값은 ```flex: 0 1 auto```
    - grow(팽창 지수) 는 정렬축 방향으로 빈 공간이 있을 때, 각 자식 요소들이 얼마나 늘어나서 남는 공간을 차지할 것인지 비율을 정하는 것
      (팽창지수는 자식 요소의 grow값 / 자식 요소들의 grow값의 총합 의 비율로 빈 공간을 가져감)
  
    - shrink
      - shrink는 grow와 반대로 설정한 비율만큼 박스 크기가 작아진다.
      - flex-grow와 굳이 함께쓰지는 말고, 비율로 레이아웃 지정할때는 shrink의 기본값인 1로지정하고 되도록 grow를 쓰자(flex shrink는 예측하기가 어려움)
    
    - basis
      - basis(기본 크기) 는 자식 박스가 flex-grow 나 flex-shrink 에 의해 늘어나거나 줄어들기 전에 가지는 기본 크기
      - **flex-grow 가 0일 때, basis 크기를 지정하면 그 크기는 유지됨.**
      
      
레이아웃 구현하면서 골치아파지는 경우 아래 세가지를 생각해보자
- width와 flex-basis를 동시에 적용하는 경우, flex-basis가 우선됩니다.
- 콘텐츠가 많아 자식 박스가 넘치는 경우, width가 정확한 크기를 보장하지 않습니다.
- (flex-basis를 사용하지 않는다면) 콘텐츠가 많아 자식 박스가 넘치는 경우를 대비해, width 대신 max-width를 쓸 수 있습니다.
