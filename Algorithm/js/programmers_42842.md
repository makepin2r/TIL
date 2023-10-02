# 프로그래머스 카펫 풀이
> 시도한 날짜: 2023. 10. 02
## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42842)  
![image](https://github.com/makepin2r/TIL/assets/39889583/72ab5934-6575-421d-b42c-32bbfc90bc7d)

## 나의 풀이 (실패)
### 아이디어
- 노란 격자 기준으로 한 면의 칸을 n, 다른 한 면의 칸을 m이라고 했을 때 다음의 식이 성립한다.
  - yellow == n*m
  - brown == 2(n+m+2)
- 식을 정리하여 미지수를 1개만 남긴 방정식을 만든다.
  - m을 기준으로 했을 때, `m == yellow/m + 2 - brown/2` 가 된다.
- 반복문을 돌며 순차적으로 m을 증가시키며 위의 식에 맞는 m을 발견했을 때, m을 이용해 n을 계산한 뒤 더 큰 숫자대로 리턴한다.
  - 노란 격자를 기준으로 했으므로 n과 m에 2씩 더해준다.
### 코드
```javascript
function solution(brown, yellow) {
    let [n,m] = [0, 1];
    while(n === 0){
        if(m === yellow/m + 2 - brown/2) {
            n = yellow / m;       
        }
        else ++m;
    }
    return n >= m ? [n+2,m+2] : [m+2,n+2];
}
```
고려하지 못한 규칙이 있었는지 테스트 결과가 정확하지 않았고,  
몇몇 테스트는 무한 루프로 실행이 제대로 되지 않았다.  
더 풀어보고 싶었지만 제한 시간이 끝나 풀이를 확인하기로 했다.

## 다른 사람 풀이
다른 분의 풀이를 참고해보았다.  
너무 복잡하게 생각해서 풀이가 제대로 되지 않았던 것 같다.  
로직이 다들 비슷해서, 여러 풀이 중 가장 눈에 잘 들어왔던 풀이를 대표로 가져왔다.
```javascript
function solution(brown, yellow) {
    var answer = [];
    let sum = brown + yellow;
    
    for(let height=3; height<=brown; height++){
        if(sum % height === 0){
            let weight = sum / height;
            if( (height-2) * (weight-2) === yellow){
                return [weight, height];
            }
        }
    }
    return answer;
}
```
총 격자의 수는 가로 * 세로 즉 갈색 격자 + 노란색 격자 수와 같다.  
따라서 카펫의 최소 높이가 될 수 있는 3부터 반복문을 돌며,  
카펫 격자 수가 높이로 나누어떨어질 경우 노란 격자를 기준으로 조건에 충족하면 바로 리턴해주는 형태이다.  
너비보다 더 작아야 하는 높이를 기준으로 최소 수부터 순회하기 때문에 따로 sorting하지 않아도 된다.

---
#### 레퍼런스
- https://ghost4551.tistory.com/115
