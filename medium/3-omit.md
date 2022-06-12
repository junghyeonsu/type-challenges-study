# Omit

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00003-medium-omit/README.ko.md)

# 풀이

```ts
type MyOmit<T, K extends keyof T> = {
  [key in keyof T as key extends K ? never : key]: T[key]
}
```

맵드 타입을 이용한다. 전체적인 과정은 `K`로 들어온 `key` 값들이 `T`에 속하는지 확인하고

속한다면 `Omit` 해야하므로, `never`을 반환하고 속하지 않으면 그대로 `key`를 반환한다.
