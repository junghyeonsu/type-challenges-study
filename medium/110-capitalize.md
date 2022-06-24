# Capitalize

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00110-medium-capitalize/README.md)

# 풀이

```ts
type MyCapitalize<S extends string> = S extends `${infer F}${infer Rest}` ? `${Uppercase<F>}${Rest}` : S;
```

`Uppercase` 유틸함수를 이용해서 string을 대문자로 바꿀 수 있다.

`infer`과 `extends`를 잘 이용하면 된다.
