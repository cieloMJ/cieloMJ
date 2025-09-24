# Model

**개념**

- 데이터베이스와 Python 클래스(객체)로 추상화된 형태로 상호작용
    - 추상화된 형태 : SQL 코드를 직접 작성하거나 실행하지 않고, Python 객체 지향으로 DB와 상호작용
- Django
    - 강력한 기능 : 데이터베이스에 대한 깊은 지식 없이도 개발자가 쉽게 데이터 관리 가능
    → Django가 개발자와 DB 사이의 중간 다리 역할을 수행함
    - 장점 : 유지 보수 및 확장성 증대
        - 데이터베이스 변경 시에도 코드 수정 최소화
        - 재 사용 가능한 데이터 모델을 통해 개발 효율성 향상

**Model을 통한 DB(데이터베이스) 관리**

- urls.py : 사용자 요청의 시작점
- views.py
: 요청 처리 및 models.py 통한 데이터 관리
- models.py : **DB 정의 및 상호작용**
- templates 
: views.py로부터 받은 데이터를 사용자에게 보여줄 화면 구성

## Model class

**개념**

- DB 테이블을 **정의**하고 데이터를 조작할 수 있는 기능 제공
- 데이터베이스 테이블의 구조를 설계하는 청사진(Blueprint) 역할
- 어떤 데이터(컬럼)를 저장하고, 그 형태는 어떠한지(타입, 길이 등)를 Python 코드로 명확히 정의

작성 방법
```
# articles/models.py

#내장된 django 패키지 안 db 서브패키지 안 models
from django.db import models

# articles 앱의 models.py에 해당 코드 작성
class Article(models.Model):
	title = models.CharField(max_length = 10)
	content = models.TextField()

# ⇒ Article : 해당 부모 클래스의 모든 것을 가져오고, 특정 코드만 작성한 상태]
```
- Django : class로 model 정의 
→ 해당 class가 데이터베이스의 테이블 표현
- models.Model
    - models 모듈 안에 정의된 Model 클래스 의미
    - Model : model에 관련된 모든 코드가 이미 작성되어 있는 Class
        - 부모 클래스를 정의한 것
        → Django 모델을 정의할 때 반드시 상속해야 함
        - 목적 
        : 개발자가 가장 중요한 테이블 구조를 어떻게 설계할 지에 대한 코드만 작성하도록 하기 위함
            
            (상속을 활용한 프레임워크 기능 제공)
            

⇒ **DB** : 여러 개의 테이블이 모여있는 것

## Model Field

- Django : class로 model 정의 
→ 해당 class가 데이터베이스의 테이블 표현
- models.Model
    - models 모듈 안에 정의된 Model 클래스 의미
    - Model : model에 관련된 모든 코드가 이미 작성되어 있는 Class
        - 부모 클래스를 정의한 것
        → Django 모델을 정의할 때 반드시 상속해야 함
        - 목적 
        : 개발자가 가장 중요한 테이블 구조를 어떻게 설계할 지에 대한 코드만 작성하도록 하기 위함
            
            (상속을 활용한 프레임워크 기능 제공)
            

⇒ **DB** : 여러 개의 테이블이 모여있는 것

**개념**

- DB 테이블의 필드 정의
- 데이터베이스 테이블의 열(column)을 나타내는 중요한 구성 요소
- 데이터의 유형(Type)을 명시하고 필요한 세부 제약 조건 정의
    - 제약 조건을 지정하는 것은 선택 사항
    - 예시 : CharField(max_length = 10)
        - SQLite : 문자열 컬럼의 길이에 대한 엄격한 제한 강제 X
        - But, 유효성 검사 및 컬럼에 들어갈 데이터의 명확성을 위해 명시적으로 설정하는 것 권장
            - 컬럼을 자동으로 생성하고, 데이터 입력 시 유효성 검사 등 필요 기능 제공
            - 애플리케이션의 안정성을 높이기 위해 정확한 필드 정의는 필수적

### Field Types

**필드 유형**

**개념**

- 데이터베이스에 저장될 데이터의 **종류** 정의
    - models 모듈의 클래스로 정의되어 있음
    - 클래스를 통한 인스턴스 생성 → column을 정의하는 것
    
- 주요 필드 유형
    - 문자열 필드 : CharField, TextField
    - 숫자 필드 : IntegerField, FloatField
    - 날짜/시간 필드 : DateField, TimeField, DateTimeField
    - 파일 관련 필드 : FileField, ImageField
    

**예시**

- CharField()
    - 제한된 길이의 문자열 저장할 때 사용
    - 선택 옵션 : max_length(필드의 최대 길이 결정)
