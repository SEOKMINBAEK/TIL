# 엄격한 null 검사
리터럴로 좁혀진 유니언은 **엄격한 null 검사**(strict null checking)라 부르는 타입 시스템 영역인,
'잠재적으로 정의되지 않은 undefined 값'으로 작업할 때 두드러진다.  
> null과 undefined : 둘 다 자기 자신, 오직 하나의 리터럴 값만 가짐  

타입스크립트는 '십억 달러의 실수'를 바로잡기 위해 엄격한 null 검사를 사용한다.

## 십억 달러의 실수
다른 타입이 필요한 위치에서 null 값을 허용하는 많은 타입 시스템을 가리키는 업계 용어  
```typescript
const firstName: string = null;
```
엄격한 null 검사가 없는 언어에서는 string 타입 변수에 null 할당이 허용된다.

타입스크립트 컴파일러 옵션 중 **strictNullChecks**는 엄격한 null 검사의 활성화 여부를 결정한다.  
```typescript
// strictNullChecks = false
let nameMaybe = Math.random() > 0.5
    ? "Marco"
    : undefined;

nameMaybe.toLowerCase();
// Potential runtime error:  Cannot read properties of undefined (reading 'toLowerCase')
```

```typescript
// strictNullChecks = true
let nameMaybe = Math.random() > 0.5
    ? "Marco"
    : undefined;

nameMaybe.toLowerCase();
//~~~~~~~
// Error: 'nameMaybe' is possibly 'undefined'.
```

엄격한 null 검사가 활성화되면,  
코드가 null 또는 undefined 값으로 인한 잠재적인 충돌을 확인한다.  

일반적으로 엄격한 null 검사를 활성화해야 모범적이며,  
그렇게 해야만 충돌을 방지하고 십억 달러의 실수를 제거할 수 있다.

## 참 검사를 통한 내로잉
자바스크립트 boolean 문맥에서, false, 0, -0, 0n, "", null, undefined, NaN 처럼 falsy로 정의된 값을 제외한 모든 값(truthy)은 참으로 평가됨.

타입스크립트는 잠재적인 값 중 truthy로 확인된 일부에 한해서 변수의 타입을 좁힐 수 있다.
```typescript
let geneticist = Math.random() > 0.5
    ? "Marco"
    : undefined;

if (geneticist) {
    geneticist.toUpperCase(); // Ok: string
}

geneticist.toUpperCase();
//~~~~~~~~
// Error: 'geneticist' is possibly 'undefined'.
```

논리 연산를 통해 참 여부를 검사할 수도 있다.
```typescript
geneticist && geneticist.toUpperCase(); // Ok: string | undefined
geneticist?.toUpperCase(); // Ok: string | undefined
```

## 초기값이 없는 변수
초기값이 없는 변수는 기본적으로 undefined가 된다.
```typescript
let mathematician: string;

mathematician?.length;
//~~~~~~~~~~~
// Error: Variable 'mathematician' is used before being assigned.
```
값이 할당되기 전 해당 변수를 사용하는 경우,  
변수가 할당되기 전에 사용됬다는 오류 메시지가 출력됨

```typescript
let mathematician: string | undefined;

mathematician?.length; // Ok
```
하지만 변수 타입에 undefined가 포함되어 있는 경우 오류가 출력되지 않음.  
undefined는 유효한 타입이기 때문에 사용 전에 정의할 필요가 없기 때문