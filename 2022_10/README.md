### 2022-11-01 (화)
- algo
	- [ ] 15683(g3)
- 42(minishell)
	- [ ] readline()사용해서 구조 잡기
	- [ ] linkedlist만들어서 tokenize
- 우테코
	- 음.
- kernel
	- 강의 하나 

### 2022-10-31 (월)
- algo
	- [ ] 15683(g3) 
- 42
	- [ ] network 2강
	- [ ] 
- 우테코
	- [ ] 1번 문제 잡기
- kernel
	- [ ] 강의 하나

### 2022-10-28 (금)
- algo
	- [ ] 15683(g3) 
- 42
	- [ ] network 1강
	- [ ] 추상구문트리 공부해서 정리
- 우테코
	- [ ] 1번 문제 잡기
- kernel
	- [ ] 강의 하나

### 2022-10-27
- algo
	- [X] 15683(g3)
		- 생각보다 더 복잡하다. 다시 손대보기
- 42
	- [O] minishell준비
		- [O] 작업 방식 이야기(공동 repo로 하자는 얘기가 나왔다)
			- [X] 어떻게 하면 효율적으로 하지?(branch 등등)
			- [X] 다음에 만나는 건 아마 다음주 월요일, 이때까지 할것들 명확히 정리.
			- [X] 미니쉘 끝낸 사람들한테 엣지 케이스나 구조를 잡을 때 시행착오 줄이는 방법 물어보러 다니기(모든 엣지 케이스와 주의사항을 잡고 시작한다)
				- [ ] 다음 주 월요일까지 할 것:
					- [ ] 네트워크 1강
					- [ ] 트리구조익히기(추상구문트리)
					- [ ] 쉘(bash)의 작동방식 이해해오기
					- [ ] minishell subject 이해해오기
	- [X] 평가하기
- 우테코
	- [ ] 야구게임
- kernel
	- [X] 가볍게 강의 하나

### 2022-10-26
- algo
	- [ ] 알고리즘 풀지 못함(2일) -> 내일은 꼭 할 것(꾸준히!!)
- fdf
	- [X] 코드 정리, 테스트
	- [X] 평가
- kernel
	- [ ] 가볍게 강의 하나라도 보기(꾸준히!!)

### 2022-10-25
- algo
	- 15683(g3)
- fdf
	- 함수 하나 작성하고, 테스트 확실히 하자. 디버깅만 3시간 보냄.
	- mlx_keyhook 마저 하자. 왜 안돌지?
- OS
	- [X] 

### 2022-10-25
- algo
	- [ ] 15683(g3)
- fdf
	- [ ] key_hook 
		  - [ ] move
		  - [ ] rotate
		  - [ ] refactoring
		  - [ ] 설명 준비
- OS
	- [ ] 

---
### 2022-10-24
- algo
	- [X] 16987(s1)
- fdf
	- [X] fdf 과제 
		- [X] isometric 적용 OK
		- [X] 브레젠험 적용 OK
- OS
	- [X] kernel

---
### 2022-10-23
- algo
	- [X] 1941(g3)
- fdf
	- [ ] isometric projection.
- OS
	- OS 다시 덧칠하기
		- https://www.youtube.com/watch?v=l5EmMAKiDlg&list=PLmQBKYly8OsWe1mNpYhZfBRL0mOGu0dEX 유튜브강의
		- https://pages.cs.wisc.edu/~remzi/OSTEP/Korean/ pdf자료 
		- 공룡책 pdf
		- blog만들어서 본격적으로 해보자! (fdf과제 끝내고 틈나는 대로)
			- [ ] github.io 로 하고 싶고,
			- [ ] 여러 컴퓨터에서 포스팅할 수 있게 docker 사용법 알고 싶다.
				- [ ] 도커 setting -> blog 첫포스팅 할 수 있게 공부
	- [ ] 입출력 시스템2
- [ ] kernel
	- [X] 프로세스~

---
### 2022-10-22
- [X] 잔나 결혼식

---
### 2022-10-21
- algo
	- [X] 1941(g3)
		- [X] 굳이 bfs로 해야하나? 생각해서 로직을 짜봤는데, 결국 모두가 인접해야 한다는 조건을 맞추는 게 bfs가 가장 간단하다. 
- fdf
	- 파싱 마무리
		- [X] convert_hex_to_dec() 함수 구현
		- [X] memory leaks check
		- [X] system call error handling
	- [ ] isometric projection.
	- [ ] draw line(dda or 브레젠험 or 직선의방정식)
- os
	- [ ] 입출력 시스템2