- TextField()
    - 길이 제한이 없는 대용량 텍스트 저장
    - 무한대는 아니며 사용하는 Django 시스템 혹은 사용하는 데이터베이스에 따라 결정됨
    

### Field Options

**필드 옵션**

**개념**

- 필드의 **동작**과 **제약 조건**을 정의
    - **Constraint** ( 제약 조건 )
        
        : 특정 규칙을 강제하기 위해 테이블의 열이나 행에 적용되는 규칙이나 제한 사항
        
        ex. 숫자만 저장되도록 제한, 100자까지만 저장 가능, 특정 규칙 정하도록 제한
        → 디테일하게 제약 조건을 걸 수 있음
        

- 주요 필드 옵션
    - null
        - 데이터베이스에서 NULL 값을 허용할 지 여부 결정
        - 기본 값 : False 
        (기본적으로 null 값은 허용하지 않음)
        - 파이썬의 None과 같은 역할
    - blank
        - form에서 빈 값을 허용할 지 여부 결정
        - 기본 값 : False
    - default
        - 필드의 기본 값 설정

# Migrations

**개념**

- Model 클래스의 변경 사항 (필드 생성, 수정, 삭제 등)을 DB에 최종 반영하는 방법
    - 모든 변경 사항은 코드로 관리
    → 협업 시 모델 변경 내역에 대해 수월하게 추적, 공유 가능
- 설계도(Field) 기반으로 제작하는 과정
    - Django에게 어떤 식으로 만들 것이라고 명령을 내리는 것을 의미
- Migration 파일은 되도록 직접 수정, 삭제하지 않는 것이 원칙
- 필요한 경우
    - Model Class에 변경사항이 생겼다면, 
    **→ Model Class 생성/수정**
    - 반드시 새로운 설계도를 생성하고,
        
        → **makemigrations**
        
    - 이를 DB에 반영해야 한다.
        
        → **migrate**

**과정**
1. 모델 클래스 작성 및 수정
    - Python 클래스로 정의
    - CharField 
    : 제한된 길이의 문자열 저장
    - TextField 
    : 길이 제한 없는 대용량 텍스트

```python
# articles/models.py

class Article(models.Model):
	title = models.CharField(max_length = 10)
	content = models.TextField()
```

2. Migration 파일 생성
    - python 코드로 된 migration 파일(설계도) 생성
    - migration 파일 == 최종 설계도
    - Django가 해당 명령어를 통해 DB가 이해할 수 있는 최종 설계도를 만드는 과정
    
    ⇒ **model class 기반 최종 설계도 작성**
         (migration 파일 생성)
    

```bash
**$ python manage.py makemigrations**

Migrations for 'articles':
	articles/migrations/0001_initial.py
		+ Create model Article
```

