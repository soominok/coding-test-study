# 1강. 코딩테스트란

### ■ 온라인 저지(Online Judge)
: 프로그래밍 대회나 코딩 테스트에서 나올 법한 문제를 시험해보는 온라인 시스템
     
     [해외]
     - 코드포스            https://www.codeforces.com
     - 탑코더              https://www.topcoder.com
     - 릿코드              https://leetcode.com        → 기업 코딩테스트 준비하기 좋음
     - 코드셰프            https://www.codechef.com
     
     [국내]
     - 백준                https://www.acmicpc.net     → 많은 문제, 유형 별로 문제 풀 수 있음
     - 코드업              https://codeup.kr           → 처음 접근하기에 좋음
     - 프로그래머스        https://programmers.co.kr   → 많은 문제 보유
     - SW Expert Academy  https://swexpertacademy.com
     
### ■ 온라인 개발 환경 (Python)
: 코딩테스트 문제 풀 때 활용하기 좋은 사이트
      
      [온라인]
      - 리플릿 : https://repl.it/languages/python3
      - 파이썬 튜터 : http://pythontutor.com/visualize.html
      
      [오프라인 - 로컬]
      - https://www.jetbrains.com/pycharm/download/
     
### ■ 소스코드 관리하기 (팀노트 - 알고리즘 노트)
      - 자신이 자주 사용하는 알고리즘 코드를 라이브러리화 하면 좋음
      - 팀 노트 예시) https://github.com/ndb796/Python-Competitive-Programming-Team-Notes
 
### ■ IT 기업 코딩 테스트 최신 출제 경향
      [가장 출제 빈도가 높은 알고리즘 유형]
      - 그리디 (쉬운 난이도)
      - 구현
      - DFS/BFS를 활용한 탐색
      
      [2016 ~ 2019년에 출제되었던 국내외 알고리즘 유형]
      구현 > DFS/DFS > 그리디 > 정렬 = 다이나믹 프로그래밍 > 이진 탐색 > 최단 경로 > 그래프 이론
      
      
# 2강. 알고리즘 성능 평가

## ■ 복잡도 (Complexity)
: 알고리즘의 성능을 나타내는 척도

     - 시간 복잡도 : 특정한 크기의 입력에 대하여 알고리즘의 수행 시간 분석
     - 공간 복잡도 : 특정한 크기의 입력에 대하여 알고리즘의 메모리 사용량 분석
     → 동일한 기능을 수행하는 알고리즘이 있다면, 일반적으로 복잡도가 낮을수록 좋은 알고리즘
     
     ※ 복잡도는 단순히 소스 코드가 복잡하게 보인다는 말과는 다름
        여기에서 말하는 복잡도는 특정한 함수의 성능적인 측면에서의 복잡도
        
     ※ 즉,
        시간 복잡도 ↑, 해당 알고리즘이 느리게 실행될 수 있다는 것
        시간 복잡도 ↓, 해당 알고리즘이 더 빠르게 실행될 수 있다는 것을 의미함
        공간 복잡도 ↑, 많은 메모리가 필요할 수 있다는 것
        
### ■ 빅오 표기법 (Big-O Notation) - 복잡도 표기 방법
 : 가장 빠르게 증가하는 항만을 고려하는 표기법
 
      - 함수의 상한만을 나타내게 됨
      - 예를 들어 연산 횟수가 3N^3 + 5N^2 + 1,000,000인 알고리즘이 있다면,
        빅오 표기법에서는 차수가 가장 큰 항만 남기므로 O(N^3)으로 표현됨. 
        ※ 계수는 무시하고 N^3만 표현 함!
        
        
       [성능을 나타내는 알고리즘 표기법]
       <좋음> 상수 시간 O(1) > 로그 시간 O(logN) > 선형 시간 O(N) > 로그 선형 시간 O(NlogN) > 
              이차 시간 O(N^2) > 삼차 시간 O(N^3) > 지수 시간 O(2^n)  <나쁨>
              
         ※ 상수 시간 : 몇 번의 연산만 거치면 완료
         ※ 로그 시간 : log N에 비례하는 만큼 시행
        
