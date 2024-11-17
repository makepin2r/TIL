# Union Type, Intersection Type
## Union Type
`|` 연산자를 이용해 두 개 이상의 타입을 하나의 타입으로 사용하는 방식.  
유니온 타입으로 정의된 값은 유니온 타입 내의 한 가지 타입을 충족해야 한다.  
```typescript
// 타입 정의 시
type type1 = string | number; // 자료형을 합친 경우
type type2 = 'apple' | 'banana'; // 특정 값을 합친 경우
```
### 활용 예시
질문: 타입으로 지정할 수 있는 값 or 자료형의 범위는 어디까지?

## Intersection Type
두 개 이상의 타입을 병합한 형태의 타입을 사용하는 방식.  
질문: Object 형태의 두 타입 내 같은 이름의 속성이 존재한다면, 어떤 것을 따르는지? 에러가 발생하는지?

---
#### 레퍼런스
- [타입스크립트 핸드북](https://joshua1988.github.io/ts/guide/operator.html#union-type)
