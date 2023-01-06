# AR contents product viewer and order system
2021년 1학기 소프트웨어설계 과목 프로젝트

## Summary  
- 기존의 2D 사진으로 볼 수 있던 제품(음식)을 Image Tracking을 사용하여 인식, 판별하여 그에 해당하는 3D모델을 AR을 통해 볼 수 있는 어플리케이션  

## Demo
<p align="center"><img width='70%' src="https://user-images.githubusercontent.com/65859079/210742574-a701fa84-dab1-4f01-9ec3-96f266c39311.png"/>
<img width='70%' src="https://user-images.githubusercontent.com/65859079/210742666-df84090c-b9bd-44b8-85d6-4c9982bdb8ba.png"/></p>

## Funtion, Implementation
- Unity의 AR Foundation에서 제공하는 AR Tracked Image Manager와 Reference Image Library를 사용   
- C#으로 작성한 TCP 소켓통신을 이용  
### [ AR contents product viewer ] 
AR 구현을 원하는 제품의 2D 사진을 Reference Image Library에 추가하고 해당 제품의 3D모델은 Gameobject에 담아둔다.   
AR Tracked Image Manager을 통해 이미지 값이 Detecting 되거나 Update되면 해당 Reference Image의 이름을 기반으로 해당하는 Gameobject을 선택한다.  
objet를 Tracking되고 있는 Image의 Position과 Rotation 값을 가지고 연동해주고 Object를 켜줌으로써 scene에 표시한다.  
### [ Order system ]
server를 먼저 만들고 그 server에 listener를 만든다.  
listener는 client 쪽에서 넘어올 socket을 받아주는 역할을 한다.  
client 쪽에서 socket을 생성한 다음에 socket을 넘겨주면 server 쪽 listener가 socket을 받는다.  
client 쪽에서 받은 socket을 client socket이라고 하고 server 쪽에서 받은 socket을 server socket이라고 한다.  
이 둘이 서로 통신을 하기 위해선 input stream과 output stream이라는 data가 오가는 통로도 필요하다.  
이러한 과정을 통해서 실시간으로 client쪽에서 server로 데이터가 넘어가면 server가 data를 표시해주고 client도 data를 표시 받는다.  

## Usage
- Unity Version(Owner): 2020.1.13f1  
- Unity Version(Customer): 2020.1.13f1  
- AR Foundation Version: 4.0.12  

repository를 clone하고 owner와 customer를 unity에서 따로 실행시킨다.  
해당 project는 android용으로 제작하였으므로 android에 build하여 사용한다.  
현재는 Customer\Assets\Res\Prefab에 위치한 ironman.png와 hulkbuster.png가 image tracking에 등록되어 있다.  
소켓통신의 경우 port forwarding과 device의 ip address가 필요하다.  
 해당 내용에 대한 자세한 설명은 reference의 유니티 C# TCP 소켓통신으로 채팅하기 참고

## Reference
[유니티 C# TCP 소켓통신으로 채팅하기](https://www.youtube.com/watch?v=y3FU6d_BpjI)  
[유니티 AR Foundation 강좌 - Image Tracking + 소스코드](https://blog.naver.com/progagmer/222247604964)  
[앱 튕김 현상 해결](https://gigglehd.com/gg/soft/10829084)
