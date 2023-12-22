# Tuple

```typescript
const person = {
  name: "Seokmin Baek",
  age: 26,
  hobbies: ["Sports", "Programming"],
  role: [1, "author"],
};
```

person 객체안에 role 속성에는 숫자와 문자열 각 1개로 구성된 식별자를 갖는 배열이 있다.  
person 객체의 타입을 명시하지 않으면 타입스크립트는 해당 role 속성을 유니온 타입으로 추론하게 된다. `(string | number)[]`

만약 role 속성이 정확히 2개의 요소만을 갖어야만 하며, 해당 요소들의 타입이 고정되어야 하는 형태라면,  
위처럼 타입스크립트의 추론에 의한 타입으로는 정확한 구조를 유지할 수 없게 된다.

```typescript
person.role[1] = 10;
person.role = [0, "admin", "user"];
```

role 속성은 요소의 순서와 상관없이 숫자와 문자열 타입을 모두 허용하기 때문에 첫 번째 코드처럼 특정 요소 타입의 변경이허용되는 문제점이 있다.  
또한 추론된 유니온 타입은 요소의 개수를 제한하지 않기 때문에 요소의 추가 삽입 혹은 삭제가 가능해진다.

만약 role 속성의 구조를 명확하게 제한하고 싶다면, person 객체 타입을 명시하여 role 속성이 튜플임을 정의해주어야 한다.

```typescript
const person: {
  name: string;
  age: number;
  hobbies: string[];
  role: [number, string];
} = {
  name: "Seokmin Baek",
  age: 26,
  hobbies: ["Sports", "Programming"],
  role: [1, "author"],
};
```

person 객체의 타입을 명시함으로써, role 속성은 정확히 두 개의 요소를 갖고, 첫 번째 타입은 숫자, 두 번째 타입은 문자열로만 이루어진 구조만을 허용하게 된다.  
이로써, 이전과 같이 role 속성을 변경하려 할 때, 제한된 구조를 벗어나게 되면 타입스크립트는 오류를 나타내준다.

```typescript
person.role[1] = 10;
//~~~~~~~~~~~~ 'number' 형식은 'string' 형식에 할당할 수 없습니다.
person.role = [0, "admin", "user"];
//~~~~~~~~~ 소스에 3개 요소가 있지만, 대상에서 2개만 허용합니다.
```

다만 일부 맹점도 존재하는데,

```typescript
person.role.push("admin");
```

위와 같이 문자열 타입의 요소를 push를 통해 추가하게 되어도, 타입스크립트는 오류를 나타내지 않는다.  
push, pop, unshift, shift 메소드를 통한 요소의 추가, 삭제는 튜플에서 허용되는 일종의 예외이다.  
타입스크립트는 해당 조작을 오류로 인식하지 않는다.

만약 해당 메소드를 통해 튜플을 조작할 수 없도록 만드려면, readonly 키워드를 통해 수정이 불가능하도록 해야한다.

만약 몇 개의 값을 배열에 담을지가 명확하고, 각 값의 타입도 미리 알고있다면 배열보다는 튜플을 사용하여 작업하여 데이터 타입을 더 명확하고 엄격하게 처리할 수 있다.
