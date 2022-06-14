# Deep Readonly

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00009-medium-deep-readonly/README.ko.md)

# 풀이

```ts
type DeepReadonly<T> = {
  readonly [K in keyof T]: keyof T[K] extends never ? T[K] : DeepReadonly<T[K]>
}
```

우선 해당 `DeepReadOnly`를 재귀적으로 돌면서 전부 `readonly`를 붙여준다.

`readonly [K in keyof T]`에서는 평범하게 맵드 타입을 이용해 돌면서 `readonly`를 붙여준다.

그 뒤에 `keyof T[K] extends never ? T[K] : DeepReadonly<T[K]>`에서는 역시 삼항 연산자를 이용해서 더 깊은 계층구조가 없는지를 먼저 파악하고, 더 깊은 계층 구조가 있다면 `DeepReadonly<T[K]>`를 통해 재귀적으로 돈다.
