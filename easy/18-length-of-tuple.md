# Length of Tuple

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00018-easy-tuple-length/README.ko.md#length-of-tuple--)

# 풀이

```ts
type Length<T extends readonly any[]> = T['length'];
```

`as const`는 `type assertion`(타입 단언)의 한 종류로써 리터럴 타입의 추론 범위를 줄이고 값의 재할당을 막기 위한 목적으로 만들어졌습니다.

문제에서 `const tesla = ['tesla', 'model 3', 'model X', 'model Y'] as const` 이런 식으로 값이 const로 단언이 되어서 들어옵니다. 단언된 값을 `typeof`로 받아오면 `readonly` 속성이 붙어있습니다.

그래서 `T extends readonly any[]`로 `T` 값은 배열 형태로 받을건데, 해당 배열은 readonly 속성이 붙어있다.
라는 조건을 붙여줍니다.

그리고 그렇게 넘어온 `T`는 `length` 속성을 가지고 있습니다. (배열임을 알고 있음) 그래서 `T['lenght']`로 길이를 반환해주면 됩니다.
