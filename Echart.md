# Study
Echart ( https://ecomfe.github.io/echarts-doc/public/en/index.html )

● echart 설치방법 4가지
1. 공식 홈페이지에서 다운
2. github에서 echart 최신 버전
3. npm 사용
4. online build tool 사용

echarrt3는 더 이상 패키지를 로드하기 위해 amd 사용 안하고 스크립트 태그 이용

너비와 높이, id를 지닌 DOM객체를 먼저 준비해야한다
echarts.init을 통해 인스턴스를 생성하고, 정의한 차트의 내용을 setOption메서드를 이용하여 생성한다.

● Custom Build 사용 가능


var option = {...}; setOption(option) 혹은
setOption({.....})으로 데이터 정의 가능

```
javascript
backgroundColor: '#2c343c'  //전체 배경색 지정

title: {text: 'Line Chart'}  // 제목 지정

textStyle: {                //전체 텍스트스타일 지정
        color: 'rgba(0, 0, 255, 1)' 
}

visualMap: {
    // hide visualMap component; use lightness mapping only
    show: false,
    // mapping with min value at 80
    min: 80,
    // mapping with max value at 600
    max: 600,
    inRange: {
        // mapping lightness from 0 to 1
        colorLightness: [0, 1]
    }
}

setOption({
  series :            //series 내에서 사용 가능한 프로퍼티들
   label: {                      //개별적으로 텍스트스타일 지정
          textStyle: {
             color: 'rgba(255, 255, 255, 0.3)'
          }
      }

   labelLine: {                //차트의 선 색상 지정
          lineStyle: {
              color: 'rgba(255, 255, 255, 0.3)'
          }
      }

   itemStyle: {                //차트의 한 아이템에 마우스를 올렸을 때 그 아이템의 속성 지정, data프로퍼티 안에 들어갈 수 있다.
          // shadow size
          shadowBlur: 200,
          // horizontal offset of shadow
          shadowOffsetX: 0,
          // vertical offset of shadow
          shadowOffsetY: 0,
          // shadow color
          shadowColor: 'rgba(0, 0, 0, 0.5)'
      }
   


}
```


● 테마 지정
```
javascript
var chart = echarts.init(dom, 'light');           //테마 지정
var chart = echarts.init(dom, 'dark');
```
위의 두 개의 테마 외에는 다운 받아서 사용해야 한다


● 팔레트 지정
        시리즈와 데이터로 자동 선택되는 색상 그룹을 제공
        전역 팔레트 또는 특정 시리즈의 독점 팔레트

```
javascript
option = {
    color: ['red', 'blue' , 'yellow'],          // 전역 팔레트
    series: [
    {
        type: 'bar',
        color: ['orange','skyblue','lightgreen'],       //독점 팔레트
        ...
    },
    {
        type: 'pie',
        color: ['pink', 'green', 'navy'],       //독점 팔레트
        ...
    }
    ]
}
```


● 명시적 스타일 커스터마이징
스타일을 명시적으로 설정하는 것이 일반적이다.
ECharts 옵션 전체에서 스타일 관련 옵션은 다양한 장소에서 설정이 가능하다 (itemStyle, lineStyle, areaStyle, label 등)

일반적으로 내장 된 모든 구성 요소 및 시리즈는 itemStyle, lineStyle, areaStyle, label 등의 명명 규칙을 따른다.
일련의 구성 요소나 구성 요소에 따라 위치가 다를 수 있다.


● Style of emphasis state
마우스가 그래픽 요소를 가리키면 표시되는 스타일
default값은 normal style
emphasis 속성을 통해 지정
강조의 옵션은 정상 상태의 옵션과 동일합니다.

※대부분의 사용자들이 normal 스타일만을 사용하기 때문에 ECharts4 이후로 normal 지정 없이 스타일을 작성 가능

● Asynchronous Loading 
초기화 후에도 데이터를 얻은 후에 jQuery와 같은 기타 툴을 이용하여 setOption()을 통해 언제든지 데이터 및 항목 전달 가능

다른 스타일을 지정하고 빈 직사각형 축만 표시한 후, 데이터가 준비됐을 때 채우기도 가능

```
javascript
var myChart = echarts.init(document.getElementById('main'));
// show title. legend and empty axis
myChart.setOption({
    title: {
        text: 'asynchronous data loading example'
    },
    tooltip: {},
    legend: {
        data:['Sales']
    },
    xAxis: {
        data: []
    },
    yAxis: {},
    series: [{
        name: 'Sales',
        type: 'bar',
        data: []
    }]
});

// Asynchronous data loading 
$.get('data.json').done(function (data) {
    // fill in data
    myChart.setOption({
        xAxis: {
            data: data.categories
        },
        series: [{
            // find series by name
            name: 'Sales',
            data: data.data
        }]
    });
});
```


xAxis프로퍼티 속 객체에 들어가는 프로퍼티
type : 축에 들어갈 데이터를 설정(data프로퍼티가 있다면 명시 안해도 됌)
boundaryGap: true(default)면 0~첫번째카테고리 여백, 마지막카테고리~여백, false면 여백없음



series프로퍼티속 배열의 객체에 들어가는 프로퍼티
data(필수): 
type(필수): line이면 라인차트, bar면 바차트
smooth : true면 곡선, false(default)면 직선
areaStyle : 그래프 밑의 영역을 채울 것인지

