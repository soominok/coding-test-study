# 11강. 파이썬 문법: 자주 사용되는 표준 라이브러리

### ■ 실전에서 유용한 표준 라이브러리

- __내장 함수__ : 기본 입출력 함수부터 정렬 함수까지 기본적인 함수들을 제공
  * 필수적인 기능을 포함
  * import 구문 없이도 사용할 수 있는 함수
  
- __itertools__ : 파이썬에서 반복되는 형태의 데이터를 처리하기 위한 유용한 기능들 제공
  * __순열과 조합 라이브러리__ 는 코딩 테스트에서 자주 사용
  * 모든 경우의 수를 고려해야 할 때 유용함
  * 특히 "순열과 조합"은 완전 탐색 문제 유형에서 소스코드 매우 간결하게 도와줌
  
- __heapq__ : 힙(Heap) 자료구조를 제공
  * 일반적으로 __우선순위 큐 기능__ 을 구현하기 위해 사용
  * 대표적으로 __다익스트라와 같은 최단 경로 알고리즘__ 에서 많이 활용
  
- __bisect__ : __이진 탐색(Binary Search) 기능__ 제공
 * 기본적인 형태의 이진 탐색 기능이 필요할 때 bisect 라이브러리를 효과적으로 사용

- __collections__ : 덱(deque), 카운터(Counter) 등의 유용한 자료구조를 포함

- __math__ : 필수적인 수학적 기능 제공
  * 팩토리얼, 제곱근, 최대공약수(GCD), 삼각함수 관련 함수부터 파이(pi)와 같은 상수를 


### ■ 자주 사용되는 내장 함수

- __sum()__ : 다수의 데이터를 포함하는 리스트나 튜플들이 들어왔을 때 그 원소들의 합을 반환
- __min(), max()__ : 가장 작은 값, 큰 값을 얻고자 할 때 이용
- __eval()__ : 수식으로 표현된 하나의 식을 계산했을 때의 결과가 반환됨
- __sorted()__ : 리스트와 같은 반복 가능한 객체가 들어왔을 때 각 원소를 정렬한 결과 반환

      (추가)
      # sorted() with key
      array = [('홍길동', 35), ('이순신', 75), ('아무개', 50)]
      result = sorted(array, key=lambda x: x[1], reverse = True)
      print(result)
      
      >>> sorted()는 일반적으로 정렬 기준을 명시해줄 수 있는데,
          이때는 람다 함수 형태로 간단히 넣어줌


### ■ 순열과 조합
- 모든 경우의 수를 고려해야 할 때 어떤 라이브러리를 효과적으로 사용할 수 있을까?
- __순열__ : 서로 다른 n개에서 서로 다른 r개를 선택하여 일렬로 나열하는 것
 * {'A', 'B', 'C'}에서 세 개를 선택하여 나열하는 경우 : 'ABC', 'ACB', 'BAC', 'CAB', 'CBA'
- __조합__ : 서로 다른 n개에서 순서에 __상관 없이__ 서로 다른 r개를 선택하는 것
 * {'A', 'B', 'C'}에서 순서를 고려하지 않고 두 개를 뽑는 경우 : 'AB', 'AC', 'BC'
 
       순열의 수 : nPr = n * (n-1) * (n-2) * ... * (n-r+1)
       
       조합의 수 : nCr = {n * (n-1) * (n-2) * ... * (n-r+1)} / r!

- 위의 공식을 이용하여 모든 경우의 수가 총 얼마나 될지를 짐작해서 해당 문제를 푸기 위해 모든 경우의 수를 고려하는 방법이 통할지 안할지 판단
 * 순열의 수를 구해봤을 때, 값이 1,000만 ~ 1억 단위로 넘어가는 경우 완전 탐색을 이용했을 때 시간 초과 판정을 받을 확률이 높을 수 있음
 * 전체 경우의 수를 고려할 때 순열과 조합을 이용함
 
 
### ▷ 순열 라이브러리
 
    from itertools import permutations
    
    data = ['A', 'B', 'C'] # 데이터 준비
    
    result = list(permutations(data, 3)) # 모든 순열 구하기
    print(result)
    
    실행 결과) [('A', 'B', 'C'), ('A', 'C', 'B'), ('B', 'A', 'C'), ('B', 'C', 'A'), ('C', 'A', 'B'), ('C', 'B', 'A')] 
    
 
 
### ▷ 순열 라이브러리

    from itertools import combinations
    
    data = ['A', 'B', 'C']
    
    result = list(combinations(data, 2)) # 모든 조합 구하기
    print(result)
    
    실행 결과) [('A', 'B'), ('A', 'C'), ('B', 'C')] 
    

### ■ 중복 순열과 중복 조합

    from itertools import product
    
    data = ['A', 'B', 'C'] # 데이터 준비
    
    result = list(product(data, repeat = 2)) # 2개를 뽑는 모든 순열 구하기 (중복 
    print(result)
    
    
    from itertools import combinations_with_replacement
    
    data = ['A', 'B', 'C'] # 데이터 준비
    
    result = list(combinations_with_replacement(data, 2)) # 2개를 뽑는 모든 조합 구하기 (중복 
    print(result)
    
    
    
### ■ Counter
- 파이썬 collections 라이브러리의 __Counter__ 는 등장 횟수를 세는 기능을 제공함
- 리스트와 같은 반복 가능한(iterable) 객체가 주어졌을 때 __내부의 원소가 몇 번씩 등장했는지__ 를 알려줌 


### ■ 최대 공약수와 최소 공배수
- 최대 공약수를 구해야 할 때는 math 라이브러리의 gcd()함수를 이용
- __최대 공약수__ : 두 수가 주어졌을 때, 공통된 약수 중에서 가장 큰 값
- __최소 공배수__ : 두 수가 주어졌을 때, 공통된 배수 중에서 가장 작은 값

      import math
      
      # 최소 공배수(LCM)를 구하는 함수
      def lcm(a, b):
        return a * b // math.gcd(a, b)
        
      a = 21
      b = 14
      
      print(math.gcd(21, 14)) # 최대 공약수 (GCD) 계산
      print(lcm(21, 14) # 최소 공배수(LCM) 계산
      
      계산 결과) 7  42