# brew 사용하기
[출처](https://dev.classmethod.jp/etc/windows10_wsl_brew/ )  
  
## brew 명령어 설치하기
패키지를 업데이트한다.  
```
$ sudo apt update
```
  
brew 명령어(linuxbrew-wrapper)을 설치한다.  
```
$ sudo apt install linuxbrew-wrapper
```
  
  
brew doctor로 명령어를 체크한다.  
```
$ brew doctor
```
  
  
만약 퍼미션이나 환경 변수가 문제가 된다면 아래 작업을 한다.  
```
$ echo 'umask 002' >> ~/.bash_profile
$ echo 'export PATH="/home/linuxbrew/.linuxbrew/bin:$PATH"' >> ~/.bash_profile
$ echo 'export PATH="/home/linuxbrew/.linuxbrew/sbin:$PATH"' >> ~/.bash_profile
```
  
  
Terminal을 재 시작하고 다시 실행한다.  
```
$ brew doctor
Your system is ready to brew.
```
  
이것으로 완료
  
  
  
## brew를 사용하여 설치한다
  
```
$ brew install remind101/formulae/assume-role
```
  
→설치가 되었다면 실행해 본다.    
  