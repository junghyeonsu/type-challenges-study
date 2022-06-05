# Awaited

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00189-easy-awaited/README.ko.md)

# 풀이

```ts
type MyAwaited<A extends Promise<unknown>> = A extends Promise<infer B> 
  ? B extends Promise<unknown> ? MyAwaited<B> : B
  : never;
```

해당 문제는 `Promise`를 재귀적으로 돌면서 벗겨주어야 하는 문제다.

```ts
// @ts-expect-error
type error = MyAwaited<number>
```

테스트케이스에서 위의 조건이 있었기 때문에, Promise 객체 형태의 타입이 들어오지 않으면
에러를 일으켜야 한다. 그래서 처음에 `type MyAwaited<A extends Promise<unknown>>`를 통해서 에러를 감지해주었다.

그 이후에는 재귀적으로 돌아야 하는지 확인하는 조건이 필요하다.
만약 `Promise<Promise<Promise<number>>>` 와 같은 타입이 있다고 생각하면 `Promise`를 한 겹씩 벗겨서 최종 타입에 도달해야 한다.

타입에서는 `extends`로 조건문을 달성할 수 있으니까 `A extends Promise<infer B>`로 조건문을 만들어준다.
`A` 타입이 `Promise` 객체인지 확인한다. 만약에 `Promise` 객체라면 두 번째 분기로 들어간다.

`B extends Promise<unknown> ? MyAwaited<B> : B` 두번 째 분기에서도 한 번더 임시 타입 변수 `B`가 Promise 객체인지 확인을 한다.
만약 또 Promise가 있는 상황이라면 해당 `MyAwaited`를 한 번 더 호출을 하면서 재귀적으로 돌린다.
만약 그게 아니라면 `Promise`가 전부 벗겨진 상황이니까 `B`를 그대로 출력하면 된다.
