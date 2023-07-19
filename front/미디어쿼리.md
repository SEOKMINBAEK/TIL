# 미디어쿼리 (@media)
반응형 디자인 처리를 돕는 css 모듈

```css
@media <미디어 유형> and (조건문) {
    /* style */
}
```

미디어 유형은 생략 가능하며, 생략시 all 키워드로 동작한다.

## 중단점 (breakpoints)
대중적으로 많이 사용하는 두가지 분기포인트가 있다.

### 최소 반응형
가장 간결한 기준이다.  
디바이스를 중점으로만 구분한다.
```css
@media (max-width: 1023px) { /* 태블릿 */ }
@media (max-width: 767px) { /* 모바일 */ }
```

### 부트스트랩 반응형
웹 UI 프레임워크인 부트스트랩의 기본 미디어 쿼리 해상도이다.  
다양한 웹 UI 프레임워크에서 대부분 동일하게 적용된다. 디바이스 구분이 아닌 화면의 크기를 중점으로 구분한다.  
통상 UI 프레임워크에서 해당 중단점에 대한 클래스 키워드를 제공한다.
```css
/* width >= 1400px 와이드 데스크탑 - xxl */
@media (max-width: 1399px) { /* 데스크탑 - xl */ }
@media (max-width: 1199px) { /* 데스크탑 - lg */ }
@media (max-width: 991px) { /* 태블릿 - md */ }
@media (max-width: 767px) { /* 모바일 가로 - sm */ }
@media (max-width: 575px) { /* 모바일 세로 - xs */ }
```

## 분기 순서

### 데스크탑 기준
- 기본 CSS 작업을 가장 큰화면을 기준으로 한다.  
- max-width를 사용하여 넓은 순으로 작성(데스크탑 - 태블릿 - 모바일 순)
```css
/* default css: width >= 1400px */
@media (max-width: 1399px) {/* ... */}
@media (max-width: 1199px) {/* ... */}
@media (max-width: 991px) {/* ... */}
@media (max-width: 767px) {/* ... */}
@media (max-width: 575px) {/* ... */}
```

### 모바일 기준
- 기본 CSS 작업을 가장 작은 화면을 기준으로 한다.
- min-width를 사용하여 좁은 순으로 작성(모바일 - 태블릿 - 데스크탑 순)
```css
/* default css: width <= 575px */
@media (min-width: 576px) {/* ... */}
@media (min-width: 768px) {/* ... */}
@media (min-width: 992px) {/* ... */}
@media (min-width: 1200px) {/* ... */}
@media (min-width: 1400px) {/* ... */}
```