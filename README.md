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
- 정답이 존재할 것으로 예상되는 모든 영역 전체 탐색 방법 => 주어진 입력이 크지 않다고 생각되면 전체 탐색 하는 브루트 포스 생각하기!!!(ex. n < 10,000)
- 오래 걸림
- **관련 문제** : 1436, 숫자의 표현(프로그래머스)

5. **다이나믹 프로그래밍(DP)** : 메모리를 적절히 사용하여 수행 시간 효율성을 비약적으로 향상시키는 방법
- 이미 계산된 결과는 별도의 메모리 영역에 저장하여 다시 계산하지 않도록 함
- 탑다운 & 바텀업 두 가지 방식으로 구성
- 다음의 조건 만족 시 사용 가능 : 
1) 최적 부분 구조 : 큰 문제를 작은 문제로 나눈 후 작은 문제의 답을 모아서 큰 문제 해결
2) 중복되는 부분 문제 : 동일한 작은 문제를 반복적으로 해결
   
## 프로그래머스 정리(틀린 것)
1) 자연수 뒤집어 배열로 만들기
   : 1) 문자열 거꾸로 출력하기 = [::-1] 존재 기억!
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
    6) **[::-1] 사용** : 
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
    => dict = {} / arr = sorted(dict.items(), key = lambda x : x[0]). => for i in range(len(arr)-1): **key = arr[i][0] & value = arr[i][1]**
21) input() 함수 : 입력의 마지막에서 줄바꿈 문자를 자동으로 **제거**.
    sys.stdin.readline() 함수 : 줄바꿈 문자를 **포함한 채**로 입력된 문자열을 반환
22) 정렬된 dict의 key & value 사용법 : 20)번 참고!! => 따라서, key 값끼리 비교 : arr[0][1] > arr[1][1] 처럼 사용,,,
23) join 함수 => 사용 방법: .join(리스트) / '구분자'.join(리스트) ex) arr = [1,2,3] 1) ''.join(arr) = abc / 2)','.join(arr) = a,b,c
24) 코테에서 reverse & pop 시간이 오래걸림. 배열을 사용할 경우 pop 해준 후, 나머지 원소들 움직여야 하기 때문에! 따라서 삭제를 해야 하는 경우가 생기면 deque 사용하기!
    reverse 사용 시, 원소의 개수가 많을 경우 오래걸리기 때문에 reverse 개수 세보고서 결정하기. ex) 5430
25) 문자열과 관련된 꿀팁 함수!!!!!!!!!!!!!!!! **1. count 함수** ex) s = s.count('0') 라고 쓰면, s 안의 0의 개수 세줌. 대신 문자(str)만 찾아야함! 정수(int) 안됨./ **2. replace 함수** ex) s = s.replace('0','')라고 쓰면, s안의 0를 없애      줌. / **3. bin 함수** ex) s = bin(len(s))[2:] 라고 쓰면, s의 길이를 다시 이진수로 바꾸어줌. 이때 [2:] 꼭 사용하기! 앞에 0b가 붙기 때문.
26) 두 숫자의 최대공약수 구하는 함수 : from math import **gcd** => 두 수의 최소공배수 = 두 수의 곱 // 두 수의 최대공약수 ; a*b //gcd(a,b) ; gcd = greatest common divisor, lcm = lowest common multiple

def generate_combinations(arr, r):

    result = []
    n = len(arr)
    def backtrack(start, path):
        # r개의 요소가 선택되었으면 결과에 추가
        if len(path) == r:
            result.append(path[:])
            return
        
        for i in range(start, n):
            # 현재 요소를 선택하고 다음 단계로 진행
            path.append(arr[i])
            backtrack(i + 1, path)
            # 백트래킹: 마지막 요소를 제거하고 다음 선택을 시도
            path.pop()
    
    backtrack(0, [])
    return result

def generate_permutations(arr, r):

    result = []
    n = len(arr)
    used = [False] * n  # 요소가 사용되었는지를 체크하기 위한 배열
    def backtrack(path):
        # r개의 요소가 선택되었으면 결과에 추가
        if len(path) == r:
            result.append(path[:])
            return
        
        for i in range(n):
            if not used[i]:
                # 현재 요소를 선택하고 사용됨을 표시
                used[i] = True
                path.append(arr[i])
                backtrack(path)
                # 백트래킹: 선택한 요소를 제거하고 다시 사용 가능하게 함
                path.pop()
                used[i] = False
    
    backtrack([])
    return result

** 생각 정리**
- 소수 찾는 함수
- n진수 만드는 함수
- 항상 dict, deque 기본적으로 생각. index와 content 같이 사용할 수 있을까 / 몫과 나누기 사용
- itertools의 함수 생각 => 사용 못할 경우도 대비하기
- heapq 사용법
- math : gcd & lcm = greatest common divisor & lowest common multiple
- Ascii code : chr & ord = characters & order
  
## 프로그래머스 오답 정리
### LV1 : 약간 하드한 코딩. 손코딩 먼저 하고, 코드 짜기
1) 제일 작은 수 제거하기
2) 문자열 내림차순으로 배치하기
3) 문자열 다루기 기본
4) 행렬의 덧셈
5) 이상한 문자 만들기
6) 시점 암호
7) 가장 가까운 같은 글자
8) 푸드 파이트 대회
9) 문자열 내 마음대로 정렬하기
10) 비밀 지도
11) 2016년
12) 기사단원의 무기
13) 덧칠하기
14) 실패율
15) 다트게임
16) 둘만의 암호
17) 완주하지 못한 선수
18) 체육복
19) 숫자 짝꿍
20) 햄버거 만들기
21) 신규 아이디 추천
22) 바탕화면 정리
23) 개인정보 수집 유효기간
24) 달리기 경주
25) 공원 산책
26) 신고 결과 받기
27) 붕대 감기
28) 가장 많이 받은 선물

### LV2 : 아이디어 생각해내기. 틀린 문제들 다양한 종류들! 다 알아두기
1) 구명 보트
2) 귤 고르기
3) n^2 배열 자르기
4) 행렬의 곱셈
5) 의상
6) H-index
7) 캐시 : X
8) 튜플
9) 프로세스
10) 피로도
11) 전화번호 목록
12) 타겟 넘버 : X
13) n 진수 게임
14) K 진수에서 소수 개수 구하기
15) 압축
16) 뒤에 있는 큰 수 찾기
17) 게임 맵 최단거리
18) 주식 가격
19) 더 맵게 : X
20) 주차 요금 계산
21) 파일명 정렬
22) 오픈 채팅방
23) 숫자 변환하기
24) 2xn 타일링
25) 프렌즈 4블록
26) 2개 이하로 다른 비트
27) 가장 큰 수
28) 다리를 지나는 트럭
29) 소수 찾기 : X
30) 삼각 달팽이
31) 두 큐 합 같게 만들기
32) 연속된 부분 수열의 합
33) 큰 수 만들기
34) 쿼드 압축 후 개수 세기
35) 124 나라의 숫자
36) 호텔 대실
37) 마법의 엘레베이터
38) 시소 짝꿍 : X
