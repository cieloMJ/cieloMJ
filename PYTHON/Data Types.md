| 범주 | 예시 | 특징 |
| --- | --- | --- |
| 텍스트 시퀀스 | `str` | 순서 있음, 변경 불가, 문자 기반 |
| 일반 시퀀스 | `list`, `tuple`, `range` | 순서 있음, 숫자/객체 저장 |
| 비시퀀스 | `int`, `float`, `bool` 등 | 순서 없음, 인덱싱 불가 |
| 기타 | `dict`, `set`, `bytes` 등 | 구조적 데이터 |

| 분류 | 종류 | 특징 |
| --- | --- | --- |
| Numeric Types |  `int` , `float`, `complex` |  |
| Text Sequence Type | `str` |  |
| Sequence Types | `list`, `tuple`, `range` |  |
| Non-Sequence Types | `set`, `dict` |  |
| 기타 | `Boolean`, `None`, `Fuctions` |  |

- 참고
    
    ## Collection
    
    **개념**
    
    - 여러 개의 값을 하나로 묶어 관리하는 자료형을 통칭하는 말
        - 여러 물건을 담는 보관함과 같음
    - 목적에 따라 다양한 종류의 컬렉션 제공
        - str, list, tuple, range, set, dict 데이터 타입이 모두 collection에 분류됨
    
    **구분**
    
    - 생성 후 내용 변경 가능 여부
        - 불변 (Immutable)
            - 특징 : 변경 불가, 안정성, 예측 가능
            
            ```python
            my_str = 'hello'
            # TypeError : 'str' object does not support item assignment
            my_str[0] = 'z'
            ```
            
            - 종류
                - str
                - tuple
                - range
                
        - 가변 (Mutable)
            - 특징 : 변경 가능, 유연성, 효율성
            
            ```python
            my_list = [1, 2, 3]
            my_list[0] = 100
            
            print(my_list)   # [100, 2, 3]
            ```
            
            - 종류
                - list
                - dict
                - set
    
    ## 형 변환
    
    **Type Conversion**
    
    **개념**
    
    - 한 데이터 타입을 다른 데이터 타입으로 변환하는 과정
    - 종류
        - 암시적 형변환 : 파이썬이 자동으로 처리
        - 명시적 형변환 : 개발자가 직접 지시
    
    ### 암시적 형변환
    
    **Implicit Conversion**
    
    **개념** 
    
    - 파이썬이 연산 중에 자동으로 데이터 타입을 변환하는 것
        - 데이터 손실을 막기 위해 더 정밀한 타입으로 자동 변환해주는 규칙
        - 개발자가 신경 쓰지 않아도 더 안전한 쪽으로 파이썬이 처리해주는 것
            - 마치 작은 정수 상자와 큰 실수 상자의 내용물을 합칠 때, 더 안전하게 담을 수 있는 큰 실수 상자로 알아서 옮겨 담는 것과 같음
    - **Boolean** 과 **Numeric Type**만 가능
        
        ```python
        	# 정수(int)와 실수(1float)의 덧셈
        print(3 + 5.0)   # 8.0
        
        # 불리언(bool)과 정수(int)의 덧셈
        print(True + 3)   # 4
        
        # 불리언 간의 덧셈
        print(True + False)   #1
        ```
        
    
    ### 명시적 형변환
    
    **Explicit Conversion**
    
    **개념**
    
    - 개발자가 변환하고 싶은 타입을 **직접 함수로 지정**하여 변환하는 것
        - 서로 다른 데이터 타입이 호환되도록 맞추는 과정
        - 파이썬은 타입에 엄격
        → 서로 다른 타입은 바로 연결 불가
        - 마치 해외에서 다른 모양의 전기 콘센트에 맞는 어댑터를 끼우는 것과 같음
    - 예시
        
        ![image.png](attachment:503821d7-ee71-454f-9de8-4f4e42fbe5e8:image.png)
        
        - str → int
            
            : 형식에 맞는 숫자만 가능
            
            ```python
            print(int('3.5'))   # ValueError
            print(int(3.5))   # 3
            print(float('3.5))   # 3.5
            ```
            
        - int → str
        : 모두 가능
    
    ---
    
    ## 연산자
    
    - 숫자형의 핵심 행동인 계산을 위한 도구
    
    **종류**
    
    - 산술 연산자
        - 사칙 연산 : 가장 기본이 되는 연산
            
            ![image.png](attachment:fa43631c-7d56-44c1-9aa4-ca2b23f1d7d6:image.png)
            
            ```python
            a = 3
            b = 4
            
            a + b  #7
            a - b  #-1
            a * b  #12
            a / b  #0.75
            a // b  #0
            a % b  #3
            a ** b  #81
            ```
            
        
        - 연산자 우선순위
            
            → 정해진 순서에 따라 연산 수행
            ( 순서가 헷갈리는 경우, 소괄호 ()를 사용하여 원하는 연산 먼저 수행)
            
            - 연산자 우선순위
                
                ![image.png](attachment:6350cbba-6a0a-4586-a18b-1847dba61e18:image.png)
                
            - 예시
                
                ```python
                -2 ** 4  #-16
                -(2 ** 4)  #-16
                (-2) ** 4  #16
                ```
                
    
    - 복합 연산자
        - 연산과 할당이 함께 이뤄짐
            
            ![image.png](attachment:2c566a84-d418-4bf1-889d-81f30540ab79:image.png)
            
        - 산술 연산자 + 대입 연산자(=)
            
            ```python
            a = 1
            
            a = a + 1
            print(a)  #2
            
            a += 1
            print(a)  #2
            ```
            
    
    - 비교 연산자
        - 두 값을 비교하여 그 관계가 맞는지 틀리는 지를 True 혹은 False로 반환
            
            ![image.png](attachment:3eca857b-c0af-405c-904b-b90daa0ce876:image.png)
            
        
        - 차이
            - == 연산자
                - 값(데이터)이 같은 지 비교
                    - 두 변수가 가르키는 객체의 내용이 같은 지 확인
                    - 가치 비교
                - 동등성 ( equality )
                
                ```python
                print(2 == 2.0)   # True
                print(2 != 2)   # False
                
                print('HI' == 'hi')   # False
                
                print(1 == True)   # True
                ```
                
            - is  연산자
                - 객체 자체가 같은 지 비교
                    - 두 변수가 완전히 동일한 메모리 주소의 객체를 가르키는 지 확인
                    - 정체성 비교
                - 식별성 ( identity )
                - 주로 싱글턴 객체 비교 시 사용
                
            
            → 같다고 확인하는 목적이 근본적으로 다름
            
            ⇒ 값 자체가 같은 지 확인 시 : == 사용
            
            ⇒ 완전히 동일한 객체인지 확인 시 : is 사용 
            
    - 논리 연산자
        - 여러 개의 조건을 조합하거나, True/False 값을 반대로 뒤집을 때 사용
        - 대표적 예시
            
            ![image.png](attachment:8011d51a-8676-458b-a6ae-1c0306073c3d:image.png)
            
            ```python
            print(True and False)   # False
            print(True or False)   # True
            print(not True)   # False
            print(not 0)   # True
            ```
            
        - 비교 연산자와 함께 사용 가능
            
            ```python
            num = 15
            result = (num > 10) and (num % 2 == 0)
            print(result)   # False
            
            name = 'Alice'
            age = 25
            result = (name == 'Alice') or (age == 30)
            print(result)   # True
            ```
            
        
        - **단축 평가**
            - 논리 연산에서 두 번째 피연산자를 평가하지 않고 결과를 결정하는 동작
            - 꼭 필요한 계산만 하고, 이미 결과가 정해졌다면 굳이 뒤에 있는 코드까지 확인하지 않는 것
                - 결과가 확정되는 순간, 평가를 단축하고 넘어가는 것
            - 코드 실행을 최적화하고, 불필요한 연산을 피할 수 잇음
            - 단순 True/False 논리 연산을 넘어, 코드 흐름을 제어하고 오류를 방지하며 간단한 코드를 작성하는데 매우 유용
            - 예시
                - and 연산자 : 하나라도 거짓이면 바로 거짓
                - or 연산자 : 하나라도 참이면 바로 참
    
    - 멤버십 연산자
        - 특정한 값이 시퀀스나 다른 컬렉션 안에 포함되어 있는지 확인
            
            ![image.png](attachment:41cc84ec-ead9-4810-891c-7a3aab71f6c7:image.png)
            
            ```python
            word = 'hello'
            print('h' in word)   # True
            print('z' in word)   # False
            
            numbers = [1, 2, 3, 4, 5]
            print(4 not in numbers)   # False
            print(6 not in numbers)   # True
            ```
            
    
    - 시퀀스형 연산자
        - 시퀀스 자료형에 특별한 의미로 사용되는 연산자
            
            ![+ : 시퀀스 연결
            * : 시퀀스 반복](attachment:3ff484eb-bfa0-4dc8-a171-16b9579e08f4:image.png)
            
            + : 시퀀스 연결
            * : 시퀀스 반복
            
            ```python
            print('Gildong' + 'Hong')   # Gildong Hong
            print([1, 2] + ['a', 'b'])   # [1, 2, 'a', 'b']
            
            print('hi' * 5)   # hihihihihi
            print([1, 2]*2)   # [1, 2, 1, 2]
            ```
            
    
    - 연산자 우선 순위
    
    ![image.png](attachment:ae39a739-ac5c-4342-9b3f-9e5347675129:image.png)
    

