# [펌] WSL에서 SSH 데몬 설치
출처: https://youngminz.github.io/main/2016/09/16/using-sshd-on-bash-on-windows.html  
  
Windows 10의 1주년 업데이트로, 리눅스 바이너리 64비트 ELF 파일을 bash를 거쳐 윈도우에서 실행시킬 수 있게 되었다.  
하지만 bash는 현재 윈도우 명령 프롬프트에서만 실행시킬 수 있고, XShell 등의 서드 파티 쉘에서는 bash를 곧바로 실행하여 사용할 수 없다.  
    
    
## 1. Windows 10의 기본 SSH 서비스 중지 및 사용 안 함
기본적으로, Windows 10 1주년 업데이트 후에는 SSH Server Broker와 SSH Server Proxy라는 서비스가 설치된다.  
이 서비스들은 기본적으로 22번 포트를 점유하고 있고, openssh-server가 22번 포트를 열 수 없게 만든다.  
Win + R + services.msc로 서비스를 열고, SSH Server Broker와 SSH Server Proxy를 찾아 각각 중지하고, 사용 안 함으로 설정한다.  
   
   
## 2. openssh-server 설치
  
```
sudo apt-get install openssh-server
```
  
  
## 3. /etc/ssh/sshd_config 파일 수정
다음을 참고하여 nano나 vi 등의 에디터를 이용해 해당 설정 파일을 적절히 수정해 준다.  
명령어 예시는 sudo nano /etc/ssh/sshd_config 나 sudo vi /etc/ssh/sshd_config 이다.  
```
ListenAddress 0.0.0.0
UsePrivilegeSeparation no
PasswordAuthentication yes
```
  
  
## 4. 실행
sudo service ssh start를 bash 창에 타이핑하면 SSH 데몬이 가동된다.  
이 경우 크게 두 가지 문제가 있다.  
첫 번째는 Bash on Windows는 백그라운드로 프로세스를 돌리는 것을 지원하지 않기 때문에, 해당 명령어를 타이핑한 창을 끄게 되면 SSH 데몬도 함께 죽어버린다.   
두 번째는 cron 등으로 부팅 시 마다 시작하게 하는 것도 지원하지 않는다.  
  
### 두 번째 문제를 해결하기 위한 방법
부팅 시마다 자동으로 SSH 서버를 켜려면, 작업 스케줄러에서 부팅 시마다 sshd를 실행시키도록 설정하면 된다.  
그 전에 먼저 sudo chmod +a /usr/sbin/sshd 명령어를 이용하여, sudo 없이도 sshd가 실행될 수 있도록 설정한다.  
    
트리거: 사용자가 로그인할 때, 프로그램/스크립트: c:\Windows\system32\bash.exe, 인수: -c "/usr/sbin/sshd -D"  
  
이렇게 설정할 시, 부팅 시마다 빈 bash 창이 뜬다. 나는 가상 바탕 화면을 하나 더 만든 다음 그 곳에 창을 끌어 보이지 않게 처리하고 사용하고 있다.  
  