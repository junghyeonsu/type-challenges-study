# Omit

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00003-medium-omit/README.ko.md)

# 풀이

```ts
type MyOmit<T, K extends keyof T> = { // 1
  [key in keyof T as key extends K ? never : key]: T[key] // 2
}
```

### 1.

우선 `K` 값에 대한 제약조건을 걸어준다.

`T` 값의 키들이 `K`로 들어왔는지 확인하고 아니라면 에러를 띄울 것이다.

### 2.

맵드 타입을 이용한다. 
 
`key in keyof T` 과정은 `key`로 설정할 값들이 `T`의 키 값인지 확인한다.

그리고 `as key extends K` 과정은 그렇게 들어온 `key`가 `K`에 속하는지 다시 조건으로 확인한다.

속한다면 `Omit` 해야하므로, `never`을 반환하고 속하지 않으면 그대로 `key`를 반환한다.
