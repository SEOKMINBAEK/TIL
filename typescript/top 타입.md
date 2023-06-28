# top 타입
**top** 타입은 시스템에서 가능한 모든 값을 나타내는 타입이다.  
모든 다른 타입의 값은 타입이 top인 위치에 제공될 수 있다. 즉, 모든 타입은 top 타입에 할당할 수 있다.  

## any
**any** 타입은 모든 타입의 위치에 제공될 수 있다는 점에서 top 타입처럼 작동할 수 있다.  
any는 일반적으로 **console.log**의 매개변수와 같이 모든 타입의 데이터를 받아들이는 위치에서 사용된다.  
```typescript
let anyValue: any;
anyValue = "Lucille Ball"; // Ok
anyValue = 123; // Ok

console.log(anyValue); // Ok
```
다만 any는 타입스크립트가 해당 값에 대한 타입 검사를 비활성화 하기 때문에 타입 오류를 보고하지 않을 수 있다.  
어떤 값이든 될 수 있음을 나타내려면 unknown 타입이 훨씬 안전하다.

## unknown
타입스크립트에서 **unknown** 타입은 진정한 **top** 타입이다.  
모든 객체를 unknown 타입의 위치로 전달할 수 있다는 점이 any와 유사하다.  
unknown 타입과 any 타입의 주요 차이점은 타입스크립트는 unknown 타입의 값을 훨씬 더 제한적으로 취급한다.  
- 타입스크립트는 unknown 타입 값의 속성에 직접 접근할 수 없다.
- unknown 타입은 top 타입이 아닌 타입에는 할당할 수 없다.
```typescript
function greetComedian(name: unknown) {
    console.log(`Announcing ${name.toUpperCase()}!`);
    //                        ~~~~
    // Error: 'name' is of type 'unknown'.
}
```
타입스크립트가 unknown 타입인 **name**에 접근할 수 있는 유일한 방법은,  
**instanceof**나 **typeof** 또는 타입 어서션을 사용하는 것처럼 값의 타입이 제한된 경우이다.
```typescript
function greetComedianSafety(name: unknown) {
    if (typeof name === "string") {
        console.log(`Announcing ${name.toUpperCase()}!`); // Ok
    } else {
        console.log("Well, I'm off.");
    }
}

greetComedianSafety("Betty White"); // [LOG]: "Announcing BETTY WHITE!"
greetComedianSafety({}); // [LOG]: "Well, I'm off." 
```

unknown 타입 값은 앞서 얘기한 두가지 제한으로 인해 any 타입보다 훨씬 안전하다.  
가능한 any 대신 unknown 타입의 사용이 권장된다. 