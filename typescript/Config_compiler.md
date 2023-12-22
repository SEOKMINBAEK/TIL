# 컴파일러 설정

## compilerOptions

컴파일 설정에 관련된 옵션들을 제어한다. `"compilerOptions": {}`

- `"target"`: 컴파일 시 생성될 자바스크립트 표준을 설정한다.

- `"lib"`: 컴파일 시 필요한 내장 라이브러리를 지정할 수 있다. ex) DOM  
  기본값은 target 속성에 지정된 자바스크립트 표준에 따라 지정된다.

- `"allowJs"`: 자바스크립트 파일을 컴파일에 포함시킨다. 컴파일된 자바스크립트 파일을 이중으로 컴파일 하지 않도록, exclude나 include 설정을 조정해야 한다.

- `"checkJs"`: 자바스크립트 파일을 컴파일에 포함시키지는 않지만, 구문을 검사하고 잠재적 오류를 보고한다.

- `"jsx"`: 리액트에서 .tsx 확장자의 컴파일 결과 jsx 코드를 어떻게 컴파일할지 결정한다.

- `"sourceMap"`: .js.map 파일을 생성하여 브라우저 개발자 도구에서 타입스크립트 소스를 통해 디버깅이 가능하도록 도와준다.

- `"outDir"`: 컴파일 시 생성된 자바스크립트 파일의 저장위치를 설정한다.

- `"rootDir"`: 컴파일 시 rootDir 위치 기준으로만 outDir 위치에 자바스크립트 파일을 저장한다.

- `"removeComments"`: 컴파일 시 타입스크립트 파일에 작성된 주석을 자바스크립트 파일에서 제거한다.

- `"noEmit"`: 컴파일러가 타입스크립트 파일을 검사하고 오류를 보고하지만 자바스크립트 파일로 컴파일 하지 않는다.

- `"downlevelIteration"`: 특정 반복문에 대해 비교적 오래된(down level) 자바스크립트 런타임 환경에서 수행되도록 해준다.

- `"noEmitOnError"`: 타입스크립트 파일에 오류가 있을 시, 자바스크립트 파일 생성 여부를 설정한다.

- `"strict"`: strict 옵션과 관련된 모든 옵션을 일괄 설정 한다.

- `"noImplicitAny"`: 암묵적인 any 타입의 허용 여부를 설정한다.

- `"strictNullChecks"`: 잠재적 null 값에 대한 허용 여부를 설정한다.

- `"noUnusedLocals"`: 사용하지 않는 지역변수가 있는 경우 오류로 보고한다.

- `"noUnusedParameters"`: 사용하지 않는 매개변수가 있는 경우 오류로 보고한다.

- `"noImplicitReturns"`: 함수가 조건에 따라 반환 여부가 다른 경우 오류로 보고한다.

## exclude

컴파일에서 제외할 파일 혹은 폴더를 설정한다. `"exclude": []`

파일명 ex) `"filename.ts"`  
확장자 ex) `"*.dev.ts"`  
폴더명 ex) `"node_modules"` - 종속된 라이브러리에 타입스크립트 코드가 들어있는 경우, 컴파일 프로세스가 느려지고, 중지될 수 있다. 일반적으로 node_modules 폴더는 제외한다. 또한 exclude 옵션을 전혀 지정하지 않는경우, node_modules 폴더는 자동으로 제외된다.

## include

컴파일에 포함할 파일 혹은 폴더를 설정한다. 나열되지 않은 파일은 컴파일에서 제외된다. `"include": []`

파일명 ex) `"filename.ts"`  
확장자 ex) `"*.dev.ts"`  
폴더명 ex) `"foldername"`

include와 exclude를 함께 설정하면, include를 exclude 기준으로 필터링한다.  
즉, include하는 폴더에서 일부 하위 폴더를 exclude하면, 그 폴더들은 제외된다.  
include - exclude

일반적으로는, exclude 옵션만을 사용하여 컴파일 조건을 설정한다.

## files

컴파일에 포함할 개별 파일을 설정한다. `"files": []`

파일명 ex) `"filename.ts"`

include와 달리 개별 파일만 지정할 수 있다.
