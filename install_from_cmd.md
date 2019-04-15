# [버역] WSL (Windows Subsystem for Linux)를 명령 줄에서 설치
출처: https://qiita.com/moriai/items/850ee91d60edc91e7b7e  
    
절차의 흐름은 GUI에서 하는 것과 다르지 않지만, Microsoft 스토어에 연결하지 않아도 좋고, 정책적으로 다양하게 제한 되어 있는 환경에서도 사용할 수 있는 경우가 많다는 것이 큰 장점.
  
## 환경
- Windows 10 Professional 또는 Enterprise version 1803 (Redstone 4)
- PC 또는 Virtualbox
  
  
## 단계
### 1. WSL 설치
관리자 권한의 PowerShell에서 아래를 실행하고 재부팅 한다.  
```
PS C : \> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
    
  
### 2. 배포판 다운로드
디스토로 패키지의 마음에 드는 것을 좋아하는 방법으로 다운로드 한다. 최신 디스토로 패키지 목록은 Microsoft의 온라인 설명서에 기재 되어 있다.   
- Ubuntu 18.04 ( https://aka.ms/wsl-ubuntu-1804 ) 
- Ubuntu 16.04 ( https://aka.ms/wsl-ubuntu-1604 ) 
- Debian GNU / Linux ( https://aka.ms/ wsl-debian-gnulinux ) 
- Kali Linux ( https://aka.ms/wsl-kali-linux ) 
- OpenSUSE ( https://aka.ms/wsl-opensuse-42 ) 
- SLES ( https : // aka. ms / wsl-sles-12 )
  
PowerShell이면 아래처럼 다운로드 할 수 있다.  
```
PS C:\> Invoke-WebRequest -Url https://aka.ms/wsl-debian-gnulinux -OutFile C:\Users\XXX\Downloads\Debian.appx -UseBasicParsing
```  
  
  
### 3. 배포판 설치 및 초기화
관리자 권한의 PowerShell에서 아래를 수행한다.  
```
PS C:\> Add-AppxPackage C:\Users\XXX\Downloads\Debian.appx
```
  
설치에 성공하면 시작 메뉴에 배포판의 이름이 있을 것이다. Windows Update가 실행 중인 경우 설치에 실패하기 때문에 업데이트 한후에 다시 설치를 실행하면 성공할지도. 그렇지 않은 경우의 대책에 대해서는 후술.  
나머지는 정상적으로. 시작 메뉴의 배포판 이름을 클릭하면 배포판의 초기화가 시작된다.  
  
#### 3a. 배포판 설치 및 초기화에 실패하는 경우
추천 방법은 아닐지 모르지만, 다음 단계에서 원하는 위치에 설치할 수 있다.  
1. 다운로드한 디스토로 패키지 확장자를 appx에서 zip으로 변경
2. 이 zip 파일을 자신이 좋아하는 폴더(예 : C:\Users\xxx\ 포판 이름 등)에 푼다.
3. 압축을 푼 폴더로 cd하고, 거기에 있는 exe 파일을 실행
4. 배포판의 초기화에 성공하면 Unix 유저 이름을 물어보면 적절한 사용자 이름(Windows 로그인 이름도 좋지만, 달라도 문제 없음) 및 암호를 설정
5. (optional)위의 exe 파일을 시작에 고정하기 
  
<pre>
PS C:\Users\xxx\Downloads> Copy-Item .\Debian.appx .\Debian.zip
PS C:\Users\xxx\Downloads> Expand-Archive .\Debian.zip C:\Users\xxx\Debian
PS C:\Users\xxx\Downloads> cd C:\Users\xxx\Debian
PS C:\Users\xxx\Debian> .\debian.exe
Installing, this may take a few minutes...
Please create a default UNIX user account. The username does not need to match your Windows username.
For more information visit: https://aka.ms/wslusers
Enter new UNIX username: xxx
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Installation successful!
</pre>
  
배포판 설치 및 초기화에 실패하는 원인은 여러가지 있는 것 같지만,이 단계에서도 안되는 경우에는 포기하는 것이 좋을 듯.  
  
  
### 4. 배포판 제거
위의 3.에서 설치한 경우에는 관리자 권한의 PowerShell에서 다음을 수행한다. 이제 사용자마다 초기화(확장된) 배포판도 모두 삭제된다.  
```
PS C:\> Get-AppxPackage *debian* | Remove-AppxPackage -AllUsers -Confirm
```
  
#### 4a. 배포판 제거
위의 3a.로 설치한 경우에는 wslconfig에서 unregister 하면서 디스트로를 푼 폴더마다 삭제한다.  
```
PS C:\Users\xxx> wslconfig /u Debian
PS C:\Users\xxx> Remove-Item .\Debian -Recurse
```
  
