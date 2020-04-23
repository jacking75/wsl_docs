# WSL2
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
  
