### 학습 목표

- 데이터 구조의 개념과 필요성
    - 문자열 메서드 활용
    - 리스트 메서드 활용 - 데이터 추가, 삭제, 탐색, 정렬
- 개념 이해 및 변수 할당 원리
    - 객체
    - 참조
    - 가변성, 불변성
- 복사의 차이와 활용
    - 얕은 복사
    - 깊은 복사
- List Comprehension
- Method Chaining

---

# 

# 데이터 구조 (Data Structure)

- 정의 : 여러 데이터를 효과적으로 사용, 관리하기 위한 구조
    - 데이터 : str, list, dict 등
    - 데이터를 효율적으로 정리하고 관리하기 위한 정리함 개념
    → 목적에 맞게 데이터를 담아두는 방법
    - 컴퓨터 공학에서는 ‘**자료 구조’**라고 함
        - 각 데이터의 효율적인 저장, 관리를 위한 구조를 나눠 놓은 것
        - 단순히 데이터를 묶는 것을 넘어, 
        프로그램의 성능과 효율성, 유지보수에 큰 영향을 미치는 핵심적인 개념
            
            ![알고리즘에서는 선형 구조, 비선형 구조를 중심으로 다](attachment:e7c48cfe-456d-49ca-b461-e2b0ae190c89:image.png)
            
            알고리즘에서는 선형 구조, 비선형 구조를 중심으로 다
            

## 메서드 (Method)

- 데이터 구조의 활용
- 문자열, 리스트, 딕셔너리 등 각 **데이터 구조**의 메서드를 호출하여 다양한 기능 활용 가능
    - 다양한 데이터 구조는 저마다 고유한 **메서드** 존재
    - 호출 : 함수에서 사용
    → 메서드도 함수라는 큰 범주 안에 들어감
- 데이터 구조의 데이터를 **효율적으로 조작**하거나 **특정 기능을 수행**하기 위해 제공
- 정의 : **객체에 속한 함수**
    - 객체가 특정 작업을 수행하도록 정의된 함수
    - 객체 : 특정 데이터(정보)와 그 데이터를 처리하는 기능(메서드)를 하나로 묶은 것
        - 예시
            - 정수 객체 : 6
            - 리스트 객체 : [ ]
            - 문자열 객체 : “1”
    - 클래스(class) 내부에 정의되는 함수
        - 클래스 : 타입을 표현하는 방법 → 예를 들어 str

<aside>
💡

메서드는 어딘가(클래스)에 속해 있는 함수이며, 
각 데이터 타입마다 다양한 기능을 가진 메서드가 존재

</aside>

- 호출 방법
    
    **데이터 타입 객체.메서드()**
    
    - 객체(데이터)에게 원하는 명령(메서드)을 내리는 방
    - 단독으로는 호출 불가

### 메서드 체이닝 (Method Chaining)

- 정의 : 여러 메서드를 연속해서 호출하는 방식
    - 메서드의 반환 값에 메서드를 추가하는 것
    - 반환 값이 없다면 None.메서드()가 발생할 수 있음
    → 메서드 사용 불가
- 예시
    
    ```python
    text = 'heLLo, woRld!'
    
    new_text = text.swapcase().replace('l', 'z')
    
    #text.swapcase() : 대소문자 반전
    #.replace('l', 'z') : 소문자 'l'을 'z'로 교체
    
    print(new_text)  #'HEzzO, WOrLD!'
    ```
    
- 주의 사항
    - 모든 메서드가 체이닝을 지원하는 것은 아님
        - 메서드가 **객체를 반환할 때**만 가능
    - None을 반환하는 메서드는 메서드 체이닝 불가능
        
        ```python
        numbers = [3, 1, 4, 1, 5, 9, 2]
        result = numbers.copy().sort()
        print(numbers)  #[3, 1, 4, 1, 5, 9, 2]
        print(result)  #None
        
        #올바른 경우 
        sorted_numbers = sorted(numbers.copy())
        print(sorted_numbers)   #[1, 1, 2, 3, 4, 5, 9]
        ```
        
    
    ⇒ 메서드 체이닝을 사용할 때에는 각 **메서드의 반환 값**을 잘 이해하고 있어야 함
    

### 문자 유형 판별 메서드

- isdecimal() : 문자열이 모두 숫자 문자(0~9)로만 이뤄져 있어야 True
- isdigit() : isdecimal()과 비슷하지만, 유니코드 숫자도 인식
- isnumeric() : isdigit()과 유사하지만, 몇 가지 추가적인 유니코드 문자 인식(분수, 지수, 루트 기호 등)
    
    ![image.png](attachment:b2b6cffc-b709-49e6-8115-513333a74968:image.png)
    

# 

---

## 시퀀스 데이터 구조

- 문자열
- 리스트
- 튜플

---

### 문자열

- 문자열 : 불변 객체
    
    → 원본을 바꾸는 것이 아니라 **새로운 문자열을 반환**하는 것
    
