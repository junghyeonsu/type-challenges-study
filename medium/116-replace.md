# Replace

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00116-medium-replace/README.md)

# 풀이

```ts
type Replace<S extends string, From extends string, To extends string> = From extends ''
  ? S
  : S extends `${infer H}${From}${infer T}`
    ? `${H}${To}${T}`
    : S;
```

`From`이 빈 칸이면 아무것도 변하지 않아도 괜찮으니까 그대로 `S`를 반환한다.

`From`에 값이 있어서 바꿔야 한다면 S extends `${infer H}${From}${infer T}`를 확인한다.
`From`이 담겨져 있는 부분을 확인한 다음에 `From`을 `To`로 바꾸고 나머지 양쪽은 그대로 반환하면 정답
