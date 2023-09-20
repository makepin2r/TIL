# 프로그래머스 연속된 부분 수열의 합 풀이
> 푼 날짜 : 23. 09. 20

## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/178870)
![image](https://github.com/makepin2r/TIL/assets/39889583/45912a01-ed46-46b6-b454-e5f2a47912c5)

## 나의 풀이
### 아이디어 (실패)
- offset(배열의 길이)를 1부터 지정하여 전체 배열을 순회하며 원소들의 합계가 k와 일치할 경우 리턴
**코드**
```javascript
function solution(sequence, k) {
    for(let offset = 1; offset < sequence.length; ++offset) {
        for(let i = 0; i < sequence.length; ++i){
            if(i + offset <= sequence.length 
               && sequence.slice(i, i + offset).reduce((total, val) => total + val, 0) === k){
                return [i, i + offset - 1];
            }
        }
    }
    return [0, 0];
}
```
시간 초과로 실패했다.
### 아이디어 2 
단순 반복문이 아닌 알고리즘이 필요하다 판단하여 검색한 결과 "투 포인터 알고리즘" 개념을 알게 되었다.
해당 알고리즘을 적용했을 때,
1. 인덱스 0부터 시작, 끝 포인터를 두고 부분합을 계산
2. k와 합계가 일치할 때의 인덱스들을 저장
3. 마지막 인덱스까지 1~2를 반복한 후 가장 인덱스 차이가 적은 케이스를 리턴
**코드**
```javascript
function solution(sequence, k) {
    let [l,r] = [0, 0]; // pointer 배열
    let candidates = []; // 합이 k인 경우의 인덱스들
    let sum = sequence[l]; // 합
    
    while(r < sequence.length) {
        if(sum < k) sum += sequence[++r];
        else if(sum > k) sum -= sequence[l++];
        else {
            candidates.push([l,r]);
            sum += sequence[++r];
            sum -= sequence[l++];
        }
    }
    return candidates.sort((a,b) => (a[1] - a[0]) - (b[1] - b[0]))[0];
}
```
투 포인터 알고리즘에 따라 쓰여진 답안을 참고했다.

## 알게 된 것
### 투 포인터 알고리즘 Two Pointer Algorithm
- 두 개의 인덱스를 기록하고 처리하는 방식
- 반복문을 돌 때마다 두 포인터 중 하나가 1씩 증가하고 포인터가 n(배열의 길이)번 누적 증가시 알고리즘 종료
  - 모든 포인터가 마지막에 다다를 때 각각 O(N) → 총 시간 복잡도 O(N)
- 순차적으로 리스트에 접근해야 할 때 사용

---
#### 레퍼런스
**투 포인터 알고리즘**
- https://butter-shower.tistory.com/226
- https://yjg-lab.tistory.com/396
