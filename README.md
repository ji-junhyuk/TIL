### 2022-10-07
- [ ] pipex
	- [ ] heredoc error 
	- [ ] 뭐가 됐든 평가보면서 평가지보기
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
