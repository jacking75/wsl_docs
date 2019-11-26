# WSL 문서
  
## wsl.exe 옵션
단축 옵션		긴 옵션	동작  
-d ＜디스트리뷰션 이름＞		--distribution ＜디스트리뷰션 이름＞	지정한 디스트리뷰션을 시작한다  
-e ＜명령 라인＞	--exec ＜명령 라인＞	명령 라인을 실행하고, 이 후 WSL에서 빠진다  
-u ＜유저 이름＞	--user ＜유저 이름＞	지정한 유저 이름으로 WSL 디스트리뷰션을 시작한다  
　						--help						간단하게 명령어 사용 방법을 표시  
　						--							이 옵션 이후의 명령 라인 해석을 하지 않고 WSL 측에 넘긴다  
  
  
## wslconfig.exe 옵션
옵션	동작  
/l, /list :		등록된 디스트리뷰션 리스트 표시  
/all:		/l /list와 조합하여 설치 중 등을 포함한 모든 디스트리뷰션 표시  
/t, /terminate ＜디스트리뷰션 이름＞ :		지정한 디스트리뷰션을 종료시킨다  
/u, /unregister ＜디스트리뷰션 이름＞ :		지정한 디스트리뷰션 등록을 해제한다  
/upgrade ＜디스트리뷰션 이름＞ :		지정한 디스트리뷰션의 VolFs를 lxFs에서 wslFs로 업그레이드 한다(실험 중인 기능이라고 생각되므로 아직은 사용하지 않는쪽을 추천)  
  
  
  
## 우분투 
### 버전 확인하기  
  
