# Day 3

GBC 첫번째 과정 **Programmer Base** 의 3일차 내용입니다.

---

# 리눅스 교재

교재에서 다음 분량을 읽고 우분투 도커 컨테이너에서 실습해주세요. 사실 너무 열심히 읽지 않아도 됩니다. 즉, 막 외우려고 애쓰지 않아도 된다는 뜻입니다. 다만 꼭 "정독" 을 하시고 한번쯤 책에 있는 실습을 따라해주세요. 

**(옵션)** 라고 되어있는 파트는 시간절약을 위해 넘겨도 됩니다.

## Chapter 05

- **244p ~ 252p 읽고 실습하기**

  - 파일의 속성, 파일의 접근 권한, 기호를 이용한 파일 접근 권한 변경

- **254p ~ 257p 읽고 실습하기**

  - 숫자를 이용한 파일 접근 권한 변경

- **260p ~ 267p 읽고 실습하기**

  - **(옵션)** 기본 접근 권한 설정, 특수 접근 권한

---

# vim

## 텍스트 편집에서 단축키 개수와 입력 횟수의 관계

텍스트 편집이란 **커서 이동**과 **텍스트 수정**입니다. 

### 일반 텍스트 에디터의 단축키 개수와 입력 회수

기존의 일반 텍스트 에디터로는 단순히 <kbd>&larr;</kbd>, <kbd>&rarr;</kbd>, <kbd>&uarr;</kbd>, <kbd>&darr;</kbd> 와 마우스 스크롤로 **커서 이동**을 했었고, 단순한 텍스트 입력과 <kbd>Backspace</kbd> 나 <kbd>Delete</kbd> 로 **텍스트 수정**을 했었습니다. 이 몇 안되는 단축키로써 모든 상황에서의 **커서 이동**과 **텍스트 수정**을 할 수 있었지만, 몇 안되는 단축키를 모든 상황에 적용하려다 보니까 조합이 복잡해지고 키보드 입력을 많이 해야만 했습니다. 

이 방식의 장점은 외워야 하는 단축키가 <kbd>&larr;</kbd>, <kbd>&rarr;</kbd>, <kbd>&uarr;</kbd>, <kbd>&darr;</kbd>, <kbd>Backspace</kbd>, <kbd>Delete</kbd> 등으로 매우 적다는 것입니다. 하지만 단점은 단축키가 적으니까 다양한 상황에서의 텍스트 편집(**커서 이동**, **텍스트 수정**) 에 적용되는 조합이 매우 복잡해진다는 것입니다.

### `vim` 의 단축키 개수와 입력 회수

| | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
|단축키 개수 | 적음 | 많음 | 
|입력 회수 | 많음 | 적음 | 

하지만 `vim` 은 단축키가 **매우 많아서** 다양한 상황에 적용되는 단축키의 조합이 단순해집니다. 그래서 `vim` 을 사용하면 코딩할 때 키보드를 치는 횟수가 압도적으로 줄어듭니다. 다음 그래프와 같이 단축키 개수가 많으면 익혀야 할 단축키가 많은 대신 입력 회수가 줄어들고, 단축키 개수가 적으면 입력 회수가 많아집니다!

<div align="center">
<img src="https://user-images.githubusercontent.com/16812446/81026898-b16b1b00-8eb6-11ea-89fa-3503770b57d4.png" width="50%" height="auto">
</div>

이것은 단조로운 단어를 쓰면 문장의 길이가 길어지고 다양한 단어를 쓰면 문장이 짧아지는 것과 같은 이치입니다. 

> 게다가 `vim` 에 익숙해지면 텍스트 편집을 할 때 마우스를 사용해야 하는 횟수가 `0` 에 수렴합니다. 키보드와 마우스의 거리는 생각보다 멀기 때문에 이로써 발생하는 시간절약 효과도 상당합니다. 

> 개인적으로 개발자로 살아간다면 `vim` 텍스트 에디터 사용법을 익혀서 불필요한 타자 횟수를 최대한 절약함으로써 시간낭비를 줄이고, 손목건강도 챙기는 것이 합리적이라고 생각합니다. 불필요한 시간이 절약된다면 남는 시간이 많아집니다. 

## `vim` 으로 일반 텍스트 에디터 대체하기

> 참고 : https://github.com/vim/vim/blob/master/runtime/tutor/tutor.ko.utf-8

이제부터 `vim` 을 사용하면 타수가 얼마나 줄어드는지 보여드림으로써 `vim` 을 사용하면 좋다는 것을 설득해드리겠습니다. 설득 안되면 어쩔 수 없지만..

보여드리는 방식은 기존 일반 에디터의 **적은 단축키가 얼마나 많은 타수를 야기하는지**, 그리고 그것이 **`vim` 에서 어떻게 효율적으로 대체될 수 있는지** 비교하는 것으로 하겠습니다. 

> 또한 모든 키보드에 <kbd>Home</kbd>, <kbd>End</kbd>, <kbd>Insert</kbd>, <kbd>PageDown</kbd>, <kbd>PageUp</kbd> 가 있지 않기 때문에 일관성을 위하여 이 키들은 상정하지 않겠습니다.

