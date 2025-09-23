**Web Application**

- Web application (web service) 개발
    - 인터넷을 통해 사용자에게 제공되는 소프트웨어 프로그램을 구축하는 과정
    - 다양한 device에서 웹 브라우저를 통해 접근하고 사용 가능
    - web service : 인터넷을 통해 접할 수 있고 이를 통해 제공되는 서비스
 
### **클라이언트 - 서버 구조**

**웹의 동작 방식**
- **Client** : 서비스를 요청하는 주체
    
    → 사용자의 웹 브라우저, 모바일 앱
    
- Server : 클라이언트의 요청에 응답하는 주체
→ 웹 서버, 데이터베이스 서버

⇒ 일반적인 웹 서비스: 클라이언트가 페이지를 요청하는 경우, 서버가 응답해줌

- **개발자 구분**
    
    ### Frontend
    
    프론트엔드
    
    - 사용자 인터페이스(UI)를 구성하고, 사용자가 애플리케이션과 상호 작용할 수 있도록 함
        - HTML, CSS, JavaScript를 이용해 UI 구성
    - 사용 예시
        
        : HTML, CSS, JavaScript, 프론트엔드 프레임워크(Vue.js 등) 
        
    
    ### Backend
    
    백엔드
    
    - 서버 측에서 동작하며, 클라이언트의 요청에 대한 처리와 데이터베이스와의 상호작용 등을 담당
        - 클라이언트의 요청에 대한 처리와 데이터베이스 상호작용
    - 사용 예시
        
        : 서버 언어 (Python, Java 등) 및 백엔드 프레임워크(Django), 데이터베이스, API, 보안



  # Framework

## Web Framework

**개념**

- 웹 애플리케이션을 빠르게 개발할 수 있도록 도와주는 도구
- 개발에 필요한 기본 구조, 규칙, 라이브러리 등 제공
    - 로그인/로그아웃, 회원관리, 데이터베이스, 보안 등
    - 현대 웹 개발의 핵심
        - 일반적인 웹 서비스에 다양한 보편적인 기능 존재
        → 혼자 개발하기 보다는 이미 만들어진 도구를 효과적으로 활용하는 것이 필요

## Django Framework

**개념**

- Python 기반의 대표적인 웹 프레임워크
- 목적 : **클라이언트 - 서버** 구조의 **서버** 구현

**사용 이유** 

- 다양성
    - Python 기반으로 웹, 모바일 앱 백엔드, API 서버 및 빅데이터 관리 등 광범위한 서비스 개발에 적합
- 확장성
    - 대량의 데이터에 대해 빠르고 유연하게 확장할 수 있는 기능 제공
- 보안
    - 취약점으로부터 보호하는 보안 기능이 기본적으로 내장되어 있음
- 커뮤니티 지원
    - 개발자를 위한 지원, 문서 및 업데이트를 제공하는 커뮤니티 활성화
- 검증된 웹 프레임 워크
    - 대규모 트래픽 서비스에서도 안정적인 서비스 제공
    - 예시 : Spotify, Instagram, Dropbox

# 가상 환경

**Virtual Environment**

**개념**

- 하나의 컴퓨터 안에서 또 다른 ‘**독립된**’ 파이썬 환경
    - 마치 같은 집 안에 방을 따로 만들고, 필요 물건을 각 방에 넣어두는 것
    → 방이 다르면 들여놓은 물건이 달라도 서로 간섭하지 않음
- 새로운 컴퓨터를 생성하는 느낌으로 상호 간섭하지 않음
- 여러 프로젝트를 진행하며 다른 패키지 버전 혹은 서로 다른 패키지 사용해야 하는 경우
→ 충돌을 피하기 위해 각각 **독립적인 개발 환경**이 필요함

## 가상 환경 생성 및 활성화

### 생성 과정

1. **가상 환경 생성**
- 현재 디렉토리 안에 venv라는 폴더 생성
- 해당 폴더 안에 파이썬 실행 파일, 라이브러리 등을 담을 공간 마련됨
- venv라는 이름의 가상 환경을 생성한 것
→ 임의의 이름으로 생성 가능하나 관례적으로 venv 이름 사용

```bash
$ python -m venv venv
```

1. **가상 환경 활성화**
- 폴더 안 이동은 상관 없음
- 활성화 된다면, 프롬프트 앞에 (venv) 표시됨
    - global에 영향 주는 것 아님
        
        → 다른 가상 환경에서는 on되지 않음
        ( 독자적 환경에서 개발이 진행되는 것)
        