```
lsb_release -a
```
  
  
### 업그레이드 하기
  
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo do-release-upgrade
```  
대부분 위 명령어를 실행하면 1시간 정도 걸린다.  
  
  
### 우분투 삭제하기  
https://webnautes.tistory.com/1172  
가장 간단하게는 시작 메뉴에서 Ubuntu 항목에서 마우스 우 클릭하고 메뉴에서 제거를 선택. 잠시 기다리면 Ubuntu 항목이 삭제된다.    
  
  
  
## Tool
- [WSL-DistroManager](https://github.com/rkttu/WSL-DistroManager )
    - Highly customizable WSL distro manager for Windows 10 and Windows Server 19H1+
    - 동일 머신에 동일 Linux 버전을 복수 설치할 수 있음.
    - Windows 10 and Windows Server 2016+
- [wsltools](https://github.com/rkttu/wsltools )
    - This repository provides batch files that enable you to quickly install and manage WSL in a command-line fashion. These batch files can be run on Windows 10 19H1 or later builds
  
  
  
## 글 모음 
  
### 일반
- [(일어)WSL용 터미널 소프트웨어에 Hyper를 추천](https://qiita.com/WGG_SH/items/65416692d545f888c6a9  )  
- [(일어)Windows 10의 CMD에서 WSL 상의 Linux 명령어를 호출(버전 1803 대응판)](http://www.atmarkit.co.jp/ait/articles/1805/24/news022.html  )  
- [(일어)Windows 10의 Linux 호환환경 WSL에서 CMD의 프로그램을 호출(버전 1803 대응판)](http://www.atmarkit.co.jp/ait/articles/1805/31/news052.html   )
- [(일어)Windows 10의 WSL에서 네트워크 드라이브 등을 마운트 하기](http://www.atmarkit.co.jp/ait/articles/1806/08/news042.html )
- [(일어)Windows 10의 WSL의 자동 마운트나 fstab에 의한 마운트 처리를 wsl.conf 파일로 제어한다](http://www.atmarkit.co.jp/ait/articles/1807/12/news036.html ) 
- [(일어)Windows 10의 WSL 환경을 초기화 하고, 클린한 상태로 되돌리기](http://www.atmarkit.co.jp/ait/articles/1807/06/news028.html )  
- [(일어)RS4의 Windows Subsystem for Linux에서의 wsl.conf에 의한 초기 설정](http://ascii.jp/elem/000/001/634/1634120/ )  
- [(일어)WSL에서 Amazon Linux 2 사용하기](https://qiita.com/noumia/items/9fecd2a7c3ea4acb696e )  
- [(일어)WSL의 콘솔을 편리하고 고 기능의 「wsltty」로 바꾸기](http://www.atmarkit.co.jp/ait/articles/1812/13/news031.html )  
- [(일어)wsl.exe 명령어 개선(Windows 10 version 1903)](https://kledgeb.blogspot.com/2019/02/wsl-168-wslexewindows-10-version-1903.html )
- [(일어)2017-12. Linux의 백그라운드 태스크(데몬이나 서비스) 지원 개선・콘솔 윈도우 종료해도 동작 가능하도록](https://kledgeb.blogspot.kr/2017/12/wsl-124-linux.html  )
- [(일어)WSL에서 백그라우드 태스크 지원 ～Windows 10 차기 업데이트「RS4」에서](https://forest.watch.impress.co.jp/docs/news/1095045.html  )
   
  
### 설치
- [Windows10에서 Bash 설치/삭제/업데이트 방법](https://blog.gaerae.com/2016/08/install-bash-windows-10.html )
- [Windows10에서 cmd로 설치](https://docs.microsoft.com/en-us/windows/wsl/install-manual )
- [WSL(Windows Subsystem for Linux) 사용기 및 ArchLinux로의 전환](https://blog.naver.com/youseok0/221220130943 )
- [Windows Server Installation Guide](https://docs.microsoft.com/en-us/windows/wsl/install-on-server )
- [윈도우10(WINDOWS10)의 스토어에서 우분투 설치 방법](http://psychoria.tistory.com/archive/20171019 )
- [(일어)Linux 디스트리뷰션 패키징과 사이드 로딩에 의한 설치](https://opcdiary.net/?p=41132 )
- [(일어)Windows Subsystem for Linux 설치와 사용 방법](http://www.buildinsider.net/enterprise/bashonwindows/01 )
- [Easily move WSL distributions between Windows 10 machines with import and export!](https://www.hanselman.com/blog/EasilyMoveWSLDistributionsBetweenWindows10MachinesWithImportAndExport.aspx )  
      
    
### 설정
- [The Windows Subsystem for Linux Guide!](http://wsl-guide.org/en/latest/ )
- [(일어)WSL에서 apt-get을 사용하여 패키지 설치하기](http://www.atmarkit.co.jp/ait/articles/1608/24/news038.html )
- [Setting up a Shiny Development Environment within Linux on Windows](https://www.hanselman.com/blog/SettingUpAShinyDevelopmentEnvironmentWithinLinuxOnWindows10.aspx )
- MobaXterm – GUI 프로그램으로 WSL에 접속하면 자동으로 GUI 환경 사용 가능
    - https://qiita.com/pedantryjp/items/716c40fba707c3aafc1a
    - http://eng-notebook.com/blog-entry-240/
- [wsl-init  https://github.com/ClouDeveloper/wsl-init
- [(일어)WSL에서 Linux의 패스워드를 잊어버린 경우 대처 방법](https://linuxfan.info/wsl-password-reset )
- [(일어)디렉토리 마다 파일 이름 대문자/소문자 구별 유무를 설정](https://kledgeb.blogspot.kr/2018/03/wsl-136.html )
- [(일어)Windows 환경 변수과 Linux의 환경 변수를 상호 연결 가능하게](https://kledgeb.blogspot.kr/2017/12/wsl-128-windowslinux.html )
- [(일어)Linux 디스트리뷰션을 관리하려면 ・WSL Config 명령어 소개](https://kledgeb.blogspot.kr/2017/12/wsl-121-linuxwsl-config.html )
- [(일어)Windows에서 Linux의 쉘을 기동하는 3가지 방법](https://kledgeb.blogspot.kr/2017/12/wsl-122-windowslinux3.html )
- [(일어)default 유저를 변경・디스트리뷰션을 클린한 상태로 돌리기](https://kledgeb.blogspot.kr/2017/12/wsl-123.html )
- [(일어)로케일을 영어 모드로 변경하기](http://www.atmarkit.co.jp/ait/articles/1610/14/news033.html )
- [(일어)WSL 환경을 초기화/재 설치 하기](http://www.atmarkit.co.jp/ait/articles/1610/05/news033.html )
  
  
### 애플리케이션 실행
- [(일어)Windows 10의 명령어 프롬프트에서 WSL 상의 Linux 명령어를 호출(버전 1803대응)](http://www.atmarkit.co.jp/ait/articles/1805/24/news022.html )
- [wsltty. Mintty as a terminal for Bash on Ubuntu on Windows / WSL](https://github.com/mintty/wsltty )
- [wsl-terminal. Terminal emulator for Windows Subsystem for Linux (WSL)](https://goreliu.github.io/wsl-terminal/ )
- [WSL Ubuntu에서 PuTTY Pageant 연동하기](https://medium.com/@rkttu/wsl-ubuntu%EC%97%90%EC%84%9C-putty-pageant-%EC%97%B0%EB%8F%99%ED%95%98%EA%B8%B0-942660a32041 )
- [WSL에서 Native Docker 실행하기](https://medium.com/@rkttu/wsl%EC%97%90%EC%84%9C-native-docker-%EC%8B%A4%ED%96%89%ED%95%98%EA%B8%B0-ff75b1627a87 )
- [(일어)WSL Interoperability with Docker](https://opcdiary.net/?p=38867 )
- [(일어)실볼 링크로 Bash에서 Windows의 파일에 간단하게 접근](https://kledgeb.blogspot.kr/2017/01/wsl-70-bashwindows.html )
- [(일어)Windows에서 Linux 명령어를 호출하는 명령어 실행 예](https://kledgeb.blogspot.kr/2016/10/wsl-50-windowslinux.html )
- [(일어)Bash on Ubuntu on Windows에 tmux 사용하기](https://kledgeb.blogspot.kr/2016/06/wsl-23-bash-on-ubuntu-on-windowstmux.html )
- [(일어)Windows와 Bash 상호 운용](https://kledgeb.blogspot.kr/2016/11/wsl-53-windowsbash.html )
  
  
### 프로그래밍
- [(일어)각 언어 환경을 Linux (WSL)에 asdf로 구축](https://qiita.com/kikuchi_kentaro/items/d951fa7ca7c9c29a77dc )
- [(일어)새로운 Windows10에 WSL을 이용한 개발 환경 갖추기](https://qiita.com/b-inary/items/0f29a825f041787430ff )   	  
- [Ubuntu on Windows 10으로 GTK# 응용프로그램 개발해보기](http://rkttu.com/2016/08/07/ubuntu-on-windows-10%EC%9C%BC%EB%A1%9C-gtk-%EC%9D%91%EC%9A%A9%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-%EA%B0%9C%EB%B0%9C%ED%95%B4%EB%B3%B4%EA%B8%B0/ )
- [WSL을 이용해 윈도우 PC 1대에서 Linux 응용 프로그램을 Visual Studio로 개발하는 방법](http://www.sysnet.pe.kr/2/0/11390 )
- [WSL을 이용해 윈도우 PC 1대에서 openSUSE 응용 프로그램을 Visual Studio로 개발하는 방법](http://www.sysnet.pe.kr/2/0/11391 )
- [(일어)Unity Plugin With WSL](https://github.com/keijiro/UnityPluginWithWSL )
- [(일어)WSL(Windows Subsystem for Linux)에 거의 최신 웹 서버 환경(Node.js 6, nginx 1.10, MySQL 5.7, PHP 7)를 도입하는 최단 수순](http://qiita.com/kent_ocean/items/dc252b5d8183dfc6da57 )
- [(일어)Bash on Ubuntu on Windows를 사용하여 「개발」을 해 보았다](http://www.buildinsider.net/enterprise/bashonwindows/02 )
- [(일어)Visual Studio Code의 통합 터미널에서 Bash on Ubuntu on Windows를 사용한다](http://qiita.com/horihiro/items/d1845d6326b7aba6a7f7 )
- [(일어)Bash on Ubuntu on Windows에서 Serverless Framework 설치까지](http://qiita.com/saitotak/items/dcd7d59a4e75242d46dc )
- [(일어)BashOnUbuntuOnWindows에서 Elixir를 동작시키자](http://qiita.com/aoshimanoa/items/e75d758dd2c7d14e3d74 )
     
  
#### C++
- [(일어)Windows Subsystem for Linux](http://samuraism.com/products/jetbrains/clion/clion-2018-1 )
- [(일어)Visual Studio + Ubuntu on Windows에서 Ubuntu 소프트웨어 개발 가능하게](https://kledgeb.blogspot.kr/2017/02/wsl-75-visual-studio-ubuntu-on.html )
- [(일어)Visual Studio 2017와 Bash on Windows를 사용하여 C++ 표준 제안 중의 컨셉을 테스트](http://nekko1119.hatenablog.com/entry/2017/04/17/024318 )
  
  
#### .NET Core
- [(일어)Windows Subsystem for Linux에서 .NET Core를 사용하여 Visual Basic의 Hello World 애플리케이션 개발](https://qiita.com/yaju/items/ce0cbb79f27110d96afe )
  
  
#### Node.js
- [Running Node.js on WSL from Visual Studio Code](https://blogs.msdn.microsoft.com/commandline/2017/10/27/running-node-js-on-wsl-from-visual-studio-code/ )
- [WSL(윈도우 서브시스템 리눅스) 에서 node.js 개발하기](http://blog.hazard.kr/archives/838 )
  
  
#### java
- [Windows 10으로 시작하는 Java 개발](https://medium.com/@rkttu/start-java-dev-with-win-10-402cb91126fd )
  
  
#### Ruby
- [bash on windows에서 ruby on rails을 움직여봤다](http://nekko1119.hatenablog.com/entry/2016/08/08/115848 )
- [(일어)Bash on Ubuntu on Windows + VcXsrv + RubyMine에서 Windows에서도 쾌적한 Rails 개발환경을 만들자](http://qiita.com/fukuramikake/items/283b817c16725af79a28 )
- [(일어)Bash on Ubuntu on Windows에서 Rails/PostgreSQL 개발환경을 구축하기](http://qiita.com/yusuke_konishi/items/bb99faceada542ce2017 )
- [(일어)Bash on Ubuntu on Windows에 rbenv 와 nvm 설치하기](http://qiita.com/rerofumi/items/d06745f7514b400e5dfd )