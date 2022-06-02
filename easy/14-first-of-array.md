# First of Array

> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00014-easy-first/README.ko.md)

# 풀이

```ts
type First<T extends any[]> = T extends [infer A, ...any[]] ? A : never;
```

`T extends [infer A, ...any[]]`에서
`T extends P`는 T는 P의 타입을 만족해야 한다는 뜻이다.
그러면 위를 해석하면 T는 배열 형태를 유지해야 한다는 뜻

배열 안에서 `[infer A, ...any[]]`에서 `infer`을 알아야 한다.
infer 키워드는 일종의 `placeholder`이다.
infer는 조건문에 쓰이는 타입 중 하나를 이름 붙여서 빼 와서, 
삼항 연산자의 true절이나 false절에 사용하기 위해 사용한다. 

그래서 다시 `[infer A, ...any[]]`를 해석하면
배열중에서 첫번째 인덱스에 있는 값은 `A`라는 이름으로 뒤에 조건문에서 사용할 것이다.
그리고 뒤에 오는 것들은 무엇이 와도 상관없다는 뜻으로 `any[]`를 붙여주었다. 그리고 spread 연산자까지.

그 다음으로 조건문을 보게 되면 T가 배열임을 만족하면 배열안에서 값으로 가져온 `A`를 반환하고,
아니라면 **불가능** 이라는 의미를 가진 `never`를 반환한다. 왜냐하면 배열에 원소가 없기 때문이다.

# 참고

[조건부 타입 + infer](https://ajdkfl6445.gitbook.io/study/typescript/condition-type-+-infer#condition-type)
[타입스크립트 정의 읽기](https://driip.me/b812974b-3974-46e3-829e-1476b9b30c94)
[타입스크립트의 Never 타입 완벽 가이드](https://ui.toast.com/weekly-pick/ko_20220323)
