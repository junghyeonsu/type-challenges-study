# Trim Left

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00106-medium-trimleft/README.md)

# 풀이

```ts
type TrimLeft<S extends string> = S extends `${' ' | '\n' | '\t'}${infer R}` ? TrimLeft<R> : S;
```

`S`로 들어온 string 값에서 왼쪽 편에 공백 혹은 `\n` 혹은 `\t`가 들어온다면 그 공백을 제외하고 오른쪽의 값을 `TrimLeft` 타입에 재귀적으로 넣어서 공백을 없애는 방식이다.

`extends` 키워드와 `infer` 키워드를 잘 사용하자.