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
   
   ※ 명시적 스타일 커스터마이징 (itemStyle, lineStyle, areaStyle, label, ...)
   
      
      
}



● 테마 지정
var chart = echarts.init(dom, 'light');           //테마 지정
var chart = echarts.init(dom, 'dark');

위의 두 개의 테마 외에는 다운 받아서 사용해야한다.


● 팔레트 지정



xAxis프로퍼티 속 객체에 들어가는 프로퍼티
type : 축에 들어갈 데이터를 설정(data프로퍼티가 있다면 명시 안해도 됌)
boundaryGap: true(default)면 0~첫번째카테고리 여백, 마지막카테고리~여백, false면 여백없음



series프로퍼티속 배열의 객체에 들어가는 프로퍼티
data(필수): 
type(필수): line이면 라인차트, bar면 바차트
smooth : true면 곡선, false(default)면 직선
areaStyle : 그래프 밑의 영역을 채울 것인지

