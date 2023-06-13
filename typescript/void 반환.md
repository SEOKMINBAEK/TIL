# void 반환 타입
일부 함수는 어떤 값도 반환하지 않음  
함수가 값을 반환하지 않는 경우 void 타입을 사용  

```typescript
function logSong(song: string | undefined): void {
    if (!song) {
        return; // Ok
    }

    console.log(`${song}`);

    return true;
    //~~~~
    // Error: Type 'boolean' is not assignable to type 'void'.
}
```

함수 타입 선언 시 void 반환 타입은 반환되는 모든 값을 무시한다. 
void 타입은 반환되는 값도 아니고, 사용하기 위한 것이 아닌 표시이다.

## never 반환 타입
never 반환 함수는 의도적으로 오류를 발생시키거나 무한 루프를 실행한다.  
```typescript
function fail(message: string): never {
    throw new Error(`Invariant failure: ${message}.`);
}

function workWithUnsafeParam(param: unknown) {
    if (typeof param !== "string") {
        fail(`param should be a string, not ${typeof param}`);
    }

    // 여기에서 Param의 타입은 string으로 알려진다.
    param.toUpperCase(); // Ok
}
```

함수가 절대 반환되지 않도록 명시하여 해당 함수 호출 후 모든 코드가 실행되지 않는다.  
fail 함수는 오류만 발생시키므로 param의 타입을 string으로 좁혀 제어 흐름 분석을 도움.
