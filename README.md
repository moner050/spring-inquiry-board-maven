# Spring Boot Inquiry Board Project
> 회원가입/로그인 구현, 문의 CRUD 및 댓글 CRD 구현

<br>

## ⚙ 프로젝트 개발 환경
- 통합개발환경 : Eclipse
- JDK 버전 : JDK 17
- 스프링부트 버전 : 2.7.1
- 사용 DB : H2
- 빌드툴 : Maven
- 관리툴 : Git, Github

## ⚒ 기술 스택
- Backend
  - Spring Boot
  - Spring Security
  - Spring Devtools
  - Spring Data Jpa
  - Lombok


- Frontend
  - JSP
  - JSTL
  - Jasper
  - Bootstrap
  - Jquery
  - Summernote
  - Spring Security Taglibs


- Database
  - H2

## yml 설정
- 서버 설정
    - context-path 를 `/` 로 설정해 프로젝트 명을 입력하지 않고 포트번호만 쳐도 메인페이지로 갈수있도록 설정.
- 뷰리졸버 설정
    - prefix(접두어) 및 suffix(접미어) 를 설정해 반복적인 타이핑 줄이기

## 메인화면
- header 부분
    - 로그인 상태이면 1:1문의, 로그아웃이 뜨게 설정
    - 로그인된 상태가 아니면 로그인 및 회원가입이 뜨게 설정
- main 부분
    - 작성한 게시글 목록이 출력되게 설정
- footer 부분
    -  만든이 및 연락처, 주소지 출력되게 설정

## 게시글 관련
- 게시글 목록
    - 게시글 3개씩 POST의 id 기준으로 내림차순 정렬해 출력
    - 이전 및 다음 페이지가 없으면 버튼 비활성화

- 게시글 작성
    - 메인 화면 상단의 `1:1문의` 버튼을 누르면 `insertPost.jsp` 로 이동
    - 제목과 내용을 작성 후 `포스트 등록` 버튼을 누르면 `post.js` 의 insertPost 함수 실행.
    - Ajax를 이용해 post Object를 JSON 으로 변환 후 서버에 넘겨주고 현재 로그인된 사용자의 정보를 받아와 post에 넣어준 뒤 작성처리.

- 게시글 상세
    - 메인화면의 `상세 보기` 버튼을 누르면 해당 게시글 번호를 변수로 받아와 model에 해당 게시글을 넣어준 뒤 `getPost.jsp` 로 이동

- 게시글 수정
    - 해당 게시글의 작성자이면 `수정하기` 버튼 활성화.
    - `수정하기` 버튼을 누르면 해당 게시글 번호를 변수로 받아와 model에 해당 게시글을 넣어준 뒤 `insertPost.jsp` 로 이동
    - `돌아가기` 버튼을 누르면 `onclick="history.back()` 를 이용해 이전 페이지로 이동.
    - `포스트 수정` 버튼을 누르면 Ajax를 이용해 제목과 내용을 서버에 넘겨준 뒤 수정처리.

- 게시글 삭제
    - 해당 게시글의 작성자이면 `삭제하기` 버튼 활성화.
    - `삭제하기` 버튼 누르면 해당 게시글 번호를 변수로 받아와 게시글 삭제처리.

## 댓글 관련
> User, Post에 양방향 매핑.
> 게시글이 삭제되면 해당 게시글에 달려있던 댓글 전체 삭제.

- 댓글 목록
    - 게시글 상세 보기 버튼을 누르면 게시글 번호를 받아와 JPQL을 통해 해당 게시글 번호에 해당하는 댓글 리스트를 DB에서 받아와 Model에 넣어준 뒤 출력.

- 댓글 등록
    - 댓글 내용을 입력한 뒤 `덧글 등록` 버튼을 누르면 해당 Post의 id를 변수로 받아 현재 로그인된 사용자의 정보를 결합해 댓글등록후 새로고침.

- 댓글 삭제
    - 현재 로그인된 유저와 댓글의 작성자가 일치하면 `삭제`버튼 활성화.
    - `삭제` 버튼을 누르면 댓글의 id값을 변수로 받아와 해당 댓글 삭제후 새로고침.


---