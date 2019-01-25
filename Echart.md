# Study
Echart

echart 설치
공식 홈페이지에서 다운
github에서 echart 최신 버전
npm 사용
online build tool 사용

echarrt3는 더 이상 패키지를 로드하기 위해 amd 사용 안하고 스크립트 태그 이용

너비와 높이, id를 지닌 DOM객체를 먼저 준비해야한다

echarts.init을 통해 인스턴스를 생성하고, 정의한 차트의 내용을 setOption메서드를 이용하여 생성한다.


xAxis프로퍼티 속 객체에 들어가는 프로퍼티
type : 축에 들어갈 데이터를 설정(data프로퍼티가 있다면 명시 안해도 됌)
boundaryGap: true(default)면 0~첫번째카테고리 여백, 마지막카테고리~여백, false면 여백없음



series프로퍼티속 배열의 객체에 들어가는 프로퍼티
data(필수): 
type(필수): line이면 라인차트, bar면 바차트
smooth : true면 곡선, false(default)면 직선
areaStyle : 그래프 밑의 영역을 채울 것인지
