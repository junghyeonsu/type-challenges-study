# 문제 제목

> [문제 링크]()

# 풀이

```ts
type Last<T extends any[]> = T extends [...infer _, infer last] ? last : never;
```

[first of array](../easy/14-first-of-array.md) 문제와 매우 비슷하게 진행을 하면 된다.

`T`가 배열로 들어오는 것을 먼저 검증하고, `T` 배열안의 원소들을 `infer`로 앞에 부분 원소들을 전개 연산자(spread operator)로 전부 받은 다음에
마지막 원소를 `infer` 키워드로 받고, 그대로 내보내면 된다.
