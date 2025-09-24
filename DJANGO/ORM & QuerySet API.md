# ORM

**Object-Relational-Mapping**

**개념**

- 객체 지향 프로그래밍 언어의 객체(Object)와 데이터베이스의 데이터를 매핑(Mapping)하는 기술
    - SQL Query를 직접 작성하지 않고도 데이터베이스 조작 가능
- Python 클래스로 DB 테이블을 1:1로 매핑하는 것
    
    → 클래스의 인스턴스는 DB의 한 행(row)에 해당
    
- 필요성
    - Django와 DB의 언어 차이
        
        ![image.png](attachment:c7b69697-afef-4ec8-aba1-50686823a902:image.png)
        
        ⇒ ORM : Django와 DB 사이에서 언어 번역자 역할 수행
        
        - Django에 내장되어 있음
        - 데이터베이스 구조를 잘 몰라도 파이썬 코드로 쉽게 데이터 다룰 수 있음
        - 코드 작성 시간을 줄이고, 실수를 줄이는데 도움

# QuerySet API

**개념**

- ORM에게 명령어를 내리기 위한 문법
- ORM 기능을 개발자가 Python 코드 안에서 객체 지향적이고 직관적인 방식으로 데이터베이스를 조작할 수 있도록 제공하는 **인터페이스** 도구
- 데이터베이스의 복잡한 SQL 쿼리문을, 직관적인 Python 코드로 다룰 수 있게 해주는 강력한 번역기
    - SQL을 직접 작성하지 않고도, 메서드를 사용하여 원하는 데이터를 쉽게 생성, 조회, 수정, 삭제 가능
- Django ORM의 핵심 기능
    - 코드의 가독성을 높이고, 개발 생산성을 극대화 가능

### **구문 기본 구조**

**동작 방식**

![ORM과 QuerySet API 동작 방식](attachment:fc75d2f4-9b03-4ddc-a955-9ec5bcf66b06:image.png)

ORM과 QuerySet API 동작 방식

**예시**

![image.png](attachment:c8eecabf-41f0-45fc-a584-0989ba410a5f:image.png)

```python
# 게시글 전체 조회 (조회문)

Article.objects.all()
```

- Article
    - Model class
    - 역할 : 데이터베이스 테이블에 대한 Python 클래스 표현
        - articles_article 테이블의 스키마(필드, 데이터 타입 등) 정의
        - Django ORM이 DB와 상호 작용 시 사용하는 기본적인 구조체

- .objects
    - Manager
    - 역할 : 데이터베이스 조회(Query) 작업을 위한 기본 인터페이스
        - Model class가 데이터베이스 쿼리 작업을 수행할 수 있도록 하는 진입점
        - Django가 자동으로 추가 → 이를 통해 쿼리 메서드 호출

- .all()
    - QuerySet API 메서드
    - 역할 : 특정 데이터베이스 작업을 수행하는 명령
        - 매니저를 통해 호출되는 메서드
        - 해당 모델과 연결된 테이블의 모든 레코드(rows)를 조회하라는 SQL 쿼리를 생성하고 실행
        → 직접적으로 수행하는 역할

### Query

**개념**

- 데이터베이스에 특정한 데이터를 보여 달라는 요청
- “쿼리문을 작성 or 보냄”
    - 원하는 **데이터**를 얻기 위해 데이터베이스에 요청을 보낼 **코드** 작성
- Django에서 Query 처리되는 과정
    1. 파이썬 코드 → ORM
        - 개발자의  QuerySet API를 ORM으로 전달
    2. ORM → SQL 변환
        - ORM이 이를 DB용 SQL 쿼리로 변환, 데이터베이스에 전달
    3. DB 응답 → ORM
        - DB가 SQL 쿼리 처리 및 결과 데이터를 ORM에 반환
    4. ORM → QuerySet 변환
        - ORM이 DB 결과를 QuerySet 형태로 변환하여 전달

### QuerySet

개념

- 데이터베이스에서 전달 받은 객체 목록 (데이터 모음)
- 순회 가능한 데이터로 1개 이상 데이터를 불러와 사용 가능
    - Django ORM을 통해 만들어진 자료형
        
        → Django에서만 볼 수 있는 특별한 자료형
        
    - 순회 가능하기에 for문으로 반복 처리 가능해짐
