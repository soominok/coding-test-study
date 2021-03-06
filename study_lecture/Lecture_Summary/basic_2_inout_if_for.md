# 7강. 파이썬 문법: 기본 입출력

### ■ 기본 입출력
- 모든 프로그램은 적절한 (약속된) 입출력 양식을 가지고 있음
- 프로그램 동작의 첫 번째 단계는 데이터를 입력 받거나 생성하는 것


### ■ 자주 사용되는 표준 입력 방법
- __input()__ : 한 줄의 문자열을 입력 받는 함수
- __map()__ : 리스트의 모든 원소에 각각 특정한 함수를 적용할 때 사용

(예시 1)
  * "공백을 기준으로 구분된 데이터를 입력 받을 때"

        list(map(int, input().split()))
        
(예시 2)
  * "공백을 기준으로 구분된 데이터의 개수가 많지 않다면, 단순히 다음과 같이 사용"
  
        a, b, c = map(int, input().split())
        
        >>> map(int, input().split()) : 패킹 (입력 받은 데이터를 하나의 묶음으로 만든 것)
            a, b, c : 언 패킹
            
            ※ 입력받은 데이터가 3개라면 a, b, c에 각각 언패킹해줄 수 있는 것
            
                        
### ■ 빠르게 입력 받기
- 파이썬의 경우 sys 라이브러리에 정의되어 있는 __sys.stdin.readline() 메서드를 이용__
  * 단, 입력 후 엔터(Enter)가 줄 바꿈 기호로 입력되므로 rsrtip() 메서드를 함께 사용
  
  * 입력의 개수가 많은 문제를 풀 때 입력을 받는 것만으로도 시간초과 받을 수도 있기 때문!!
  ※ 이진 탐색, 정렬, 그래프 문제에서 주로 사용되는 테크닉
  
      (예시)
      import sys
      
      data = sys.stdin.readline().rstrip()
      print(data)
      
### ■ 자주 사용되는 표준 출력 방법
- 기본 출력은 print() 함수
 * 각 변수를 콤마(,)를 이용하여 띄어쓰기로 구분하여 출력
- print()는 기본적으로 출력 이후에 줄 바꿈을 수행
  * 줄바꿈을 원치 않는 경우 __'end'__ 속성을 이용할 수 있음
  
        (예시)
        print(7, end=" ")
        print(8, end=" ")
        
        출력 결과> 7 8
      
### ■ f-string
- 문자열 앞에 접두사 __'f'__ 를 붙여 사용 (파이썬 3.6부터 사용 가능)
- 중괄호 안에 변수명을 기입하여 간단히 문자열과 정수를 함께 넣을 수 있음

      (예시)
      answer = 7
      print(f"정답은 {answer} 입니다.")
      
      >>> 그냥 print()만 사용한다면
          print("정답은" + str(answer) + "입니다.")로 써줘야 함.
          ※ 문자와 정수는 함께 적지 못하지만, f-string을 써주면 같이 쓸 수 있음
          
          
---

# 8장. 조건문

### ■ 조건문
- __프로그램의 흐름을 제어하는 문법__
- 조건문을 이용해 조건에 따라서 프로그램의 로직을 설정할 수 있음

  ※ 조건문은 대부분의 프로그램에서 필수적으로 사용
  ※ 어떤 변수의 값에 따라서 서로 다른 로직을 수행하거나 할 때 효과적으로 사용 가능
  
### ▷ 들여쓰기
- 파이썬에서는 __코드의 블록(Block)을 들여쓰기(Indent)로 지정__
  * 블록(Block) : 특정한 기능을 수행하기 위한 한 단위의 코드 묶음
- 탭을 사용하는 쪽과 공백 문자(space)를 여러 번 사용하는 쪽으로 두 진영 있음
- 파이썬 스타일 가이드라인에서는 __4개의 공백 문자를 사용하는 것을 표준으로 설정__


### ▷ 조건문의 기본 형태
- __if ~ elif ~ else __

      if 조건문 1:
          조건문 1일 True일 때 실행되는 코드
      elif 조건문 2:
          조건문 1에 해당하지 않고, 조건문 2가 True일 때 실행되는 코드
      else:
          위의 모든 조건문이 모두 True 값이 아닐 때 실행되는 코드
          
          
### ■ 비교 연산자
- __특정한 두 값을 비교할 때 이용__
  * 대입 연산자(=)와 같음 연산자(==)의 차이점에 유의
  
비교 연산자|설명
---|---
X == Y|X와 Y가 서로 같을 때 참(True)이다.
X != Y|X와 Y사 서로 다를 때 참(True)이다.
X > Y|X가 Y보다 클 때 참(True)이다.
X < Y|X가 Y보다 작을 때 참(True)이다.
X >= Y|X가 Y보다 크거나 같을 때 참(True)이다.
X <= Y|X가 Y보다 작거나 같을 때 참(True)이다.


### ■ 논리 연산자
- 논리 값(True/False) 사이의 연산을 수행할 때 사용
  * __파이썬에서는 &, |, !를 사용하지 않고 and, or, not을 사용!__

논리 연산자|설명
---|---
X and Y|X와 Y가 모두 참(True)일 때 참(True)이다.
X or Y|X와 Y 중에 하나만 참(True)이어도 참(True)이다.
not X|X가 거짓(False)일 때 참(True)이다.


