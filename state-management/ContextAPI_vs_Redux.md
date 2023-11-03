# Context API vs Redux

먼저 컨텍스트를 사용하면 prop 체인이나 prop 드릴링을 하지 않을 수 있다.

Context와 ContextProvider 컴포넌트를 중심으로 상태관리가 가능하다.

## 리액트 컨텍스트의 잠재적인 단점

잠재적이라 함은 구축하는 앱에 따라 중요하지 않을 수 있다.

컨텍스트와 리덕스 모두 중요하기 때문에 둘 중 하나를 선택해야하는 의사결정의 개념이 아니다. 둘 다 사용이 가능.

- 설정, 상태관리의 복잡도 (Complex Setup/Management)  
   소규모 프로젝트 에서는 문제 되지 않을 가능성이 높다. 하지만 대규모 앱 프로젝트에서는 문제가 될 수 있다.  
   다수의 컴포넌트나 전체 앱에 영향을 미치는 다양한 상태를 관리하는 ContextProvider 컴포넌트가 아주 많이 생기게 된다. 이는 결과적으로 아주 심하게 중첩된 JSX 코드를 만들 수 있게된다.

  ```javascript
  return (
    <AuthContextProvier>
      <ThemeContextProvider>
        <UIInteractionContextProvider>
          <MultistepFormContextProvider>
            <UserRegistration />
          </MultistepFormContextProvider>
        </UIInteractionContextProvider>
      </ThemeContextProvider>
    </AuthContextProvier>
  );
  ```

  만약 앱의 전체 상태와 다양한 모든 상태들을 관리하기 위해 큰 컨텍스트 하나에 관리한다면 하나의 컨텍스트와 프로바이더 컴포넌트를 유지하고 관리하기가 어려워 질 수 있다.

  큰 컨텍스트 하나가 앱의 모든 상태(인증, 테마, 사용자 입력, 모달 표시 여부 등)들을 관리하게 된기 때문.

  결국 컨텍스트를 상태별로 분리하면 중첩된 JSX코드가 발생하고, 하나로 통합하면 컨텍스트의 복잡도가 증가한다.

- 성능 (Performance)  
   리액트 팀의 공식 언급에 따르면, 테마 변경, 인증 같은 저빈도 업데이트에는 적합하나, 데이터의 변경이 잦은 고빈도 업데이트 같은 경우에는 적합하지 않다고 한다.

  또한 유동적인 상태 확산을 대체할 수 없다고도 하였다.

  리덕스는 유동적인 상태 관리 라이브러리로써,  
   요약하자면 모든 시나리오, 모든 경우에서 리덕스를 대체할 수는 없다고 언급하였다.

  또한 리덕스는 Redux Devtools라는 강력한 디버깅 도구를 지원한다.

## 결론

해결하려는 문제에 접합한 방식을 선택하라.

- 단순 전역 상태관리, prop drilling을 피하는 것이 목적이라면 Context
- 대규모 프로젝트, 상태관리 외의 기능, 혹은 미들웨어, 디버깅 도구가 필요하다면 Redux
