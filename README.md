# TX2-JetPack-Installation-Guide-Kr

## TX 2
![tx2_module_170203_0017_transp_2000px](https://user-images.githubusercontent.com/35001605/48240171-24581a80-e415-11e8-838d-a77551b386b4.png)
* NVIDIA 에서 개발한 AI 컴퓨팅에 적합한 고성능 저전력 임베디드 모듈 시스템
  * Processor: ARM 기반 / HMP Dual Denver 2/2 MB L2 + Quad ARM® A57/2 MB L2
  * Gpu: (Pascal Arch/ Cuda 256 Core)
  * Ram: 8GB (LPDDR4)
  * Storage: 32GB eMMC, SDIO, SATA
  * Size: 50mm x 87mm
  * 4Kx2K 60hz HEVC Video 실시간 디코딩 가능/ 4Kx2K 30hz HEVC Video 실시간 인코딩 가능
  
>[TX2 Developer Kit 구매 링크](http://www.mdsshop.co.kr/product/detail.html?product_no=98&cate_no=43&display_group=1)
  
### Developer Kit
![intelligent-machines-jetson-tx2-developer-kit-625-ud](https://user-images.githubusercontent.com/35001605/48240330-caa42000-e415-11e8-95e3-9cde11624f16.jpg)

* 구성
  * NVIDIA Jetson TX2 Developer Board (17cm x 17cm)
  * AC Adapter
  * USB Micro-B to USB A Cable
  * USB Micro-B to Female USB A Cable
  * Rubber Feet (4)
  * Quick Start Guide
  * Safety Booklet
  * Antennas to connect to Wi-Fi enabled devices (2)

위는 TX2 를 이용하여 개발을 할 수 있도록 제공되는 TX2 Developer Kit(개발자 키트)의 구성입니다.

**TX2 모듈** 자체의 크기는 **(50mm x 87mm)** 로 그리 크지 않지만 **TX2 개발 보드**의 크기는 **(17cm x 17cm)** 으로 상당히 큽니다.

![20181109_100614](https://user-images.githubusercontent.com/35001605/48244426-0dbbbe80-e429-11e8-836a-c2ef39ffcb95.jpg)

## JetPack
![jetpack_falcon](https://user-images.githubusercontent.com/35001605/48244860-3c3a9900-e42b-11e8-8689-c490225d0fea.jpg)
~~JetPack 은 사실 하늘을 날기 위한 수단~~ 
* JetPack SDK는 NVIDIA에서 제공하는 AI 응용 프로그램 구축을 위한 종합적인 솔루션
  * OS 이미지
  * 각종 라이브러리 및 API
  * 개발 도구
  * 샘플
  * 문서
* 설치전 선행 작업 및 준비물 필요

### 선행 작업 및 준비물
* **마우스** 와 **키보드**를 연결할 **USB 허브** (TX2 개발보드는 USB A 포트가 하나이기 때문에 USB허브는 거의 필수 입니다.)
* **모니터** 및 **HDMI**
* **USB Micro-B to USB A Cable**
* **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**(가급적이면 가상머신이 아닌 직접 설치하는 것을 추천합니다.)
* **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC** 와 **TX2 개발 보드**를 동일한 내부 네트워크망에 연결하기 위한 공유기

1. TX2에 기본적으로 flash 되어있는 Ubuntu 16.04 설치

1.1. TX2에 전원을 넣기 전, USB 허브를 TX2에 연결하고 마우스와 키보드, 모니터의 Hdmi 를 연결합니다.
  
1.2. TX2에 전원을 넣습니다.
 
1.3. 화면에 출력된 안내문에 따라 순서대로 커맨드를 입력합니다.
 ```
 cd ~/NVIDIA-INSTALLER/
 sudo ./installer.sh
 password:nvidia
 ```
**기본적으로 설정된 유저 id와 password는 id: nvidia/ pw: nvidia 입니다.**
**password 는 입력하더라도 화면에 출력되지 않습니다. 혼란스러워 하지 마시고 올바르게 nvidia 입력 후 엔터를 입력하면 됩니다.**
 
 설치가 완료된 후 재부팅을 실행합니다.
 ```
 reboot
 ```

TX2 는 잠시 내버려두고 다음단계로 넘어가도록 합니다.

2. **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**에 JetPack 을 설치합니다.

>[JetPack 3.3 설치 링크](https://developer.nvidia.com/embedded/jetpack)

![jetpack3 3](https://user-images.githubusercontent.com/35001605/48245783-f59b6d80-e42f-11e8-88be-bb99fa084a77.png)

2.1 위의 [링크](https://developer.nvidia.com/embedded/jetpack)를 들어간 뒤에 사진에 보라색 밑줄로 강조되어 있는 링크를 클릭하여 JetPack 3.3 파일(**JetPack-L4T-3.3-linux-x64_b39.run**)을 다운로드 받습니다.(**다운로드를 위해 회원가입을 해야합니다.**)

JetPack 3.3 은 기본적으로 CUDA Toolkit 9.0, cuDNN v7.1.5, OpenCV 3.3.1 을 지원합니다. 


2.2 아래의 커맨드를 순서대로 입력하여 **JetPack-L4T-3.3-linux-x64_b39.run** 파일을 옮기고 실행 가능하도록 
권한을 설정합니다.
 
```
mkdir ~/JetPack
mv ~/Downloads/JetPack-L4T-3.3-linux-x64_b39.run ~/JetPack
cd ~/JetPack
chmod 777 ./JetPack-L4T-3.3-linux-x64_b39.run
```

2.3 다운로드 받은 **JetPack-L4T-3.3-linux-x64_b39.run** 파일을 실행합니다.
```
cd ~/JetPack
./JetPack-L4T-3.3-linux-x64_b39.run
```
2.4 아래의 사진과 같이 설정하며 진행합니다. (별도의 설정없이 라이브러리는 모두 설치하도록 하겠습니다.)
![jetpack 0](https://user-images.githubusercontent.com/35001605/48248885-6d6f9500-e43c-11e8-8a34-0f67fafd086f.png)
![jetpack1](https://user-images.githubusercontent.com/35001605/48248998-e242cf00-e43c-11e8-9536-b32d2d55fe22.png)
![jetpack 2](https://user-images.githubusercontent.com/35001605/48249006-e7a01980-e43c-11e8-9bfa-932c79879235.png)
![jepack3](https://user-images.githubusercontent.com/35001605/48249013-e969dd00-e43c-11e8-8c81-310e0360f6dc.png)
![jetpack4](https://user-images.githubusercontent.com/35001605/48249014-ea9b0a00-e43c-11e8-89ac-2b5a164aee24.png)
![jetpack5](https://user-images.githubusercontent.com/35001605/48249840-9c3b3a80-e43f-11e8-907d-13e6cbed451b.png)

이 단계까지 설치가 진행되었다면 **TX2 개발 보드** 와 **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**를 

서로 동일한 내부 네트워크망에 연결 되도록 한 공유기에 물려줍니다. 이 후 계속해서 설치를 진행합니다.


![jetpack6](https://user-images.githubusercontent.com/35001605/48250048-503cc580-e440-11e8-8c2d-f6fa27cbb616.png)
![jetpack7](https://user-images.githubusercontent.com/35001605/48250102-82e6be00-e440-11e8-948d-19660d8c219d.png)
![jetpack8](https://user-images.githubusercontent.com/35001605/48250232-f25cad80-e440-11e8-95cd-a1265659c67c.png)

서로 동일한 내부 네트워크망에 성공적으로 연결이 되어있다면 위의 사진과 같이 장치가 인식된 모습을 볼 수 있습니다. 

계속해서 설치를 진행하면 아래의 창과 같은 안내문이 뜹니다.

![jetpack9](https://user-images.githubusercontent.com/35001605/48250277-1ae4a780-e441-11e8-8240-7699b11ee245.png)


2.3.1 TX2 의 전원을 종료합니다.(전원선 또한 뽑아주는 것이 좋습니다.)

2.3.2 **USB Micro-B to USB A Cable**을 준비하고, USB A 커넥터를 **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**에 연결하고 USB Micro-B 커넥터를 **TX2 개발 보드**에 연결하고 전원선을 다시 TX2에 연결합니다.

![usb to micro](https://user-images.githubusercontent.com/35001605/48250862-18834d00-e443-11e8-8bad-6b06bf06306c.jpg)
![pc](https://user-images.githubusercontent.com/35001605/48250865-19b47a00-e443-11e8-89ce-a06c6adc8a61.jpg)
![board](https://user-images.githubusercontent.com/35001605/48250866-1ae5a700-e443-11e8-88d0-b2e4f1e8f5b7.jpg)

2.3.3 **POWER 버튼**을 누르고 빛의 속도로 **FORCE RECOVERY** 버튼을 꾹 눌러줍니다.

2.3.4 **FORCE RECOVERY** 버튼을 계속 누른 상태로 **RESET** 버튼을 누르고 뗍니다. 2초 정도 대기한 후 **FORCE RECOVERY** 버튼에서 손을 뗍니다.

![recoverymode](https://user-images.githubusercontent.com/35001605/48252005-dd831880-e446-11e8-8ddb-4985dc4d7511.gif)


좌측에서 첫 번째에 위치한 버튼이 RESET 버튼이며, 세 번째 버튼이 FORCE RECOVERY 버튼, 네 번째 버튼이 POWER  버튼입니다.

2.3.5 **TX2 개발 보드**가 성공적으로 recovery mode로 전환됐을 경우 **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**에서 

커맨드 창에 lsusb 입력시 **TX 개발 보드**가 **NVidia Corp.** 로 잡히는 것을 확인하실 수 있습니다.

![successsss](https://user-images.githubusercontent.com/35001605/48252417-0fe14580-e448-11e8-8d93-a59fd9114fbc.png)


이후 아래의 커맨드 창에서 엔터를 입력합니다.

![jetpack9](https://user-images.githubusercontent.com/35001605/48250277-1ae4a780-e441-11e8-8240-7699b11ee245.png)


설치가 진행됩니다.

![jetpack10](https://user-images.githubusercontent.com/35001605/48252522-5a62c200-e448-11e8-861f-8a7bd94fd9ef.png)

![finish](https://user-images.githubusercontent.com/35001605/48253807-93e8fc80-e44b-11e8-8426-3ee2b0b662cb.png)

![realfinshed](https://user-images.githubusercontent.com/35001605/48253955-f215df80-e44b-11e8-8122-87a2fa568491.png)

설치가 완료되었습니다!

3. 마무리

3.1. TX2 를 재부팅 합니다.

3.2. TX2 에서 설치가능한 패키지의 목록을 업데이트 하고 현재 설치되어 있는 패키지를 최신화하도록 업그레이드 커맨드를 입력합니다.
```
sudo apt-get update
sudo apt-get upgrade
```

현재 우분투의 최신 버전이 18.04이기 때문에 부팅시 OS 업데이트에 대한 의사여부를 묻는 안내창이 뜰 수 있습니다.

저 같은 경우에는 18.04 버전에서 정상적으로 호환이 안되는 라이브러리 및 API가 간혹 존재하는 것을 확인하였습니다.

되도록이면 OS 업데이트는 무시하시고 16.04 를 사용하는 것을 추천합니다.

이제 TX2 와 즐거운 시간을 보내시면 됩니다!
