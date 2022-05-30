> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00004-easy-pick/README.md)

# 풀이

```ts
// K extends keyof T: 제네릭 제약조건을 통해서 K의 타입을 제한시킨다.
// key값은 K로 받은 key들로 제한시키고, mapped 타입으로 반복
type MyPick<T, K extends keyof T> = {
  [Key in K]: T[Key]
}
```

# 참고 한 글

- [In TypeScript, what do "extends keyof" and "in keyof" mean?](https://stackoverflow.com/questions/57337598/in-typescript-what-do-extends-keyof-and-in-keyof-mean)
- [제네릭 제약조건](https://www.typescriptlang.org/ko/docs/handbook/2/generics.html#%EC%A0%9C%EB%84%A4%EB%A6%AD-%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4-generic-constraints)
- [맵드 타입](https://joshua1988.github.io/ts/usage/mapped-type.html#%EB%A7%B5%EB%93%9C-%ED%83%80%EC%9E%85-mapped-type-%EC%9D%B4%EB%9E%80)
