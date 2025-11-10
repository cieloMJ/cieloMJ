# Querying data

데이터베이스에 저장된 정보 중 필요한 데이터를 **검색**하고 **추출**하는 과정

## Select

```sql
SELECT 
	select_list
FROM
	table_name;
```

**개념**

- 테이블에서 필드의 데이터를 조회 및 반환
- 키워드
    - **SELECT** : 데이터를 선택하려는 필드를 **하나 이상** 지정
    - **FROM** : 데이터를 선택하려는 테이블의 이름을 지정
- 실행 순서
: 테이블에서(FROM) 조회하여(SELECT) 정렬(ORDER BY)

**활용 방법**

- 테이블의 모든 데이터 조회 (전체 선택)
    
    ```sql
    SELECT * FROM table_name;
    ```
    
- 특정 필드의 모든 데이터 조회
    
    ```sql
    SELECT 
    	필드명 (여러 개 작성 가능)
    FROM 
    	table_name;
    ```
    
    - 모든 데이터를 조회하되, 필드 명이 아닌 다른 이름으로 출력
        
        ```sql
        SELECT 
        	필드명 AS '원하는 이름'
        FROM
        	table_name;
        ```
        
        ```sql
        SELECT
        	Name,
        	Milliseconds / 60000 AS '재생 시간(분)'
        FROM 
        	table_name;
        ```
        
    

# Sorting data

## ORDER BY

```sql
SELECT
	select_list
FROM
	table_name
ORDER BY
	column 1 [ASC|DESC],
	column 2 [ASC|DESC], 
	...;
```

**개념**

- 조회 결과의 레코드 정렬
    - FROM clause 뒤에 위치
- 하나 이상의 컬럼을 기준으로 결과를 차순 정렬
    - 오름차순(기본 값) : ASC
    - 내림차순 : DESC

**활용 방법**

- 필드의 모든 데이터 오름차순, 내림차순으로 조회
    
    ```sql
    SELECT 
    	Country, City
    FROM
    	customers
    ORDER BY
    	Country DESC, City;
    ```
    
- NULL 값이 존재하는 경우
    
    ```sql
    SELECT 
    	ReportsTo
    FROM 
    	employees
    ORDER BY
    	ReportsTo;		
    
    ```
    
    - 오름차순 정렬 시 결과에 NULL이 먼저 출력됨

# Filtering data

**개념**

- 관련 키워드
    - **Clause (절)**
        - SQL 문장에서 특정 기능을 수행하도록 하는 지정하는 문장 구성 요소
        - Keywords
            - DISTINCT
            - WHERE
            - LIMIT
    - **Operator**
        - SQL에서 조건을 비교하거나 데이터를 선택하기 위해 사용하는 명령 기호 또는 키워드
        - Keywords
            - BETWEEN
            - IN
            - LIKE
            - Comparison
            - Logical

## DISTINCT

```sql
SELECT DISTINCT
	select_list
FROM
	table_name;
```

**개념**

- 조회 결과에서 중복된 레코드 제거
    - SELECT 키워드 바로 뒤에 작성해야 함
    - SELECT DISTINCT 키워드 다음에 고유한 값을 선택하려는 **하나 이상**의 필드 지정
- 예시

```sql
SELECT 
	Country 
FROM 
	customers
ORDER BY
	County
```

```sql
SELECT DISTINCT
	Country 
FROM 
	customers
ORDER BY
	County
```

customers 테이블에서 Country 필드의 데이터를 오름차순 조회

- 기존에는 단순 오름차순 정리로 중복 값들이 발생
- DISTINCT의 사용으로 중복 없이 조회 가능해짐

## WHERE

```sql
SELECT
	select_list
FROM 
	table_name
WHERE
	search_condition;	
```

**개념**

- 조회 시 특정 검색 조건 지정
    - 파이썬의 IF문 역할
    - FROM clause 뒤에 위치
    - search_condition은 비교연산자 및 논리연산자(AND, OR, NOT 등)를 사용하는 구문 작성

**활용 방법**

- 특정 필드 값이 ‘Prague’인 데이터 조회

```sql
SELECT
	LastName, FirstName, City
FROM 
	customers
WHERE
	City = 'Prague';
```

- 특정 필드 값이 NULL이고 USA가 아닌 데이터 조회

```sql
SELECT
	LastName, FirstName, Company, Country
FROM
	customers
WHERE
	Company IS NULL
	AND County != 'USA';
```

- 범위 지정 조회 (오름차순 정리)

