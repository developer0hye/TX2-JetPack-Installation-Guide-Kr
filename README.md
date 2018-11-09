# tx2-Jetpack-installation-guide-kr

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
* **마우스** 와 **키보드**를 꽂을 **USB 허브** (TX2 개발보드는 USB 포트가 하나이기 때문에 USB허브는 거의 필수 입니다.)
* **모니터** 및 **Hdmi**
* **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**
* **PC** 와 **TX2 개발 보드**를 한 네트워크에 연결하기 위한 공유기

1. TX2에 기본적으로 flash 되어있는 Ubuntu 16.04 설치

1.1. TX2에 전원을 넣기 전, USB 허브를 TX2에 연결하고 마우스와 키보드, 모니터의 Hdmi 를 연결합니다.
  
1.2. TX2에 전원을 넣습니다.
 
1.3. 화면에 출력된 안내문에 따라 순서대로 커맨드를 입력합니다.
 ```
 cd ~/NVIDIA-INSTALLER/
 sudo ./installer.sh
 password:nvidia
 ```
**기본적으로 설정된 유저 id와 password는 id: nvdia/ pw: nvidia 입니다.**
**password 는 입력하더라도 화면에 출력되지 않습니다. 혼란스러워 하지 마시고 올바르게 nvidia 입력 후 엔터를 입력하면 됩니다.**
 
 설치가 완료된 후 재부팅을 실행합니다.
 ```
 reboot
 ```

TX2 는 잠시 내버려두고 다음단계로 넘어가도록 합니다.

2. **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**에 JetPack 을 설치합니다.

>[JetPack 3.3 설치 링크](https://developer.nvidia.com/embedded/jetpack)

![jetpack3 3](https://user-images.githubusercontent.com/35001605/48245783-f59b6d80-e42f-11e8-88be-bb99fa084a77.png)

2.1 위의 [링크](https://developer.nvidia.com/embedded/jetpack)를 들어간 뒤에 사진에 보라색 밑줄로 강조되어 있는 링크를 클릭하여 JetPack 3.3 파일(**JetPack-L4T-3.3-linux-x64_b39.run**)을 다운로드 받습니다.

**다운로드를 위해 회원가입을 해야합니다.**

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