- kernel

---
### 2022-10-20
- algo 
	- [ ] 1941(g3)
		- bfs와 dfs를 동시에 하는 건 굉장히 복잡하다.
		- dfs로 모든 순열을 찾은 뒤에 bfs로 연결되어 있는지 검사하는 로직으로 한다.
- fdf
	- [X] 코드 작성 시작!
		- fdf parsing
	- [ ] 회전변환 + 유도 과정 공책에 정리
- os
	- [X] 입출력 시스템1
- kernel
	- [X] ftrace 분석

---
### 2022-10-19
- algo
	- [X] 1759(g4)
- fdf
	- [.] MLX42 docs 읽기
		- [ ] Try making textures by generating the image in loops.
		- [ ] make add_shade func 
			- accepts a double (distance) and a int (color) as arguments, 0 will add no shading to the color, whilst 1 will make the color completely dark. 0.5 will dim it halfway, and .25 a quarter way. 
		- [ ] make get_opposite func
			- accepts a int (color) as argument and that will invert the color accordingly.
		- [ ] esc를 누르면 창 꺼지게 하기
		- [ ] window is resized, you should print something in your terminal.
		- [ ] X를 누르면 창 꺼지게 하기
		- [ ] ~초 이상 누르면 터미널에 무언가를 출력하기
		- [ ] 마우스가 창에 들어가면 hello 출력하기, 나갈 때 bye 출력하기
		- [X] a key is pressed, it will print the key code in the terminal.
		- [ ] 마우스를 움직이면, 터미널에 현재 마우스 좌표 출력하기
		- [ ] a mouse is pressed, it will print the angle at which it moved over the window to the terminal.
		- [ ] w a s d 를 이용해 화면에서 움직일 수 있는 원
		- [ ] 루프에서 만든 이전의 작은 원형 게임을 가져와서 mlx_sync를 렌더링에 추가하십시오!

	- [ ] 점과 점 연결하기
	- [ ] 삼각형 그리기
	- [ ] 입체적으록 그리기
- os
	- [X] 파일시스템 3
- kernel
	- [X] ftrace

---
### 2022-10-18
- algo
	- [X] 6603(s2)
- fdf
	- [ ] MLX42 docs 쭉 읽기
	- [X] 무지개 원 그리기
	- [ ] 점과 점을 연결해보기
	- [ ] 삼각형 그리기
	- [ ] 입체적으로 그리기
- os
	- [o] 파일시스템 2
		- [X] file system에서 hash table 어떻게 구현할까?(간단하게)
		- [X] page in, out 등 page_cache를 알아보는 명령어
- kernel 
  	- [X] printk(kernel console)
	- [X] dump_stack

---
### 2022-10-17
- algo
	- [X] 15665(s2)
	- [X] 15666(s2)
	- [X] boj, fast I/O의 원리가 궁금하다.
- fdf
	- [X] docs 쭉 읽어보기
	- [X] 점 찍어보기
	- [X] 선 만들어보기
	- [X] 점 찍어보기
		- [X] 픽셀로 찍어보기
		- [X] 이미지로 찍어보기
	- [ ] 기초 수학 익히기
		- [ ] 삼각함수, 라디안(행렬연산)
	- [ ] 등축 투영
	- [ ] 두 점을 선으로 이어보기(직선의 방정식 공부해보기)
	- [ ] 평면에서 3차원을 표현하는 방법 
		- [ ] 직선의 방정식을 케이스별로 나눠서 해보기
		- [ ] 브레젠험 알고리즘 사용해보기
	- [ ] 회전해보기
- os
	- [X] 파일시스템 2
- Kernel
	- [X] Kernel debugging
		- use patch code
		- use ftrace

---
### 2022-10-17
- algo
	- [X] 15665(s2)
	- [X] 15666(s2)
	- [X] boj, fast I/O의 원리가 궁금하다.
- fdf
	- [ ] docs 쭉 읽어보기(codam 말고, 42docs에서 읽고 정리하기)
	- [ ] 점 찍어보기
		- [ ] 픽셀로 찍어보기
		- [ ] 이미지로 찍어보기
	- [ ] 기초 수학 익히기
		- [ ] 삼각함수, 라디안(행렬연산)
	- [ ] 등축 투영
	- [ ] 두 점을 선으로 이어보기(직선의 방정식 공부해보기)
	- [ ] 평면에서 3차원을 표현하는 방법 
		- [ ] 직선의 방정식을 케이스별로 나눠서 해보기
		- [ ] 브레젠험 알고리즘 사용해보기
	- [ ] 회전해보기
