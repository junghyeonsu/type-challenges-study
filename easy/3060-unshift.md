# Unshift

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/03060-easy-unshift/README.md)

# 풀이

```ts
type Unshift<T extends unknown[], U> = [U, ...T];
```

`T`는 배열로 들어오기 때문에 `extends` 키워드로 조건을 걸어주게 되면 구현 부분에서 스프레드 연산자(`...`)를 사용할 수 있다.

새로운 배열에 새롭게 들어온 `U`를 이어주고, 기존에 있던 `T`를 스프레드 연산자로 나열하면 끝
