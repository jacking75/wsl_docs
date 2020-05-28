# WSL2

## Windows 10에 WSL 1 과 WSL 2 설치하기
 
### 1.PowerShell 시작
"PowerShell"을 관리자 권한으로 실행한다.    
  
### 2.WSL 설치
아래 명령을 실행하여 "WSL"를 설치한다.  
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
    
설치가 완료되면 설치 결과가 표시된다.  
  
WSL 1만 이용하는 경우
- "WSL 1" 설치 완료는 이것으로 끝이다.
- "WSL 1"만 이용할 경우 PC를 다시 시작한다.
  
WSL 2도 이용하는 경우
- 아래에 이어지는 "3"의 단계를 수행한다.  
  

### 3.Virtual Machine Platform 설치
아래 명령을 실행하여 "Virtual Machine Platform"을 설치한다.  
```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
  
설치가 완료되면 설치 결과가 표시된다.  
설치가 완료되면 PC를 다시 시작한다. 
  

### 4.WSL의 기본 버전을 2로 변경한다
"WSL 2"를 메인으로 사용하는 경우 아래 명령을 실행하여 'WSL"의 기본 버전을 "2"로 변경한다.  
```
wsl --set-default-version 2
```
    
이제 남은 것은 원하는 Linux 배포판을 설치하는 것 뿐이다.  
Linux 배포판은 「Microsoft Store」에서 설치한다.  
  
<br>    
  
## WSL 기본 버전 변경
"WSL"에는 "WSL 1" 과 "WSL 2"가 있으며, 이들은 동시에 설치할 수 있다.  
"WSL" 기본 버전을 변경하는 방법이다.
아래 명령으로 "WSL" 기본 버전을 변경할 수 있다.  
```
wsl --set-default-version <버전>
```
  
<버전>은 "1" 또는 "2"를 지정한다.  
예를 들어 "WSL 2"를 기본값으로 설정하려면 아래 명령을 실행한다.  
```
wsl --set-default-version 2
```
  
기본값은 WSL 1로 되어 있다.  
향후 기본 버전 설정은 "WSL 2"로 바뀔 예정이다.  
  
    
## Linux 배포판이 사용하는 WSL 버전 변경
Linux 배포판은 어느 버전을 사용하여 시작한다.  
각 Linux 배포판에는 시작할 때 사용하는 "WSL" 버전이 설정되어 있으며, 이 설정에 따라 "WSL 1" 또는"WSL 2"를 사용한다.
Linux 배포판 설치 시 기본 "WSL" 버전이 설정된다.  
사용자는 기본 설정과 각 Linux 배포판의 설정을 나중에 변경할 수 있다.  
  
### Linux 배포판을 사용하는 "WSL"의 버전을 확인하는 방법
아래 명령으로 설치된 Linux 배포판과 함께 각 Linux 배포판을 사용하는 'WSL' 버전이 표시된다.  
```
wsl -l -v
```
  
"NAME" 열이 Linux 배포판 이름이다.  
"VERSION" 열이 "WSL" 버전을 보여준다.
  
  
### Linux 배포판이 사용하는 WSL의 버전을 변경하기
Linux 배포판이 사용하는 "WSL" 버전을 변경하는 방법이다.  
  
1.Linux 배포판 이름을 확인
우선 위의 방법으로 변경하는 Linux 배포판의 이름을 확인한다.  
  
2.WSL 버전을 변경
아래 명령으로 "WSL" 버전을 변경한다.  
```
wsl --set-version <배포판 이름> <버전>
```
  
<배포판 이름>은 "1"에서 조사한 Linux 배포판 이름을 입력한다.  
<버전>은 "1" 또는 "2"를 지정한다.  
  
예를 들어 "Ubuntu 18.04 LTS" 버전을 "2"로 변경하려면 아래 명령을 실행한다.  
```
wsl --set-version Ubuntu-18.04 2
```
  
머신 성능에 따라서 변경에 시간이 걸릴 수 있다.  
  
"Ubuntu 18.04 LTS" 버전을 확인하면 아래와 같이 "VERSION"이 "2"로 되어 있다.  
  
<br>    
  
## WSL 재시작 하기
WSL2에서 알 수 없는 이유로 어떤 기능이 동작하지 않을 때 해결하는 방법  
```
wsl --shutdown
```  
위 명령어로 wsl을 재 시작하도록 한다.    
  
<br>  
  
## X Server를 이용하기 위한 설정(DISPLAY 환경 변수를 자동 설정한다)  
[출처](https://qiita.com/mhangyo/items/6201ec3e2f8f403c909e  )  
[(일어)WSL2의 VcXsrv 설정](https://qiita.com/ryoi084/items/0dff11134592d0bb895c) 에서 나온 글을 중심으로 한다.  
WSL의 디스플레이 설정 공정에서 WSL2 측의 ip 주소를 지정해야 한다.  
이 글에서는 ipconfig로 확인하여 설정하고 있지만, 글에도 있듯이 다시 시작할 때마다 ip 주소가 달라진다는 문제가 있다.  
아래와 같은 명령으로 WSL2 측에서 ip 주소를 취득하고, DISPLAY 환경 변수에 넣을 수 있다. 이것을 설정 파일(zshrc 든지)에 적어 놓으면 부팅 시 자동으로 설정하는 것이 가능하다.  
```
export DISPLAY=`grep -oP "(?<=nameserver ).+" /etc/resolv.conf`:0.0
```
  
  
  
## 글 모음 
- [WSL2의 Export / Import 기능을 사용한 개발 환경의 공유](https://docs.google.com/document/d/1DG-xaB1IkjYKtwSXsqmS6dL1U0v-7fC20W-5I_Y_egw/edit?usp=sharing)
- [(일어)WSL2에서 극적으로 변화는 Web 애플리케이션 개발 환경 - 2：도입편](https://tech-lab.sios.jp/archives/18437 )
- [(일어)WSL2에서 극적으로 변화는 Web 애플리케이션 개발 환경 - 3：실전편】](https://tech-lab.sios.jp/archives/18446 )
- [How to set up Docker within Windows System for Linux (WSL2) on Windows 10](https://www.hanselman.com/blog/HowToSetUpDockerWithinWindowsSystemForLinuxWSL2OnWindows10.aspx)
  
