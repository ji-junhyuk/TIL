### 22.11.10
- algo
	- [ ] simultation 15683, review
- 42
	- [ ] Minishell
		- [ ] 
		- [ ] 문서화 계속
			- [ ] 날짜별 처리한 것들 정리.
	- [ ] FDF 컴파일 되게 하기
	- [ ] pipex 제대로 되게 하기
- network
	- [ ] 전송계층 5
	- [ ] 데이터 전송 단위
- kernel
	- [ ] thread_info 구조체 분석

### 22.11.09(수)
- algo
	- [X] simulation 15683
- 42
	- [X] Minishell
		- [X] 여태까지 한 거 정리하고, 앞으로 할 것들 문서화 틈틈이 계속! 
		- [X] execute, SIGPIPE 흐름 정리.
			- 구조 수정
				- yes | head -2 : 해당 케이스를 잡기 위해 마지막 command가 끝나기만을 기다림 -> wait(마지막 pid, 0);
				- 해당 로직을 -> 모든 커맨드가 끝날 때까지 기다림(case: sleep 3 | sleep 1)
					- 그렇다면, yes | head -2는 어떻게 처리하나?
						- yes를 SIGPIPE로 종료시킴. (reader를 모두 닫아주면, 해당 프로세스가 종료된다)
- network
	- [X] 전송계층 4
	- [X] 스위치가 하는 일이 무엇인지
- kernel
	- [X] threadinfo 구조체

### 22.11.08(화)
- java
	- [X] 우테코
- network
	- [X] 전송계층 3
	- [X] port번호
- kernel
	- [X] 프로세스 실행시각 정보
- raspberrypi bluetooth 연결, 해제, 제거 터미널에서 하기(오류 해결)
	 
### 22.11.07(월)
- algo
	- [ ] simul
- 42
	- [ ] Minishell study
		- [ ] 여태까지 한 거 문서로 예쁘게 정리(틈틈이)
		- [X] tokenize 구현
- network
	- [ ] 전송계층 3
	- [X] IP주소 체계
- java
	- [ ] 우테코 TDD 시작
- kernel 
  	- [X] 프로세스 간의 관계(연결리스트)
-  예외 처리
	- [X] bool is_pair_bracket(const char *line)
 	- [X] bool is_correct_pair(const char *line)
- [ ] 토큰화
- [ ] 환경변수 확장 (getenv, opendir, readdir)
- [ ] wait, waitpid, wait3, wait4
- [ ] getcwd, chdir
- [ ] stat, lstat, fstat
- [ ] opendir, readdir, closedir
- [ ] isatty, ttyname, ttyslot, ioctl
- [ ] getenv
- [ ] tcsetattr, tcgetattr, tgetent, tgetflag, tgetnum, tgetstr, togoto, tputs
		
// command shift e, spacebar
// f12 ctrl b
// control fn1 esc terminal 
23
### 22.11.06(일)
- [X] AWS CLOUD GAME
<img width="797" alt="Screen Shot 2022-11-06 at 3 35 00 PM" src="https://user-images.githubusercontent.com/67992469/200157851-6ac8ac47-1850-4690-bff1-f2024f077337.png">

- algo
	- [ ] simul
- network
	- [ ] 널널한 개발자 강의 2개 보기
		- [X] host, switch, network 관계
- java
	- [ ] 우테코 TDD시작
- kernel
	- [X] task 디스크립터, 프로세스 식별 코드

### 22.11.05(토)
- algo
	- [ ] simul
- network 
	- [X] 6강 전송계층
	- [ ] 널널한 개발자 강의 보기
- java
	- [ ] 우테코 코드 작성
- kernel 
	- [X] 커널 내부에서 프로세스 생성하는 흐름
	- [X] 프로세스가 종료되는 과정
	 
### 22.11.04(금)
- algo
	- [ ] simul
- 42
	- [X] token 구조체 
	- [X] tokenize 코드 작성 시작! 
- network
	- [ ] 6강 전송계층2
- java
	- [X] 우테코 README 정리
- kernel
	- [ ] 커널 내부에서 프로세스를 생성하는 흐름

### 22.11.03(목)
- algo
	- [X] simulation 문제 다시 시작!
- 42
	- [X] tree push, 순회 기본 메소드 구현
	- [X] tokenize 본격적으로 시작! 리스트에 담기
		- 괄호, 쿼트 로직 생각했음.
- network
	- [X] 5강 전송계층1
- java
	- [ ] 야구게임
- kernel
	- [X] 강의. 커널 스레드가 어떻게 생성할까? 

### 22.11.02(수)
- 42
	- [X] List
	- [X] Makefile
	- [X] tree 대략적인 구조
	- [ ] token struct
- network
	- [X] 4강. 애플리케이션 레이어 2
- kernel
	- [X] 커널스레드란, 커널스레드 종류
- ctrl shifh H : 한번에 바꾸기
- ctrl option 방향키
- option cmd 방향

### 22.11.01(화)
- 42
	- [X] 폴더구조
	- [X] read_line
