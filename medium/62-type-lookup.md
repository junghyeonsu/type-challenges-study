# Type Lookup

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00062-medium-type-lookup/README.md)

# 풀이

```ts
type LookUp<U, T> = U extends { type: infer _type, [properties: string]: any }
  ? _type extends T ? U : never
  : never;
```

두 번의 조건으로 `U`를 반환하는 것이 목적인 타입

첫 번째 조건은 `U extends { type: infer _type, [properties: string]: any }`이다. 말 그대로 들어온 `U` 타입이 `{ type: infer _type, [properties: string]: any }`의 구조를 만족하는지, 그리고 `type`의 프로퍼티에 해당하는 value는 `_type` 변수에 담겠다는 의미다.

만약 첫 번째 조건을 만족한다면 두 번째 조건을 확인한다. `_type` 변수가 `T`에 속하는지 확인하고 속한다면 `U`를 반환한다.

그게 아니라면 전부 `never`을 반환한다.
