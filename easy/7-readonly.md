> [문제 링크](https://github.com/type-challenges/type-challenges/blob/main/questions/00007-easy-readonly/README.ko.md)

# 풀이

```ts
// 우선 제네릭으로 들어온 값에 대해서 맵드 타입으로 돌면서 적용시켜야 한다고 생각했다
// [K in keyof T]에서 T에 들어온 key값들만 뽑아서 맵드 타입으로 key값을 적용시켜 주고
// 타입은 그대로 T[K]로 들어온 제네릭과 똑같이 적용
// readonly는 key값에 적용되는 키워드이기 때문에 맵드 앞에 readonly를 적용시켜주었다.
type MyReadonly<T> = {
  readonly [K in keyof T]: T[K]
}
```
