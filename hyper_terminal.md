# Hyper 터미널 앱
WSL을 사용할 때 Hyper 터미널 앱을 사용하면 편리하다
  
## 설치
[공식 사이트의 다운로드](https://hyper.is/#installation )에서 받아서 설치한다.
  
설치 후 실행하면 cmd 실행 화면이 나온다.
  
  
## wsl 설정
하이퍼 터미널 앱을 실행 후 왼쪽 상단의 메뉴를 통해서 [Edit]-[ Preferences] 항목을 선택한다.  

아래 부분을 찾아서 변경한다.   
```
shell: 'C:\\Windows\\System32\\wsl.exe',
shellArgs: [],
```  
저장 후 재 시작하면 wsl을 실행한다.     
  
  
  
## 확장 기능
[awesome-hyper](https://github.com/bnb/awesome-hyper )에 많은 플러그인을 소개하고 있다.
  
### 설치
npm 패키지의 이름을 설정 파일의 'plugins' 항목에 입력하면 설치할 수 있다.    
  
#### hyper-material-theme
인기 있는 테마.  
  
#### hyper-overlay  
Linux에서는 tilda나 guake에서 채용 되고 있는 Dropdown Terminal 기능을 사용할 수 있게 해주는 확장 기능이다.  
아래 그림처럼 설정 키를 누르면 바로 Hyper가 표시된다. 표시 되지 않을 때는 태스크 바 등에도 표시 되지 않으므로 다루기 편한다.  
![hyper-overlay](https://camo.qiitausercontent.com/74110995c212c9168df6afff07f0b8bf0181d7d4/68747470733a2f2f6d656469612e67697068792e636f6d2f6d656469612f3574375a3565524d535875414a4a5043726c2f67697068792e676966)    
    
#### hyperpower  
키보드 타이핑 할 때 파티클을 표시해 준다.    
  
#### hyperlinks
https://www.npmjs.com/package/hyperlinks  
URL을 하이퍼링크 해주는 플러그인   Hyper의 화면이나 default 브라우저에서 URL를 열어준다.
  
#### hyper-tab-icons
https://www.npmjs.com/package/hyper-tab-icons  
Tab 아이콘을 실행해하고 프로세스에 맞추어서 변경해주는 아이콘  
Node를 동작시키고 있을 때는 탭에 Node의 아이콘이 표시된다.  

#### hyper-ayu
https://www.npmjs.com/package/hyper-ayu  
테마 중의 하나이다  
  
#### hyper-opacity
https://preview.npmjs.com/package/hyper-opacity  
Windows 환경에서도 터미널을 반투명으로 해주는 플러그인  
Electron의 문제인지 default로는 Mac OS만 반투명 대응하고 있으므로 이것을 설치하면 윈도우도 반투명하게 해준다  
포커스를 받을 때와 포커스를 받지 않을 때의 반투명도가 달라진다는 이점도 있다  
    
	
	
## 단축키
  
| 단축키                                                     | 설명                           |
|--------------------------------------------------------------------|--------------------------------|
| Ctrl + Shift + i                                                   | 개발자 툴 실행       |
| Ctrl + Shift + r                                                   | 윈도우 클리어. 같은 윈도우 내의 탭 등의 표시 모두가 클리어된다             |
| Ctrl + Shift + F5                                                  | 윈도우 클리어. 같은 윈도우 내의 탭 등을 모두 닫아서, 기동 했을 때의 상태와 같게 된다             |
| Ctrl + ,                                                           | 설정 파일(.hyper.js)을 연다  |
| Ctrl + 0                                                           | 폰트 사이즈를 default로 한다 |
| Ctrl + ;                                                           | 폰트 사이즈를 크게         |
| Ctrl + –                                                           | 폰트 사이즈를 작게         |
| Ctrl + Shift + n                                                   | 신규 윈도우 실행           |
| Ctrl + Shift + m                                                   | 윈도우 최소화             |
| F11                                                                | 윈도우 풀스크린 화   |
| Ctrl + Shift + q                                                   |                                |
| Alt + F4                                                           | 윈도우 닫기             |
| Ctrl + Shift + ]                                                   |                                |
| Ctrl + Shift + →                                                   |                                |
| Ctrl + Alt + →                                                     |                                |
| Ctrl + Tab                                                         | 오른쪽 탭으로 이동                 |
| Ctrl + Shift + [                                                   |                                |
| Ctrl + Shift + ←                                                   |                                |
| Ctrl + Alt + ←                                                     |                                |
| Ctrl + Shift + Tab                                                 | 왼쪽 탭으로 이동                |
| Ctrl + 숫자                                                        | 숫자 번호의 탭으로 이동           |
| Ctrl + PageUp                                                      | 다음 Pane에 이동                 |
| Ctrl + PageDown                                                    | 전의 Pane에 이동                 |
| Ctrl + Shift + d                                                   | Pane을 세로로 분할                |
| Ctrl + Shift + e                                                   | Pane을 가로로 분할                |
| Ctrl + Shift + w                                                   | Pane을 닫는다                   |
| Ctrl + Shift + c                                                   | 복사                        |
| Ctrl + Shift + v                                                   | 붙여 넣기                       |
| Ctrl + Shift + a                                                   | 모두 선택                        |
| Ctrl + ←                                                           | 앞 단어로 커서 이동       |
| Ctrl + →                                                           | 다음 단어로 커서 이동       |
| Home                                                               | 선두로 커서 이동           |
| End                                                                | 꼬리로 커서 이동           |
| Ctrl + BackSpace                                                   | 앞 단어를 삭제                 |
| Ctrl + Del                                                         | 다음 단어를 삭제                 |
| Ctrl + Shift + k                                                   | 버퍼 삭제                 |
| Ctrl + Shift + u                                                   | 플러그인 갱신               |  
  
  
  