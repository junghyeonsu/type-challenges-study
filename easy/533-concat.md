# Concat

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00533-easy-concat/README.ko.md)

# 풀이

```ts
type Concat<T extends unknown[], U extends unknown[]> = [...T, ...U];
```

어떤 정답에 아래와 같이 `any`로 배열의 타입을 결정하는 정답이 있었다.

```ts
type Concat<T extends any[], U extends any[]> = [...T, ...U];
```

`any`와 `unknown`의 차이는 구글링을 하면 잘 나오지만 간단하게 말해서
- `any`: 모든 타입을 허용한다. 그냥 모든 타입에 대해서 검사를 하지 않는다.
- `unknown`: 모든 타입을 허용한다. 프로퍼티나 연산을 하는 경우에는 컴파일러가 타입 체킹을 한다. 그래서 사전에 에러를 방지할 수 있다.

그래서 `any`와 `unknown` 둘 중 하나를 사용한다면 타입 체킹이 조금 더 가미된 `unknown`을 사용하는 것이 조금 더 낫겠다.

그래서 `<T extends unknown[], U extends unknown[]>`로 배열 타입인지 확인을 한다.
그 다음에 배열인지 확인을 했으니 배열과 관련된 연산을 수행할 수 있는데
배열과 관련된 연산중에 우리는 스프레드 연산자를 이용해서 배열 두 개를 하나의 배열로 만들 수 있다.
`[...T, ...U]` 이런식으로 `T`로 들어온 배열의 요소들을 나열해주고, `U`로 들어온 배열의 요소도 똑같이 나열해주면
`concat`을 한 것 같은 연산을 수행할 수 있다.
