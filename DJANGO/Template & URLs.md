# emplate System

## Django Template System

**개념**

- 파이썬 데이터(context)를 HTML 문서(Template)와 결합하여, 로직과 표현을 분리한 채 동적인 웹페이지를 생성하는 도구
    - 예시 : 뉴스 사이트
        - 동일한 틀(Template) 공유_ 헤더, 폰트, 광고 위치 등
        - 데이터(context), 즉 각 페이지에 들어가는 기사 제목 등은 모두 다름
- 목적
    - ‘페이지 틀’에 ‘데이터’를 동적으로 **결합**하여 수 많은 페이지를 효율적으로 만들어 내기 위함

**실습**

- 변수 값에 따른 HTML 콘텐츠 변경
    - render의 인자 3번째 항목 사용

```python
# views.py

def index(request):
	context = { 'name': 'Jane', }
	return render(request, 'articles/index.html', context)
```

```html
# index.html

<body>
	<h1> Hello, {{ name }} </h1>
	
# **Hello, Jane**
```

## Django Template Language

**개념**

- Template에서 조건, 반복, 변수 등의 프로그래밍적 기능을 제공하는 시스템

### **DTL Syntax**

**Variable** 

- Django Template에서의 변수
    - render 함수의 세 번째 인자
- 딕셔너리 (Dict) 타입
    - key에 해당하는 문자열 = template에서 사용 가능한 변수명
    - dot(’.’) 사용 : 변수 속성에 접근 가능

```python
context = {
	'variable_1' : 'value_1',
	'variable_2' : {
		'attribute' : 'value_2',
	}
}
```

```html
{{ variable_1 }}
{{ variable_2.attribute }}
```

**Filters**

- 표시할 변수 수정 시 사용
    - 변수 | 필터
- chained(연결)이 가능하며 일부 필터는 인자를 받기도 함
- 약 60개의 built-in template filters 존재
    - 모두 외울 필요는 없음

```html
{{ variable | filter }}
{{ name|truncatewords:30 }}
```

**Tags**

- 반복 또는 논리 수행 → 제어 흐름 만듦
    - {% tag %}
    - Template 상에서 조건문 작성 가능
        - 하지만 python과 변수, 문법이 다름
        - 화면에 출력 X
- 일부 태그는 시작, 종료 태그 필요
    - 영역이 필요하기 때문
- 약 24개의 built-in template tags 존재
- 예시 1
    - if, else, endif 태그

```python
context = {
	'login': False,
}
```

```html
{% if login %}
	<h1>Hello, User</h1>
{% else %}
	<h1>Please, login.</h1>
{% endif %}
```

```html
<h1>Please, login</h1>
```

- 예시 2
    - for 태그

```python
context = {
	'num' : [1, 2, 3],
}
```

```html
<ul>
	{% for num in nums %}
		<li>{{ num }}</li>
	{% endfor %}
</ul>
```

```html
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
</ul>
```

→  bootstrap card 반복 사용 가능해짐

**Comments**

- 주석 처리
- 종류
    - inline
        - 잘 사용하지 않음
            
            ```html
            <h1> Hello, {# name #} </h1>
            ```
            
    - multiline
        - {% 태그 사용
            
            ```html
            {% comment %}
            ...
            {% endcomment %}
            ```
            
    - ‘/’ : 기존 주석 처리 단축키


```python
# urls.py

urlpatterns = [
	path('admin/', admin.site.urls,
	path('articles/', views.index),
	path('dinner/', views.dinner),
]
```

```python
# views.py

def dinner(request):
	foods = [
		'국밥', 
		'국수', 
		'카레', 
		'탕수육',
	]
	picked = random.choice(foods)
	context = {
		'foods' : foods,
		'picked' : picked,
	}
	return render(request, 'articles/dinner.html', context)
```

```html
<!-- articles/dinner.html -->
<p> {{ picked }} 메뉴는 {{ picked|length }} 글자입니다.</p>

<h2> 메뉴판 </h2>
<ul>
	{% for food in foods %}
	 <li> {{food}} <li>
	{% endfor %}
</ul>

{% if foods|length == 0 %}
	<p> 메뉴가 소진되었습니다 </p>
{% else %}
	<p> 아직 메뉴가 남았습니다 </p>
{% endif %}
```

→ {{ picked|length }} 외에도 

views.py에서 

context = { 이  안에 정의해도 됨}

# Template 상속

**상속**

- 사용 방법 : Class, OOP
- 부모 클래스가 있으면 이를 자식 클래스에 재정의할 필요가 없음
    
    → 재사용성, 유지 보수 용이
    

**기존 템플릿 구조의 한계**

: 모든 템플릿에 Bootstrap 적용하려면 모든 템플릿에 CDN 작성해야 함

또한, 하다 보면 유사 구조가 반복되는 경우가 있음

- 예시 : 뉴스 페이지

## 템플릿 상속

Template inheritance

- 공통 틀 (Base Template) 만들어두고 그 안에서 내용(Content)만 변경
→ 부모의 역할을 할 수 있는 무언가 필요함
    - 페이지의 공통 요소 포함
        - 상위 template : base.html
            - skeleton 역할을 함
            - 모든 템플릿이 공유했으면 하는 공통 요소 작성
            - 파일 명이 반드시 base일 필요는 없음
    - 하위 템플릿이 재 정의 할 수 있는 공간 정의
        - extends 태그 : 상속받을 템플릿 결정
        - block 태그 활용
            
            → 이름으로 작성된 block 태그의 내용 대체 
            
    
    → 여러 템플릿이 공통 요소를 공유할 수 있게 해주는 기능
    

## 상속 관련 DTL 태그

- extends
    
    ```html
    {% extends 'articles/base.html' %}
    ```
    
    - 자식 (하위) 템플릿이 부모 템플릿을 확장한다는 것을 알림
    - 반드시 자식 템플릿 최상단에 작성되어야 함
    - 2개 이상 사용 불가
- block
    
    ```html
    {% block 'content' %} {% endblock 'content' %}
    ```
    
    - 하위 템플릿에서 재정의 할 수 있는 블록 정의
        - 상위 템플릿에서 작성
        - 하위 템플릿이 작성할 수 있는 공간 지정

# 요청과 응답

## HTML form

- 사용자와 서버 간의 상호 작용
    - 데이터를 보내고 가져오기
    - HTML Form Element
        - 사용자로부터 할당된 데이터를 서버로 전송하는 HTML 요소
        - 웹에서 사용자 정보를 입력하는 여러 방식 (text, password, checkbox 등) 제공

- HTTP 요청을 서버에 보내는 가장 편리한 방법
    - Client - Server 구조
        - 인터넷에 연결된 서로 다른 두 컴퓨터가 데이터를 주고 받는 웹의 동작 방식 중 하나
- 예시 : 로그인 template
```html
<form action="#" method="GET">
	<div>
		<label for="name"> 아이디 : </label>
		<input type="text" name="name" id="name">
	</div>
	<div>
		<label for="password"> 패스워드 : </label>
		<input type="password" name="password" id="password">
	</div>
	<input type="submit" value="로그인">
</form>
```
