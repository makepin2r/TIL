# 연속 부분 수열 합의 개수 풀이

## 문제
[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/131701)  
![image](https://github.com/makepin2r/TIL/assets/39889583/17e3000b-2cc9-4f8f-a59a-4746da0c078d)

## 나의 풀이
### 아이디어 : 전체 값에서 부분 수열에 해당되지 않는 원소만 뺀 값들의 수를 리턴 (실패)
아이디어를 완성하지 못했다.  
- 중복 합을 방지하기 위해 모든 합들은 `set` 객체에 저장한다.
- 부분 수열의 길이를 1부터 전체 길이까지 고려해야 하므로, 반복문을 통해 길이를 제한하며 순회한다 (첫 번째 for문)
- 두 번째 for문에서는 수열의 시작 인덱스를 정하고 부분 수열의 합을 구한다.
    - 모든 원소들의 합인 total을 미리 계산해두고, 포함되지 않을 인덱스의 경우를 total에서 뺀다.
    - set에 add해준다.
이 아이디어의 마지막 부분을 코드로 일반화하지 못해 제 시간에 풀지 못했다.
for문이 한 번 더 중첩되는 문제도 있어보였다.  
검색을 통해 슬라이딩 윈도우 알고리즘이 내가 택한 방법과 유사점이 있다 생각해서 알아보았다.
### 아이디어 2 : 슬라이딩 윈도우 알고리즘 활용
슬라이딩 알고리즘을 활용하면 시간복잡도를 낮추면서 더 효과적으로 문제 풀이가 가능했다.  
total에서 빼는 방식이 아닌, 일정 길이의 부분 수열 합을 특정 인덱스 기준으로 구한 뒤 맨 앞과 맨 뒤의 요소들을 빼고 더하면서 진행하면 된다.  
### 코드
```javascript
function solution(elements) {
    const set = new Set(); 
    for(let i = 1; i <= elements.length; ++i){ // 부분 수열 길이
        let sum = 0;
        for(let j = 0; j < elements.length; ++j){ // 수열 시작 인덱스
            // 부분 수열의 합 구하기
            if(j === 0){
                // 최초 인덱스에 대한 합
                for(let k = 0; k < i; ++k){
                    sum += elements[k];
                }
            } else {
                sum -= elements[j - 1];
                sum += elements[(i + j - 1) % elements.length];
            }
            // set에 넣기
            set.add(sum);
        }
    }
    return set.size;
}
```
제대로 풀지 못해 아쉽다.  
조금 더 최적화가 가능해보이는데 한 번 더 풀어봐야겠다.

## 알게 된 것
### 슬라이딩 윈도우 알고리즘
배열 또는 리스트 같은 순차적인 데이터에서 일정한 범위의 값을 검증해야 할 때 많이 쓰이는 알고리즘이다.  
![image](https://github.com/makepin2r/TIL/assets/39889583/3e9c49ba-703a-4ebb-8cba-1ea08ccd94b1)  
인덱스가 하나씩 이동할 때 새로운 윈도우의 교집합에서 제외된 맨 왼쪽 원소는 빼주고, 추가된 맨 오른쪽 원소를 더해준다.  
이때 첫번째 범위의 합은 반복문을 통해 구해주어야 하므로, 시간 복잡도는 O(n)이 된다.

---
#### 레퍼런스
- 슬라이딩 윈도우 알고리즘
-   - [블로그 1](https://ji-musclecode.tistory.com/37)
    - [블로그 2](https://velog.io/@dianestar/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EC%97%B0%EC%86%8D-%EB%B6%80%EB%B6%84-%EC%88%98%EC%97%B4-%ED%95%A9%EC%9D%98-%EA%B0%9C%EC%88%98-JavaScript-%EA%B5%90%EA%B3%B5-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EC%8A%A4%ED%84%B0%EB%94%94-48%EC%A3%BC%EC%B0%A8)