- os
	- [ ] 파일시스템 2
- Kernel
	- [ ] 3장 ~

---
### 2022-10-16
- algo
	- [ ] 
- fdf
	- [ ] docs 쭉 읽어보기
	- [ ] 점 찍어보기
	- [ ] 기초 수학 익히기
		- [ ] 삼각함수, 라디안(행렬연산)
	- [ ] 등축 투영
	- [ ] 두 점을 선으로 이어보기(직선의 방정식 공부해보기)
	- [ ] 평면에서 3차원을 표현하는 방법 
		- [ ] 직선의 방정식을 케이스별로 나눠서 해보기
		- [ ] 브레젠험 알고리즘 사용해보기
	- [ ] 회전해보기
- kernel
	- [X] raspberrypi, Username(default pi) 변경하기
	- [X] linux 설치, 전처리
- os
	- [X] file system 
### 2022-10-15
- algo
	- [X] +boj 1564
	- [X] +지역변수와 전역변수의 이름이 같을 때
- FDF
	- [X] +Makefile 의존성 문제
	- mlx사용법 익히기
		- [X] +grep으로 필요한 코드만 보고 싶다.
		- [ ] docs 쭉 읽어보기
		- [ ] 점 찍어보기
		- [ ] 기초 수학 익히기
			- [ ] 삼각함수, 라디안(행렬연산)
		- [ ] 등축 투영
		- [ ] 두 점을 선으로 이어보기(직선의 방정식 공부해보기)
		- [ ] 평면에서 3차원을 표현하는 방법 
			- [ ] 직선의 방정식을 케이스별로 나눠서 해보기
			- [ ] 브레젠험 알고리즘 사용해보기
		- [ ] 회전해보기
- kernel
	- [ ] Make다시 하기(어제 1시간 반 넘게 make가 안됐음)
		- [ ] 설정 변경하기(와이파이, -j 4) -> (LAN선, -j 6)
	- [ ] 3장 시작하기
 
### 2022-10-14
- FDF 환경 설정
	- mlx library 
		- https://github.com/codam-coding-college/MLX42
		- https://harm-smits.github.io/42docs/
	- [X] Makefile mlx library 사용해보기
- raspberry pi4 시작하기


### 2022-10-13
- TDL
	- [ ] graphic과제 정해서 subject 정리
	- [X] Makefile
		- [X] 왜 all_check, bonus_check을 써야 하는가?, phony
		- [X] phony가 없고, all과 fclean이라는 파일이 있을 때 왜 all은 실행되지만 fclean은 실행되지 않을까?
		- [X] 모든 소스파일들은 헤더파일의 상대 경로를 가지고 있다. 헤더파일이 변경되었을 때 일일이 수정해야 하는가? 
		- [X] 헤더 파일의 경로를 수정하면 현재 사용하는 NVIM에서 syntax error가 생긴다.

---
### 2022-10-12
- pipex
	 - [X] here_doc일 때, 입력을 못받아오는 문제.
	 - [X] here_doc일 때, 개행을 자르고 받아오는 문제
	 - [X] pipex, fdtable 부모프로세스 close부분.
	 - lsof -p 명령어
	 - existing command binary가 실행파일을 말한다면, PATH에 PWD도 파씽해주어야 한다.
---
### 2022-10-11
- 구조
    - 부모는 fork만 한다.
    - 매번 한 쌍의 파이프만 만들어준다.
    - 이전 파이프의 내용을 읽을 수 있도록 PREV_PIPE_IN에 fd값을 저장한다.
    - `첫 번째 자식`은 `infile을 열고`, `현재 파이프`에 내용을 쓴다.
    - `중간 자식`은 `이전 파이프`에 내용을 읽어오고, `다음 자식`이 읽을 수 있게 `현재 파이프`에 내용을 쓴다.
    - `마지막 자식`은 `이전 파이프`에 내용을 읽어오고, `outfile`에 내용을 쓴다.

- [ ] Mandatory 코드 구현
	- [X] 기존에는 부모가 command를 파씽해서 가지고 있었지만, path만 파씽한 뒤, 자식에서 command를 파씽 후 execve로 메모리를 해제할 필요 없이 사라진다. (fork되는 메모리 크기도 커지지 않음)
	- [ ] leak test
- [ ] Bonus 코드 구현
	- [ ] 구현
	- [ ] leak test
	- [ ] 파일 생성, append 옵션 테스트, +infile여부

