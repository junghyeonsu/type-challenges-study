# Trim

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00108-medium-trim/README.md)

# 풀이

```ts
type Trim<S extends string> = S extends `${' ' | '\t' | '\n'}${infer R}` | `${infer R}${' ' | '\t' | '\n'}`
  ? Trim<R>
  : S;
```

`S`로 받은 `string` 값의 왼쪽과 오른쪽 중에 공백이 하나라도 존재한다면 재귀적으로 제거하는 방식