그리고 문자와 문자 사이의 커서 이동 횟수가 **1번** 이기 때문에 

|이동 거리|퉁 치는 횟수|
|:---|:---|
|커서가 (문자가 모여있는) 단어를 이동하는 횟수 | **n 번** |
|커서가 (단어가 모여있는) 문장을 이동하는 횟수 | **n<sup>2</sup> 번**| 
|커서가 (문장이 모여있는) 전체파일을 이동하는 횟수 | **n<sup>3</sup> 번**|

 이라고 하겠습니다.

그러면 먼저 우분투 도커 컨테이너에 접속하셔서 다음 명령어를 입력하세요.

##### **<div align="center"> ⬇ EXECUTE! ⬇ </div>**  

```shell
$ cd
$ git clone https://github.com/jaseg/lolcat
$ cd lolcat
$ make
```

`lolcat` 은 `cat` 명령어의 출력에 무지개 색깔을 입힙니다. 다음 명령어를 실행해보세요.

##### **<div align="center"> ⬇ EXECUTE! ⬇ </div>**

```shell
$ cat /etc/passwd     # 텍스트 파일이 밋밋한 색깔로 출력된다. 
$ ./lolcat /etc/passwd 
```

실행결과는 다음 그림과 비슷할 겁니다. 

<div align="center">
<img src="https://user-images.githubusercontent.com/16812446/81272615-a7007b00-9088-11ea-9e2b-bb8ce711ad6b.png" width="85%" height="auto">
</div>

다음과 같이 `ps -ef` 명령어로 실행중인 모든 프로세스 목록을 출력하는 것에 색깔을 입힐 수도 있습니다. 

##### **<div align="center"> ⬇ EXECUTE! ⬇ </div>**

```shell
$ ps -ef            # 밋밋한 색깔로 출력된다. 
$ ps -ef | ./lolcat
```

이제 `lolcat` 의 소스코드 `lolcat.c` 를 `vim` 으로 열어봅시다.

##### **<div align="center"> ⬇ EXECUTE! ⬇ </div>**

```shell
$ vim lolcat.c
```

그러면 `vim` 텍스트 에디터로 파일이 열리는데 일단 `100gg` 를 눌러보세요. 그러면 파일의 `100` 번째 행으로 이동하게 되고 성공적으로 이동하셨다면 

```c shell
...
int main(int argc, char** argv)
{
    char* default_argv[] = { "-" };
    int cc = -1, i, l = 0;
    wint_t c;
    int colors    = isatty(STDOUT_FILENO);
    int force_locale = 1;
    int random = 0;
    double freq_h = 0.23, freq_v = 0.1;

    struct timeval tv;
    gettimeofday(&tv, NULL);
    double offx = (tv.tv_sec % 300) / 300.0;

    for (i = 1; i < argc; i++) {
...
```

위와 같은 코드가 보일 것입니다. 이제 특별한 언급이 없는 한 이 `100` 번째 줄에서 실습을 진행하겠습니다. 커서가 `100` 행에서 이탈되었다면 다시 `100gg` 를 누르면 `100` 번째 행으로 이동할 수 있습니다. 

### 기본 커서 이동

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 왼쪽 이동 | <kbd>&larr;</kbd> | `h` | 
| 오른쪽 이동 | <kbd>&rarr;</kbd> | `l` | 
| 위쪽 이동 | <kbd>&uarr;</kbd>| `k` | 
| 아래쪽 이동 | <kbd>&darr;</kbd>| `j` | 

- 실습 

  위 단축키로 커서를 이동해보세요. 

  `15k` 를 눌러 `15` 줄 위에 있는 행으로 이동하세요. 

  다시 `15j` 를 눌러 되돌아올 수 있습니다. 

  이렇게 `<N>k` 를 누르면 `<N>` 번 위로 갑니다. 다른 커서 이동 키도 마찬가지!

### 기능 반복 

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 이전에 실행한 기능 반복하기 |  | `.` | 

`.` 를 누르면 이전에 실행한 기능이 반복됩니다. 

### 입력하기

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 입력하기 | | `i` | 
| 다음 글자에 입력하기 | <kbd>&rarr;</kbd> | `a` | 
| 다음 행에 입력하기 | <kbd>&rarr;</kbd> × **n<sup>2</sup>** + <kbd>Enter</kbd> | `o` | 
| 이전 행에 입력하기 | <kbd>&uarr;</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** + <kbd>Enter</kbd> | `O` | 
| 문장 마지막에 입력하기 | <kbd>&rarr;</kbd> × **n<sup>2</sup>** | `A` | 
| 문장 처음에 입력하기 | <kbd>&larr;</kbd> × **n<sup>2</sup>** | `I` | 

일반 텍스트 에디터가 **입력 모드** 만 있는 반면 `vim` 은 **입력 모드** 와 **명령 모드** 가 있습니다. `vim` 을 처음 켰을 때는 항상 **명령 모드** 이고 위 표의 입력 단축키 `i`, `a`, `o`, `O`, `A`, `I` 를 입력하면 **입력 모드** 가 됩니다. 

> 에디터의 하단에 **`-- INSERT --`** 라는 상태표시가 보이면 지금이 **입력 모드** 인 것입니다. 

