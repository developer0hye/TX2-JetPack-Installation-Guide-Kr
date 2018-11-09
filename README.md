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

위는 TX2 를 이용하여 개발을 할 수 있도록 제공되는 tx2 Developer Kit(개발자 키트)의 구성이다.

**TX2 모듈** 자체의 크기는 **(50mm x 87mm)** 로 그리 크지 않지만 **TX2 개발 보드**의 크기는 **(17cm x 17cm)** 으로 상당히 크다.

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
* **마우스** 와 **키보드**를 꽂을 **USB 허브**
* **모니터** 및 **Hdmi**
* **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**
* **PC** 와 **TX2 개발 보드**를 한 네트워크에 연결하기 위한 공유기

1. TX2에 기본적으로 flash 되어있는 Ubuntu 16.04 설치
 1.1 우선 TX2에 전원을 넣기 전에 TX2 를 컨트롤 하기 위해 USB 허브를 TX2에 꽂습니다.


2. **Ubuntu 16.04** 가 설치된 **인텔 프로세서 기반 PC**에 JetPack 을 설치합니다.

>[JetPack 3.3 설치 링크](https://developer.nvidia.com/embedded/jetpack)

![jetpack3 3](https://user-images.githubusercontent.com/35001605/48245783-f59b6d80-e42f-11e8-88be-bb99fa084a77.png)
