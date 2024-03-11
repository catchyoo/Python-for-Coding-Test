# Python for Coding-Test

### 중요한 혹은 알면 좋은 python 문법들 정리(순서는 없음) 
### 생각나는대로 혹은 문제풀다가 배우는대로 작성함. 대신 관련 문제 적어두기

## 알고리즘 분석
### 구현/DFS&BFS/그리디/이분탐색/DP/정렬 우선순위!!
1. **그리디 알고리즘** : 현재 상황에서 지금 당장 좋은 것만 고르는 방법 => 최소한의 아이디어 떠올릴 수 있는 능력 필요
- 일반적인 상황에서 그리디 알고리즘은 최적의 해 보장 불가
- 따라서, 코딩 테스트에서는 보통 그리디 알고리즘으로 얻은 값이 **정답이 되는 상황**이 되도록 문제 출제 => 떠올린 아이디어가 당연히 정답이 되는 것!!!!!!!
- **관련 문제** : 1931
  
2. **구현** : 많은 연습을 통해 필요로 하는 라이브러리 사용법을 익혀야 함
- 2차원 배열 자주 사용
- 문법 정리에 다양한 라이브러리 정리

3. **정렬** : 데이터 특정한 기준으로 순서대로 나열

4. **브루트포스** : 가능한 모든 경우의 수를 탐색하여 충족되는 결과 출력
- 정답이 존재할 것으로 예상되는 모든 영역 전체 탐색 방법
- 오래 걸림
- **관련 문제** : 1436

5. **다이나믹 프로그래밍(DP)** : 메모리를 적절히 사용하여 수행 시간 효율성을 비약적으로 향상시키는 방법
- 이미 계산된 결과는 별도의 메모리 영역에 저장하여 다시 계산하지 않도록 함
- 탑다운 & 바텀업 두 가지 방식으로 구성
- 다음의 조건 만족 시 사용 가능 : 
1) 최적 부분 구조 : 큰 문제를 작은 문제로 나눈 후 작은 문제의 답을 모아서 큰 문제 해결
2) 중복되는 부분 문제 : 동일한 작은 문제를 반복적으로 해결
  
## 문법 정리(라이브러리)
1) import sys => input = sys.stdin.readline => 입력 받을 때, 필수
2) from collections import deque => bfs 구현 시 사용
3) from itertools import combinations => 조합 구현 시 사용
4) sys.setrecursionlimit(100000) => dfs 구현 시 사용
5) dict = {} & new_dict = sorted(dict.items(), key = lambda x = (-x[0], len(x[1]))) : 관련 문제 = 20920,7785
6) 배열에서의 원소 삽입 : ex) arr = [1,2,3]
   - arr.append(4) : 배열의 끝에 값 추가 => arr = [1,2,3,4]
   - arr.insert(1,4) : 1번 index에 4 추가 => arr = [1,4,2,3]
   - arr + arr2(=[5,6]) : 배열 끝에 값 추가 => arr = [1,2,3,4,5,6]
   - arr.extend(arr2) : 배열 끝에 배열 추가 => arr = [1,2,3,4,5,6]
7) 배열에서의 원소 삭제 : ex) arr = [1,2,3,4,5,6,7]
   - del arr[1] : 배열의 1번 index 값 삭제 => arr = [1,3,4,5,6,7]
   - arr.remove(3) : 배열에서 원하는 값 삭제 => arr = [1,2,4,5,6,7]  *remove(x)는 리스트의 첫 번쨰로 나오는 x를 삭제. 즉, 동일한 x 여러 개 일 경우, 가장 첫 번째 x 값만 삭제
   - arr.pop() or arr.pop(2) : 배열에서 원하는 index 값 리턴 후 삭제(괄호 안에 아무것도 없을 시 마지막 원소 리턴) => arr[1,2,3,4,5,6] or arr[1,2,4,5,6]
8) 배열에서의 주요 문법 : ex) arr = [1,3,5,7,9] 
   - reverse() : 배열을 역순으로 뒤집는 연산 => arr.reverse() = [9,7,5,3,1]
   - index(x) : 배열에 x 값 존재 시, x의 위치 리턴 => arr.index(5) = 2
   - count(x) : 배열 안에 x 라는 원소 몇 개 있는 지 리턴 => arr.count(3) = 1
