# BEM (Block Element Modifier)

css 구조를 개선시키기 위한 css 방법론이다.
구성 요소의 구조, 목적, 기능에 근거하는 클래스 이름을 짓는데 구조적인 방법을 제시한다.  

BEM의 기본 구조는 Block, Element, Modifer로 구성된다.

- Block: 독립적이고 분리할 수 있는 일종의 컨테이너
- Element: Block을 구성하는 요소. Block 내에서만 의미를 가지는 의존적인 형태
- Modifier: Block 또는 Element의 속성을 정의

## Block
독립적이고 분리할 수 있는 일종의 컨테이너.  
같은 기능을 위해서 필요한 것들을 모아두고 레이아웃 배치의 역할이다.

클래스의 이름을 정의할 때, 해당 Block의 목적을 기술해야 하며, Block 자체의 형태는 고려하지 않는다.  
> ex) button, header, modal, textarea ...
```html
<button class="button">...</button>
<header class="header">...</header>
<div class="modal">...</div>
<textarea class="textarea">...</textarea>
```

Block은 환경에 영향을 받으면 안된다. 이를테면, margin, top, left 값을 조절하는 등 여백이나 위치를 설정하면 안된다.  
Block은 재사용 가능하게 독립성을 보장받아야 한다.

Block은 중첩이 가능하다.

## Element
Block을 구성하는 요소. Block 내에서만 의미를 가지는 의존적인 형태  
Element는 두 개의 언더바(__)로 표시한다.  
두 개로 표시하는 이유는, Block 이름 자체에 하이픈 및 언더바가 사용될 수 있기 때문에 네이밍에 혼동을 주지 않도록 위함이다.
```html
<div class="qna-form">
    <p class="qna-form__text">
        ...
    </p>
</div>
```

Element는 중첩이 가능하다.
```html
<div class="block">
    <ul class="block__ul">
        <li class="block__li"></li>
    </ul>
</div>
```
여기서 block__li를 block__ul의 하위 Element로 보지 않고 똑같은 block의 Element로 취급한다.  
따라서 css 작성에 캐스케이딩을 여러번 해줄 필요가 없다.  

