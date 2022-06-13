# ReadOnly 2

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00008-medium-readonly-2/README.ko.md)

# 풀이

```ts
type MyReadonly2<T, K extends keyof T = keyof T> = { // 1
  [key in keyof T as key extends K ? never : key]: T[key] // 2
} & { readonly [key in keyof T]: T[key] } // 3
```

### 1.

제네릭 타입에 대한 제약조건을 명시한다.

`T`는 잘 알겠는데, `K extends keyof T = keyof T`는 무엇일까?

`K extends keyof T`는 우선 `K`를 받긴 받을건데, `T`의 key 값들중에서만 받을거야. 라는 뜻이다.

만약에 그렇게 하지 않으면 에러가 뜬다. 근데 `T`의 key가 정확하게 명시가 되지 않고 내려오는 테스트케이스도 만족을 시켜야한다.

```ts
// 1번 테스트 케이스 (key값이 제대로 명시가 안되어있다.)
Expect<Alike<MyReadonly2<Todo1>, Readonly<Todo1>>>
```

이럴 때는 기본 값을 설정해놓을 수 있다. `= keyof T`는 만약 `K extends keyof T`를 만족하지 못하면 `K`는 `keyof T`로 기본값을 정하겠다 라는 뜻이다.

### 2.

`[key in keyof T as key extends K ? never : key]`를 살펴보자.

앞 부분인 `key in keyof T`은 `key` 라는 값은 `T`의 `key` 값 중에 하나여야 한다 라는 뜻이다.

그리고 뒤에 `as key extends K`는 추가적으로 그렇게 들어온 `key` 값이 `K`에 속하는지 조건을 확인한다.

만약 속하게 된다면 `readonly` 속성으로 넣어야 하니까 우선은 `never`로 넘겨둔다.

만약 속하지 않는다면 `key`를 그대로 반환해서 `readonly`를 붙이지 않도록한다.

### 3.

그렇게 `2`에서 `never`로 넘어온 값들은 `3`번으로 이동한다.

`readonly [key in keyof T]: T[key]`은 간단한 `ReadOnly` 문제다.

맵드 타입을 이용해서 `T`안에 있는 값들을 `readonly`를 붙여주는 모습을 볼 수 있다.