```sql
SELECT 
	Name, Bytes
FROM
	tracks
WHERE
	Bytes BETWEEN 10000 AND 500000;
ORDER BY
	Bytes
	
-- WHERE
--	Bytes >= 10000
--	AND Bytes <= 500000
```

- 특정 필드 값이 Canada, Germany, France 중 일치하는 것이 있는 경우

```sql
SELECT
	LastName, FirstName, Country
FROM
	customers
WHERE
	Country IN ('Canada', 'Germany', 'France');

-- WHERE
-- 	Country = 'Canada'
-- 	OR Country = 'Germany'
-- 	Or Country = 'France';
```

- 특정 조건과 일치하는 경우

```sql
SELECT
	LastName, FirstName
FROM
	customers
WHERE
	LastName LIKE '%son'
	FirstName LIKE '___a';
```

## Operators

### Comparison Operators

**비교 연산자**

- 예시
    - =, ≥, ≤, ≠
    - IS, LIKE, IN
        - IN Operator : 값이 특정 목록 안에 있는지 확인
        - LIKE Operator
            - 값이 특정 패턴에 일치하는지 확인
            - Wildcard와 함께 사용
                - **Wildcard Characters**
                    - ‘%’ : **0개 이상의 문자열**과 일치하는 지 확인
                    - ‘_’ : **단일 문자**와 일치하는 지 확인
    - BETWEEN … AND …

### Logical Operators

**논리 연산자**

- 예시
    - AND (&&)
    - OR (||)
    - NOT (!)

## LIMIT

```sql
SELECT
	select_list
FROM 
	table_name
LIMIT [offset,] row_count;
```

**개념**

- 조회하는 레코드 수 제한
    - 하나 또는 두 개의 인자 사용
        - 0 또는 양의 정수
    - row_count : 조회하는 최대 레코드 수 지정
    - offset : 인덱스 같은 역할 ( 선택사항 )

**활용 방법**

- 내림차순으로 7개만 조회

```sql
SELECT 
	TrackID, Name, Bytes
FROM 
	tracks
ORDER BY Bytes DESC
LIMIT 7;
```

- offset 활용, 특정 부분 데이터만 조회

```sql
SELECT 
	TrackID, Name, Bytes
FROM 
	tracks
ORDER BY Bytes DESC
LIMIT 3, 4;

-- LIMIT 4 OFFSET 3;
```

# Grouping data

## GROUP BY

```sql
SELECT
	c1, c2, ..., cn, aggregate_function(ci)
FROM
	table_name
GROUP BY
	c1, c2, ..., cn;
```

**개념**

- 레코드를 그룹화하여 요약본 생성
    - FROM 및 WHERE 절 뒤에 배치
    - GROUP BY 절 뒤에 그룹화 할 필드 목록 작성
- 집계 함수와 함께 사용
    - Aggregation Functions (집계 함수)
        
        : 값에 대한 계산을 수행하고 단일한 값을 반환하는 함수
        
        - 예시 : SUM, AVG, MAX, MIN, COUNT
- DISTINCT와의 비교
    - 공통점 : 중복 제거
    - 차이점 : GROUP BY는 정렬까지 진행

**활용 예시**

- 그룹화

```sql
SELECT 
	Country
FROM 
	customers
GROUP BY
	Country;
```

- 그룹 별로 묶은 총 수 반환

```sql
SELECT
	Country, COUNT(*)
FROM 
	customers
GROUP BY
	Country;
```

- 평균 값을 내림차순 조회

```
SELECT 
	Composer,
	AVG(Bytes)
	-- AVG(Bytes) AS RealName
FROM
	tracks
GROUP BY
	Composer
ORDER BY
	AVG(Bytes) DESC;
	-- RealName DESC;
```

## HAVING

**개념**

- 집계 항목에 대한 세부 조건을 지정
    - 그룹화된 것에 대해 세부 조건을 지정할 때 사용
- 주로 GROUP BY와 함께 사용됨
    - GROUP BY가 없다면 WHERE처럼 동작
        - WHERE 과의 비교
          - WHERE 절
            - 개별 행에 대한 조건을 지정하여 데이터를 필터링하는 데 사용
            - FROM과 JOIN 등의 단계 이후, GROUP BY 이전에 적용
            - 특정 조건을 만족하는 행만을 대상으로 집계나 정렬 등의 작업을 수행할 때 사용
          - HAVING 절
            - GROUP BY에 의해 그룹화된 결과에 대해 조건을 지정하여 그룹을 필터링하는 데 사용
            - HAVING은 그룹핑 및 집계 함수가 적용된 이후에 조건이 평가
            - 그룹별 집계 결과에 조건을 걸어 특정 그룹만을 선택할 때 사용
