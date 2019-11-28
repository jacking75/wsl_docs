# WSL 디스트리뷰션 import/export 
[Easily move WSL distributions between Windows 10 machines with import and export!](https://www.hanselman.com/blog/EasilyMoveWSLDistributionsBetweenWindows10MachinesWithImportAndExport.aspx )    
    
"Windows Subsystem for Linux(WSL)"를 조작 · 관리하는 "wsl" 명령에는 내보내기/가져오기를 위한 옵션을 제공하고 비교적 쉽게 다른 시스템 간에 "WSL 2" 환경 마이그레이션을 할 수 있다. 예를 들어, "PowerShell"로 내보내기 하려면 아래와 같은 명령어 입력하면 된다.  
```
wsl --export PerfectWSLDistro ./PerfectWSLDistro.tar
```
  
이제 "PerfectWSLDistro" 라는 WSL/Linux 환경이 "PerfectWSLDistro.tar"라는 파일에 함께 저장된다.    
다음은 이 파일을 다른 PC로 옮기거나, 다른 사람에게 배포하고, 사용하려는 PC의 **"~/AppData/Local/"** 폴더에 풀어서 "WSL"로 가져오면 된다.  
```
mkdir ~/AppData/Local/PerfectDistro
wsl --import PerfectDistro ~/AppData/Local/PerfectDistro ./PerfectWSLDistro.tar --version 2
```
  
덧붙여서 "~"는 홈 디렉토리를 나타내는 Linux에서는 친숙한 기호로 "PowerShell"에서도 사용할 수 있다.  
그러나 "명령 프롬프트"는 이에 대응하지 않고 전체 경로로 지정해야 한다.  
  
  
내보내기가 완료되면 "wsl --list -v" 명령으로 제대로 이행이 성공했지 확인한다.  
"wsl --list -v" 명령으로 마이그레이션 확인을 하는 예  
<pre>
C:\Users\Scott\Desktop> wsl --list -v
  NAME            STATE           VERSION
* Ubuntu-18.04    Stopped         2
  WLinux          Stopped         2
  Debian          Stopped         1
  PerfectDistro   Stopped         2
</pre>
  
최신 버전의 "Windows Terminal" 이라면 마이그레이션 한 WSL/Linux 환경을 자동으로 감지하고이 쉘이 자동으로 추가되는 것도 편리하다(이전 프로필을 삭제해야 하는 경우가 있으므로 주의).  
    