3. DB에 반영하기
    - Migration 파일 : 0001_initial.py
    → 모델 변경사항을 기록한 python 코드
    (DB 테이블 변경 내역을 순차적으로 저장 및 추적, 관리
    - migrate 명령어로 **SQL 실행 (자동 변환)**
    
    ⇒ **최종 설계도를 DB에 전달 및 반영**
    

```bash
**$ python manage.py migrate**
```



**필드 추가** 
- 기존 레코드가 있는 테이블에 새로운 필드를 추가하는 경우,
    - 어떤 값을 기준으로 채울 지를 결정해야 함 (기본 값에 대한 처리 필요)
    - Django의 makemigrations 실행 시 기본 값 설정을 요구하는 프롬프트 표시됨

**과정**

1. 새로운 필드 작성
    - Django 기존 모델 수정
    (모델 클래스 수정)
    - **Model Field**
        
        **: models.필드 유형(필드 옵션)**
        
    - auto_now
    : 데이터가 **저장될 때마다** 자동으로 현재 날짜, 시간 저장
    - auto_now_add
    : 데이터가 **처음 생성될 때만** 자동으로 현재 날짜, 시간 저장

```python
# articles/models.py

class Article(models.Model):
	title = models.CharField(max_length = 10)
	content = models.TextField()
	create_at = models.DateTimeField(auto_now_add=True)
	updated_at = models.DateTimeField(auto_now=True)
```

1. **makemigrations** 명령어 입력

- 기존 테이블이 존재하기에, 추가 입력 시 필드의 기본 값 설정 필요
- 설정 방법

    
    1. 현재 대화 유지하며 직접 기본 값 입력
        - 일회성 기본값 제공
        → 현재 대화형 프롬프트에서 기본값 직접 입력
            
            ⇒ 입력한 기본값은 기존의 모든 데이터 행에 적용
            
        - 아무것도 입력하지 않고 enter 누르면 Django 제안 기본 값 설정

            
    2. 현재 대화에서 나간 후 models.py에 기본 값 관련 설정 진행

```bash
$ python manage.py makemigrations
```

- 해당 과정 이후 migration 파일 추가 생성
→ 설계도를 쌓아가며 추후 문제 발생 시 복구 가능 (마치 git commit)
    


1. migrate 명령어 입력


```bash
$ python manage.py migrate
```

- migrate 후 테이블 필드 변화 확인


# Admin Site

### **관리자 인터페이스**

**Automatic admin interface**

**개념**

- Django가 추가 설치 및 설정 없이 자동으로 제공하는 관리자 인터페이스
    - Django 관리자 인터페이스는 추가 설정 없이 자동 생성되는 웹 기반 관리 도구임
    - 관리자 인터페이스를 만들기 위해서는 admin 계정 생성 필요
- 주요 기능
    - 데이터베이스 모델의 **CRUD 작업**을 간편하게  수행 가능
        - Create (생성)
        - Read (읽기)
        - Update (업데이트)
        - Delete (삭제)
- 활용
    - 빠른 프로토타이핑
    - 비개발자 데이터 관리
    - 내부 시스템 구축

**생성 방법**

1. 터미널 열기
    - Django 프로젝트 폴더로 이동
    → manage.py 파일 있는 위치에서 터미널 열기
    
2. 관리자 계정 생성 명령어 입력

```bash
$ python [manage.py](http://manage.py) createsuperuser
```

1. 정보 입력
    - 사용자 이름 (username) : 관리자 페이지에 로그인할 때 사용할 아이디 입력
    - 이메일 (email address) : 선택 사항 (입력하지 않아도 됨_enter)
    - 비밀번호 (password) : 로그인할 때 사용할 비밀번호 입력 ( 콘솔 창에 아무 것도 나타나지 X)
    - 비밀번호 확인 (password(again)) : 한 번 더 입력하여 확인
    
2. 모델 클래스 등록
    
    ```python
    #articles/admin.py
    
    from django.contrib import admin
    from .models import Article
    
    **admin.site.register(Article)**
    ```
    

Admin도 하나의 유저 데이터

⇒ 데이터 베이스 안에 저장되어야 함
(auto_user 파일 안에 저장됨)

http://127.0.0.1:8000/admin 이동 후 로그인 확인

→ 로그인 후 아무 것도 안 보이는 것이 정상

(해당 모델을 관리하려면 추가 설정 필요)

⇒ admin.py에 작성한 모델 클래스를 등록해야만 확인 가능

⇒ 등록 이후 **CRUD 가능**

# 참고

- 데이터베이스 초기화

1. Migration 파일 삭제
    - Migration 파일 : makemigrations 명령어로 생성되는 설계도
    - 단, __init__.py, migrations 폴더는 삭제 금지
2. db.sqlite3 파일 삭제

- Migrations 기타 명령어

showmigrations

```bash
$ python manage.py showmigrations
```

- migrations 파일이 migrate 되었는지 여부를 확인하는 명령어
- [X] 표시가 있는 경우 migrate된 것

sqlmigrate

```bash
$ python manage.py sqlmigrate <앱이름><마이그레이션 이름>
```

- 해당 migrations 파일이 SQL 언어로 어떻게 번역되어 DB에 전달되는지 확인하는 명령어
    
    ex. sqlmigrate articles 0001
    

**SQLite**

**개념**

- 데이터베이스 관리 시스템 중 하나
- Django의 기본 데이터베이스로 사용됨
- 로컬 컴퓨터에 저장된 데이터 기록
- 파일 기반
    - 데이터 베이스가 하나의 파일로 저장되어, 설치/설정 없이 간편하게 복사/이동/백업 가능
- 장점
    - 가볍고 빠름
        - 별도 서버 없이 파일로 직접 데이터 처리
        - 소규모 앱이나 모바일 환경에 최적화
    - 높은 호환성
        - 다양한 운영체제와 프로그래밍 언어에서 폭넓게 사용 가능

**유의 사항**

- db.sqlite3 파일은 Git 등 버전 관리 시스템에서 관리하지 않는 것이 원칙
    - 데이터가 변경될 때마다 파일 전체가 변경되기 때문
- .gitignore 파일에 db.sqlite3을 추가하여 Git 버전 관리에서 제외해야 함
    - gitignore.io
        - 개발자들이 .gitignore 파일을 쉽게 생성할 수 있도록 도와주는 웹 서비스
        - Django를 기술 스택으로 추가한 뒤 .gitignore 파일을 자동 생성하면 db.sqlite3 자동 포함됨
