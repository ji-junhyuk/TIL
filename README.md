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
