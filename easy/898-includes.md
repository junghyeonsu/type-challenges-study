# Includes

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00898-easy-includes/README.ko.md)

# 풀이

```ts
type Includes<T extends readonly unknown[], U> = T extends [infer First, ...infer Rest]
  ? Equal<U, First> extends true
    ? true
    : Includes<Rest, U>
  : false;
```

전체적인 풀이방법은 `T`로 들어온 배열을 첫번째 원소부터 하나씩 `U`와 같은지 반복적으로 확인하는 방식.

`T extends [infer First, ...infer Rest]`에서는 배열의 첫번째 원소를 infer 키워드를 통해서 `First` 변수로 담아주고, 나머지 원소는 `Rest` 변수로 infer 키워드를 통해서 만들어준다.

위 과정을 통해서 첫번째 원소를 잘 뽑아줬다면, 조건문을 통해서 `U`와 `First`가 같은지 비교하는 작업을 진행한다. 

`Equal<U, First> extends true` 요기서 `true`가 나온다면 포함이 되었다는 얘기라서 바로 `true`를 반환해주고, 아니라면 나머지 원소에 대해서 다시 `Includes`를 실행시켜준다.

그리고 애초에 `T extends [infer First, ...infer Rest]`에서 `false`가 나왔다면 배열 원소가 없다는 뜻이므로 `false`를 반환해준다.