- 조회 / 탐색 및 검증 메서드
    - .find(x) : x의 첫 번째 위치를 반환. 없으면 **-1** 반환
        
        ```python
        print('banana'.find('a'))  #1
        print('banana'.find('z'))  #-1
        ```
        
    - .index(x) : x의 첫 번째 위치를 반환. 없으면 **오류** 발생
        
        ```python
        print('banana'.index('a'))  #1
        print('banana'.index('z'))  # valueError : substring not found
        ```
        
    - .isupper( ) : 문자열 내의 모든 문자가 대문자인지 확인
        
        ```python
        string1 = 'HELLO'
        string2 = 'Hello'
        
        print(string1.isupper())  #True
        print(string2.isupper())  #False
        ```
        
    - .islower( ) : 문자열 내의 모든 문자가 소문자인지 확인
        
        ```python
        string1 = 'HELLO'
        string2 = 'Hello'
        
        print(string1.islower())  #False
        print(string2.islower())  #False
        ```
        
    - .isalpha( ) : 문자열 내의 모든 문자가 알파벳인지 확인 (유니코드 상 letter_한국어도 포함)
        
        ```python
        string1 = 'Hello'
        string2 = '123heis98576ssh'
        
        print(string1.isalpha())  #True
        print(string2.isalpha())  #False
        ```
        

- 문자열 조작 메서드 **(새로운 문자열 반환)**
    - .replace(old, new[, count]) : 바꿀 대상 글자를 새로운 글자로 바꿔서 전환
        
        ```python
        text = 'Hello, world! world world"
        new_text1 = text.replace('world', 'Python')
        new_text2 = text.replace('world', 'Python', 1)
        
        print(new_text1)  #Hello, Python! Python Python
        print(new_text2)  #Hello, Python! world world
        ```
        
        - old : 바꿀 대상
        - new : 새로운 대상
        - count : 바꿀 개수
    - .strip([chars]) : 문자열의 시작과 끝에 있는 공백이나 특정 문자를 제거
        
        ```python
        text = '    Hello, world    "
        new_text = text.strip()
        left_text = text.lstrip()
        right_text = text.rstrip()
        
        print(new_text)  #'Hello, world'
        print(left_text)  #'Hello, world    '
        print(right_text)  #'    Hello, world'
        ```
        
        - lstrip( ) : 왼쪽 공백, 특정 문자 제거
        - rstrip( ) : 오른쪽 공백, 특정 문자 제거
    - .split(sep=None, maxsplit=-1) : sep를 구분자 문자열로 사용 → 문자열의 단어를 리스트로 반환
        
        ```python
        text = 'Hello, world!'
        word1 = text.split(',')
        word2 = text.split()
        
        print(word1)  #['Hello', ' world!']
        print(word2)  #['Hello,', 'world!']
        ```
        
        - sep : 구분자
        - maxsplit : 최대 분할 개수
            - 기본 값 :  -1 (제한 없이 모두 나누는 것)
            - 이 횟수만큼 나누고, 남은 부분은 마지막 요소로 들어감
    - ‘separator’.join(iterable) : iterable의 문자열을 연결한 하나의 문자열 반환
        
        ```python
        words = ['Hello', 'world!']
        text = '-'.join(words)
        
        print(text)  #'Hello-world!'
        ```
        
        - separator : 문자열 사이에 들어갈 구분자
            - 구분자를 앞쪽에 씀
        - iterable : 리스트, 튜플, 문자열 등 반복 가능한 문자열 모음
            - 반복 가능한 객체를 인자로 받음
            - 반복 가능한 객체의 문자열을 받아서 각각 구분자로 연결 → 하나의 문자열로 반환함
    - .capitalize( ) : 문장 첫 알파벳 대문자, 나머지 소문자
    - .title( ) : 단어들 첫 알파벳 대문자, 나머지 소문자
    - .upper( ) : 전부 대문자
    - .lower( ) : 전부 소문자
    - .swapcase( ) : 문자열과 반대되도록 작성 → 대문자는 소문자로, 소문자는 대문자로 변환
        
        ```python
        text = 'heLLo, woRld!'
        new_text1 = text.capitalize()
        new_text2 = text.title()
        new_text3 = text.upper()
        new_text4 = text.lower()
        new_text5 = text.swapcase()
        
        print(new_text1)   #Hello, world!
        print(new_text2)   #Hello, World!
        print(new_text3)   #HELLO, WORLD!
        print(new_text4)   #hello, world!
        print(new_text5)   #HEllO, WOrLD!
        ```
        

---

### 리스트

- 리스트 : 가변 객체
    
    → 원본을 조작하는 것이기에 반환 값이 없음 (일부 메소드는 반환 有)
    
- 리스트 값 추가 메서드
    - .append(x)
        
        ```python
        my_list = [1, 2, 3]
        my_list.append(4)
        
        print(my_list)  #[1, 2, 3, 4]
        ```
        
        - 리스트 마지막에 항목 x를 추가
            - x 그 자체로 추가 → 중첩 리스트가 될 수 있음
        - 리스트에는 추가되지만 반환되지 않음 → None 반환
    - .extend(iterable)
        
        ```python
        my_list = [1, 2, 3]
        my_list.extend([4, 5, 6])
        
        print(my_list)  #[1, 2, 3, 4, 5, 6]
        ```
        
        - 리스트에 다른 반복 가능한 객체의 모든 항목 추가
        - append와의 차이점
            - append는 X에 1개를 작성하지만 
            extend는 여러 개를 작성할 수 있으며 반복 가능한 객체가 아니면 들어갈 수 없음
                
                ```python
                my_list.extend(100)
                #TypeError: 'int' object is not iterable
                ```
                
            - append 는 x 그대로 들어가기에 중첩 리스트가 될 수 있으나
            extend는 반복 가능한 객체가 아니면 들어갈 수 없으며 항목의 요소로 풀어서 들어감
                
                ```python
                my_list.append([5, 6, 7])
                print(my_list)  #[1, 2, 3, 4, 5, 6, [5, 6, 7]]
                ```
                
    - .insert(i, x)
        
        ```python
        my_list = [1, 2, 3]
        my_list.insert(1, 5)
        
        print(my_list)  #[1, 5, 2, 3]
        ```
        
        - 지정한 리스트 인덱스 i 위치에 항목 x 삽입
            - 위치에 삽입하는 것이지 변경이 아님
            
