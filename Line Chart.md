# Line Chart's property
```
javascript
var chart1 = echarts.init(document.getElementById('chart1'));

var option = { ... };
chart1.setOption(option);
```

● areaStyle
- 영역의 스타일을 의미

  ※지닌 프로퍼티들
    ○ color
    - default value = black
    - 'keyword', RGB, RGBA, hexadecimal, gradation(linear, radial), HTML요소 및 Canvas요소를 채울 수 있다
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
      x: 0.5,
      y: 0.5,
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
    
    
    ○ origin
    
