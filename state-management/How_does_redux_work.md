# Redux의 작동 방식

리덕스는 애플리케이션에 있는 하나의 중앙 데이터 저장소이다.(Central Data Store)

여기서 데이터는 상태(state)를 의미하고 리덕스는 정확히 한개의 저장소만을 갖는다. 그리고 앱 전체의 모든 상태를 저장한다.

## 구독 (Subscription)

궁극적으로 컴포넌트에서는 중앙 저장소의 데이터를 사용할 수 있다.  
저장소의 데이터가 변경되면 컴포넌트는 그걸 인지해서 그에 맞춰 대응하고 UI를 업데이트 한다.

그러기 위해선 컴포넌트는 저장소에 대한 구독을 설정한다.  
컴포넌트가 저장소를 구독하고 데이터가 변경될 때마다, 저장소는 컴포넌트에 알림(Notify)을 주고 컴포넌트는 다시 필요한 데이터를 받게 된다.

## 변경 (Mutates)

저장소의 데이터는 상태이기 때문에 변경이 필요할 수 있다.

변경에 있어서 아주 중요한 규칙이 하나 있다.

컴포넌트는 절대로 저장된 데이터를 직접 조작하지 않는다.  
데이터는 저장소에서 컴포넌트로 흐르며, 절대 반대 플로우로 흐르지 않는다.

그 대신 리듀서 개념을 이용한다.

리듀서 함수는 저장소 내 데이터의 변경을 담당한다.

리듀서 함수는 입력을 받아서, 입력을 변환하거나 줄여 새로운 출력을 뱉어내는 일반적인 함수형 프로그래밍 개념이다.

리덕스에서 리듀서를 간략히 정리하면, 입력에 따라 새로운 상태를 뱉어내며, 새로운 상태는 기존 상태를 대체한다.

## 전송 (Dispatch)

리듀서 함수가 데이터를 변경하기 위해서는 함수의 트리거가 필요하다.  
그 역할은 컴포넌트가 담당하기 때문에 컴포넌트와의 연결이 필요하다.

액션(Action)이라는 개념을 사용하여 컴포넌트는 액션을 전송한다.

액션은 단순한 자바스크립트 객체이며, 객체는 리듀서가 수행해야 할 작업을 설명한다.

리덕스는 컴포넌트가 전송한 액션을 리듀서로 전달하고, 리듀서는 수행해야할 작업에 대한 설명, 즉 액션 객체를 입력받게 된다. 따라서 액션에 맞는 작업을 리듀서가 수행하게 된다.

리듀서는 새로운 상태를 뱉어내고, 실제 저장소의 기존 상태를 대체하게 된다.

##

결과적으로 리덕스는 위 과정들을 통해 저장소 내 상태를 변경하고 컴포넌트에 전달하게 된다.

즉, 컴포넌트는 직접 저장소 내 상태를 직접 조작하지 않고, 상태 변경에 대한 액션 객체를 저장소에 전달하며,  
저장소내 리듀서 함수가 새로운 상태를 뱉어 내 기존 상태를 대체하게 된다.

1. 구독중인 컴포넌트가 액션을 전송
2. 전달받은 액션을 리듀서 함수에 입력
3. 리듀서 함수는 전달받은 액션을 토대로 새로운 상태를 출력
4. 저장소는 기존상태에서 새로운 상태로 대체 및 구독중인 컴포넌트에 알림 전송
5. 알림을 받은 컴포넌트는 새로운 상태를 받고 UI를 업데이트