9) from collections import Counter : 여러 형태의 데이터를 인자로 받는 경우, 중복된 데이터가 저장된 배열을 인자로 넘기면 원소가 몇 번씩 나오는지 저장된 객체 얻을 수 있음
    - ex) Counter(['red', 'blue', 'red', 'green', 'blue', 'blue']) => Counter({'blue': 3, 'red': 2, 'green': 1})
    - Counter("hello world") => Counter({'h': 1, 'e': 1, 'l': 3, 'o': 2, ' ': 1, 'w': 1, 'r': 1, 'd': 1})
10) 배열의 슬라이싱 사용하기 => ex) arr = [1,2,3,4,5,6,7,8] / arr[start:stop:step]
    1) start, stop 이용하기 :
       - arr[2:6] = [3,4,5,6]
    2) 음의 index 사용하기 :
       - arr[:-2] = [1,2,3,4,5,6]
       - arr[-4:] = [5,6,7,8]
       - arr[-5:-2] = [4,5,6]
    3) step 이용하기 :
       - arr[::2] = [1,3,5,7]
       - arr[::3] = [1,4,7]
    4) start,stop,step 전부 사용하기 :
       - arr[1::3] = [2,5,8]
       - arr[2:6:2] = [3,5]
    6) [::-1] 사용 : 
      - arr[::-1] = [8,7,6,5,4,3,2,1]
      - arr[::-2] = [8,6,4,2]
      - arr[::-3] = [8,5,2]
11) s = sys.stdin.readline().split() 로 입력 받을 때,
    split() 사용하였어도, 문자열 s가 하나만 받을 수 있다. 
    ex) s = push_front  2 라고 했을 때, s[0], s[1]로 사용 가능.
        s = empty 라고 했을 때, s[0]로 사용 가능
12) BFS 는 항상 deque() 사용하여 while 문에서 처리할 것을 염두해두기!
13) 이진탐색 : 정렬된 자료를 반씩 나누어 탐색하는 방법 => time complexity : O(MlogN). for 문 사용 시 : O(NM)
  - left, right 사용! 관련 문제 : 1920, 10816
14) dict = {} 사용 시, dict의 key 값에 따른 value 찾고 싶다면 => dict.get(key) 사용하는 것이 좋음
    - dict[key] 사용 시, key 값이 없을 경우 keyError가 뜨지만, dict.get(key) 사용 시, 존재하지 않는 key에 대해 none을 리턴하기 때문에 에러 피할 수 있음.
15) split()의 사용법 => 보통 split()을 사용할 때는, 띄어쓰기 기준으로 사용하기 위해서 input().split()을 사용하게 됨. 하지만 내가 원하는 기준에 맞추어 split() 하고 싶을 때는 괄호안에 기준에 해당하는 값을 넣어주면 됨. ex) split('-') : - 부호 기준으로 문자열 나누기. split('+') : + 부호 기준으로 문자열 나누기 등.
16) 1차원 리스트에서 min,max 찾는 법 : ex) arr = [] / min(arr) & max(arr)
17) 1차원 리스트에서 min,max의 index 찾는 법 : ex) arr = [] / arr.index(min(arr)) & arr.index(max(arr))
18) 1차원 리스트에서 min,max 빼내는 법 : ex) arr = [] / arr.pop(arr.index(min(arr))) & arr.pop(arr.index(max(arr)))
19) 2차원 배열 안에 [[x,y]] 만 들어갈 필요 없음. [[x,y,z,w,,,]] 여러 개 들어 갈 수 있음을 명시. => ex) arr = list([] for _ in range(n+1)) & arr[x].append(y). y 안에 1,2,3...
20) dict를 sorted 하여 리스트로 만든 후, key & value 찾고 싶다면,,, 
    => dict = {} / arr = sorted(dict.items(), key = lambda x : x[0]). => for i in range(len(arr)-1): key = arr[i][0] & value = arr[i][1] 
