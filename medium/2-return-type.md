# Get Return Type

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00002-medium-return-type/README.ko.md)

# 풀이

```ts
type MyReturnType<T> = T extends (...args: any) => infer K ? K : never;
```

### 1.

`T extends (...args: any) => infer K ? K : never`는 자세히보면 `조건 ? true: false`와 같다.

우리는 `T`로 들어온 함수의 반한 값을 다시 내보내야 한다.

그러기 위해서는 우선 들어온 `T`가 함수인지 확인하기 위해서 삼항연산자를 통해 확인.

그리고 `infer K`를 통해서 조건문에서 반환 값을 임시 변수로 생성

그리고 함수인 것이 맞다면 `K`를 그대로 출력하고, 아니라면 에러는 내지 않는 반환 값 `never`를 반환하면 끝
