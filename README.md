### 2022-10-11
- [ ] 부모는 fork(), 자식이 파일을 열고 처리하는 구조
- [ ] 2가지 구조 가능
	- [ ] 1. 부모가 command갯수만큼 파이프를 열고 처리하는 구조.
		cf. https://stackoverflow.com/questions/8389033/implementation-of-multiple-pipes-in-c
		cf. http://www.cs.loyola.edu/~jglenn/702/S2005/Examples/dup2.html
	- [ ] 2. 부모가 파이프를 한 쌍을 열고, 자식에서 처리하는 구조. (현 구조랑 비슷한 이 구조로 진행하고 싶다)
	(다음 자식은 이전 자식이 파이프에 쓴 내용을 읽어올 수 있어야 하는데, 이 처리가 안됌)
```c
int main(int argc, char *argv[])
{
	pid_t pid;
	char *exec_argv[] = {"ls", "-al", 0};
	char *exec_argv2[] = {"grep", "hello", 0};
	int fdin;
	int fdout;

	int cnt = -1;
	int fdpipe[2];
	while (++cnt < 2)
	{
		printf("parent: helloda\n");
		if (cnt == 1)
			fdout = open("outfile", O_CREAT | O_WRONLY | O_APPEND, 00666);
		else
			pipe(fdpipe);
		pid = fork();
		if (pid == 0)
		{
			if (cnt == 0)
			{
				fdin = open("infile", O_WRONLY, 00666);
				dup2(fdpipe[0], 0);
				close(fdpipe[0]);
				dup2(fdpipe[1], 1);
				close(fdpipe[1]);
				execve("/usr/bin/grep", exec_argv2, 0);
			}
			if (cnt == 1)
			{
			/*
				이전 파이프에 쓴 내용을 읽어오고,
				현재 파이프에 새로운 내용을 쓴다.
				(다음 파이프는 현재 파이프에 새로운 내용을 읽어와야됌)
			*/
				dup2(fdpipe[0], 0); // 이렇게 하면 입력을 전 파이프에서 받아오지 못한다. 그림 그려보면 알 수 있을듯?
				dup2(fdout, 1);
				execve("/usr/bin/grep", exec_argv2, 0);
			}
		}
	}
	waitpid(pid, NULL, 0);
}
```

### 2022-10-08
- [ ] 자식 구조이 파일을 읽고 dup하는 구조로 바꾸기
- [ ] here_doc이면 here_doc만 검사하기(뒤에 인자처리 로직은 필요 없다)
- [ ] 불필요한 부분 빼기

### 2022-10-07
- [O] pipex
	- [X] heredoc error 
	- [X] leaks error
	- [X] norm check
	- [X] error handling
		- [X] 서브젝트 보면서 다시 한번 점검해보고 평가받기.
```c
./pipex infile cmd cmd1 outfile
```

```bash
처음에는 부모에서 파씽을 한 뒤, 인자가 적합하지 않은 게 있다면 
아예 실행되지 않는 로직이 맞다고 생각했다. 
실제 bash에서는 먼저 나온 인자가 적합하지 않아도 뒤에 인자를 실행한다.

$ ls < infile | wc -l
- infile이 없는 경우 zsh: no such file or directory: infile
$ cmv < infile | wc -l
- infile이 없는 경우: zsh: no such file or directory: infile
       								0 
- infile이 있는 경우: zsh: command not found: cmv
									0
$ cmv < infile | wd | ls
- zsh: no such file or directory: infile
- zsh: command not found: wd 
- ls결과
```
- `실제 shell에서는 infile이 없으면 error를 출력하는 건 같지만, 뒤에 명령어도 실행`한다. 즉, infile에서 파일을 여는 작업부터 자식프로세스에서 하게 된다.
- 현재 구조에서는 부모 프로세스에서 path, cmd parsing을 해둔 후에 파일을 연다. 파일이 존재하지 않을 경우 바로 exit한다.
	- `부모 프로세스에서 다 parsing을 할 필요가 있을까?` 부모프로세스가 무거우면 execve로 더 크게 메모리를 복사한다. 부모는 모든 자식에게 필요한 만큼만 제공하고, 나머지는 자식 쪽에서 처리하는 것이 낫다.
	- 부모가 모든 걸 parsing하고 fork를 진행하면, 메모리는 커지지만 시간은 빠르다. 부모에서 자식에게 필요한 명령어를 mapping 시킬 수 있으면 trade-off아닐까? 근데, 파이프가 여러개 들어오고 계속해서 fork를 한다고 생각하면, 부모는 최대한 가볍게 가져가는 것이 옳다.
	 
