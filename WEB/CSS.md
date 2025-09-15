# CSS

Cascading Style Sheet

**개념**

웹 페이지의 **디자인**과 **레이아웃**을 구성하는 언어 (웹 스타일링)

![image.png](attachment:8e2d6d6e-13d6-4481-9671-0a633551bf57:image.png)

**적용 방법**

- 스타일 적용 우선순위 : 인라인 > 내부 > 외부 순으로 적용
- 종류
    
    **인라인 스타일**
    
    - HTML 요소 안에 style 속성 값으로 작성

        
        - HTML : 웹 페이지의 의미와 구조를 정의하는 언어
        - style 속성 값 : 특정 요소 하나에만 CSS 스타일을 직접 적용하는 속성
        - 단점
            1. 가독성 떨어짐 
            2. 재사용이 어렵고 유지 보수 방해됨
            → 텍스트나 특수한 경우에만 사용
            
            ⇒ 이러한 이유로 실습 등에서 활용하지 않음
            
    
    **내부 스타일 시트 (Internal Style Sheet)**
    
    - head 태그 안에 style 태그에 작성
        - <head> 태그 : 제목, CSS 등 보이지 않는 설정 정보를 담는 태그
        - <style> 태그 : CSS 코드를 작성하여 페이지 전체에 적용하는 태그
        

    
    **외부 스타일 시트 (External Style Sheet)**
    
    - 별도 CSS 파일 생성 후 HTML link 태그를 사용하여 불러오기
        - <link> 태그 : 외부 스타일 시트(CSS)를 HTML 문서에 연결하는 태그