- DB가 단일 객체를 반환하는 경우 Model Class의  인스턴스로 반환됨

## CRUD

**개념**

- 가장 기본적인 소프트웨어의 디자인 흐름
    - QuerySet 조작한다는 것은 CRUD를 하는 것으로 생각해도 됨
- 대부분의 소프트웨어가 가지는 기본적인 데이터 처리 기능을 묶어 이르는 말
    - Create : 새로운 데이터를 **생성** (저장)
    - Read : 기존 데이터를 **조회**
    - Update : 기존 데이터를 **수정** (갱신)
    - Delete : 기존 데이터를 **삭제**
- QuerySet API를 통해, 복잡한 SQL문 없이 Python 코드로 CRUD 작업을 직관적으로 수행 가능

### Create

**데이터 객체를 만드는 (생성하는) 방법**

(가정 : 게시글 작성 로직)

1. 빈 객체 생성 후 값 할당 및 저장

```bash
# 특정 테이블에 새로운 행을 추가하여 데이터 추가
# Article(class)로부터 article(instance) 생성
>>> article = Article()
>>> article
<Article: Article object (None)>

# 인스턴스 변수에 값 할당
>>> article.title = 'first'
>>> article.content = 'django!'

# save 하지 않으면 DB에 값 저장 안됨
>>> article
<Article: Article object (None)>

>>> Article.objects.all()
<QuerySet []>
```

![image.png](attachment:9f325d26-d97e-4bad-aeed-0b3e4505a098:image.png)

```bash
# save를 호출하고 저장된 것을 확인
>>> article.save()
>>> article
<Article: Article object (1)>

>>> article.id
1

>>> article.pk
1

>>> Article.objects.all()
<QuerySet [Article: <Article object (1)>]>
```

```bash
# 인스턴스 article 활용하여 인스턴스 변수 활용하기
>>> article.title
'first'

>>> article.content
'django!'

>>> article.created_at
datetime.datetime(2023, 6, 30, 6, 55, 42, 322526, tzinfo=datetime.timezone.utc)
```

1. 초기 값과 함께 객체 생성 및 저장

```bash
# 아직 저장되지 않음
>>> article = Article(title='second', content='django!')
>>> article
<Article: Article object (None)>

# save 메서드를 호출해야 저장됨
>>> article.save()

>>> article
<Article: Article object (2)>
>>> Article.objects.all()
<QuerySet [<Article: Article object (1)>, <Article: Article object (2)>]>
```

```bash
>>> article.pk
2

>>> article.title
'second'

>>> article.content
'django!'
```

![image.png](attachment:6eb7be1f-6cef-4d9b-be98-aca60adc3c6a:image.png)

1. create() 메서드로 한 번에 생성 및 저장

```bash
# 바로 저장 이후 바로 생성된 데이터가 반환됨

>>> Article.objects.create(title='third', content='django!')
<Article: Article object(3)>
```

![반복이 가능해지고, 그 반복을 하면서 게시물을 튀어나오게 하는 등 처리 가능해짐 (for)](attachment:3407373e-78e2-4a9a-a50d-6dfe95c55aab:image.png)

반복이 가능해지고, 그 반복을 하면서 게시물을 튀어나오게 하는 등 처리 가능해짐 (for)

### Read

- 대표적인 조회 메서드
    - QuerySet 반환 메서드
        - all()
        - filter()
    - QuerySet을 반환하지 않는 메서드
        - get()

**all( )**

- 전체 데이터 조회
    - 조건을 걸 수 없음
- 1개의 QuerySet 반환

```python
>>> Article.objects.all()
<QuerySet [<Article: Article object (1)>, <Article: Article object (2)>, <Article: Article object (1)>]>
```

**filter( )**

- 주어진 매개변수와 일치하는 객체를 포함하는 QuerySet 반환
    - 매개변수로 조건 걸 수 있음
        - 키워드 인자로 작성
        
        ```python
        Model.objects.filter(필드이름=값)
        ```
        

        
    - 조건을 만족하지 못해도 결과는 QuerySet으로 나옴
    

