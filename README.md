# PhotonCloudNetworkSolution_sum
Unity 기술 이용 다자간 협업 솔루션 프로젝트


### source code(private) 
https://github.com/sywtit/PhotonCloudNetworkSolution


### 연구 배경
-----

가상현실(Virtual Reality) 기술은 최근 주목받고 있는 컴퓨팅 기술로, 여러 서비스들과 융합할 수 있는 인프라 기술이다. 

이 연구는 위 기술을 이용해서 산업현장에서 쓰이는 VR 가상 장비와 “원격”으로 관제 센터가 소통을 하는 과정을 기반으로 한다. 여기에 온라인 게임과 같은 다자간으로 소통이 이뤄지는 시스템을 바탕으로, 여러 개의 관제 서버가 한번에 scene 에 접근하여 작업을 할 수 있게 만들기 위해서 “Unity Photon Realtime”- Photon Cloud, “Photon Voice”서비스를 이용한다.

이 솔루션을 통해 원격의 상태에서 작업 공유와 참여가 가능해지고 따라서 업무작업이 활발하게 이뤄지고, 관계자들의 편리한 협업활동을 지원한다.

### 연구 진행 과정
-----

**1. VR/AR 기반 unity 교육 진행**

<img src = "https://user-images.githubusercontent.com/52434154/112987575-d6870d00-919d-11eb-883c-85a47115d714.png">

**2. “Unity Photon Cloud”- PUN2를 이용해 각 client인 관제서버 네트워크 연결 후 공유하고자 하는 room에 접근**

<img src = "https://user-images.githubusercontent.com/52434154/112987705-fb7b8000-919d-11eb-8ced-00bd0c376e52.png" width = "450" height = "200">

**3. RPC function & prefab Instantiation으로 공유하는 room 안에서 작업가능 요소와 공통된 뷰 제공**

<img src = "https://user-images.githubusercontent.com/52434154/112987933-3978a400-919e-11eb-9264-7bc1b9edcdac.png" width = "450" height = "200">

### 사용 기술
-----

**1. Photon CLOUD**
  * REALTIME
  * PUN
  * VOICE
  
**2. unity**

### 결과 및 분석
-----

**1. Photon Cloud에 접근한 관제 서버 Client 2개 연결해 1:1 통신 구현**


<p align="center"><img src = "https://user-images.githubusercontent.com/52434154/112988583-f9fe8780-919e-11eb-96a1-5784b7ad9691.png" width = "450" height = "200"></p>

각 관제 서버 Client가 임의로 지정하는 client nickname 으로 room 에 접근하는 main 화면 구현 → wait for opponent(other clients)

**-공유하는 scene 환경-**

**Robot(object)** - 공동 작업이 필요한 object를 의미<br>
**RotateMachine(button)** – 특정 object를 회전시키면서 관제 서버에서 자세히 관찰 가능<br>
**view(camera, object)** - player(view 이동 script 생성 → 시연 시각화를 위해 sphere형태를 가진다)를 통해 각 client 가 원하는 뷰를 키보드와 마우스 input를 이용해서 볼 수 있음<br>
**createObject(button)** - 시연 시각화를 위해 object를 sphere로 지정, 이후에 생성하려는 prefab가 뭐가 들어가든 적용 가능. 관제서버가 공유하는 scene에서 요소를 넣어 상대에게 보여주려고 할 때 사용되는 기능.(draggable by client)<br>
**createText(button)** – text 생성 및 공유, 통신하는 상대에게 특정 부분의 구체적인 설명이 필요할 때 사용되는 기능

RotateMachine 과 view는 각자 다른 부분을 관찰할수 있게 지원한다.

<p align="center"><img src = "https://user-images.githubusercontent.com/52434154/112988874-4d70d580-919f-11eb-9bec-954bc741943d.png" width = "500" height = "300"></p>

**2. 다자간 통신 구현 & 오디오 스트림 환경 구성**


<p align="center"><img src = "https://user-images.githubusercontent.com/52434154/112989001-6d07fe00-919f-11eb-9c1c-fd83959c7001.png" width = "500" height = "300"></p>

**오디오 스트림** – photon voice 활용