- 리스트 값 삭제 메소드
    - .remove(x)
        
        ```python
        my_list = [1,2, 3, 2, 2, 2]
        my_list.remove(2)
        
        print(my_list) = [1, 3, 2, 2, 2]
        ```
        
        - 리스트에서 첫 번째로 일치하는 항목 삭제
            - 모든 요소를 삭제하는 것이 아닌 해당 요소를 처음 발견한 요소만 삭제
            - 그렇기에 계속 반복하다가 보면 예시의 2를 다 없을 수도 있음
    - .pop(i)
        
        ```python
        my_list = [1, 2, 3, 4, 5]
        item1 = my_list.pop()
        item2 = my_list.pop(0)
        
        print(item1)  #5
        print(item2)  #1
        print(my_list)  #[2, 3, 4]
        ```
        
        - i : index 선택 값
        - 리스트에서 지정한 인덱스의 항목을 제거하고 반환
            - 작성하지 않을 경우 마지막 항목을 제거
    - .clear()
        
        ```python
        my_list = [1, 2, 3]
        my_list.clear()
        
        print(my_list)  #[]
        ```
        
        - 리스트의 모든 항목을 삭제
            - 리스트 자체를 정리하는 것이 아니라 리스트 안 요소만 정리하는 것
            → 빈 리스트로 만드는 것
    - del 함수와의 차이점
        
        ```python
        a = [1, 2, 3]
        del a[1]
        print(a)   #[1, 3]
        ```
        
        - del 함수는 인덱스, 슬라이싱을 통해 요소 값 혹은 전체 제거 가능
        remove : 해당 요소 값 삭제 / pop : 해당 인덱스 값 반환 후 제거

- 리스트 탐색 메서드
    - .index(x) : 리스트에서 첫 번째로 일치하는 항목 x의 인덱스를 반환
        
        ```python
        a = [1, 2, 3]
        a.index(3)  #2
        ```
        
    - .count(x) : 리스트에서 항목 x의 개수 반환
        
        ```python
        a = [1, 2, 3, 1]
        a.count(1)   #2
        ```
        

- 리스트 정렬 메서드
    - .reverse()
        
        ```python
        my_list = [1, 3, 2, 8, 1, 9]
        my_list.reverse()
        
        print(my_list)  #[9, 1, 8, 2, 3, 1]
        print(my_list.reverse())  #None
        ```
        
        - 리스트의 순서를 역순으로 변경
            - 정렬 아님 (정렬 : 숫자 순서 맞춤)
        - 반환 값이 없음 → None 반환
    - .sort()
        
        ```python
        my_list = [3, 2, 100, 1]
        my_list.sort()
        
        print(my_list)  #[1, 2, 3, 100]
        
        #내림차순 정렬
        my_list.sort(reverse=True)
        print(my_list)  #[100, 3, 2, 1]
        ```
        
        - 원본 리스트를 오름차순으로 정렬 (기본 값)
            - 내림차순은 reverse = True 인 경우 가능
        - None 반환 → 원본 값 수정, 반환 값 없음

- 기타 다양한 리스트 메서드
    - https://docs.python.org/3.11/tutorial/datastructures.html#data-structures

# 

---

## 비시퀀스 데이터 구조

- 딕셔너리 (dictionary)
- 세트 (set)

---

### 딕셔너리 (Dictionary)

- 정의 : 키(Key)와 값(Value)을 짝지어 저장하는 자료 구조
    - 내부적으로 해시 테이블을 사용하여 키-값 쌍을 관리
    - 키를 통한 값의 삽입, 삭제, 검색이 데이터 크기와 관계없이 동일
        - 거대한 데이터에서 검색할 때 **매우 빠르게 진행** 가능
    - 키 (Key) : **hashable**한 **고유 값**
    - 값 (Value) : 중복이 가능하고 어떤 자료형도 저장 가능