**입력 모드** 에서는 모든 키보드 입력이 단축키가 아닌 입력으로 취급되기 때문에 **명령 모드** 로 되돌아가려면 <kbd>Esc</kbd> 를 누르면 됩니다.

- 실습 

  단축키를 눌러서 **입력 모드**로 들어간 다음

  ```c
  int test_int = 200;
  ```

  이라는 코드를 입력하고 <kbd>Esc</kbd> 를 눌러 **명령 모드** 로 되돌아오세요. 

  입력모드로 들어갈 수 있는 단축키 `i`, `a`, `o`, `O`, `A`, `I` 들을 실행하고 결과가 어떤지 보세요. 

- 실습 

  ![Peek 2020-05-07 20-15](https://user-images.githubusercontent.com/16812446/81288404-8a237200-909f-11ea-8b4d-121b5527b058.gif)

  위와 같이 `94` 행으로 이동하고 `I` 로 입력모드에 들어간 후 주석처리 `//` 를 입력해보세요.
  
  그리고 밑으로 이동해서 기능반복키 `.` 를 누르며 입력을 반복해보세요.

### 에디터 종료

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 저장 | <kbd>Ctrl</kbd> + <kbd>s</kbd> | `:w` | 
| 종료 | <kbd>Alt</kbd> + <kbd>F4</kbd> | `:q` | 
| 저장 후 종료 | <kbd>Ctrl</kbd> + <kbd>s</kbd> 🠲 <kbd>Alt</kbd> + <kbd>F4</kbd>| `:wq` 또는 `ZZ` |<kbd>Alt</kbd> + <kbd>F4</kbd> 
| 강제 종료 |  | `:q!` | 
| 다른 이름(`<NAME>`)으로 저장 |  | `:w <NAME>` | 

`vim` 에서 저장과 종료 단축키입니다. 강제 종료는 저장하지 않은 내용을 사라지게 합니다.

- 실습 

  단축키들을 실행해서 에디터를 종료해보고 다시 `vim lolcat.c` 로 켜서 `100gg` 를 눌러 `100` 번째 행으로 되돌아오세요. 

### 지우기 

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 지우기 | <kbd>Backspace</kbd> 또는 <kbd>Delete</kbd> | `x` | 
| 단어 지우기 | <kbd>Backspace</kbd> × **n** | `dw` | 
| 문장 지우기 | <kbd>Backspace</kbd> × **n<sup>2</sup>** | `dd` | 
| 커서로부터 문장 끝까지 지우기 | <kbd>Delete</kbd> × **n<sup>2</sup>** | `D` | 

- 실습 

  커서를 `102` 번째 행인

  ```c
  struct timeval tv;
  ```

  로 옮기세요. 이제 `x` 를 눌러서 문자들을 지워보세요.

  이때 `2x` 와 `3x` 를 누르면 각각 `2` 글자, `3` 글자가 지워진다는 것을 확인하세요.

  `<N>x` 를 누르면 `<N>` 개의 문자가 한번에 지워집니다. 

- 실습

  단어를 한번에 지우기 위해서 `dw` 를 눌러도 됩니다. 이것도 `struct` 나 `timeval` 같은 변수 위로 커서를 두고 실행해보세요. `4dw` 를 누르면 `4` 개의 단어가 `3` 회의 입력만에 한번에 지워집니다. 

  > 일반 텍스트 에디터에서 `4` 개의 단어를 지우려면 `3` 회보다 훨씬 많은 키보드 입력이 필요합니다.

  `4dw` 를 누르고 `.` 을 누르면 `4` 개의 단어가 지워지는 기능이 반복됩니다. `3` 회만 누르면 그 다음부터는 `.` 만 누르면 되니까 `1` 회만 누르면 됩니다.

- 실습

  `dd` 와 `D` 도 커서를 움직여서 다른 곳에서 실행보세요. `5dd` 를 누르면 `5` 개의 문장이 `3` 회의 입력만에 한번에 지워집니다. 

  > 일반 텍스트 에디터에서 `5` 개의 문장을 지우려면 `3` 회보다 훨씬 많은 키보드 입력이 필요합니다.

  ![Peek 2020-05-07 20-20](https://user-images.githubusercontent.com/16812446/81288724-28173c80-90a0-11ea-81fe-4186fe10676d.gif)

  마찬가지로 위와 같이 `10dd` 누르고 `.` 를 누르면 `10` 개 문장이 지워지는 기능이 반복됩니다. `4` 회 입력 이후에 `1` 회 입력만 하면 되는 것이죠. 

### 지우고 편집하기

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 한 글자 지우고 편집하기 | <kbd>Backspace</kbd> | `r` | 
| 단어 지우고 편집하기 | <kbd>Backspace</kbd> × **n** | `cw` | 
| 커서로부터 문장 끝까지 지우고 편집하기 | <kbd>Delete</kbd> × **n<sup>2</sup>** | `C` | 
| 문장에서 `<OLD>` 를 `<NEW>` 로 치환하기 |  | `:s/<OLD>/<NEW>` | 
| 전체 파일에서 `<OLD>` 를 `<NEW>` 로 치환하기 |  | `:s/<OLD>/<NEW>/g` | 
| 전체 파일에서 하나씩 확인하면서 `<OLD>` 를 `<NEW>` 로 치환하기 |  | `:s/<OLD>/<NEW>/gc` | 

- 실습 

  커서를 `98` 번째 행인 

  ```c
  int force_locale = 1;
  ```

  의 `1` 로 옮겨서 `r` 을 누르고 `0` 을 눌러보세요. 그러면 `1` 이 `0` 으로 바뀝니다. 

- 실습 

  커서를 다른 코드로 옮겨서 `cw` 와 `C` 를 실행해보세요. 그러면 단어가 지워지고 **입력 모드** 로 곧장 들어갑니다. **명령 모드** 로 되돌아오기 위하여 <kbd>Esc</kbd> 를 눌러야 합니다. 

- 실습 

  `:s/int/long long/g` 을 실행해보세요. 파일 전체의 `int` 가 `long long` 으로 바뀝니다. 

### 화면 내의 커서 이동 

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 원하는 문자로 이동 | <kbd>&rarr;</kbd> × **n<sup>2</sup>** | `f<C>` | 
| 오른쪽 단어로 이동 | <kbd>Ctrl</kbd> + <kbd>&rarr;</kbd> | `e` | 
| 왼쪽 단어로 이동 | <kbd>Ctrl</kbd> + <kbd>&larr;</kbd> | `b` | 
| 문장의 처음으로 이동 | <kbd>Ctrl</kbd> + <kbd>&larr;</kbd> × **n**  | `0` | 
| 문장의 마지막으로 이동 | <kbd>Ctrl</kbd> + <kbd>&rarr;</kbd> × **n**  | `$` | 
| 화면의 처음으로 이동 | <kbd>&uarr;</kbd> × **n<sup>3</sup>**  | `H` | 
| 화면의 가운데로 이동 |  | `M` | 
| 화면의 마지막으로 이동 | <kbd>&darr;</kbd> × **n<sup>3</sup>**  | `L` | 

커서 이동이 `h`, `j`, `k`, `l` 밖에 없다면 커서를 이동해야 하는 다양한 상황에서 이것들을 똑같이 다양하게 조합해야하기 때문에 일반 텍스트 에디터의 <kbd>&larr;</kbd>, <kbd>&rarr;</kbd>, <kbd>&uarr;</kbd>, <kbd>&darr;</kbd> 를 많이 입력해야 하는 것과 다를 것이 없을 겁니다.

하지만 위 표에서처럼 다양한 커서 이동이 하나의 단축키로 가능합니다. 

- 실습 

  `104` 행으로 이동하면 

  ```c
  double offx = (tv.tv_sec % 300) / 300.0;
  ```

  라는 코드가 있는데 `300` 이라는 숫자를 조작하고 싶다면 `f3` 를 누르면 `3` 이라는 문자로 커서가 바로 이동됩니다. 

  마찬가지로 `f%` 를 누르면 `%` 라는 문자로 커서가 바로 이동됩니다.

- 실습 

  ![Peek 2020-05-07 20-22](https://user-images.githubusercontent.com/16812446/81288924-7c222100-90a0-11ea-98ab-aacd88046007.gif)

  위와 같이 커서 이동 단축키를 눌러보면서 실습해보세요.

  > 일반 방향키를 엄청 많이 눌러야 갈 수 있는 곳을 `vim` 에서는 단축키 하나만 누르면 갈 수 있습니다. 

### 취소

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 취소 | <kbd>Ctrl</kbd> + <kbd>z</kbd> | `u` | 
| 취소한 것을 취소 |  | <kbd>Ctrl</kbd> + <kbd>R</kbd> | 
| 문장을 원래대로 복원 | | `U` | 

- 실습 

  `50dd` 를 눌러서 문장 `50` 개를 `4` 회의 입력만에 삭제해보세요. 

  > 일반 텍스트 에디어테서 문장 `50` 개를 삭제하기 위해서 얼마나 많은 시간이 걸리는지 상상이 안되네요. 

  그리고 `u` 를 눌러서 삭제했던 것을 복구해보세요. 

  그리고 다시 <kbd>Ctrl</kbd>+<kbd>R</kbd> 을 눌러서 삭제해보세요. 

  `u` 와 <kbd>Ctrl</kbd>+<kbd>R</kbd> 를 번갈아서 계속 눌러보세요. 

### 드래그 

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 드래그 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n** | `v` | 

- 실습 

  `gg` 를 누르면 첫행으로 이동합니다. 바로 밑에 있는 `3` 번째 행으로 커서를 이동하면 

  ```shell
   * DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
  ```

  이라는 라이센스가 보입니다. 이 소스코드를 갖고 하고싶은 게 뭐든간에 다 하라는 의미군요. `e` 또는 `b` 를 몇번 눌러서 `FUCK` 의 `F` 로 커서를 이동하세요.

  `v` 를 누르고 `l` 을 몇번 누르면 `FUCK` 이 드래그됩니다. 잘 드래그 되고 있다면 `vim` 의 하단부에 `-- VISUAL --` 이라는 상태줄이 뜹니다.

  그러면 `r` 을 누르고 `x` 를 누르세요. 그러면 `FUCK` 이 `xxxx` 로 바뀝니다. 

  이렇게 드래그를 잘 활용하면 여러 문자와 문장에 대하여 기능을 한번에 실행할 수 있습니다. 

- 실습 

  다시 `FUCK` 이 있는 곳으로 커서를 옮겨서 `v` 를 누르고 이번에는 `e` 를 한번만 누르세요. 그러면 `FUCK` 이 단지 `2` 회의 입력만에 드래그됩니다. 

  `v` 를 누르고 `e` 를 계속 누르거나 `j` 를 눌러서 밑에 문장까지 드래그하고 `x` 를 눌러서 삭제해보세요. 

  > 드래그를 하기 위해서 일반 텍스트 에디터에서는 <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n** 를 얼마나 많이 눌러야 하는지 모르겠네요. 

### 복사하기

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 단어 복사하기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n** 🠲 <kbd>Ctrl</kbd> + <kbd>c</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `yw` 🠲  `p` | 
| 문장 복사하기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** 🠲 <kbd>Ctrl</kbd> + <kbd>c</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `yy` 🠲  `p` | 
| 드래그해서 복사하기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** 🠲 <kbd>Ctrl</kbd> + <kbd>c</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `v` 🠲 `y` 🠲 `p` | 

- 실습 

  `33gg` 를 눌러서 `33` 행으로 가면 

  ```c
  ...
  static char helpstr[] = "\n"
                          "Usage: lolcat [-h horizontal_speed] [-v vertical_speed] [--] [FILES...]\n"
                          "\n"
  ...
  ```

  가 보이는데 `yy` 를 누르고 `5p` 를 누르세요. 그러면 복사된 문장이 `5` 번 붙혀넣어집니다. 

- 실습 

  `55` 번째 행으로 이동하고 맨 마지막 "`, 33`" 을 `v` 로 드래그하고 `y` 를 눌러보세요. 그 다음 `33` 오른쪽으로 커서를 옮겨서 `p` 를 몇번 눌러보고 `10p` 를 누르세요. 

  ![Peek 2020-05-07 19-19](https://user-images.githubusercontent.com/16812446/81283458-a3c0bb80-9097-11ea-806d-093450a922e2.gif)

  그러면 위와 같이 복사된 것이 단번에 `10` 번 붙혀넣어집니다. 

  > 이 일을 일반 텍스트 에디터로 하려면 `vim` 보다 훨씬 많은 키보드 입력을 해야 합니다. 

### 잘라내기

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 한 글자 잘라내기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>x</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `x` 🠲  `p` | 
| 단어 잘라내기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n** 🠲 <kbd>Ctrl</kbd> + <kbd>x</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `dw` 🠲  `p` | 
| 문장 잘라내기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** 🠲 <kbd>Ctrl</kbd> + <kbd>x</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `dd` 🠲  `p` | 
| 특정 영역 잘라내기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** 🠲 <kbd>Ctrl</kbd> + <kbd>x</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `v` 🠲 `x` 🠲 `p` | 

- 실습 

  ![Peek 2020-05-07 20-29](https://user-images.githubusercontent.com/16812446/81289495-7a0c9200-90a1-11ea-82b7-1ca5706bf7f5.gif)

  `75` 행으로 이동하고 `6dd` 를 로 함수 코드 전체를 잘라내고 `10j` 로 커서 이동을 한 후 `p` 를 눌러 붙혀넣으세요. 
  
  > 이 작업을 키보드 입력 `10` 번으로 끝냈습니다. 


### 화면 밖으로의 커서 이동 

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 파일의 맨 마지막으로 이동 | <kbd>&darr;</kbd> × **n<sup>3</sup>** | `G` | 
| 파일의 맨 처음으로 이동 | <kbd>&uarr;</kbd> × **n<sup>3</sup>** | `gg` | 
| `<N>` 번째 행으로 이동 | <kbd>&uarr;</kbd> × **n<sup>3</sup>** 또는 <kbd>&darr;</kbd> × **n<sup>3</sup>** | `<N>gg` | 

- 실습 

  `G` 와 `gg` 로 커서를 이동해보세요. 그리고 `100gg` 로 `100` 번째 행으로 이동해보세요. 

### 찾기

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 아랫방향으로 찾기 | <kbd>Ctrl</kbd> + <kbd>f</kbd> | `/` | 
| 윗방향으로 찾기 |  | `?` | 
| 커서가 위치한 단어 아랫방향으로 찾기 |  | `*` | 
| 커서가 위치한 단어 윗방향으로 찾기 |  | `#` | 
| 찾고나서 같은방향으로 단어 찾기 | <kbd>Enter</kbd> | `N` | 
| 찾고나서 반대방향으로 단어 찾기 | <kbd>Shift</kbd> + <kbd>Enter</kbd> | `n` | 
| 괄호의 짝 찾기 |  | `%` | 

- 실습 

  ![Peek 2020-05-07 20-35](https://user-images.githubusercontent.com/16812446/81290019-48e09180-90a2-11ea-9f59-0f361090e0e8.gif)

  위와 같이 `/static` 으로 `static` 키워드를 찾고 `n` 을 누르며 다음 것을 찾아보세요. 


### 화면 이동

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 화면을 한 행만큼 아래로 이동 | <kbd>&darr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `e` | 
| 화면을 한 행만큼 위로 이동 | <kbd>&uarr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `y` | 
| 화면을 반 페이지만큼 아래로 이동 | <kbd>&darr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `d` | 
| 화면을 반 페이지만큼 위로 이동 | <kbd>&uarr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `u` | 
| 화면을 한 페이지만큼 아래로 이동 | <kbd>&darr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `f` | 
| 화면을 한 페이지만큼 위로 이동 | <kbd>&uarr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `b` | 

- 실습 

  위 단축키로 화면을 편하게 이동해보세요. 

### 커서를 기준으로 화면 이동

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 커서를 기준으로 화면을 최대한 아래로 이동 |  | `zt` | 
| 커서를 기준으로 화면을 최대한 위로 이동 |  | `zb` | 
| 커서를 기준으로 화면을 정중앙으로 이동 |  | `zz` | 

- 실습 

  ![Peek 2020-05-07 20-38](https://user-images.githubusercontent.com/16812446/81290241-ae348280-90a2-11ea-8ece-3b54397ba5f0.gif)

  위와 같이 `zt` 을 누르고 `L` 을 반복해서 눌러서 커서를 아래로 이동하다가 원하는 코드를 찾으면 `zz` 로 화면을 포커싱 해보세요. 

- 실습 

  반대로 `zb` 을 누르고 `H` 을 반복해서 눌러서 커서를 위로 이동하다가 원하는 코드를 찾으면 `zz` 로 화면을 포커싱 해보세요. 

  물론 화면을 위 아래로 이동하기 위하여 <kbd>Ctrl</kbd>+<kbd>d</kbd> 또는 <kbd>Ctrl</kbd>+<kbd>u</kbd> 가 더 편할 수도 있습니다. 

### 명령 실행 

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 파일 위치에서 `<CMD>` 명령 실행 |  | `:!` + `<CMD>` | 
| 파일 위치에서 쉘 실행 |  | `:shell` | 

- 실습 

  ![Peek 2020-05-07 20-41](https://user-images.githubusercontent.com/16812446/81290520-2f8c1500-90a3-11ea-858b-da89bb26b571.gif)

  위와 같이 `:!pwd` 를 입력해보세요. 

- 실습 

  `:shell` 을 입력해서 `vim` 의 서브 프로세스로써 쉘을 실행시켜보세요. `vim` 으로 되돌아오기 위해 `exit` 명령어로 쉘을 종료하면 됩니다. 
  
  `vim` 밑에서 쉘을 실행했다는 것을 잊어버리고 그 쉘에서 계속 작업을 하면 안되요! 현재 쉘이 `vim` 의 서브 프로세스인지 확인하는 방법은 `ps` 명령어를 입력하는 것입니다.
  
  현재 쉘이 `vim` 의  서브 프로세스도 아니라면 `ps` 명령 결과는 다음과 같습니다. 

  ##### **<div align="center"> ⬇ EXECUTE! ⬇ </div>**

  ```shell
  $ ps
    PID TTY          TIME CMD
      1 pts/0    00:00:00 bash
    960 pts/0    00:00:00 ps
  ```

  먄약 현재 쉘이 `vim` 의 서브 프로세스라면 `ps` 명령어 결과가 다음과 같이 출력됩니다. 

  ```shell
  $ ps
    PID TTY          TIME CMD
      1 pts/0    00:00:00 bash
    961 pts/0    00:00:00 vim
    962 pts/0    00:00:00 sh
    963 pts/0    00:00:00 ps
  ```

### 대문자, 소문자 변경

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 대문자로 변경 |  | `v` 🠲 `U` | 
| 소문자로 변경 |  | `v` 🠲 `u` | 

- 실습 

  ![Peek 2020-05-07 20-50](https://user-images.githubusercontent.com/16812446/81291224-59920700-90a4-11ea-8eae-1e63a31c5c70.gif)

  위와 같이 `6` 행으로 이동해서 `v$` 으로 문장 전체를 드래그하고 `j` 로 밑의 문장까지 드래그한 다음 `U` 를 눌러서 대문자로 바꿔보세요. 

  > 이 작업을 단지 키보드 입력 `4` 회로 했습니다. 


### 다중 입력

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 블록 드래그 |  | <kbd>Shift</kbd> + `v` | 
| 드래그 상태에서 다중 입력 |  | <kbd>Shift</kbd> + `i` | 

블록 드래그는 드래그와 달리 네모 모양으로 드래그를 할 수 있습니다. 이때 다중입력도 가능합니다. 

- 실습 

  ![Peek 2020-05-07 20-55](https://user-images.githubusercontent.com/16812446/81291625-11271900-90a5-11ea-8dc9-da6b03f0e352.gif)

  코딩을 하다보니 `#define` 문을 여러번 사용했는데 실수로 `#` 을 붙히는 걸 까먹었네요. 하지만 괜찮습니다.
  
  위와 같이 `0` 으로 문장 앞으로 이동하고 블록 드래그 <kbd>Shfit</kbd>+`v` 를 한 다음 `10j` 로 커서를 내립니다.

  그리고 <kbd>Shfit</kbd>+`i` 로 다중입력을 하고 `#` 을 입력한 후 <kbd>Esc</kbd> 를 눌러보세요. 

### 문장 붙히기 

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 문장 붙히기 | <kbd>&rarr;</kbd> × **n<sup>2</sup>** + <kbd>Delete</kbd> | `J` | 

- 실습 

  ![Peek 2020-05-07 21-00](https://user-images.githubusercontent.com/16812446/81292014-d1acfc80-90a5-11ea-9ef1-e3b593b75497.gif)

  `J` 를 누르면 위와 같이 문장이 연결됩니다. `.` 를 누르면 기능이 반복됩니다. 

### sp, vsp

## 수고하셨어요..

이걸 읽으셨다면 `vim` 실습을 다 하신 거겠죠. 아마 힘들 수도 있었겠지만 포기하지 않고 `vim` 에 익숙해져서 마음대로 `vim` 으로 코딩을 할 수 있게 된다면 코딩 속도가 너무 빨라져서 `vim` 배우길 잘했다 라고 생각하게 되실 거에요. 

> 이제부터는 **Google** 에 `vim` 을 검색해보면서 스스로 `vim` 의 더 다양한 기능을 찾아보세요. 저도 `vim` 을 에디터로 사용하지만 아직 기능의 **절반도 모르는것 같네요.** 하지만 일반 에디터로 다시는 되돌아갈 수 없는 몸이 되버렸어요. 코딩 속도가 너무 느려서 답답하거든요.

# vim 요약

| | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
|단축키 개수 | 적음 | 많음 | 
|입력 회수 | 많음 | 적음 | 

|이동 거리|퉁 치는 횟수|
|:---|:---|
|커서가 (문자가 모여있는) 단어를 이동하는 횟수 | **n 번** |
|커서가 (단어가 모여있는) 문장을 이동하는 횟수 | **n<sup>2</sup> 번**| 
|커서가 (문장이 모여있는) 전체파일을 이동하는 횟수 | **n<sup>3</sup> 번**|

| 기능 | 일반 텍스트 에디터 | `vim` |
|:---:|:---:|:---:|
| 왼쪽 이동 | <kbd>&larr;</kbd> | `h` | 
| 오른쪽 이동 | <kbd>&rarr;</kbd> | `l` | 
| 위쪽 이동 | <kbd>&uarr;</kbd>| `k` | 
| 아래쪽 이동 | <kbd>&darr;</kbd>| `j` | 
| 이전에 실행한 기능 반복하기 |  | `.` | 
| 입력하기 | | `i` | 
| 다음 글자에 입력하기 | <kbd>&rarr;</kbd> | `a` | 
| 다음 행에 입력하기 | <kbd>&rarr;</kbd> × **n<sup>2</sup>** + <kbd>Enter</kbd> | `o` | 
| 이전 행에 입력하기 | <kbd>&uarr;</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** + <kbd>Enter</kbd> | `O` | 
| 문장 마지막에 입력하기 | <kbd>&rarr;</kbd> × **n<sup>2</sup>** | `A` | 
| 문장 처음에 입력하기 | <kbd>&larr;</kbd> × **n<sup>2</sup>** | `I` | 
| 저장 | <kbd>Ctrl</kbd> + <kbd>s</kbd> | `:w` | 
| 종료 | <kbd>Alt</kbd> + <kbd>F4</kbd> | `:q` | 
| 저장 후 종료 | <kbd>Ctrl</kbd> + <kbd>s</kbd> 🠲 <kbd>Alt</kbd> + <kbd>F4</kbd>| `:wq` 또는 `ZZ` |<kbd>Alt</kbd> + <kbd>F4</kbd> 
| 강제 종료 |  | `:q!` | 
| 다른 이름(`<NAME>`)으로 저장 |  | `:w <NAME>` | 
| 지우기 | <kbd>Backspace</kbd> 또는 <kbd>Delete</kbd> | `x` | 
| 단어 지우기 | <kbd>Backspace</kbd> × **n** | `dw` | 
| 문장 지우기 | <kbd>Backspace</kbd> × **n<sup>2</sup>** | `dd` | 
| 커서로부터 문장 끝까지 지우기 | <kbd>Delete</kbd> × **n<sup>2</sup>** | `D` | 
| 한 글자 지우고 편집하기 | <kbd>Backspace</kbd> | `r` | 
| 단어 지우고 편집하기 | <kbd>Backspace</kbd> × **n** | `cw` | 
| 커서로부터 문장 끝까지 지우고 편집하기 | <kbd>Delete</kbd> × **n<sup>2</sup>** | `C` | 
| 문장에서 `<OLD>` 를 `<NEW>` 로 치환하기 |  | `:s/<OLD>/<NEW>` | 
| 전체 파일에서 `<OLD>` 를 `<NEW>` 로 치환하기 |  | `:s/<OLD>/<NEW>/g` | 
| 전체 파일에서 하나씩 확인하면서 `<OLD>` 를 `<NEW>` 로 치환하기 |  | `:s/<OLD>/<NEW>/gc` | 
| 원하는 문자로 이동 | <kbd>&rarr;</kbd> × **n<sup>2</sup>** | `f<C>` | 
| 오른쪽 단어로 이동 | <kbd>Ctrl</kbd> + <kbd>&rarr;</kbd> | `e` | 
| 왼쪽 단어로 이동 | <kbd>Ctrl</kbd> + <kbd>&larr;</kbd> | `b` | 
| 문장의 처음으로 이동 | <kbd>Ctrl</kbd> + <kbd>&larr;</kbd> × **n**  | `0` | 
| 문장의 마지막으로 이동 | <kbd>Ctrl</kbd> + <kbd>&rarr;</kbd> × **n**  | `$` | 
| 화면의 처음으로 이동 | <kbd>&uarr;</kbd> × **n<sup>3</sup>**  | `H` | 
| 화면의 가운데로 이동 |  | `M` | 
| 화면의 마지막으로 이동 | <kbd>&darr;</kbd> × **n<sup>3</sup>**  | `L` | 
| 취소 | <kbd>Ctrl</kbd> + <kbd>z</kbd> | `u` | 
| 취소한 것을 취소 |  | <kbd>Ctrl</kbd> + <kbd>R</kbd> | 
| 문장을 원래대로 복원 | | `U` | 
| 드래그 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n** | `v` | 
| 단어 복사하기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n** 🠲 <kbd>Ctrl</kbd> + <kbd>c</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `yw` 🠲  `p` | 
| 문장 복사하기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** 🠲 <kbd>Ctrl</kbd> + <kbd>c</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `yy` 🠲  `p` | 
| 드래그해서 복사하기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** 🠲 <kbd>Ctrl</kbd> + <kbd>c</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `v` 🠲 `y` 🠲 `p` | 
| 한 글자 잘라내기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>x</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `x` 🠲  `p` | 
| 단어 잘라내기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n** 🠲 <kbd>Ctrl</kbd> + <kbd>x</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `dw` 🠲  `p` | 
| 문장 잘라내기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** 🠲 <kbd>Ctrl</kbd> + <kbd>x</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `dd` 🠲  `p` | 
| 특정 영역 잘라내기 | <kbd>Shift</kbd> + <kbd>&rarr;</kbd> × **n<sup>2</sup>** 🠲 <kbd>Ctrl</kbd> + <kbd>x</kbd> 🠲 <kbd>Ctrl</kbd> + <kbd>v</kbd> | `v` 🠲 `x` 🠲 `p` | 
| 파일의 맨 마지막으로 이동 | <kbd>&darr;</kbd> × **n<sup>3</sup>** | `G` | 
| 파일의 맨 처음으로 이동 | <kbd>&uarr;</kbd> × **n<sup>3</sup>** | `gg` | 
| `<N>` 번째 행으로 이동 | <kbd>&uarr;</kbd> × **n<sup>3</sup>** 또는 <kbd>&darr;</kbd> × **n<sup>3</sup>** | `<N>gg` | 
| 아랫방향으로 찾기 | <kbd>Ctrl</kbd> + <kbd>f</kbd> | `/` | 
| 윗방향으로 찾기 |  | `?` | 
| 커서가 위치한 단어 아랫방향으로 찾기 |  | `*` | 
| 커서가 위치한 단어 윗방향으로 찾기 |  | `#` | 
| 찾고나서 같은방향으로 단어 찾기 | <kbd>Enter</kbd> | `N` | 
| 찾고나서 반대방향으로 단어 찾기 | <kbd>Shift</kbd> + <kbd>Enter</kbd> | `n` | 
| 괄호의 짝 찾기 |  | `%` | 
| 화면을 한 행만큼 아래로 이동 | <kbd>&darr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `e` | 
| 화면을 한 행만큼 위로 이동 | <kbd>&uarr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `y` | 
| 화면을 반 페이지만큼 아래로 이동 | <kbd>&darr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `d` | 
| 화면을 반 페이지만큼 위로 이동 | <kbd>&uarr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `u` | 
| 화면을 한 페이지만큼 아래로 이동 | <kbd>&darr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `f` | 
| 화면을 한 페이지만큼 위로 이동 | <kbd>&uarr;</kbd> × **n<sup>2</sup>** | <kbd>Ctrl</kbd> + `b` | 
| 커서를 기준으로 화면을 최대한 아래로 이동 |  | `zt` | 
| 커서를 기준으로 화면을 최대한 위로 이동 |  | `zb` | 
| 커서를 기준으로 화면을 정중앙으로 이동 |  | `zz` | 
| 파일 위치에서 `<CMD>` 명령 실행 |  | `:!` + `<CMD>` | 
| 파일 위치에서 쉘 실행 |  | `:shell` | 
| 대문자로 변경 |  | `v` 🠲 `U` | 
| 소문자로 변경 |  | `v` 🠲 `u` | 
| 블록 드래그 |  | <kbd>Shift</kbd> + `v` | 
| 드래그 상태에서 다중 입력 |  | <kbd>Shift</kbd> + `i` | 
| 문장 붙히기 | <kbd>&rarr;</kbd> × **n<sup>2</sup>** + <kbd>Delete</kbd> | `J` | 


