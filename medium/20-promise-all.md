# Promise.all

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00020-medium-promise-all/README.md)

# 풀이

```ts
declare function PromiseAll<T extends unknown[]>(values: readonly [...T]): Promise<{
  [P in keyof T]: T[P] extends Promise<infer R> ? R : T[P]
}>
```

`PromiseAll`로 들어온 `T`를 하나 하나 돌아가면서 `Promise` 타입인지 확인하면서 알맞은 타입을 반환한다.

들어오는 `T` 타입이 단언 형태로 들어오기 때문에 `readonly`를 붙여주지 않으면 에러가 난다.