---
### 2022-10-10
- [X] 부모는 fork()만, 자식이 파일을 열고 처리하는 구조
- [X] 2가지 구조 가능
	- [ ] 1. 부모가 command갯수만큼 파이프를 열고 처리하는 구조.
		cf. https://stackoverflow.com/questions/8389033/implementation-of-multiple-pipes-in-c
		cf. http://www.cs.loyola.edu/~jglenn/702/S2005/Examples/dup2.html
	- [ ] 2. 부모가 파이프를 한 쌍을 열고, 자식에서 처리하는 구조. (현 구조랑 비슷한 이 구조로 진행하고 싶다)
	(다음 자식은 이전 자식이 파이프에 쓴 내용을 읽어올 수 있어야 하는데, 이 처리가 안됌)

---
### 2022-10-08
- [ ] 자식 구조이 파일을 읽고 dup하는 구조로 바꾸기
- [ ] here_doc이면 here_doc만 검사하기(뒤에 인자처리 로직은 필요 없다)
- [ ] 불필요한 부분 빼기

---
### 2022-10-07
- [X] pipex
	- [X] heredoc error 
		- [X] heredoc에 쓴 내용을 pipe에서 읽어오지 못한다.
			- [X] 파일 오프셋 수정(열고, 닫아주고 다시 열기)
	- [X] leaks error
	- [X] norm check
	- [X] error handling
		- [X] 서브젝트 보면서 다시 한번 점검해보고 평가받기.
- 현재 구조 문제점
	- [ ] bash 쉘에서는 앞에 인자가 잘못되었더라도, 파이프마다 병렬적으로 실행한다. 반면 내 구조는 앞에 인자가 잘못되었다면, 뒤에는 실행하지 않음.
	- [ ] 부모프로세스에서 dup2로 표준 입력과 출력을 막아두고 fork하기 때문에, 부모에서는 표준입출력을 쓸 수가 없다.
- 평가에서 틀린 부분
	- [X] infile이 없거나 infile에 읽기 권한이 없을 때 에러를 출력해야 한다.
	- [X] 나머지는 정상작동.
- `추가적인 의문`
	- [ ] 파이프 2쌍을 쓸 필요가 있을까?
	- [ ] 이전 자식은 다음 자식에게 stream을 보내기만 하지, stream을 다시 받지 않는다. 내 생각에 pipe는 1쌍이면 충분하다.
	
---
### 2022-10-06
- [ ] pipex
	- [X] heredoc구현
	- [X] Access error handling (실패해도 -1, 권한이 없을 때도 -1)
	- [ ] code review받기

---
### 2022-10-05
- [O] pipex
	- [X] fix segfault error
	- [X] list delete func
	- [ ] implement `heredoc`
	- [X] handling error
	- [X] check norm
	- [X] check leak
- 의문
	- [ ] acccess 시스템 콜, 예외처리(권한 없는 경우와 실패했을 때 return value가 -1로 같다)
- 알아가기 
	- [X] 자식 프로세스에서 동적할당 한 다음 execve로 하면, 당연하게도 leak이 아니다.
	- [X] list모든 원소 free할 때, 리스트를 담는 주소를 2차원으로 받아야 할 필요는 없다.

---
### 2022-10-04
- [X] for loop in fork에서 기본 로직과 pipex(execve)에서 동작하는 방식의 차이
- [X] pipex argv(cmd) parsing 처리하기
	- [X] argv를 ' '를 기준으로 split해서 list에 넣기.
	- [X] 리스트 만들기(prev를 쓸 이유는 없기 때문에 단방향 연결리스트
		- [X] insert함수
		- [ ] all delete함수
		- [X] iterator
- [X] path도 리스트로 만들 필요가 있을까?
	- [X] 지금 구조를 보면, 항상 PWD가 먼저나온다는 가정이 있어서 바꾸는 게 좋다.
- [X] `링크 추가하기`

```html
<div align = "right">
	<b><a href = "#Contents">🎈 contents</a></b>
</div>
[🎈리스트란](#리스트)
```
---
### 2022-10-03
- [ ] pipex argv(cmd) parsing
- [X] next_permutation(Permutation, Combination, 사용법, 구현 ..)
- [X] 운영체제에서 동적바인딩, C++ 가상함수의 동적 바인딩의 차이는 무엇인가?

---
### 2022-10-02
- [X] pipex argv parsing

---
### 2022-09-30
- [ ] 1. 메인보드에서 하드웨어들이 어디에 위치하고, 어떤 역할을 하는지 정리.
- [X] 2. pipex 로직(dup2, dup, , pipe)매끄럽게 설명해보기.
