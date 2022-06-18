# Pop

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00016-medium-pop/README.md)

# 풀이

```ts
type Pop<T extends unknown[]> = T extends [...infer rest, infer _] ? rest : never;
```

배열을 다루는 문제는 대부분 비슷하게 흘러간다. `T`로 받은 배열의 원소들을 `infer` 키워드로 받은 다음에 잘 처리해주면 된다.

pop을 구현하기 위해서는 제일 마지막 원소를 빼고 나머지 원소들을 반환하면 되는데 `infer` 키워드와 `전개 연산자`를 이용해서 맨 마지막 원소 빼고 앞 부분을 받고,

해당 원소를 반환하면 된다.