**get( )** 

- 주어진 매개 변수와 일치하는 객체 반환

- 특징
    - 예외 발생시킴 (오류 발생)
        - 값이 없을 경우 : DoesNotExist
        - 여러 개의 값이 있는 경우 : MultipleObjectsReturned
    
    ⇒ 명확한 목적이 결정되고, Primary Key와 같이 **식별자를 사용**하고 **고유성을 보장**하는 조회에서 사용
    
    - 주어진 조건을 부합하는 하나의 객체 반환
    

### Update

- 데이터 수정 방법
    1. 수정할 인스턴스 우선 조회
        
        ```python
        >>> article = Article.objects.get(pk=1)
        ```
        
    2. 인스턴스 변수 변경
        
        ```python
        >>> article.title = 'byebye'
        ```
        
    3. 저장
        
        ```python
        >>> article.save()
        ```
        

### Delete

- 데이터 삭제 방법
    1. 삭제할 인스턴스 우선 조회
        
        ```python
        >>> article = Article.objects.get(pk=1)
        ```
        
    2. delete 메서드 호출
        - 삭제된 객체 반환
        
        ```python
        >>> article.delete()
        (1, {'articles.Article': 1})
        ```
        
    3. 삭제한 데이터는 더 이상 조회 불가
        
        ```python
        >>> Article.objects.get(pk=1)
        DoesNotExist: Article matching query does not exist.
        ```
        

- 삭제 이후 게시글을 추가한다면?
    
    : 삭제된 id 숫자가 아닌 현재 있는 숫자 다음의 숫자(4)로 기록
    

    
    - why? django는 기본적으로 지워진 pk를 재활용하지 않음
        - 1로 생성하게 된다면 creat_at, updated_at의 날짜가 그 뒤의 값보다 더 최근이기 때문에 나중에 정렬할 때 문제가 생길 수 있음
        - 그리고 잘못 삭제한 경우 백업하거나 (유료로) 롤백해주는 경우도 있음
            - 아니면 라이브러리에서 찾으면 찾을 수도 있음
            - 그리고 기본값이 아니라 강제로 id 숫자를 지정해줄 수도 있긴 함 하지만 권장하진 x

Read

1. 전체 게시글 조회



# ORM with view

View 함수에서 QuerySet API 활용



- 웹페이지에 보여줄 데이터를 DB에서 가져올 때 사용함
- 데이터를 저장, 수정할 때 사용
- 사용자가 입력한 새로운 데이터를 DB에 저장할 때 사용
- 2가지의 READ (조회)
    1. 전체 게시글 조회
        - 요청 정의
            
       
```python
# crud(Django 프로젝트 이름)/urls.py
from django.urls import path, include

urlpatterns = [
	path('admin/', admin.site.urls),
	path('articles/', include('articles.urls')),
]
```

```python
# articles/urls.py
from django.urls import path
from . import views

urlpatterns = [
	path('', views.index, name='index'),
]
```

```python
# articles/views.py

form .models import Article

def index(request):
	articles = Article.objects.all()
	context = {
		'articles':articles,
	}
return render(request, 'articles/index.html', context)
```

```html
<!-- article/index.html -->

<h1>Articles</h1>
<hr>

{% for article in articles %}
	<p>글 번호: {{ article.pk }}</p>
	<p>글 제목: {{ article.title }}</p>
	<p>글 내용: {{ article.content }}</p>
	<hr>

{% endfor %}
```

1. 단일 게시글 조회

# 참고

ORM, QuerySet API를 사용하는 이유

- **생산성** 때문
    - 데이터 베이스 추상화
        
        : 개발자는 특정 DB 시스템에 종속되지 않고 일관된 방식으로 데이터 다룰 수 있음
        
    - 생산성 향상
        
        : 복잡한 SQL 쿼리를 직접 작성하는 대신 python 코드로 데이터베이스 작업 수행 가능
        
    - 객체 지향적 접근
        
        : 데이터베이스 테이블을 Python 객체로 다룰 수 있어 객체 지향 프로그래밍의 이적 활용 가능