```bash
$ source venv/Scripts/activate

# Mac/Linux에서는 명령어 다름
$ source venv/bin/activate
```

1. **가상 환경 종료**
- deactivate 명령 실행
→ 다시 python global 환경으로 돌아가는 것
- 터미널을 삭제해서 꺼지긴 함
(하지만 안 꺼지는 경우도 있기에 비추)

```bash
$ deactivate
```

## 의존성 패키지

**개념**

- 프로젝트가 의존하는 ‘개별 라이브러리’들을 가리키는 말
- 프로젝트가 실행되기 위해 꼭 필요한 각각의 패키지
- 의존성
    - 하나의 소프트웨어가 동작하기 위해 필요로 하는 다른 소프트웨어나 라이브러리
    - 예시
        - 컴퓨터가 잘 동작하기 위해 CPU, GPU, RAM 등 필요
        (CPU, GPU, RAM 등 : 컴퓨터 입장에서의 의존성)
        → 이것들을 각각 의존성 패키지라고 부름

1. **패키지 목록 확인**
- 현재 가상 환경에 설치된 라이브러리 목록 확인
    - 갓 생성된 가상 환경은 별도의 패키지가 없음
        
        → 기본 환경 구성을 위한 pip, setuptools 정도만 존재
        

```bash
$ pip list
```

1. **의존성 기록**
- pip freeze 명령어
    
    → 가상 환경에 설치된 모든 패키지를 버전과 함께 특정한 형식으로 출력
    
- requirements.txt
    - venv 파일의 환경을 정리해서 보여줌
    - 생성 파일 명으로 나중에 동일한 환경을 재현할 때 유용
    - 의존성 리스트로, 
    협업 시 동일한 버전의 라이브러리 설치하도록 공유하는 것에 사용
    - 관례적으로 해당 이름 사용

```bash
$ pip freeze > requirements.txt
```

‘>’ : CLI (Shell)의 Redirection Operator

→ 이전 명령어의 출력을 파일로 redirect
(즉, 생성하고 작성)

⇒ 같은 명령어를 다시 사용할 경우,
이전 파일의 내용을 덮어씀

1. 의존성 패키지 관리의 필요성
    - 패키지마다 버전이 다름
        - 버전이 다른 경우 함수명이나 동작이 달라질 수 있음
    - 프로젝트가 커질수록 사용하는 패키지 개수도 늘어남
        - 어떤 버전을 쓰고 있는지 기록 및 공유 필수적
    
    ⇒ 다른 PC나 팀원들과 동일한 환경을 구성할 때 반드시 필요
    

## 의존성 패키지 기반 설치

- 동일한 패키지 버전 설치 방법
    - requirements.txt 파일 통한 설치
    - venv 파일 공유 X

```bash
# 1. 가상 환경 준비 -> 새로운 가상 환경을 생성 및 활성화

$ python -m venv venv
$ source venv/Scripts/activate

# 2. 패키지 설치 -> requirements.txt 패키지 버전을 통해 같은 환경으로 설치

$ pip install -r requirements.txt
```

## 가상 환경 주의 사항

- 주의 사항 및 권장 사항
    1. 사용할 Python 환경을 “ON/Off”로 전환하는 개념
        - 가상 환경에 들어가고 나오는 것이 아님
        - 가상 환경 활성화는 현재의 터미널 환경에만 영향을 끼침
        - 새로운 터미널 창을 열면 다시 활성화해야 함
    2. 프로젝트마다 별도의 가상 환경 사용
        - 일반적으로 가상환경 폴더 venv는 관련된 프로젝트와 동일한 경로에 위치시킴
            - on 하는 위치가 중요한 것
                
                → 그렇기 때문에 각 프로젝트 파일에서 venv 폴더 만듦
                이 때, 파일 명은 venv1 과 같이 수정하여 사용하면 안됨.
                
    3. venv 폴더는 .gitignore 파일에 작성되어 원격 저장소에 공유하지 않음
        - 저장소 크기를 줄여 효율적인 협업 및 배포 가능
        - 사용 OS 차이로 인한 문제 방지
        
        → 대신 requirements.txt 공유하여 각자의 가상 환경을 구성함
        
    
- 가상 환경의 필요성
    1. 프로젝트마다 다른 버전의 라이브러리 사용
        - 프로젝트별 다른 버전을 사용하는 경우 존재
        → 가상 환경을 활용하여, 서로 다른 버전을 동시 설치해도 충돌 없이 각각의 프로젝트 유지 가능
    2. 의존성 충돌 방지
        - 프로젝트별 독립적인 라이브러리 관리 가능
        - 같은 라이브러리를 동시에 여러 프로젝트가 사용하더라도 버전 충돌 문제 예방
    3. 팀원 간 협업
        - 모두 동일한 방식으로 가상 환경 생성
        → 동일한 라이브러리 설치로 에러 가능성 줄이기 가능

