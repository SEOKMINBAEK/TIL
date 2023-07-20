# 그리드 시스템 (grid system)
페이지 컨텐츠를 논리적이고 일관성 있는 질서와 구조로 디자인할 수 있도록 돕는 그래픽 시스템이다.  
격자 선(Grid)에 맞춰 디자인에 규칙을 부여하고, 해상도에 상관 없이 안정적인 UI를 구현시키는데 사용한다.

그리드는 컬럼(column), 거터(gutter), 마진(margin) 세 가지 요소로 구성된다.

- 컬럼(column): 실제 컨텐츠를 포함하는 부분. 하나의 컬럼 안에는 반드시 양 옆에 거터를 동반한다.
- 거터(gutter): 컬럼과 컬럼 사이의 공간. 컨텐츠 사이의 간격이 된다.
- 마진(margin): 화면 양쪽 가장자리의 여백 공간.

## 부트스트랩 그리드 시스템
부트스트랩이 가장 많이 이용되는 이유이자 반응형 웹페이지를 만들기 위해 가장 많이 사용되는 기능
- flexbox 기반
- container, rows, column으로 컨텐츠 배치, 정렬
- 12개의 column, 6개의 grid breakpoint

### container
컨텐츠를 감싸고 그리드 시스템을 사용하기 위해서는 컨테이너 요소가 필요하다.  
반응형 고정 폭 컨테이너를 만드는 **.container** 클래스,  
뷰포트의 전체 폭까지 늘어나는 **.container-fluid** 클래스가 있다.

### row
columns의 wrapper, column을 감싸주는 역할, **.row** 클래스

### col-
row에 들어가는 각각의 컨텐츠. 오직 columns만 row의 바로 하위 자식일 수 있다, **.col-\*** 클래스  
row당 가능한 12개 중 사용하려는 column 수를 나타낸다.

### gutters
column 사이의 padding을 지정, **.gx-\***, **.gy-\***, **.g-\*** 클래스

### offset
지정한 만큼의 column 공간을 무시하고 다음 공간부터 적용, **.offset-\*** 클래스

### nesting
row > col-* > row > col-*의 방식으로 중첩 사용 가능