### ■ 파이썬의 기타 연산자
- 다수의 데이터를 담는 자료형을 위해 __in 연산자와 not in 연산자__ 가 제공
  * 리스트, 튜플, 문자열, 딕셔너리 모두에서 사용 가능
  
in 연산자와 not in 연산자|설명
---|---
x in 리스트|리스트 안에 x가 들어가 있을 때 참(True)이다.
x not in 문자열|문자열 안에 x가 들어가 있지 않을 때 참(True)이다.

### ■ 파이썬의 pass 키워드
- 아무것도 처리하고 싶지 않을 때 pass 키워드를 사용

(예시) 
 * 디버깅 과정에서 일단 조건문의 형태만 만들어 놓고 조건문을 처리하는 부분은 비워놓고 싶은 경우
 * 나중에 작성할 코드 부분을 일단 무시하고 넘어가기 위해 사용함
 
        score = 85
        if score >= 80:
          pass # 나중에 작성할 소스코드
        else:
          print('성적이 80점 미만입니다.')
          
### ▷ 조건문의 간소화
- 조건문에서 실행될 소스코드가 한 줄인 경우, 굳이 줄 바꿈을 하지 않고도 간략하게 표현 가능
        
      score = 85
        
      if score >= 80: result = "Success"
      else: result = "Fail"
        
- __조건부 표현식__(Conditional Expression)은 __if ~ else문을 한줄에 작성 가능__
  ※ if가 중간에 들어간다는 점을 유의!
  * 삼항 연산자와 같은 개념?

        score = 85
        result = "Success" if score >= 80 else "Fail"

        print(result)
      
### ▷ 파이썬 조건문 내에서의 부등식
- 파이썬은 조건문 안에서 수학의 부등식을 그대로 사용 가능

(예시) x > 0 and x < 20 과 0 < x < 20은 같은 결과 반환

 * 다른 언어에서는 x > 0 and x < 20 방법으로만 실행 가능
 
 
---

# 9강. 반복문

### ■ 반복문
- 특정한 소스코드를 반복적으로 실행하고자 할 때 사용하는 문법
- __while문__ vs. __for문__
  * 어떤 것을 사용해도 상관 없음
  * 다만 코딩 테스트에서의 실제 사용 예시를 확인해보면, for문이 더 간결한 경우 많음
  
(while문 예시 1) <1부터 9까지의 모든 정수의 합 구하기>

    i = 1
    result = 0
    
    while i <= 9:
      result += i:
      i += 1
    print(result)
    
(while문 예시 2) <1부터 9까지의 홀수의 합 구하기>
    
    i = 1
    result = 0
    
    while i <= 9:
      if i % 2 == 0:
        result += i
      i += 1
    print(result)
    
    
### ▷ 반복문에서의 무한 루프 (주의)
- __무한 루프(Infinite Loop)__ 란 끊임없이 반복되는 반복 구문을 의미
  * 코딩 테스트에서 무한 루프를 구현할 일은 거의 없으니 유의
  * 반복문을 작성한 뒤에는 항상 반복문을 탈출할 수 있는지 확인
  
        (예시)
        x = 10
        
        while x > 5:
          print(x)
          
        실행 결과> 값이 계속 출력
        
        
### ▷ 반복문 : for문
[for문의 구조]
- 특정한 변수를 이용하여 'in' 뒤의 오는 __데이터(리스트, 튜플 등)에 포함되어 있는 원소를 첫 번째 인덱스부터 차례대로 하나씩 방문__

      for 변수 in 리스트 :
          실행할 소스코드
          
      array = [1, 2, 3, 4, 5]
      for x in array:
          print(x)
          
- for문에서 연속적인 값을 차례대로 순회할 때는 __range()__ 를 주로 사용
  * range(시작 값, 끝 값 + 1) 형태로 사용
  * 인자를 하나만 넣으면 자동으로 시작 값은 0이 됨

        result = 0
        
        for i in range(1, 10):
            result += i
            
        print(result)
        
        
### ■ 파이썬의 continue 키워드
- 반복문에서 남은 코드의 실행을 건너뛰고, 다음 반복을 진행하고자 할 때 continue 사용

(예시) 1부터 9까지의 홀수의 합을 구하기

    result = 0
    
    for i in range(1, 10):
        # 짝수일 때는 건너뛰는 것
        if i % 2 == 0:
            continue
        result += i
        
    print(result)
    
    실행 결과> 25
    
### ■ 파이썬의 break 키워드
- 반복문을 즉시 탈출하고자 할 때 break 사용

(예시) 1부터 5까지의 정수를 차례대로 출력

    i = 1
    
    while True:
        print("현재의 i의 값:" , i)
        # i가 5에 도달했을 때 반복문 탈출!
        if i == 5:
            break
        i += 1
        
        
### ▷ 반복문 예제
 
(예제 1) 점수가 80점만 넘으면 합격
 
    scores = [90, 85, 77, 65, 97]
    
    for i in scores:
        if scores[i] >= 80:
            print(i + 1, "번 학생은 합격입니다.")


(예제 2) 특정 번호의 학생은 제외하기

    scores = [90, 85, 77, 65, 97]
    cheating_student_list = {2, 4}
    
    for i in scores:
       if i + 1 in chating_student_list:
         continue:
       if score[i] >= 80:
         print(i + 1, "번 학생은 합격입니다.")
      
      
### ▷ 중첩된 반복문(이중 for문) : 구구단 예제

    for i in range(2, 10):
       for j in range(1, 10):
         print(i, "X", j, "=", i * j)
       print()