# Django 프로젝트

## 프로젝트 생성 및 서버 실행

1. Django 설치
    - 버전 명시 X 
    → python 기준 최신 버전 설치

```bash
$ pip install django
```

2. 프로젝트 생성
```bash
$ django-admin startproject firstpjt .
```

. 현재 디렉토리
즉 현재 디렉토리에 firstpjt라는 startproject를 시작할 것이라는 말

startproject (목적) firstpjt (pjt 이름)

3. 서버 실행
   - manage.py와 동일한 위치에서 명령어 진행
      → manage.py : 장고 명령어 제공

1. 서버 실행
    - [manage.py](http://manage.py)와 동일한 위치에서 명령어 진행
    → manage.py : 장고 명령어 제공
    
    ![image.png](attachment:605a0a5e-ee60-4894-99f8-586e07895d38:4b335be4-4872-4500-b93e-ff57b099f3bc.png)
    

```bash
$ python manage.py runserver
```

→ 해당 명령어를 실행하면, 
옆의 그림과 같이 나오며, 서버는 http:// ~
이렇게 작성되어 있는 것을 접속하여 확인하면 됨

# Django Design Pattern

## Design Pattern

**디자인 패턴**

**개념**

- 소프트웨어 설계에서 반복적으로 발생하는 문제에 대한, 검증되고 재사용 가능한 일반적인 해결책
- 애플리케이션의 구조는 이렇게 구성하자는 모범 답안 또는 관행
    - 대표적인 디자인 패턴
        - MVC
            
            : 하나의 애플리케이션을 구조화하는 대표적인 구조적 디자인 패턴
            
            - Model : 데이터 및 비즈니스 로직 처리
            - View : 사용자에게 보이는 화면 담당
            - Controller : 사용자의 입력을 받아 Model 과 View 제어
                
                ⇒ 시각적 요소와 뒤에 실행되는 로직을 서로 영향 없이, 독립적이고 쉽게 유지 보수할 수 있는 애플리케이션을 만들기 위함
                
        - MTV
            
            : Django에서 애플리케이션을 구조화하는 디자인 패턴
            → 기존의 MVC 패턴과 동일하나 단순히 명칭을 다르게 정의한 것
            
            - Model
                - 데이터와 관련된 로직 관리
                - 응용프로그램의 데이터 구조를 정의하고 데이터베이스의 기록 관리
            - Template
                - 레이아웃과 화면 처리
                - 화면 상의 사용자 인터페이스 구조와 레이아웃 정의
            - View
                - Model & Template과 관련한 로직을 처리하여 응답 반환
                - 클라이언트의 요청에 대해 처리를 분기하는 역할
                - 예시
                    - 데이터 필요 시 , Model에 접근하여 데이터 가져오고
                    해당 데이터를 template으로 보내 화면 구성
                    → 이를 응답으로 만들어 클라이언트에 반환

## 프로젝트와 앱

- Django에서 프로젝트와 앱의 관계
- 애플리케이션의 집합
    - DB 설정, URL 연결, 전체 앱 설정 등을 처리
- Django application
    - 독립적으로 작동하는 기능 단위 모듈
    - 각자 특정한 기능 담당
        
        → 다른 앱들과 함께 하나의 프로젝트 구성
        

**APP**

**생성**
```bash
$ python manage.py startapp articles
```

- articles 라는 폴더 + 내부 여러 파일 새로 생성
- 앱의 이름은 복수형으로 지정하는 것을 권장


등록
- 반드시 앱 생성 후 등록
    - 등록 후 생성은 불가함
    - 등록을 먼저 하는 경우, 생성을 위한 명령어 실행 중 존재하지 않는 articles 앱 찾다가 실패함

## 프로젝트 및 앱 구조

- **프로젝트 구조**
**settings.py**

- 프로젝트의 모든 설정 관리

**urls.py**

- 요청이 들어오는 URL에 따라, 이에 해당하는 적절한 views 연결

**__init__.py**

- 해당 폴더를 패키지로 인식하도록 설정하는 파일

**asgi.py**

- 비동기식 웹 서버와의 연결 관련 설정
    - 클라이언트와 서버 간에 동시에 얼마나 효율적으로 연결을 유지하고 처리할 지에 대한 옵션 설정하는 것을 의미

**wsgi.py**

- 웹 서버와의 연결 관련 설정

**manage.py**

- Django 프로젝트와 다양한 방법으로 상호 작용하는 커맨드 라인 유틸리티


앱 구조
**admin.py**

- 관리자용 페이지 설정

**models.py**

- DB와 관련된 Model 정의 (MTV 패턴의 M)

**views.py**

- HTTP 요청을 처리하고 해당 요청에 대한 응답 반환 (MTV 패턴의 V)
    - url, model, template과의 연동

**apps.py**

- 앱 정보가 작성된 곳

**tests.py**

- 프로젝트 테스트 코드를 작성하는 곳

# 요청과 응답

## Django에서의 요청과 응답
- **URLs**

```bash
# urls.py

from django.contrib import admin
from django.urls import path
from articles import views        # articles 패키지에서 views 모듈 가져오는 것

urlpatterns = [
	path('admin/', admin.site.urls),
	path('articles/', views.index),
]
```

- http://127.0.0.1:8000/articles/ 로 요청이 온 경우, request 객체를 views 모듈의 index view 함수에 전달하여 호출

- path 함수
    - path(url 경로, 뷰 함수)
    - url로 articles/까지 일치한 경우, 두 번째 인자에 있는 view 함수 호출
    - URL 경로는
    반드시 ‘/’ (slash)로 끝나야 함

- **View**

```python
# 템플릿을 만들어 내는 친구임
from django.shortcuts import render
# create your views here
# 메인 페이지를 응답하는 함수
# 무조건 써야함, 쓸 지 말지는 선택권 없음
def index(request): 
	return render(request, 템플릿 경로_views.index)
	# 이 때, views.index()로 쓰면 안됨. 
	# path가 수행될 때 해당 위치로 이동해야 하는데
	# views.index()로 작성하면 그대로 호출
```

- view 함수가 정의되는 곳
    - 특정 경로에 있는 template과 request 객체를 결합하여 응답 객체 반환
    - 모든 view 함수는 첫 번째 인자로 요청 객체를 필수적으로 받음 → 안 쓰면 동작하지 않음
    - 매개 변수 이름은 관례적으로 request로 작성

 - Template
   ```python
# views.py

from django.shortcuts import render

def index(request):
	return render(request, 'articles/index.html')
```

- articles 앱 폴더 안에 templates 폴더 생성
    - 폴더 명은 반드시 templates
    - 개발자가 직접 생성해야 함
- templates 폴더 안에 articles 폴더 생성
- articles 폴더 안에 템플릿 파일 생성

**Django에서 template을 인식하는 경로 규칙**

app 폴더 / templates / articles / index.html

app 폴더 / templates / example.html

→ Django는 templates / 까지 기본 경로로 인식

- view 함수에서 template 경로 작성 시,
해당 지점 이후의 경로를 작성해야 함

⇒ 데이터 흐름에 따른 코드 작성
URLs → View → Template 순으로 
코드 작성해야 함

# 참고

- Django 프로젝트 생성 전 루틴
    
    ```bash
    # 가상 환경 생성
    $ python -m venv venv
    
    # 가상 환경 활성화
    $ source venv/Scripts/activate
    
    # Django 설치
    $ pip install django
    
    # 패키지 목록 파일 생성
    ## 패키지 설치 시마다 진행
    $ pip freeze > requirements.txt
    ```

- render 함수
    
    ```python
    render(request, template_name, context)
    ```
    
    **개념**
    
    : 주어진 template을 주어진 context 데이터와 결합하고,  rendering된 text와 함께 HttpResponse 응답 객체를 반환하는 함수
    
    - request
        - 응답을 생성하는 데 사용되는 요청 객체
    - template_name
        - 템플릿 이름의 경로
    - context
        - 템플릿에서 사용할 데이터
        - 딕셔너리 타입으로 작성
        - 생략 가능

- Django 규칙
    - urls.py에서 각 url 문자열 경로는 반드시 ‘/’로 끝남
    - views.py에서 모든 view 함수는 첫 번째 인자로 요청 객체를 받음
        - 매개변수 이름은 반드시 request로 지정
    - Django는 특정 경로에 있는 template 파일만 읽어올 수 있음
        - 특정 경로 예시 : app 폴더/templates

- 프레임워크의 규칙
    - 일정한 규칙에 따라야 하며, 이는 각각의 설계 철학이나 목표를 반영함
        - 일관성 유지, 보안 강화, 유지보수성 향상 등의 이유
    - 프레임워크란?
    개발자에게 도움을 주는 도구와 환경을 제공하기 위해 규칙을 정해 놓은 것
