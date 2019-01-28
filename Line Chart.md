# Line Chart's property
```
javascript
var chart1 = echarts.init(document.getElementById('chart1'));

var option = { ... };
chart1.setOption(option);
```

### symbol ( string )
- default value = 'circle' ( 'circle', 'rect', 'roundRect', 'triangle', 'diamond', 'pin', 'arrow', 'none' , 'image://url'(or dataURI ) 
- 축에 해당하는 값마다 Icon

### symbolSize ( number, Array, Function )
- default value = 4
- 단일 숫자로 설정하거나, 배열을 이용하여 너비와 높이를 나타낼 수 있다. (ex [20, 10])
- 크기가 각기 달라야하는 경우 콜백 함수를 사용하여 설정
**※(value: Array|number, params: Object) => number|Array ( value는 데이터의 값, params은 데이터 항목의 나머지 매개변수 )**

### symbolRotate ( number )
- Icon의 회전 각도
- symbole이 'arrow'로 설정된 경우 이 값은 무시되고, 탄젠트 각도를 강제로 사용

### symbolKeepAspect ( boolean )
- default value = false
- Icon의 모양을 path:// 형식으로 유지할 지 여부
- 잘 모르겠다.

### symbolOffset ( Array )
- default value = [0, 0]
- 원래의 위치와 관련된 Icon의 offset
- 기본적으로 기호는 데이터의 가운데 위치
- **사용자 정의 vector 경로** 혹은 **이미지**에서 나온 Icon일 경우 가운데 위치에 올 것으로 보장할 수 없기 때문에 사용.
- 절대 위치이거나 상대 백분율 값. (ex [0, 50%]는 Icon 높이의 위쪽 측면 위치를 이동한다. 안 먹힘.)

### showSymbol ( boolean )
- default value = true
- Icon을 표시할 지 여부

### showAllSymbol ( boolean )
- default value = 'auto' ( 'auto' , 'true' , 'false' )
- 주 축이 'category'축인 경우에만 동작.
- 'auto'인데 공간이 모자라면 'axis.Label.interval'을 따른다.
- 'false'는 항상 'axis.Label.interval'을 따른다.

### hoverAnimation ( boolean )
- default value = true
- 마우스가 Icon 위에 있을 때 애니메이션 효과를 사용할 지 여부

### legendHoverLink ( boolean )
- default value = true
- 마우스가 범례 위에 있을 때 Icon 강조 사용 여부

### stack ( string )
- default value = null
- 값을 스택할 경우 사용.
- 동일한 카테고리 축에서 동일한 스택 이름을 가진 시리즈가 서로 겹쳐진다. 축에 나타나는 값은 total 값.
- 즉, stack을 사용하면 차트A뒤에 오는 차트B의 값이 차트A보다 낮아도 위에 그려질 수 있다.

```
javascript
series : [
       {
           name:'chartA',
           type:'line',
           stack: 'S',
           areaStyle: {},
           data:[120, 132, 101, 134, 90, 230, 210]
       },
       {
           name:'chartB',
           type:'line',
           stack: 'S',
           areaStyle: {},
           data:[220, 182, 191, 234, 290, 330, 310]
       }
]
```

### cursor ( string )
- default value = 'pointer'
- 요소에 마우스가 있을 때 마우스 커서의 스타일
- css의 cursor 속성과 동일한 값을 지닌다.

### connectNulls ( boolean )
- default value = false
- 데이터에 Null 값이 존재할 때 가로 질러 라인을 연결할 지 여부

### clipOverflow ( boolean )
- default value = true
- 오버플로우 되는 부분을 자를지 여부
- 잘 모르겠다.

### step ( string, boolean )
- default value = false ( true, false, 'start', 'middle', 'end' )
- 단계선으로 표시할 지 여부
- step line의 턴 포인트를 설정( example 보면 잘 알 수 있다. )

### LineStyle ( Object )
- 선 스타일을 의미

##### color
- default value = "#000" ( 'keyword', RGB, RGBA, hexadecimal, gradation(linear, radial), HTML요소 및 Canvas요소를 채울 수 있다. )
- 선 색상을 의미
- global value = true 일 때, 위치 변수는 절대 픽셀 위치를 의미

```
javascript
color: 'red'
color: 'rgb(128, 128, 128)'
color: 'rgba(128, 128, 128, 1)' //default alpha value = 1
color: '#0056'

color: {
      type: 'linear',
      x: 0,
      y: 0,
      x2: 0,
      y2: 1,
      colorStops: [{
          offset: 0, color: 'red'     //도착점
      }, {
          offset: 1, color: 'blue'    //시작점
      }],
      global: false                   //default value = false
}

color: {
      type: 'radial',
      x: 0.5,                         //중심의 x
      y: 0.5,                         //중심의 y
      r: 0.5,
      colorStops: [{
          offset: 0, color: 'red'
      }, {
          offset: 1, color: 'blue'
      }],
      global: false
}
    
color: {
      image: imageDom,          //String path is not supported
      repeat: 'repeat'          //repeat-x, repeat-y, or no-repeat
}
```

##### width ( number )
- default value = 2
- 선의 너비를 의미

##### type ( string )
- default value = 'solid' ( 'solid' , 'dashed' , 'dotted' )
- 선의 종류를 의미

##### shadowBlur ( number )
- 그림자 덩어리 크기를 의미
- shadowColor, shadowOffsetX, shadowOffsetY와 함께 사용하여야 한다.

##### shadowColor, shadowOffsetX ( number ), shadowOffsetY ( number )
- 그림자 색상, 수평·수직 방향으로 오프셋 거리를 의미한다.

```
javascript
lineStyle: {
            color: 'yellow',
            shadowColor: 'red',
            shadowBlur: 0,
            shadowOffsetY: 50,
            shadowOffsetX: 25
}
```

##### opacity ( number )
- 구성 요소의 불투명도.
- 0에서 1까지의 값으로 지정하며 구성 요소는 0으로 설정된 경우 그려지지 않는다.
- lineStyle : {}로 설정 시 default value = 1

### areaStyle ( Object )
- 영역의 스타일을 의미

##### color
- default value = "#000" ( 'keyword', RGB, RGBA, hexadecimal, gradation(linear, radial), HTML요소 및 Canvas요소를 채울 수 있다 )
- global value = true 일 때, 위치 변수는 절대 픽셀 위치를 의미
※ **lineStyle과 코드 작성 동일**

##### origin ( string )
- default value = 'auto'
- 'auto', 'start', 'end' 값이 들어갈 수 있으며, 축과 데이터 사이의 영역이 채워진다.
- 'end'일 경우 그래프 윗 부분이 채워짐.
    
##### shadowBlur ( number )
- 그림자 덩어리 크기
- shadowColor, shadowOffsetX, shadowOffsetY와 함께 사용하여야 한다.
    
##### shadowColor, shadowOffsetX ( number ), shadowOffsetY ( number )
- 그림자 색상, 수평·수직 방향으로 오프셋 거리를 의미한다.

```
javascript
areaStyle: {
            color: 'yellow',
            shadowColor: 'red',
            shadowBlur: 0,
            shadowOffsetY: 50,
            shadowOffsetX: 25
}
```
    
##### opacity ( number )
- 구성 요소의 불투명도.
- 0에서 1까지의 값으로 지정하며 구성 요소는 0으로 설정된 경우 그려지지 않는다.
- areaStyle : {}로 설정 시 default value = 0.7

### itemStyle ( Object )
- 점선의 기호 점 스타일
##### color, borderColor, borderWidth, borderType, shadowBlur, shadowColor, shadowOffsetX, shadowOffsetY, oacity 속성이 있다.

### label ( Object )
- 그래픽 항목에 대한 값, 이름 등과 가은 일부 데이터 정보를 설명
- ECharts 2.x에서 itemStyle 아래 배치되었지만, ECharts3에서 itemStyle과 동일한 수준으로 올라왔으며, 강조점이 있다.

##### show ( boolean )
- default value = false
- 라벨을 사용할 지 여부

##### position ( string, Array )
- default value = 'top' ( 'top', 'left' , 'right', 'bottom', 'inside', 'insideLeft', 'insideRight', 'insideTop', 'insideBottom', 'insideTopLeft', 'insideBottomLeft', 'insideTopRight', 'insideBottomRight', [10, 10], ['50%', '50%'] )
- 라벨의 위치

##### distance ( number )
- default value = 5
- 호스트 그래픽 요소까지의 거리를 의미
- position속성이 문자열 값일 때 작동.

##### rotate ( number )
- default value = 0 ( -90 ~ 90 )
- 양수는 반시계 방향, 음수는 시계 방향

##### offset ( Array )
- 텍스트 이동 ( ex [30, 40]은 수평으로 30도 움직이고, 수직으로 40도 움직인다 )

##### fontStyle ( string )
- default value = 'normal' ('normal', 'italic', 'oblique')

##### fontWeight ( string )
- default value = 'normal' ('normal', 'bold', 'bolder', 'lighter')

##### fontFamily ( string )
- default value = 'sans-serif' ( 'serif', 'monospace', ... )

##### fontSize ( number )
- default value = 12

##### align ( string )
- 'left', 'center', 'right' 값을 적용할 수 있으며, 정의되어 있지 않다면 부모의 상태를 따라간다.

##### verticalAlign ( string )
- 'top', 'middle', 'bottom' 값을 적용할 수 있으며, 정의되어 있지 않다면 부모의 상태를 따라간다.

##### lineHeight ( number )
- 정의되어 있지 않다면 부모의 상태를 따라간다.

##### backgroundColor ( string, Object )
- default value = 'transparent'
- '#123234', 'red', 'rgba(0,23,11,0.3)', image: 'xxx/xxx.png', dataURI, HTMLImageElement, HTMLCanvasElement로 적용할 수 있다.
- 배경 이미지를 사용할 때, 너비와 높이를 지정할 수 있으며 기본적으로 'auto'로 적용된다.
- 'auto'인 경우 색상이 series 색상과 같이 시각적 색상으로 지정된다.
 
##### borderColor ( string )
 - default value = 'transparent'
 - 'auto'인 경우 색상이 series 색상과 같이 시각적 색상으로 지정된다.

##### borderWidth ( number ), borderRadius ( number )
- default value = 0

##### padding ( number, Array )
- default value = 0
- width와 height은 padding을 사용하지 않고 지정한다.

##### shadowColor ( string )
- default value = 'transparent'

##### shadowBlur ( number ), shadowOffsetX ( number ), shadowOffsetY ( number )
- default value = 0

##### width ( number, string ),  height ( number, string )
- 기본적으로 텍스트 너비
- padding을 사용하지 않고 지정한다.
- '100%'와 같은 문자열은 contentWidth의 백분율을 나타낸다.

##### textBorderColor ( string )
- default value = 'transparent'
- 'auto'인 경우 색상이 series 색상과 같이 시각적 색상으로 지정된다.

##### textBorderWidth ( number )
- default value = 0

##### textShadowColor ( string )
- default value = 'transparent'

##### textShadowBlur ( number ), textShadowOffsetX ( number ), textShadowOffsetY ( number )
- default value = 0

##### rich ( Object )
- 임의로 지정하여, 개별적으로 스타일을 지정해줄 수 있다.
- 잘 모르겠다.

### emphasis
- 그래픽 강조 스타일을 의미

##### label, itemStyle을 지님

### smooth ( boolean, number )
- default value = false
- 부드러운 곡선으로 표시할 지 여부
- 값이 boolean 타입일 경우 곡선을 사용할지 여부를 의미한다.
- 0에서 1 사이의 숫자가 입력되면 곡선의 정도를 의미하며, 값이 커질수록 곡선의 정도가 크다.
- true일 경우 default value = 0.5
 
### smoothMonotone ( string )
- 점선이 곡선을 이룰 때 단조를 유지하는지 여부
- x축 또는 y축에 단조를 유지하기 위해 'x', 'y'로 설정할 수 있으며 'none'도 사용 가능하다.
- 잘 모르겠다.

### sampling ( string )
- 'average', 'max', 'min', 'sum' 값을 적용할 수 있다.
- downsampling strategy은 데이터 크기가 픽셀 크기보다 훨씬 클 때 사용된다.
- 사용하면 성능이 향상.
- 기본값은 해제되어 모든 데이터 요소가 그려진다.
- 잘 모르겠다.

### dimensions ( Array )
- 차원을 이용하여 series.data 또는 dataset.source 차원 정보를 정의
- dataset을 사용하면, dataset.source의 첫번째 행렬에 차원의 이름을 제공할 수 있으므로 여기에 차원을 지정할 필요가 없다.
- **그러나 여기에 차원을 지정하면, echarts는 더 이상 dataset.source의 첫번째 행렬에서 차원 이름을 검색하지 않는다.**


# dimensions 더 해야함.


### seriesLayoutBy ( string )
- default value = 'column' ( 'column', 'row' )
- dataset이 사용될 때, dataset의 행열이 series에 매핑되는지 여부를 지정. 즉, series는 행열의 레이아웃이다.



### animation ( boolean )
- default value = true
- 애니메이션을 사용할 지 여부
  
### animationThreshold ( number )
- default value = 2000
- 그래픽 숫자 임계치를 애니메이션으로 설정할 지 여부
- 그래픽 숫자가 임계치보다 클 경우 애니메이션 비활성화

### animationDuration ( number, Function )
- default value = 1000
- 다른 데이터가 다른 애니메이션 효과를 갖도록 하는 콜백함수를 지원하는 첫번째 에니메이션의 지속 시간을 의미
- 다음 데이터의 지연 시간이 더 크다

```
javascript
animationDuration: function (idx) {
    return idx * 100;
}
```

### animationEasing ( string )
- default value = linear
- 첫 번째 애니메이션에 사용되는 메서드

### animationDelay ( number, Function )
- default value = 0
- 다른 데이터가 다른 애니메이션 효과를 갖도록 하는 콜백 함수를 지원하여 첫 번째 애니메이션을 업데이트하기 전에 지연 시간을 의미

```
javascript
animationDelay: function (idx) {
    return idx * 100;
}
```
  
### animationDurationUpdate ( number, Function )
- default value = 300
- 다른 데이터가 다른 애니메이션 효과를 갖도록 하는 콜백 함수를 지원하여 완료되는 애니메이션 시간을 의미
- 잘 모르겠다.

```
javascript
animationDurationUpdate: function (idx) {
    return idx * 100;
}
```

### animationEasingUpdate ( string )
- default value = cubicOut
- 애니메이션에 사용되는 Easing 방법
- 'elasticOut', 'cubicOut' 등
 
### animationDelayUpdate ( string )
- default value = 0
- 다른 데이터가 다른 애니메이션 효과를 갖도록 하는 콜백 함수를 지원하여 애니메이션 업데이트 전 지연 시간을 의미
- 잘 모르겠다.

```
javascript
animationDelayUpdate: function (idx) {
    return idx * 100;
}
```
