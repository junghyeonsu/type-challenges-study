# Chainable Options

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00012-medium-chainable-options/README.md)

# 풀이

```ts
type Chainable<T extends {} = {}> = {
  option<K extends string, V = unknown>(key: K, value: V): Chainable<T & Record<K, V>>;
  get(): T;
}
```

`option` 프로퍼티에 대해서 들어오면 `Chainable`을 재귀적으로 호출해주어야 한다.

`<K extends string, V = unknown>`에서 `K`로 들어오는 값은 객체의 key이므로 string을 만족하도록 하고, `V`는 어떤 값이 들어올지 모르니 `unknown`을 할당한다.

그리고 함수의 값에는 `Chainable<T & Record<K, V>>`으로 재귀적으로 돌도록 한다.

`Record`는 `Record<Key, Type>` 형태로 객체를 키는 `Key` 타입이고, `Type`에는 value의 타입이 들어가도록 설정해서 객체에 접근할 수 있는 유틸 함수다.

# 참고

- [[TypeScript]Record Type 사용 방법](https://developer-talk.tistory.com/296)