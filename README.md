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