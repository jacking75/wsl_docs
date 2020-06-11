# WSL2
WSL2는 아키텍처 수준에서 WSL1과 다르다.  
WSL1이 Linux 시스템 콜과 Windows NT 커널 간의 변환층을 필요로 하는 반면, WSL2는 완전한 Linux 커널을 실행하는 경량 VM을 포함한다. 이 VM은 Windows Hipervisor 층에서 직접 실행한다.  
![wsl2](./images/wsl2-001.png)            
  
기존의 VM과의 차이  
![wsl2](./images/wsl2-002.png)            
    
커널은 시스템 호출의 완전 호환성을 갖추고 있기 때문에 Docker나 FUSE 등의 앱으로도 Linux에서 자연스럽게 실행 가능하다. 이 새로운 구현에서는 Linux 커널에서 Windows 파일 시스템에 대한 전체 액세스가 가능하게 되어 있다.  
  
또 파일 시스템 액세스가 필요한 상호 작용에서 성능이 크게 개선 되었다. Microsoft의 프로그램 관리자인 Craig Loewan씨에 의하면 응용 프로그램 파일 집합의 수준에 따라 다르지만 3 ~ 6배의 성능 향상이 가능하다고 한다. tar 압축 해제에서는 성능이 20배 향상된 예도 있다.  
![wsl2](./images/wsl2-003.png)            
    
WSL 2의 Linux 파일은 Windows의 파일 시스템(NTFS)가 아닌 EXT4로 포맷된 가상 하드웨어 디스크(VHD)에 저장된다. 그래서 WSL1에서 문제가되었던 디스크 접근 성능이 대폭으로 개선 되었다.
![wsl2](./images/wsl2-004.png)            
이 VHD는 필요에 따라서 자동적으로 확장되지만 초기 상태에서 최대에서의 최대 사이즈는 256GB로 제한 되어 있으므로 디스크 영역이 부족하면 에러가 발생한다. 이 경우는 수동으로 VHD 사이즈 제한을 완화해야 한다.  
  
Windows 10 2004 버전에서는 WSL2 설치 및 업데이트 프로세스는 매우 쉬운 것이 된다. 기존 Linux 커널은 Windows OS 버전의 일부로 포함 되어 있었지만, 이 다음 릴리스에서는 분리 되기 때문에 타사 드라이버를 설치할 때처럼 Windows Update를 통해 커널을 업데이트 할 수 있다.    
      
  
[microsoft/WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel)  
[MS Doc Windows 10에 Linux용 Windows 하위 시스템 설치 가이드](https://docs.microsoft.com/ko-kr/windows/wsl/install-win10 )  
[WSL2(Windows Subsystem For Linux 2) 사용하기](https://medium.com/@seunghunhan_15321/wsl2-windows-subsystem-for-linux-2-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-a0998b84d5fe  )  

  


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
  
  
## 네트워크
WSL1에서는 Windows 10쪽 에뮬레이션을 실시하기 위해, Linux 측에서 TCP/IP 등의 프로토콜은 처리하지 않고, Windows 10의 네트워크 기능을 이용한다. 따라서 Linux의 IP 주소도 Windows 10 쪽과 동일하게 된다.  

이것애 비해 WSL2는 가상 머신에서 Linux 커널이 동작하여 네트워크 스택도 작동하기 때문에 IP 주소는 Win32 측과는 다른 것을 사용한다. 이 때, 가상 네트워크(가상 네트워크 스위치)가 만들어지고, 자신의 내부 네트워크에 WSL2와 Win32 측의 가상 네트워크 어댑터를 연결한 구조가 된다. 현재 이 IP 주소 할당은 WSL2의 가상 네트워크가 기동할 때 발생하므로 반드시 일정한 IP 주소가 되는 것은 아니다.  
  
그러나 Windows 10 쪽에서는 항상 WSL2 측은 Localhost로 액세스가 가능한 구조이다. 이것은 WSL2 측에서 수신 포트(Listen 포트)를 Win32 측의 소프트웨어가 중계하는 것으로 이루어진다.  
  
또한 WSL2 내에서는 "/etc/resolv.conf"에 기재되어 있는 DNS 서버가 항상 Win32 측의 가상 네트워크 측 IP 주소를 나타내게 되어 있다(이 파일은 WSL2 시작 시 자동 생성된다). 이 구조를 이용하여 Linux 측에서도 일정한 단계에서 Win32 측의 IP 주소를 얻는 것이 가능하다.  
    


## WSL2의 git을 Windows 10에서 사용하기
1. [여기](https://github.com/andy-5/wslgit/releases)에서 다운로드 후 원하는 위치에 둔다.
2. 일반적인 git으로 사용하고 싶다면 1에서 받은 실행파일의 이름을 git.exe 로 변경한다.
  
  
## 글 모음 
- [WSL2의 Export / Import 기능을 사용한 개발 환경의 공유](https://docs.google.com/document/d/1DG-xaB1IkjYKtwSXsqmS6dL1U0v-7fC20W-5I_Y_egw/edit?usp=sharing)
- [(일어)WSL2에서 극적으로 변화는 Web 애플리케이션 개발 환경 - 2：도입편](https://tech-lab.sios.jp/archives/18437 )
- [(일어)WSL2에서 극적으로 변화는 Web 애플리케이션 개발 환경 - 3：실전편】](https://tech-lab.sios.jp/archives/18446 )
- [How to set up Docker within Windows System for Linux (WSL2) on Windows 10](https://www.hanselman.com/blog/HowToSetUpDockerWithinWindowsSystemForLinuxWSL2OnWindows10.aspx)
  