```c
fork();
1. 첫번째 자식에서 파일을 연다. (infile -> CMD)
2. 나머지 자식 -> 부모가 PATH해둔 결과를 가지고 본인의 CMD가 적합한지 찾는다. 적합하다면 실행, 아니라면 Error.
3. 가장 끝에 자식은 파일을 연다. (CMD -> outfile)
4. 부모프로세스는 가장 끝에 자식만 기다린다.
```
 
- `추가적인 의문`
	- 파이프 2쌍을 쓸 필요가 있을까?
	- 이전 자식은 다음 자식에게 stream을 보내기만 하지, stream을 다시 받지 않는다. 내 생각에 pipe는 1쌍이면 충분하다.
	
- 평가에서 틀린 부분
	- infile이 없거나 infile에 읽기 권한이 없을 때 에러를 출력해야 한다.
	- 나머지는 정상작동.
```c
pipe_tool->fdin = open(argv[1], O_RDWR, 00666);
pipe_tool->fdin = open(argv[1], O_RDONLY);
```

- 문제 해결
```c
heredoc의 입력을 pipe자식이 읽어오는 구조인데,
heredoc이라는 임시 파일에 쓰고 다시 닫지 않는다면,
offset이 처음 위치가 아닌, 끝에 위치해 있다.
그래서 파일에는 써지지만, 
pipe자식은 읽어올 데이터가 없다.
heredoc에 쓰고 나서, 닫고 다시 열어주면
오프셋이 다시 처음 위치로 가서 간단히 해결된다.
```

```c
heredoc이라는 임시 파일에는 쓰여지는데,
pipe 자식 프로세스가 이를 읽어오질 못한다.
그런데, 종료 후 다시 시작해서 heredoc을 작동해주기만 하면
이전 프로세스에서 실행했던 게 그제서야 outfile에 담긴다.
write가 쓰기는 하지만, 이를 실제로 파일에 쓰는 건
뒤로 미루기 때문에 이를 grep해서 잡히는 게 없는 거 같기도 하고,
잘 모르겠다.
```


### 2022-10-06
- [ ] pipex
	- [X] heredoc
	- [X] Access error handling (실패해도 -1, 권한이 없을 때도 -1)
	- [ ] code review받기

### 2022-10-05
- [O] pipex
	- [X] fix segfault error
	- [X] list delete func
	- [ ] implement `heredoc`
	- [X] handling error
	- [X] check norm
	- [X] check leak
- 의문
```c
while (--p_count >= 0)
{
	all_path = ft_strjoin(p_node->path, c_node->cmd[0]);
	if (access(all_path, F_OK) == 0)
	{
		free(all_path);
		return (0);
	}
	free(all_path);
	p_node = p_node->next;
}
```
	- access시스템 콜 실패했을 때 예외처리를 하려면 어떻게 해야할까? access함수는 권한 여부를 체크할 때 해당 권한이 없으면 -1을 리턴한다. access함수가 실패할 때도 -1을 리턴한다. 이 경우 실패할 때 예외처리를 못하는거 아닌가?
	 
- 신기했던 것
	- pipe_tool->cmd 동적할당한 것을 execve로 하면 leak이 아니다. leak이 아닌가 순간 당황.
```c
pipe_tool->cmd = get_cmd(path_list, cmd_list, pipe_tool->i - 2);
if (execve(pipe_tool->cmd, pipe_tool->c_node->cmd, 0) == -1)
{
	perror("execve");
	exit(1);
}
```
- 헷갈렸던 것
	- list모든 원소 free할 때, list를 2차원으로 해야하는 지
		 - 그럴 필요 없음.

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
- [X] 링크 추가하기
```html
<div align = "right">
	<b><a href = "#Contents">🎈 contents</a></b>
</div>
[🎈리스트란](#리스트)
```
```c
norminette규정으로 함수를 쪼개다가
현재 segfault오류가 뜬다. 
내일 고쳐야함.
구체적으로 예외처리, 디테일, 설명부분도 신경쓰기.
```
 
------
### 2022-10-03
- [ ] pipex argv(cmd) parsing
- [X] next_permutation(Permutation, Combination, 사용법, 구현 ..)
- [X] 운영체제에서 동적바인딩, C++ 가상함수의 동적 바인딩의 차이는 무엇인가?

### 2022-10-02
- [X] pipex argv parsing

### 2022-09-30
- [ ] 1. 메인보드에서 하드웨어들이 어디에 위치하고, 어떤 역할을 하는지 정리.
- [X] 2. pipex 로직(dup2, dup, , pipe)매끄럽게 설명해보기.