- 메서드
    - .get(key[,default])
        - 키에 연결된 값을 반환하거나 키가 없으면 None 혹은 기본 값 반환
        - default : 선택 인자
        → 키가 없을 때 반환할 값(기본 값) 지정
        
        ```python
        person = {'name':'Alice', 'age':25}
        
        print(person.get('name'))  #Alice
        print(person.get('age'))  #25
        
        print(person.get('country'))  #None
        print(person.get('country', 'Unknown'))  #Unknown
        print(person['country'])  #KeyError : 'country'
        ```
        
    - .keys()
        - dict **키**를 모은 객체만 따로 반환
            
            ```python
            person = {'name':'Alice', 'age' : 25}
            person_keys = person.keys()  #dict_keys(['name', 'age'])
            person['country'] = 'KOREA'
            print(person_keys)
            ```
            
            - dict_keys([’name’, ‘age’])
                - 해당 dict의 키를 실시간으로 동기화하는 확인 창 (view) 같은 것
                
                ```python
                person = {'name':'Alice', 'age' : 25}
                print(person.keys())  #dict_keys(['name', 'age'])
                
                for key in person.keys():
                	print(key)    #name
                	              #age
                ```
                
    - .values()
        - dict **값**을 모은 객체 반환
            - .keys()와 비슷하지만 키 값과 value 값을 각각 뽑아내는 것
            
            ```python
            person = {'name':'Alice', 'age' : 25}
            print(person.values())  #dict_values(['Alice', 25])
            
            for item in person.values():
            	print(item)
            	
            """
            Alice
            25
            """
            ```
            
    - .items()
        - dict **키-값 쌍**을 모은 객체 반환
            
            ```python
            person = {'name':'Alice', 'age' : 25}
            print(person.items())  #dict_items([('name', 'Alice'), ('age', 25)])
            
            for key, value in person.items():
            	print(key, value)
            	
            """
            name Alice
            age 25
            """
            ```
            
    - .pop(key[,default])
        - 키를 제거하고 연결됐던 값을 반환 (없으면 에러나 default 반환)
            - 리스트에서도 있던 메서드 
            → 특징 : 반환 + 제거
            
            ```python
            person = {'name':'Alice', 'age' : 25}
            
            print(person.pop('age'))  #25
            print(person)  #{'name':'Alice'}
            print()  #None
            
            print(person.pop('country'))  #KeyError : 'country'
            print(person.pop('country', None))   #None
            ```
            
    - .clear()
        - 딕셔너리의 모든 키-값 쌍 제거
            - 리스트에서도 있던 메서드
            → 빈 dict가 되는 것
            
            ```python
            person = {'name':'Alice', 'age' : 25}
            person.clear()
            print(person)   #{}
            
            #clear와 초기화{}의 차이점 (리스트도 마찬가지)
            	#똑같은 딕셔너리 유지
            	D1 = {'name':'Alice', 'age' : 25}
            	D1.clear()
            	
            	#재할당_다른 딕셔너리가 된 것
            	D2 = {'name':'Alice', 'age' : 25}
            	D2 = {}
            ```
            
    - .setdefault(key[, default])
        - 키와 연결된 값을 반환
            
            **키가 없다면 default와 연결한 키를 dict에 추가하고 default 반환**
            
            - 키와 연결된 값을 반환하는 것은 .get()과 동일
            (하지만 .get()은 키가 없으면 default만 반환_추가 X)
            - 조건문을 줄일 수 있음 (→ 기능에 추가할 수 있는 게 있기 때문)
                - get + 추가 기능
            
            ```python
            person = {'name':'Alice', 'age' : 25}
            
            print(person.setdefault('country', 'KOREA'))  #KOREA
            print(person.setdefault('name', 'KOREA')) 
            print(person)  #{'name':'Alice', 'age' : 25, 'country':'KOREA'}
            ```
            
    - .update([other])
        - other가 제공하는 키-값 쌍으로 dict를 갱신하고 기존 키는 덮어씀
            - 키 : 나중에 입력한 값으로 저장 (→ 중복 안되기 때문)
                
                → 근본적으로 함수이기 때문에 **키 값에 문자열을 쓰지 않음**
                (즉, person.update(’age’=100, ‘address’=’SEOUL’) 라고 쓰지 않음)
                
            
            ```python
            person = {'name':'Alice', 'age' : 25}
            other_person = {'name':'Jane', 'country':'KOREA'}
            
            person.update(other_person)
            print(person)  #{'name':'Jane', 'age' : 25, 'country':'KOREA'}
            
            person.update(age=100, address='SEOUL')
            print(person)  #{'name':'Jane', 'age' : 100, 'country':'KOREA', 'address':'SEOUL'}}
            ```
            
    - [다양한 딕셔너리 메서드](https://docs.python.org/3.11/library/stdtypes.html#dict)

### 세트 (Set)

- 정의 : 고유한 항목들의 정렬되지 않은 **컬렉션**
    - 비시퀀스 자료형이기 때문에 중복 및 정렬 X
    - 내부적으로 **해시 테이블**을 사용하여 데이터 저장
        - dict와 유사
    - 항목의 **고유성**을 효율적으로 보장
    - 항목의 추가, 삭제, 존재 여부 확인(in 연산) : 데이터 크기에 상관 없이 **매우 빠름**
    - 합집합(Union),  교집합(Intersection), 차집합(Difference) 등 **수학적 집합 연산** 간편 수행 가능
- 메소드
    - .add(x)
        - 세트에 항목 x를 추가
            - .append 메소드와 비슷
        - 이미 x가 있다면 변화 없음
        - 해시 테이블에 의해서 실행할 때마다 값의 순서가 바뀜
        → 규칙성 X, **임의의 순서 (random 아님)**
        
        ```python
        my_set = {'a', 'b', 'c', 1, 2, 3}
        
        my_set.add(d)
        print(my_set)  # {1, 'b', 3, 2, 'c', 'd', 'a'}
        
        my_set.add(d)
        print(my_set)  # {1, 'b', 3, 2, 'c', 'd', 'a'}
        ```
        
    - .update(iterable)
        - 세트에 다른 iterable 요소 추가
            - dict 메소드에도 있음
        
        ```python
        my_set = {'a', 'b', 'c', 1, 2, 3}
        
        my_set.update([1, 4, 5])
        print(my_set)   #{'c', 2, 3, 1, 'b', 4, 5, 'a'}
        ```
        
    - .clear()
        - 세트의 모든 항목 제거
            - 빈 세트는 set( ) _ 중괄호 X
        
        ```python
        my_set = {'a', 'b', 'c', 1, 2, 3}
        
        my_set.clear()
        print(my_set)   #set()
        ```
        
    - .remove(x)
        - 세트에서 항목 x 제거
        - 항목 x가 없을 경우 KeyError
        
        ```python
        my_set = {'a', 'b', 'c', 1, 2, 3}
        
        my_set.remove(2)
        print(my_set)  #{'b', 1, 3, 'c', 'a'}
        
        my_set.remove(10)  #KeyError : 10
        ```
        
    - .pop()
        - 세트에서 임의의 요소를 제거하고 반환
            - **무작위(Random)이 아님
            →** “임의”라는 의미에서의 **무작위** (By ‘arbitrary’ the docs don’t mean ‘random’)
        
        ```python
        my_set = {'a', 'b', 'c', 1, 2, 3}
        
        element = my_set.pop()
        print(element)  #1
        print(my_set)  #{2, 3, 'b', 'a', 'c'}
        ```
        
    - .discard(x)
        - 세트 s에서 항목 x 제거
            - 기본 기능은 remove이지만 키가 없는 것을 지울 때 에러가 없음
            → 아무런 반환, 출력이 없음
            - pop 메소드도 임의의 요소를 반환하지만 discard는 반환 X
        
        ```python
        my_set = {'a', 'b', 'c', 1, 2, 3}
        
        my_set.discard(2)
        print(my_set)  #{1, 3, 'a', 'c', 'b'}
        
        my_set.discard(10)  # error 없음
        ```
        
    - 집합 메서드
        
        ![image.png](attachment:c28c3c04-5204-40e8-87c1-c64d819242dc:image.png)
        
        ```python
        set1 = {0, 1, 2, 3, 4}
        set2 = {1, 3, 5, 7, 9}
        set3 = {0, 1}
        
        print(set1.difference(set2))  #{0, 2, 4}
        print(set1.intersection(set2))  #{1, 3}
        print(set1.issubset(set2))  #False
        print(set3.issubset(set1))  #True
        print(set1.issuperset(set2))  #False
        print(set1.union(set2))  #{0, 1, 2, 3, 4, 5, 7, 9}
        ```
        

### 해시테이블

- 정의 : 키(Key)와 값(Value)을 짝지어 저장하는 자료구조
    - 리스트 : 순차 검색을 할 수 밖에 없음
    - 해시테이블 : 키 값을 통해 바로 값에 접근 가능(해시 함수 덕분)
- 원리
    - 키를 해시 함수를 통해 해시 값으로 변환
    - 변환된 해시 값을 인덱스로 삼아 데이터를 저장하거나 찾음
    - 이로 인해 검색, 삽입, 삭제를 매우 빠르게 수행 (길이에 상관 X)
    
    ![해시 함수에 따라 키를 넣으면 무조건 어떠한 해시 테이블 값이 나옴](attachment:58d95bcd-9cbe-45c4-afeb-405d393d3cf0:image.png)
    
    해시 함수에 따라 키를 넣으면 무조건 어떠한 해시 테이블 값이 나옴
    

- **해시 (Hash)**
    - 정의 : **임의의 크기**를 가진 데이터를 고정된 크기의 고유한 값으로 변환하는 것
        - **고유한 정수 :** 데이터를 식별하는 ‘지문’ 역할
        - 해시 값을 이용하여 해시 테이블에 데이터 저장
            
            → 변환을 수행하는 것이 해시 함수
            

- **해시 함수 (Hash Function)**
    - 정의 : 임의의 길이를 가진 데이터를 입력 받아 고정 길이 (정수)로 변환해 주는 함수
        - 해시 테이블을 구현할 때, 매우 빠른 검색 및 데이터 저장 위치 결정하기 위해 사용
        → ‘해시 알고리즘’ 이라고도 부름
    - 해시 테이블이 매우 빠른 이유
        - 해시 함수는 키(Key)를 입력 받아 데이터를 저장하거나 찾을 배열의 **‘정확한 인덱스’ 즉시 계산**
        - 마치 책의 제목(키)을 알면 색인(해시 함수)을 통해 페이지 번호(인덱스)를 바로 알아내고, 해당 페이지(배열 위치)로 **곧바로 이동**하여 내용을 찾는 것과 동일

- **set의 요소**와의 관계
    - 각 요소를 해시 함수로 변환해 나온 해시 값에 맞춰 해시 테이블 내부 버킷(bucket)에 위치시킴
    - 그래서 “순서”라기보다 “버킷 위치(인덱스)”가 요소의 위치를 결정
    - set은 순서를 보장하지 않음
    → 동일 프로세스에서 연속 실행 시 결과가 어느 정도 일정해 보이지만
    여전히 set은 순서가 없으므로 pop되는 순서는 예측 불가능함
    - 예시
        - 정수 (숫자) 값 : 숫자 자기 자신과 동일하거나 단순 계산으로 고정
            
            ![같은 정수는 항상 같은 해시 값을 가짐 → hash(1)은 여러 번 호출해도 동일한 결과](attachment:ac4dc73c-dc75-44a5-be88-f943b84c98a2:image.png)
            
            같은 정수는 항상 같은 해시 값을 가짐 → hash(1)은 여러 번 호출해도 동일한 결과
            
        - 문자열 : 해시 난수화(Hash Randomization)가 적용되어 실행마다 순서가 달라질 수 있음
            - 파이썬 프로세스가 새로 시작될 때마다 해시를 계산할 때 사용하는 난수 시드가 달라짐
            → 함수가 매번 바뀌는 것이 아닌, 해시 계산에 쓰이는 시드 값이 실행마다 달라지는 것
            ⇒ 동일한 데이터라도 매번 해시 값이 달라져 결과적으로 버킷 배치가 달라짐
            - 내부적으로 해시 테이블을 참조하기 때문에, 실행 때마다 다른 요소가 먼저 나올 수 있음
            → 내부 요소의 배치가 달라질 수 있음
            
            ![문자열 해시 : 난수 시드(seed)가 달라질 수 있음 (보안상 이유로 해시 난수화 도입)
            → 각 실행마다 달라질 수 있기에 ‘a’의 해시 값도 매번 바뀔 수 있음](attachment:2e32418d-39f4-431b-abf2-0d9a57731acb:image.png)
            
            문자열 해시 : 난수 시드(seed)가 달라질 수 있음 (보안상 이유로 해시 난수화 도입)
            → 각 실행마다 달라질 수 있기에 ‘a’의 해시 값도 매번 바뀔 수 있음
            
- **dict의 키**와의 관계
    - 키(key) → 해시 함수 → 해시 값 → 해시 테이블에 저장
    - “삽입 순서” **유지 보장**
        - 키를 추가한 순서대로 반복문 순회 시 나오게 됨
        - 즉, 사용자에게 보여지는 키 순서는 삽입 순서가 유지되도록 설계
        작성 순서 그대로가 나올 뿐

set의 요소 dict의 키와 해시 테이블의 관계

- set 의 pop()은 임의의 요소를 제거하고 반환함
    - 실행할 때마다 다른 요소를 얻는다는 의미에서의 무작위가 아니라 임의라는 의미에서의 무작위
        - 순서가 정해져 있지 않기 때문에 임의는 맞긴 하지만 버킷 배치 순서는 있기에 랜덤까지는 아님
- 내부적으로 해시 테이블(버킷)을 참조하기 때문에, 실행마다 다른 요소가 먼저 나올 수 있음
    - 해시 난수화로 인해 문자열 같은 해시 값이 실행마다 달라질 수 있고, 따라서 set 내부 요소의 배치가 달라질 수 있음
    - 정수는 해시 값이 항상 동일하기 때문에, 파이썬을 동일 프로세스에서 연속 실행할 때는 결과가 어느 정도 일정해 보이기도 하지만, 여전히 set은 순서가 없으므로 pop 되는 순서는 예측 불가능

hasable

- 대부분의 불변 타입은 해시 가능 (어차피 바뀌지 않기에)
- 가변형은 안됨 (키는 불변해야하는데 리스트로 쓰면 언제든 바뀔 수 있는 거→ 해시 함수에서 동일한 결과가 나오는게 약속인데 계속 바뀌면 안되는 거임) : 무결성이 깨짐
- 해시 테이블에 쓸 수 없는 키는 딕셔너리에서도 사용할 수 없음!
- 불변이면 무조건 hashable? 아님
    - hashable과 불변성의 관계
- 가변형 객체가 hashable하지 않은 이유
    - 값이 변경될 수 있으므로, 같은 객체라도 값이 바뀌면 해시 값도 달라질 수 있음
    - 해시 테이블에서는 동일키 → 동일 위치로 가정하고 빠른 검색을 수행하는데 이 가정이 깨짐
- 

EBNF : BNF를 확장한 표기법

![image.png](attachment:1ac86135-531b-48df-ad31-1c567d486756:image.png)

why? 이러한 표기법 사용

→ 서로 다른 프로그래밍 언어, 데이터 형식, 프로토콜 등의 문법을 통일하여 정의하기 위함

→ 문서화 할 때 서로의 표기를 이해할 수 있게 동일한 표기법 사용하는 

set dict 설계를 할 때 임의라는 것을 고려하지 않음 → 저장이 뭔가 난수화된 키 값을 가지고 저장을 하기 때문에 받아들이는 것이 임의로 생각되는 것 뿐이지 pop()도 임의로 나올 생각이 없음

임의인 것 같이 저장되는 이유는 알긴 알아야 함. 구현할 필요는 없지만 알긴 알아야 함

느낌표 차이만으로도 해시 값이 차이날 수 있음 (난수 seed 고정값으로 두고 해시 값을 구하는 것도)

hash의 충돌…? 버킷이라는 개념은 해시 함수를 사용해서 반환 받은 키들이 담기는 곳으로 키가 인덱스로 value와 쌍으로 잡힌다. 버킷은 유한함. 입력할 수 있는 값은 무한함. 그렇기에 무한하게 입력할 수 있기에 언젠가 해시의 충돌이 발생할 수 있음. 이러한 **충돌을 방지**할 수 있도록 해시 함수 만들어둠

서로 다른 두개의 데이터가 입력 되었음에도 불구하고 동일한 해시값으로 맵핑되는 상황은 유한한 버킷에 무한한 입력 때문에 발생할 수 있는 해시의 충돌임

(해시테이블 = 충돌을 방지하는 것을 우선시, 빠른 삽입을 우선시, 테이블이기 때문에 지금 우리는 그냥 리스트를 사용하기 때문에 이 리스트가 무한히 늘어날 수 있는 것처럼 보임 이게 괸장히 메모리가 많이 드는 작업 그래서 이게 컴퓨터의 메모리도 많이 잡아먹는 작업 해시 테이블을 사용할 때도 효율성 있게 사용해야 함→ 저장 공간의 효율성도 높이는 해시함수, 테이블까지도 고려해야함) → 충돌 방지 차원, 과정 중에서 테이블의 임의의 위치에 데이터 삽입하게 되었고 임의로 데이터가 반환되는 것으로 보여졌을 뿐이다.

해시 테이블이란? (충돌까지도 물어볼 수도 있음 → 좋은 해시 함수는 무엇인가에 대한 답: 다양한 입력 데이탁 있을 때 해시 값이 고르게 되어 있어서 충돌이 없게 HOW? 모름~)

## 

## 객체와 참조

→ 객체가 어느 것을 참조하는가? (객체 복사의 핵심) _ 변수 다룰 때 나옴

### **변수 할당**

- 정의 : 객체에 대한 참조를 생성하는 과정
    - 메모리 참조 방식 : 변수는 객체의 ‘메모리 주소’를 저장 → 여러 변수가 동일한 객체를 참조 가능
    - 변수 : 객체의 메모리 주소를 가르키는 Label 역할
    - ‘=’ 연산자를 사용하여 변수에 값을 할당
        - 할당 시 새로운 객체가 생성되거나 기존 객체에 대한 참조가 생성됨
            - 새로운 객체 생성 후 참조 : 객체를 메모리에 만들고, 변수가 그 객체를 가르키게 함
            - 기존 객체에 대한 참조 : 해당 객체에 대한 참조만 생성

### 메모리 주소 확인

- id() 함수 : 객체의 메모리 주소 확인 가능
- is 연산자 : 두 변수가 같은 객체를 참조하는지 확인 가능
    
    ```python
    x = [1, 2, 3]
    y = x          #가변 객체로 그대로 재할당하는 것
    z = [1, 2, 3]
    
    print(id(x))  #1682231207424
    print(id(y))  #1682231207424
    print(id(z))  #1682231224896
    
    print(x is y)   #True
    print(x is z)   #False   #x와 z는 단순히 값이 같을 뿐 다른 객체임
    ```
    

### **가변 객체 (Mutable)**

- 정의 : 생성 후 내용을 변경할 수 있는 객체
- 예시 : 리스트, 딕셔너리, 집합
- 특징
    - 그 값으로 할당하는 것
        
        ```python
        a = [1, 2, 3, 4]
        b = a 
        b[0] = 100
        
        print(a)  #[100, 2, 3, 4]
        print(b)  #[100, 2, 3, 4]
        print(a is b)  #True
        ```
        
- 메모리 관리 방식
    - 생성 후에도 그 내용을 수정할 수 있음
    - 객체의 내용이 변경되어도 같은 메모리 주소 유지
    - 이유
        - 성능 최적화 : 내용 수정이 빈번할 때, 새로운 객체를 생성하는 대신 기존 객체를 직접 수정 가능
        → 객체 생성 및 삭제에 드는 비용을 절감하여 성능 향상시킴
        - 메모리 효율 : 크기가 큰 데이터를 효율적으로 수정 가능

### **불변 객체 (Immutable)**

- 정의 : 생성 후 내용을 변경할 수 없는 객체
- 예시 : 정수, 실수, 문자열, 튜플
- 특징
    - 그 값이 보고 있는 메모리 주소만 변경
        
        ```python
        a = 20 
        b = a
        b = 10
        
        print(a)  #20
        print(b)  #10
        print(a is b)  #False
        ```
        
- 메모리 관리 방식
    - 생성 후 그 값을 변경할 수 없음
    - 새로운 값을 할당하면 새로운 객체가 생성되고, 변수는 새 객체를 참조하게 됨
    - 이유
        - 성능 최적화 : 변경이 불가능하므로, 여러 변수가 동일한 객체를 안전하게 공유 가능
        - 메모리 효율성 : 동일한 값을 가진 여러 변수가 같은 객체를 참조하여 메모리 사용을 최소화 가능

### 

---

## 복사

### 얕은 복사 (Shallow Copy)

- 정의 : 객체의 최상위 요소만 새로운 메모리에 복사하는 방법
    - 내부에 **중첩된 객체**가 있다면 그 객체의 **참조**만 복사 (해당 객체를 복사하는 것이 아님)
    - 원본 리스트와 동일한 내용의 새로운 리스트 만듦
    → 요소 자체 값이 아니라, 해당 객체들이 참조하는 주소를 참조하는 것 (방 주소 자체 복사X)
    - 함정 : ‘가변 객체’
        - 얕은 복사 후 중첩된 리스트나 딕셔너리 같은 가변 객체를 수정하면,
        원본 객체와 복사본 객체가 **함께 변경 
        →** 복사본의 중첩 객체가 여전히 **원본 객체의 중첩 객체를 참조**하기 때문
            (내부 객체의 주소가 같기 때문)
        - 다차원 리스트의 경우, 
        최상위 요소까지만 복사하기 때문에 그 안에 있는 객체는 다시 같은 주소를 바라보게 됨
        → 내부적으로는 중첩된 객체 주소가 같음
        (1차원 리스트의 경우, 얕은 복사로도 충분히 독립적인 복사본 만들 수 있음)
- 구현 방법
    - 리스트 슬라이싱
        
        ```python
        a = [1, 2, 3]
        b = a[:]        #리스트 슬라이싱 [:]
        
        print(a)  #[1, 2, 3]
        print(b)  #[1, 2, 3]
        ```
        
    - copy( ) 메서드
        
        ```python
        a = [1, 2, 3]
        b = a.copy()
        
        print(a)  #[1, 2, 3]
        print(b)  #[1, 2, 3]
        ```
        
    - list( ) 함수
        
        ```python
        a = [1, 2, 3]
        d = list(a)   #list()함수 활용 얕은 복사본 생성
        
        #원본 리스트 a의 첫 번째 요소 변경
        a[0] = 100
        
        print(a) = [100, 2, 3]
        print(d) = [1, 2, 3]
        ```
        

### 깊은 복사 (Deep Copy)

- 정의 : 객체의 모든 수준의 요소를 새로운 메모리에 복사하는 방법
    - 모든 레벨의 요소를 새로운 메모리에 복사
    - 최상위를 포함하여 중첩된 객체까지 모두 새로운 객체로 생성
    → 원본 객체와 복사본의 **완전한 독립성 보장**
        (복사본의 어떤 수준에 있는 중첩된 내용을 변경하더라도 **원본 객체에 절대 영향 X**)
- 구현 방법
    - deepcopy( ) 함수 사용 _  copy 모듈 제공
        
        ```python
        import copy
        new_object = copy.deepcopy(original_object)
        
        import copy
        a = [1, 2, [3, 4, 5]]
        b = copy.deepcopy(a)
        
        b[2][1] = 100
        
        print(a)  #[1, 2, [3, 4, 5]]
        print(b)  #[1, 2, [3, 100, 5]]
        print(a[2] is b[2])  #False
        
        #중첩된 객체에서의 깊은 복사
        original = {'a':[1, 2, 3], 'b':{'c':4, 'd':[5, 6]}}
        copied = copy.deepcopy(original)
        
        copied['a'][1] = 100
        copied['b']['d'][0] = 500
        
        print(original)  #{'a':[1, 2, 3], 'b':{'c':4, 'd':[5, 6]}}
        print(copied)   #{'a':[1, 100, 3], 'b':{'c':4, 'd':[500, 6]}}
        print(original['b'] is copied['b'])  #False
        ```
        

### 

## List Comprehension

- 정의 : 간결하고 효율적인 리스트 생성 방법
    - 한 줄로 축약해서 표현 가능_pythonic한 코드
- 구조
    
    **표현식 for 변수 in 순회 가능한 객체 [if 조건]**
    
    - 빈 리스트를 만드는 것이 아닌 한 줄로 바로 할당 가능
    - 생성 방법은 다양함 : for문, while문, if문 등
    
    ```python
    # 사용 전
    
    numbers = [1, 2, 3, 4, 5]
    squared_numbers = []
    for num in numbers:
    	squared_numbers.append(num**2)
    print(squared_numbers)   #[1, 4, 9, 16, 25]
    
    # 사용 후 
    
    numbers = [1, 2, 3, 4, 5]
    
    squared_numbers = [num**2 for num in numbers]
    print(squared_numbers)   #[1, 4, 9, 16, 25]
    ```
    
    ```python
    # 2차원 배열 생성 (인접 행렬 생성)
    
    data1 = [[0] * (5) for _ in range(5)]
    
    data2 = [[0 for _ in range(5)] for _ in range(5)]
    
    #결과
    [[0, 0, 0, 0, 0], 
    [0, 0, 0, 0, 0]
    [0, 0, 0, 0, 0]
    [0, 0, 0, 0, 0]
    [0, 0, 0, 0, 0]]
    ```
    
- 생성 방법은 다양함 : for문, while문, if문 등
- 성능 비교
    - List Comprehension : 대부분 우수한 성능 보임
    - map
        - 특정 상황 (int, str 등 내장 함수와 함께 사용할 때)에 가장 빠름
        - 사용자가 직접 만든 함수나 lambda와 함께 사용할 때에는 List Comprehension 과 비슷하거나 약간 느림
    - for loop
        - 일반적으로 가장 느림
            - 하지만 파이썬 버전이 올라가면서 개선됨 → 사실 이 셋의 차이는 마이크로 초 차이임
    
    ⇒ 일반적인 상황에서는 List Comprehension → map → for loop 순으로 빠름
