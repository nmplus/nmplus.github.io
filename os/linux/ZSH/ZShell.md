# Zsh이란?

Z 셸은 상호작용 로그인 셸이자 셸 스크립트를 위한 강력한 명령 줄 인터프리터로 사용할 수 있는 유닉스 셸이다. Zsh는 bash, ksh, tcsh의 일부 기능을 포함하여 수많은 개선 사항이 갖추어진 확장형 본 셸이다. [참고 위키백과 https://ko.wikipedia.org/wiki/Z_%EC%85%B8]

- root계정이 아닌 user 계정을 할당받아 적용하도록 한다!!  

- zsh설치 및 버전확인, 설치여부체크
```
sudo yum install zsh
zsh --version
cat /etc/shells
```
- 쉘위치확인 후 기본쉘 지정
  - 설치후 세션을 다시 접속하면 적용됨
```
which zsh
chsh -s /usr/zsh
```
- Oh My ZSH 프레임워크 설치  
  - 테마, 단축어 등 환경설정을 다루는 프레임워크  
```
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```
- zsh 테마변경
  - /home/본인계정 위치로 이동시 숨김파일으로 .zshrc을 vi로 실행  
  - ZSH_THEME부분을 수정하면됨 ohmyzsh설치시 테마가 설치된다.  
  - 테마경로 /home/본인계정/.oh-my-zsh/themes  
  ```
  vi .zshrc

  ...중략

  # Set name of the theme to load --- if set to "random", it will
  # load a random theme each time oh-my-zsh is loaded, in which case,
  # to know which specific one was loaded, run: echo $RANDOM_THEME
  # See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
  ZSH_THEME="cloud"  #구름테마로 변경
  ```