---

---

# **Numeric Types**

**숫자형 데이터** 

**개념**

- 프로그래밍에서 가장 기본이 되는 데이터 타입
- 값을 계산하고, 수량을 세고, 데이터 분석하는 등에서 사용

## 정수형

**Integer; int**

- 소수점이 없는 숫자 (음수, 0, 양수)
    
    ```python
    student_count = 30
    temperature = -5
    balance = 0
    ```
    

---

## 실수형

**Floating-point; float**

- 소수점이 있는 숫자 (더욱 정밀한 숫자 표현)
    
    ```python
    pi = 3.14
    weight = 65.5
    tax_rate = 0.1
    ```
    

### 컴퓨터식 지수 표현 방식

- 지수 표현법 : 아주 크거나 작은 실수를 간결하게 표현
    - ‘e’ 또는 ‘E’ 사용
        
        ![어떤 것으로 코드 작성하든, 내부적으로 모두 같은 숫자 값으로 인식
        print() 함수는 10진수로 변환하여 보여주는 것](attachment:306238ff-12d7-4f28-9f60-b3c917673bff:image.png)
        
        어떤 것으로 코드 작성하든, 내부적으로 모두 같은 숫자 값으로 인식
        print() 함수는 10진수로 변환하여 보여주는 것
        
    - 예시
    
    ```python
    #1,230,000,000 (1.23 * 10^9)
    big_number = 1.23e9
    
    #0.00314 (3.14 * 10^-3)
    small_number = 3.14e-3
    ```
    
    - 부동소수점 오차 (Floationg-point Rounding Error_
        - 발생 원인
            - 컴퓨터 2진법 사용 : 모든 숫자를 2진수로 변환, 저장함
                
                → 무한 소수 발생과 근사값 저장
                
                → 근사치 때문에 미세한 오차 발생
                
        - 해결책
            - 예시 1. Decimal 모듈 사용
                
                ```python
                # 해결 전
                a = 3.2 - 3.1
                b = 1.2 - 1.1
                print(a) # 0.10000000000000009
                print(b) # 0.09999999999999987
                print(a == b) #False
                
                # 해결 후
                from decimal import Decimal
                
                a = Decimal('3.2') - Decimal('3.1')
                b = Decimal('1.2') - Decimal('1.1')
                
                print(a) #0.1
                print(b) #0.1
                print(a == b) #True
                ```
                
            - 예시 2. round 사용

---

## 복소수

**Imaginary number; j 혹은 J 사용**

- 표현 방식
    
    ```python
    a = 2 + 3j  #(2+3j)
    b = complex(3, -4)  #(3-4j)
    ```
    
    ```python
    b.real  #3.0
    b.imag  #-4.0
    b.conjugate  #3+4j
    abs(b)  #5.0_복소수 크기*루트(복소수*켤레복소수)
    ```
    

---

---

# Sequence Types

**시퀀스 타입**

**개념**

- 여러 개의 값들을 순서대로 나열하여 저장하는 자료형
    - 여러 데이터가 정해진 순서대로 일렬로 늘어선 자료 구조

**특징**

- 순서 (Order)
    - 값들이 순서대로 저장 (정렬X)
- 인덱싱 (Indexing)
    - Index : 시퀀스 자료형에서 각 값의 위치를 식별하기 위해 부여된 고유한 번호
        - 0 부터 시작
        - X[인덱스 숫자]
    - 인덱스를 통해 원하는 칸의 데이터로 바로 접근하여 선택, 수정 가능
- 슬라이싱 (Slicing)
    - 인덱스 범위를 조절하여 전체 데이터 중 원하는 부분만 값을 잘라내서 사용 가능
    - 시퀀스의 일부분을 잘라내어 **새로운 시퀀스 생성**
        - X[start:stop:step]
            - stop : 슬라이싱을 끝낼 인덱스로, 포함되지 않음
            - step :  몇 개씩 건너뛰며 값을 가져올 지에 대한 간격
- 길이 (Length)
    - len( ) 함수를 사용하여 저장된 값의 개수 (길이) 계산 가능
        - len(x)
- 반복 (Iteration)
    - 반복문을 사용하여 각 값을 하나씩 순서대로 꺼내 사용 가능
        - for i in x
        - item in x (포함 여부)

**종류**

- 대표 시퀀스 타입
    - str
    - list
    - tuple
    - range
    
    | 시퀀스 종류 | 자료형 | 특징 |
    | --- | --- | --- |
    | 텍스트 시퀀스 | `str` | 문자들의 나열, 불변 |
    | 컬렉션 시퀀스 | `list`, `tuple` | 여러 객체 저장, 순서 있음 |
    | 숫자 시퀀스 | `range` | 연속된 정수 범위, 불변 |
    | 바이너리 시퀀스 | `bytes`, `bytearray` | 이진 데이터 다룸 (예: 파일 입출력 등) |

---

## 문자열

**String; str**

**개념**

- 연속된 문자들의 나열
- 문자들의 **순서가 있는,** **변경 불가능**한 시퀀스 자료형
    - **불변성**
        
        : 한번 생성된 문자열 객체는 그 내용을 절대 수정할 수 없음
        
        - 문자열 바꾸기 위해서는 **새로운 문자열** 생성해야 함
        
        ```python
        my_str = 'Hello'
        new_str = my_str[0] + 'a' + my_str[2:]
        
        # Hallo
        print(new_str)
        ```
        

**문자열 생성**

- 따옴표 활용 : 따옴표로 둘러싸여 있으면 모두 문자열
    
    → 작은 따옴표( ‘ ) 혹은 큰 따옴표 ( “ )로 감싸서 표현
    
- 문자열 안에 따옴표가 있다면, 서로  다른 종류의 따옴표로 감싸서 표현
(**구문 오류** Syntax Error 발생 방지)
    
    ```python
    # Hello, World!
    print('Hello, World!"
    
    # str
    print(type('Hello, World!')
    
    # 문자열 안에 "큰 따옴표" 사용 시 작은 따옴표로 묶기
    print('문자열 안에 "큰 따옴표" 사용 시 작은 따옴표로 묶기')
    
    # 문자열 안에 '작은 따옴표' 사용 시 큰 따옴표로 묶기
    print("문자열 안에 '작은 따옴표' 사용 시 큰 따옴표로 묶기")
    ```
    
    ```python
    "Python's favorite food is perl"  #구문오류 방지
    'Python\'s favrorit food is perl' #역슬래시 사용하여 오류 방지
    
    '"Python is very easy." he says'  #구문오류 방지
    "\"Python is very easy.\" he says" #역슬래시 사용
    ```
    

- **이스케이프 시퀀스**
    
    **Escape sequence**
    
    - 사용 목적 : 출력물을 보기 좋게 정렬하기 위함
    - 사용법 : 역슬래시(\)와 문자 조합
    
    ![image.png](attachment:be7e8271-5ece-4e3d-ac6d-08a93bb4a147:image.png)
    
    ![image.png](attachment:c8e2eafd-f6ec-40fc-b4a9-bfcc700783cf:image.png)
    
    → 하지만 읽기 불편하고 줄이 길어지는 단점이 있음
    
    ⇒ 이러한 단점을 극복하는 방안으로 연속된 작은따옴표 혹은 큰따옴표 3개를 사용
    
    ```python
    # 따옴표 앞 \를 붙여 문자로 인식
    print('He's a boy')
    
    # \n은 줄바꿈을 의미
    print('첫째 줄\n둘째 줄')
    
    # \t은 탭을 의미
    print('첫 문장\t다음 문장')
    
    #여러 줄 문자열 작성 시 """ 혹은 ''' 사용
    multi_line_str = """
    이것은
    여러 줄로 이루어진
    문자열입니다.
    """
    print(multi_line_str)  #이것은
    											 #여러 줄로 이루어진
    											 #문자열입니다.
    ```
    

- **문자열 포매팅**
    
    **string formatting; f-string**
    
    : 문자열 내에 어떤 값(변수나 표현식의 결과)를 삽입하는 강력한 방법
    
    ```python
    name = '홍길동'
    age = 25
    
    greeting = f'제 이름은 {name}이고 나이는 {age}살입니다.'
    
    # 제 이름은 홍길동이고 나이는 25살입니다.
    print(greeting)
    ```
    
    - 문자열 시작 : f ’
    - 삽입 부분(표현식) : 중괄호 { }로 감싸기
    - 알고리즘 등에서도 거의 매번 사용 (중요!)
    - 심화 사용법
        - 표현식 직접 삽입 (계산/함수 호출 등)
            
            ```python
            #할인가격은 800원입니다.
            price = 1000
            discount = 0.2
            print(f'할인가격은 {price*(1-discount)}원입니다.')
            
            #결과:합격
            score = 85
            print(f'결과:{'합격' if score >= 60 else '불합격'}")
            #삼항 연산자 : A if 조건 else B
            
            #메시지:Jay님, 반갑습니다!
            def greeting(name):
            	return f'{name}님, 반갑습니다!'
            
            user = "Jay"
            print(f'메시지:{greeting(user)}')
            #함수 호출
            ```
            
        - 숫자 포맷팅 (자리수, 소수점 등)
            
            ```python
            value = 1234.56789
            
            #1234.57
            print(f'{value:.2f')  #소수점 둘째 자리까지
            
            #   1234.57
            print(f'{value:10.2f}')  #인덱스 10칸, 소수점 둘째자리까지
            
            #1,234.568
            print(f"{value:,}")  #천 단위 쉼표
            
            num = 7
            
            # '    7'
            print(f"{num:>5}")   #오른쪽 정렬
            
            # '7    '
            print(f"{num:<5}")   #왼쪽 정렬
            
            # '  7  '
            print(f"{num:^5}")   #가운데 정렬
            
            num = 42
            
            #00042
            print(f"[{num:0>5}]")  #5자리 확보, 앞을 0으로 채움
            
            #42____
            print(f"[{num:_<6}]")
            ```
            
        - 문자열 포맷팅
            
            ```python
            name = "Jay"
            print(f"{name:>10}")  # 오른쪽 정렬
            print(f"{name:<10}")  # 왼쪽 정렬
            print(f"{name:^10}")  # 가운데 정렬
            
            f"{값:채움문자<10}"  # 왼쪽 정렬 + 채움문자
            f"{값:채움문자^10}"  # 가운데 정렬 + 채움문자
            f"{값:채움문자>10}"  # 오른쪽 정렬 + 채움문자
            
            name = "Jay"
            
            #Jay*******
            print(f"[{name:*<10}]")  #왼쪽 정렬, *로 채우기
            
            # ###Jay###
            print(f"[{name:#^10}]")  #가운데 정렬, #로 채우기
            
            #.......Jay
            print(f"[{name:.>10}]")  #오른쪽 정렬, .으로 채우기
            ```
            
        - 딕셔너리/리스트 등 자료구조 접근
            
            ```python
            #딕셔너리 
            
            user = {"name": "Jay", "age": 25}
            print(f"이름: {user['name']}, 나이: {user['age']}")
            ```
            
            ```python
            #리스트
            
            fruits = ['사과', '배', '바나나']
            print(f"가장 좋아하는 과일: {fruits[0]}")
            ```
            
        - 다중 줄 f-string
            
            ```python
            name = "Jay"
            age = 25
            msg = f"""
            안녕하세요, 제 이름은 {name}입니다.
            나이는 {age}살이고, 파이썬을 좋아합니다.
            """
            print(msg)
            ```
            
        - 날짜/시간 포맷팅
            
            ```python
            from datetime import datetime
            
            now = datetime.now()
            print(f"오늘 날짜: {now:%Y-%m-%d %H:%M:%S}")
            ```
            
        - 중첩 표현 / if 문 (삼향 연산자 등)
            
            ```python
            score = 85
            print(f"합격 여부: {'합격' if score >= 60 else '불합격'}")
            ```
            
        - = 연산자로 디버깅 (변수명 + 값 출력)
            
            ```python
            x = 10
            y = 20
            print(f"{x=}, {y=}, {x + y=}")
            # 출력: x=10, y=20, x + y=30
            ```
            
        - 예시
            - 보고서 출력
                
                ```python
                employee = "홍길동"
                sales = 1250000
                print(f"{employee}의 3월 매출은 {sales:,}원입니다.")
                ```
                
            - 파일 경로 자동 완성
                
                ```python
                folder = "images"
                filename = "logo.png"
                print(f"파일 경로: /usr/local/{folder}/{filename}")
                ```
                
            - 반복문
                
                ```python
                for i in range(1, 6):
                    print(f"{i}번째 반복입니다.")
                ```
                
- **특징**
    
    ![image.png](attachment:ca9043e0-8cae-400f-bbaa-730e06ef99e7:image.png)
    
    - 인덱싱 (Indexting)
        - 인덱스 : 각 값의 위치를 식별하기 위해 부여된 고유 번호
        - 인덱스는 0부터 사용
            
            ![image.png](attachment:97276590-8f98-4159-845d-5cf3d13dd89e:image.png)
            
            - 양수 인덱스
                
                ```python
                	a = "Life is too short, you need Python"
                	a[3]  #'e'
                	
                	b = a[0] + a[1] + a[2] + a[3]
                	b  #'Life'
                ```
                
            - 음수 인덱스
                - 파이썬은 다른 언어와 달리 음수 인덱스 지원
                - 마지막 요소 확인 시 편리
                
                ```python
                a = "Life is too short, you need Python"
                a[-1]  #'n'
                ```
                
    - 슬라이싱 (Slicing)
        - 시퀀스의 일부분을 잘라내어 **새로운 시퀀스를 만드는** 작업
        - 대괄호 [ ] 사용
            
            ```python
            # 슬라이싱 사용 방법
            my_sequence[start:stop:step]  #'hello' 예시
            
            #ll
            my_str[2:4]  #index 2부터 index3까지
            
            #hello
            my_str[:]  #처음부터 끝까지
            
            # hel
            my_str[:3]  #처음부터 index 2까지
            
            # lo
            my_str[3:]  #index 3부터 마지막까지
            
            #el
            my_str[1:-2]  #1번째부터 -3번까지 (이 때도 -2는 불포함)
            
            # hlo
            my_str[::2]  #처음부터 끝까지 2칸 간격
            
            # olleh
            my_str[::-1]  #역순
            
            # ell
            my_str[1:4][::-1]  #index 1에서 3까지 값 역순
            ```
            
    - 길이
        
        ```python
        #5
        
        text = "hello"
        print(len(text))
        
        #13
        sentence = "Hello, world!"
        print(len(sentence))
        ```
        
    - 반복
        
        ```python
        #hihihi
        print("hi" * 3)
        
        #*****
        star = "*" * 5
        print(star)
        
        #['hello', 'hello', 'hello']
        print(["hello"] * 3)
        
        #------ (글자 수만큼 - 출력)
        word = "python"
        print(f"{word}의 길이는 {len(word)}자입니다.")
        print("-" * len(word))
        ```
        

---

## 리스트

**List**

**개념**

- 여러 개의 값을 순서대로 저장하는, 변경 가능한 (mutable) 시퀀스 자료형
    - 가변성 : 생성한 후에도 그 내용(값)을 변경할 수 있는 성질
        - 문자열과는 정 반대인 중요한 특징
        - 수정, 추가, 삭제 가능
            - 인덱싱으로 값 수정
            
            ```python
            my_list = [1, 2, 3, 4, 5]
            my_list[1] = 'two'
            print(my_list)   #[1, 'two', 3, 4, 5]
            ```
            
            - 슬라이싱으로 여러 값 한 번에 바꾸기
            
            ```python
            my_list = [1, 2, 3, 4, 5]
            my_list[2:4] = ['three', 'four']
            print(my_list)   #[1, 2, 'three', 'four', 5]
            ```
            
        

**리스트 만들기**

- 대괄호 [ ] 안의 값(요소)들을 쉼표( , )로 구분하여 만듦
    
    ```python
    # 값이 없는 리스트 생성
    my_list_1 = []
    a = list()
    
    # 숫자와 문자열을 담은 리스트
    my_list_2 = [1, 'a', 3, 'b', 5]
    
    # 숫자, 문자열, 다른 리스트를 포함한 리스트
    my_list_3 = [1, 2, 3, 'python', ['hello', 'world']]
    print(len(my_list_3)) = 5  # 리스트도 1개로 취급
    ```
    
    → 숫자, 문자열, 다른 리스트까지 포함 가능
    

**특징**

- 인덱싱
    
    ```python
    my_list = [1, 'a', 3, 'b', 5]
    
    print(my_list[1])  #a
    
    a = [1, 2, 3, ['a', 'b', 'c']]
    
    a[-1]  #['a', 'b', 'c']
    a[-1][0]  #'a'
    
    #리스트 요소 삭제하기
    a = [1, 2, 3]
    del a[1]
    a   #[1, 3]
    ```
    
- 슬라이싱
    
    ```python
    print(my_list[2:4])  #[3, 'b']
    ```
    
    ```python
    my_list_2 = [1, 2, 3, 4, 5]
    my_list_2[2:4] = ['three', 'four']
    print(my_list_2)  #[1, 2, 'three', 'four', 5]
    ```
    
    ```python
    a = [1, 2, 3, 4, 5]
    del a[2:]
    a   #[1, 2]
    ```
    

- 길이
    
    ```python
    print(len(my_list))  #5
    ```
    

- 반복
    
    ```python
    a = [1, 2, 3]
    a * 3  #[1, 2, 3, 1, 2, 3, 1, 2, 3]
    ```
    

### 중첩 리스트

**Nested List**

**개념**

- 다른 리스트를 값으로 가진 리스트
- 중첩 : 어떤 자료 구조 안에 같은 종류의 자료 구조가 포함된 형태

**접근 방법**

- 인덱스를 연달아 사용하여 안쪽 리스트 값에 접근
    
    ```python
    my_list = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]
    
    print(len(my_list))   # 5
    print(my_list[4][-1])   # !!!
    print(my_list[-1][1][0])   # w
    ```
    
    - 먼저 바깥 리스트의 인덱스로 안쪽 리스트 선택
    - 선택된 안쪽 리스트에 다시 한번 인덱스 사용

- 주의
    - 리스트 연산 오류
        
        ```python
        a = [1, 2, 3]
        a[2] + "hi"  #error
        
        str(a[2]) + "hi"  #3hi
        ```
        

---

## 튜플

**Tuple**

**개념**

- 여러 개의 값을 순서대로 저장하는 변경 불가능한 시퀀스 자료형
    - 불변성
        
        ⇒ 개발자가 사용하는 데이터 타입이 아닌, **내부 동작**같이 안전한 데이터 전달 시에 사용
              데이터의 안정성과 무결성 보장
        

**튜플 생성**

- 소괄호 ( ) 안 값(요소)들을 쉼표( , )로 구분하여 만듦
    - 소괄호를 생략해도 됨
    - 단일 요소 튜플을 만들 때에는 반드시 trailing comma (후행 쉼표)를 사용
        
        ```python
        t1 = ()
        t2 = (1,)
        t3 = (1, 2, 3)
        t4 = 1, 2, 3
        t5 = ('a', 'b', ('ab', 'cd'))
        ```
        
- 한번 만들어지면 절대 수정, 추가, 삭제 불가
    - 다중 할당, 값 교환, 함수 다중 반환 값 등에서 사용
    
    ```python
    # 다중 할당
    x, y = 10, 20
    print(x)  #10
    print(y)  #20
    ## 실제 내부 동작
    (x, y) = (10, 20)
    
    # 값 교환
    x, y = 1, 2
    x, y = y, x
    ## 실제 내부 동작
    temp = (y, x)  # 튜플 생성
    x, y = temp   # 튜플 풀어냄
    print(x, y)  # 2 1
    ```
    

**특징** 

- 인덱싱
- 슬라이싱
- 길이 확인
- 반복
- 연산
    
    ![image.png](attachment:47029962-8aff-491f-883a-85337904064b:image.png)
    

---

## Range

**개념**

- 연속된 정수 시퀀스를 생성하는, 변경 불가능한 (immutable) 자료형
- 주로 반복문과 함께 사용
    - 특정 횟수만큼 코드를 반복 실행할 때 유용
    - 모든 숫자를 메모리에 저장하는 대신, 특정 규칙만 기억하여 효율적으로 메모리 사용
- range(start, stop, step)
    - 1개, 2개 또는 3개의 매개변수(인자)를 가질 수 있음
        - 1개 : range(stop)
        - 2개 : range(start, stop)
        - 3개 : range(start, stop, step)
    - list로 형 변환 시 내부 값을 확인 가능

**규칙**

- 값의 범위
    - stop : 생성되는 시퀀스에 미포함
    - step : 숫자 시퀀스의 간격과 방향 결정
        - 양수인 경우
            - start → stop 으로 증가
        - 음수인 경우
            - start → stop 으로 감소
            - start > stop 이어야 함

### 

---

---

# Non-Sequence Types

## 딕셔너리

**dict**

**개념**

- key-value 쌍으로 이루어진 순서와 중복이 없는 변경 가능한 자료형
    - 순서가 없기에 인덱스 X
    → 순서를 탐색하지 않고 키로 바로 접근
- 데이터에 순서가 필요 없고, 각 데이터에 의미 있는 이름을 붙여 관리하고 싶을 경우 사용
- 핵심
    - 순서가 없는 자료형
    - Key를 통한 접근
    

**딕셔너리 생성**

- 중괄호 { } 안 값(요소)들을 쉼표( , )로 구분하여 만듦
- key-value 쌍 (1개의 값)
    - key (키)
        - 값을 식별하기 위한 고유한 이름표
        - 중복 불가 (고유해야 함)
        - **변경 불가능한 자료형**만 사용 가능
            - O (가능) : str, int, float, tuple
            - X (불가) : list, dict
    - value (값)
        - 키에 해당하는 실제 데이터
        - 어떤 자료형이든 자유롭게 사용 가능
            - 여러 개의 값을 담을 수 있음
            - 각 값에는 순서가 없음

**값 접근 방법**

- 대괄호 [ ] 사용
- key를 사용하여 해당 value 접근 가능
    - 존재하지 않는 key로 접근 시 KeyError 발생

```python
my_dict = {'name': '홍길동', 'age': 25}

print(my_dict['name'])   #'홍길동'
print(my_dict['test'])   # KeyError: 'test'

# 추가
my_dict['apple'] = 50
print(my_dict)  #{'name': '홍길동', 'age': 25, 'apple': 50}

# 변경
my_dict['apple'] = 100
print(my_dict)  #{'name': '홍길동', 'age': 25, 'apple': 100}
```

---

## 세트

**set**

**개념**

- 순서와 중복이 없는 변경 가능한 자료형
- 수학에서의 집합과 동일한 연산 처리 가능
    - 두 데이터 그룹 간의 관계를 파악하는 데 효율적
    
    ```python
    my_set_1 = {1, 2, 3}
    my_set_2 = {3, 6, 9}
    
    # 합집합
    print(my_set_1 | my_set_2)   # {1, 2, 3, 6, 9}
    
    # 차집합
    print(my_set_1 - my_set_2)   # {1, 2}
    print(my_set_2 - my_set_1)   # {6, 9}
    
    # 교집합
    print(my_set_1 & my_set_2)   # {3}
    ```
    

**특징**

- 중복 허용 안 함
    - 똑같은 값은 단 하나만 존재 가능
- 순서 없음
    - 인덱싱이나 슬라이싱 사용 가

**세트 생성**

- 중괄호 { } 사용
    - 쉼표로 값 구분
- 빈 세트는 set( )으로 만듦
    - 빈 딕셔너리와 혼동 피하기 위함

### 

---

---

# Other Types

## None

**개념**

- ‘값이 없음’을 표현하는 특별한 데이터 타입
    - 마치 내용물이 없는 빈 상자와 같음
    - 숫자 0, 빈 문자열 (’ ‘)과는 다른, 
    ‘**값이 존재하지 않음**’ 혹은 ‘**아직 정해지지 않음**’이라는 상태 나타내기 위해 사용
- 변수에 아직 아무 것도 할당하고 싶지 않은 경우에 사용

---

## Boolean

**개념**

- 참(True)과 거짓(False), 단 두 가지 값만 가지는 데이터 타입
    - 마치 on/off 스위치와 같음
- 비교 / 논리 연산의 평가 결과로 사용
    - 주로 조건/반복문과 함께 사용
    - 조건문에서 맞음 또는 틀림을 판단하는 역할

```python
is_active = True
is_logged_in = False

print(is_active)   # True
print(is_logged_in)   # False
print(10>5)   # True
print(10 == 5)   # False
```
