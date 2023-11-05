# RolltheDice
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=JavaScript&logoColor=white"/>

<br/><br/>

[RolltheDice(스코어보드) 바로가기](https://woot9009.github.io/RolltheDice/)

- 스코어보드 기능의 웹앱입니다. 보드게임 및 생활스포츠 등의 상황에서 활용가능합니다.
- 8명까지 사용자가 원하는 만큼의 인원수를 입력하고, 미니게임별 순위를 저장하면, 종합 랭킹을 계산해줍니다.
- 종합랭킹은 동점자가 있을 경우, 그만큼 차순위를 건너뛰고 순위를 매깁니다.
- 하단의 라운드 기록을 클릭하면 그동안 저장한 기록이 나타납니다.

<br/><br/>
###### 인원수 입력
<img src="https://github.com/Woot9009/RolltheDice/assets/128044785/3e0ed8cf-3702-433a-a6c4-ba3ec11c7fa2" width=50% height=auto/>

<br/><br/>
###### 순위입력 및 종합랭킹 계산, 라운드별 기록
<img src="https://github.com/Woot9009/RolltheDice/assets/128044785/de60aecf-a19e-467e-9f7d-db901c489d55" width=50% height=auto/>


<br/><br/>

#### <만들며 어려웠던 점과 해결방법>
<br/>
❔: 종합랭킹의 동점자처리. (sort기능만을 사용해서 배열을 정렬하고, 배열의 인덱스를 이용해 랭킹을 매기면 동점자처리가 안되고 순차적으로 순위가 매겨짐)
<br/><br/>

❗: 동점자처리를 할 별도의 순위변수를 설정하고, if문을 활용해 동점자가 없는 일반적인 경우 순위변수는 1씩 증가, 동점자가 있을 경우 동점자의 수만큼 순위변수가 증가하도록 설정.
___

❔: 순위 입력란이 공백인 상태에서 점수입력 버튼을 누르면 null값이 전달되면서 에러.(숫자정규표현식으로는 문자 등의 입력에러는 방지가능하나, null값 입력에러를 막을 수 없었음.)

❗: 우선 점수입력 버튼을 비활성화상태로 기본값 설정. forEach를 이용해 모든 순위입력란이 공백이 아니면 점수입력 버튼이 활성화 되도록 함수선언. 이 함수를 addEventListener로 input값이 변경될 때마다 호출.
___

❔: 라운드기록의 css를 height:auto;로 설정하면 슬라이드 애니메이션 적용이 안되고 기록이 단순히 보이고 안보이는 기능만 구현.

❗: 슬라이드를 접은 상태에서의 height:0;은 자바스크립트가 계산을 하지만, 슬라이드를 펼친 상태의 height:auto;는 정확한 값을 계산하지 못해 transition이 적용이 안됨.
이럴땐 접은 상태는 max-height:0;, 펼친 상태는 max-height:100vh;로 설정하면 transition이 적용되면서 슬라이드 애니매이션 구현 가능.

<br/><br/>

##### <추후 개선점>
- 모바일 환경에서 너무 많은 인원과 너무 긴 이름을 입력시, 라운드 기록의 가시성이 떨어짐.(새로운 레이아웃 고민)
- 데이터베이스를 활용하지 않다보니 중간에 새로고침할 경우 기록이 날아감.(백엔드 추가 필요 or 로컬스토리지 활용)
