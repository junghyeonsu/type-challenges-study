# Exclude

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00043-easy-exclude/README.ko.md)

# 풀이

```ts
type MyExclude<T, U> = T extends U ? never : T;
```

타입 조건문을 사용하고 싶다면 `extends` 키워드를 사용해서 조건을 만들 수 있다.

그래서 `T extends U`로 U가 T에 속하는지를 보고,

만약 속한다면, 제거할 타입이므로 없다는 의미를 뜻하지만, 에러를 일으키지 않는 `never`를 반환하고

속하지 않는다면 그대로 그 속성을 반환한다.
