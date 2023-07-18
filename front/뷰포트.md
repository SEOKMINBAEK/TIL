# 뷰포트 (viewport)

웹 페이지가 렌더링 되는 화면의 영역이다.

- 브라우저에서 뷰포트는 메뉴바, 탭영역 등을 제외한 순수 화면 영역이다.  
- 뷰표트의 영역은 디바이스 크기와, 각각의 브라우저 마다 계산되는 영역이 달라 같은 웹페이지라도 환경에 따라 달라질 수 있다.
- 대부분 모바일 디바이스에서 브라우저가 전체 화면 모드일 때 뷰표트는 전체 화면이다.

```javascript
// 디바이스 화면 사이즈
screen.width;
screen.height;

// 브라우저 창 사이즈
document.body.outerWidth;
document.body.outerHeight;

// 레이아웃 뷰포트 (Layout viewport)
document.body.innerWidth;
document.body.innerHeight;

// 비주얼 뷰포트 (Visual viewport)
visualViewport.width;
vsiualViewport.height
```

뷰포트에는 레이아웃 뷰포트와 비주얼 뷰포트 두가지가 있다.

- 레이아웃 뷰포트: 고정된 화면, 사용자의 액션에 영향을 받지 않음.
- 비주얼 뷰포트: 유동적인 화면, 사용자의 액션에 영향을 받는다.

레이아웃 뷰포트는 웹 페이지가 렌더링될 고정될 사이즈이고,  
비주얼 뷰포트는 모바일에서 줌인, 내장 키보드 인터페이스 등 액션에 의해 축소될 수 있다.

데스크탑을 기반으로 설계된 웹 페이지를 작은 모바일 화면에서 모두 표시하려고 하면 컨텐츠의 배율 축소가 발생해 가독성이 떨어지게 된다.  
이럴 때 뷰포트를 설정하면 다양한 모바일 기기에서 페이지의 너비나 화면 배율을 설정할 수 있다.

## 사용 예시
```html
<meta name="viewport" content="width=device-width, inital-scale=1.0">
```
통상적으로 html 스니펫을 통해 입력하는 경우 자동 삽입된다.

### 속성
- width: 뷰포트 가로 크기, device-width는 계산된 화면 폭을 의미
- height: 뷰포트 세로 크기
- initial-scale: 시작 배율. 1일때 css 픽셀과 기기종속적인 픽셀간의 1:1 관계를 형성
- minimum-scale: 최소 배율. 기본값은 0.25
- maximum-scale: 최대 배율. 기본값은 1.6
- user-scalable: 확대/축소 기능 허용 여부. 기본값은 yes