### ■ 시간 복잡도 계산 1)
     - N개의 데이터의 합을 계산
     array = [3, 5, 1, 2, 4] # 5개의 데이터 (N = 5)
     summary = 0 # 합계를 저장할 변수 (초기화했음)
     
     # 모든 데이터를 하나씩 확인하며 합계를 계산
     for x in array:
          summary += x
          
     # 결과를 출력
     print(summary)
     
     - 수행 시간은 데이터의 개수 N에 비례할 것임을 예측할 수 있음
       시간 복잡도 : O(N) 
       → 이유) 모든 데이터를 하나씩 확인하며 합계를 계산하기 때문!

### ■ 시간 복잡도 계산 2)
     - 2중 반목문을 이용
     array = [3, 5, 1, 2, 4]
     
     for i in array:
          for j in array:
               temp = i * j
               print(temp)
               
     - 시간 복잡도 : O(N^2) 
     - 참고) 모든 2중 반복문의 시간 복잡도가 O(N^2)인 것은 아님.
             소스 코드가 내부적으로 다른 함수를 호출한다면 그 함수의 시간 복잡도까지 고려
     
     ※ i*j가 구해지는 횟수는 25회
     
### ■ 알고리즘 설계 Tip
     - 일반적으로 CPU 기반의 개인 컴퓨터나 채점용 컴퓨터에서 연산 횟수가 5억을 넘어가는 경우:
       → Python을 기준으로 통산 5 ~ 15초 가량의 사긴이 소요됨
         PyPy의 경우 때때로 C언어보다도 빠르게 동작하기도 함
         ※ PyPy를 지원한다면 가능하면 PyPy로 하는 것이 시간 복잡도 측면에서 유리할 수 있음!
            하지만, Python보다 더 많은 메모리가 사용될 수도 있다는 점을 유의하기!
          ※Python으로 제출했는데 시간 초과가 뜬다면, PyPy로 다시 해보기!
     - O(N^3)의 알고리즘을 설계한 경우, N의 값이 5,000이 넘는다면 얼마나 걸릴까?
       - 코딩 테스트 문제에서 시간제한은 통상 1 ~ 5초 가량이라는 점을 유의!
         → 혹여 문제에 명시되어 있지 않은 경우 대략 5초 정도라고 생각하고 문제를 푸는 것이 합리적
       
     → 5,000 X 3번 = 1,250억
       즉, 파이썬이 1초에 약 5,000만 번정도의 계산을 처리할 수 있다고 한다면
           약 2,500초 정도가 걸린다고 말할 수 있음!!
           
     ※ 이렇게 수행시간 예측해서 알고리즘을 설계하는 것이 중요함!
        특히, 채점용 서버에서는 파이썬이 1초에 약 2,000만 번 정도의 연산만 처리할 수 있다고 가정하고 문제 접하기     
        
### ■ 요구사항에 따라 적절한 알고리즘 설계하기      
     - 문제에서 가장 먼저 확인해야 하는 내용은 데이터의 조건, 시간제한(수행시간 요구사항)
     - 시간 제한이 1초인 문제를 만났을 때, 일반적인 기준은 다음과 같음
       ＊ N의 범위가 500인 경우 : 시간 복잡도가 O(N^3)인 알고리즘을 설계하면 문제를 풀 수 있음
       ＊ N의 범위가 2,000인 경우 : 시간 복잡도가 O(N^2)인 알고리즘을 설계하면 문제를 풀 수 있음
       ＊ N의 범위가 100,000인 경우 : 시간 복잡도가 O(NlogN)인 알고리즘을 설계하면 문제를 풀 수 있음
       ＊ N의 범위가 10,000,000인 경우 : 시간 복잡도가 O(N)인 알고리즘을 설계하면 문제를 풀 수 있음
       
### ■ 알고리즘 문제 해결 과정
 1. 지문 읽기 및 컴퓨터적 사고  (문제를 단계별로 잘게 분해보기)
 2. 요구사항(복잡도) 분석 ★★★
 3. 문제 해결을 위한 아이디어 찾기
 4. 소스코드 설계 및 코딩
 
 → 일반적으로 대부분의 문제 출제자들은 핵심 아이디어를 캐치한다면, 간결하게 소스코드를 작성할 수 있는 형태로 문제를 출제함
 
 ### ■ 수행 시간 측정 소스코드 예제
     import time
     start_time = time.time() # 측정 시작 → 프로그램이 시작되는 부분에 작성
     
     # 프로그램 소스코드
     end_time = time.time() # 측정 종료 → 프로그램이 종료되는 부분에 작성
     print("time:", end_time - start_time) # 수행 시간 출력
     
