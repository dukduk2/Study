# Bar Chart
- 막대형 차트
- 막대의 높이를 통해 데이터를 보여주며, 최소 1개의 category 축이 있는 직사각형 좌표에서 사용.

### legendHoverLink ( boolean )
- default : true
- legend가 강조될 지 여부.

### coordinateSystem ( string )
- default : 'cartesian2d'
- xAxisIndex와 yAxisIndex를 사용하여 해당 축의 구성 요소를 지정하여 2차원 직각 좌표를 사용.

### xAxisIndex ( number )
- default : 0
- 결합할 x축의 index
- 하나의 차트에서 여러 x축이 있을 때 유용.

### yAxisIndex ( number )
- default : 0
- 결합할 y축의 index
- 하나의 차트에서 여러 y축이 있을 때 유용.

### label ( Object )
- 그래프 요소의 값, 이름 등과 같은 일부 데이터 정보를 표현

##### show ( boolean )
- default : false ( 안보임 )

##### position ( string, Array )
- default : 'inside'
- 정해진 'keyword' 외에도 ['50%', '50%'], [10, 10]과 같이 왼쪽 상단을 기준으로 절대값, 상대 백분율을 사용할 수 있다.

##### distance ( number )
- default : 5
- position이 'keyword' 값일 때, 그래프 요소와의 간격.

##### rotate ( number ) ...

### itemStyle ( Object )

### emphasis ( Object )

### stack ( string )

### cursor ( string )

### barWidth ( number )
- default : null
- 지정하지 않으면 반응형.
- coordinateSystem의 마지막 bar 차트 series 안에 설정해야함.

### barMaxWidth( number )
- default : null
- 지정하지 않으면 반응형
- coordinateSystem의 마지막 bar 차트 series 안에 설정해야함.

### barMinHeight ( number )
- default : 0
- 일부 데이터 항목의 값이 너무 작아서 다른 데이터들과의 상호 작용에 영향을 받을 때 사용.

### barGap ( string )
- default : '30%'
- barWidth에 대한 상대 비율
- '-100%'로 설정하면 다른 series의 bar차트를 겹칠 수 있다.
- coordinateSystem의 마지막 bar 차트 series 안에 설정해야함.

### barCategoryGap ( string )
- default : '20%'
- 고정 값으로 지정할 수 있다.
- coordinateSystem의 마지막 bar 차트 series 안에 설정해야함.

### large ( boolean )
- default : false
- 대용량 데이터의 최적화 여부. ( 대용량 데이터로 인해 성능 문제가 발생할 때 설정 )
- 적용 후 largeThreshold는 최적화를 수해하기 위한 최소 숫자를 나타내는데 사용 가능.

### largeThreshold ( number )
- default : 400
- 최적화 임계값

### progressive ( number )
- default : 5000
- "progressive rendering"이 활성화된 경우 한 프레임 내에서 렌더링될 수 있는 그래프 요소의 양을 지정.
- 데이터 양이 1000에서 10000 이상이 되면 렌더링에 소요되는 시간이 크다.
- ECharts 4부터 workflow에서 브라우저의 UI 쓰레드를 차단하지 않고 각 프레임별로 대용량의 데이터를 한덩어리로 처리하고 렌더링하는 "progressive rendering"이 지원된다.

### progressiveChunkMode ( string )
- default : 'mod' ( 'mod', 'sequential' )
- 'sequential' : data index에 의한 data 조각화 
- 'mod' : mod별로 조각화하여 각 덩어리의 데이터 항목을 모든 데이터에서 가져와서 점진적 렌더링 동안 더 나은 시각적 효과를 일으킨다.

### dimensions ( Object )


### encode ( Object )
- 각 데이터 dimension에 대해 인코딩 대상을 지정

```
javascript
dataset: {
    source: [
            // Each column is called a dimension.
            // There are five dimensions: 0, 1, 2, 3, 4。
            [12, 44, 55, 66, 2],
            [23, 6, 16, 23, 1],
            ...
        ]
    },
    series: {
        type: 'xxx',
        encode: {
            x: [3, 1, 5],      // Dimension 3, 1, 5 is mapped to x axis.
            y: 2,              // Dimension 2 is mapped to y axis.
            tooltip: [3, 2, 4] // Dimension 3, 2, 4 will be displayed in tooltip.
   }
}
```
