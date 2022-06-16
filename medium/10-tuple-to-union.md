# Tuple to Union

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00010-medium-tuple-to-union/README.ko.md)

# 풀이

```ts
// 1.
type TupleToUnion1<T> = T extends Array<unknown> ? T[number] : never;

// 2.
type TupleToUnion2<T extends unknown[]> = T[number];

// 3.
type TupleToUnion3<T> = T extends [infer F, ... infer REST] ? F | TupleToUnion2<REST> : never
```

1번과 2번에서 사용하는 `T[number]`은 `T`가 만약 배열로 들어온다면 해당 배열의 요소들을 나열한 것이랑 똑같습니다.

그래서 `T`로 들어오는 값이 배열인지 판단하는 로직의 위치만 다르고 나머지는 같습니다.

3번은 재귀적으로 배열의 맨 앞의 요소부터 차례차례로 union 연산을 해주는 방식입니다.

`infer` 키워드를 통해서 임시 변수로 저장하고, 맨 앞에 변수는 union 연산과 동시에 나머지 요소들은 다시 타입의 제네릭으로 넘겨 구현했습니다.

# 참고

- [What's the T[number] mean in typescript code?](https://stackoverflow.com/questions/59187941/whats-the-tnumber-mean-in-typescript-code)
- [[TypeScript]인덱스 시그니처(Index Signature) 사용 방법](https://developer-talk.tistory.com/297)