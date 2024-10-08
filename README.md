<div align="center">
  
# AWS와 NHN Cloud를 이용한 멀티클라우드 재해복구시스템
</div>

> ‼️이 프로젝트는 [NHN 클라우드를 활용한 IaaS 티켓팅 웹사이트](https://github.com/KDT-EEM/TickettingWeb/edit/main/README.md#5-클라우드-구축-과정)에서 클라우드 구조를 멀티 클라우드로 재구축한 프로젝트입니다.‼️

<div align="center">
  
## 충북대 정보통신공학부 19학번 졸업작품



<h1>📚STACKS</h1>

![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)

![Jenkins](https://img.shields.io/badge/jenkins-%232C5263.svg?style=for-the-badge&logo=jenkins&logoColor=white)
![Grafana](https://img.shields.io/badge/grafana-%23F46800.svg?style=for-the-badge&logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=Prometheus&logoColor=white)

![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)
![StrongSwan](https://img.shields.io/badge/StrongSwan-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)

![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white)
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)

![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)

</div>
# 👨‍💻팀원 구성

| 강석진   | 양현수    | 주상민   |
|--------------|--------------|--------------|--------------|--------------|
| <img src="https://avatars.githubusercontent.com/u/169283479?v=4" width="150" height="150"/> | <img src="https://avatars.githubusercontent.com/u/105273042?v=4" width="150" height="150"/> | <img src="https://avatars.githubusercontent.com/u/105378841?v=4" width="150" height="150"/> | <img src="https://avatars.githubusercontent.com/u/110795226?v=4" width="150" height="150"/> | <img src="https://avatars.githubusercontent.com/u/158993111?v=4" width="150" height="150"/> |
| [@goodniceboy](https://github.com/goodniceboy) | [@Dkdneidi](https://github.com/Dkdneidi) | [@sangmin310](https://github.com/sangmin310) |

# 🤸역할분담

**강석진(백엔드)** : NHN 아키텍처 설계 및 구축, Docker & Kubernetes 활용한 서버 구축 및 배포, NHN RDS, VPN 구축 및 연동, AWS,NHN RDS 동기화, failover 시스템 구현

**양현수(서버)** : NHN 아키텍처 구축, Docker & Kubernetes 활용한 Web 배포, NKS 오토스케일링 구축, CICD(Jenkins)파이프라인 구축, 모니터링(prometheus, Grafana)

**주상민(클라우드)** : AWS 아키텍처 구성 및 구축, 클라우드 아키텍처 구성 및 구축, 웹 페이지 구현, 데이터 베이스 구축

## 1. 프로젝트 소개
AWS 클라우드와 NHN 클라우드를 활용한 멀티 클라우드 티켓팅 웹 서비스

## 2. 개발배경 및 목적
티켓팅 웹 서비스의 경우 대형 이벤트나 인기 있는 콘서트의 티켓 판매 시 한번에 많은 사용자가 접속하게 되므로 서비스의 안정성과 확장성이 매우 중요합니다. 기존 단일 클라우드포

#### Autoscailing
- Deployment.yaml 파일과 Hpa.yaml 파일 작성.
- 부하 → CPU 확인 → Auto Scaling → CPU 확인.  
  command: ["ab", "-n", "100000", "-c", "100", "http://133.186.209.216/"]  
  Apache Benchmark 도구를 사용하여 http://133.186.209.216/ URL에 대해 부하 테스트를 수행.
  - `-n 100000`: 총 100,000개의 요청.
  - `-c 100`: 100개의 동시 연결 사용.

### NHN - RDS for mySQL
- RDS는 데이터베이스 패치 관리, 백업, 복구 등을 자동으로 수행.
- 자동 스케일링을 통해 마스터 인스턴스에 장애가 있을 시 예비 마스터가 마스터 역할 수행.

### NHN - RDS for mySQL 백업
- RDS 백업 설정을 통해 주기적으로 백업 실행 가능.
- 로그를 통해 백업이 정상적으로 실행되었는지 확인 가능.

### NHN - RDS for mySQL 모니터링
- NHN RDS에서 지원하는 모니터링 기능을 통해 RDS의 트래픽 변화량 확인 가능.

### NHN - Object Storage
- S3 API 자격 증명 기능을 통해 AWS의 S3 호환 기능 사용
- RDS와 Object storage를 연동하여 스크립트와 crontab 을 이용한 자동 백업 데이터 생성

### NHN - Block Storage
- NKS로 인스턴스를 생성하여 하나의 인스턴스 당 한 개의 블록 스토리지가 자동으로 생성.
- 블록 스토리지는 여러 개의 인스턴스에서 동시에 연결하여 사용할 수 있으며, 연결이 해제된 블록 스토리지는 다른 인스턴스에 연결하여 사용 가능.
- 스냅샷을 이용해 특정 시점의 블록 스토리지 상태를 저장 및 복구 가능.

### NHN - VPN 서버
- management 서버에 strongswan설치 ->  VPN 서버로 설정 -> AWS와 VPN으로 연동
- /etc/ipsec.conf 에 VPN 터널 가용성을 위해 tunnel 1 과 tunnel 2 정보 입력
- left id 에는 VPN 서버의 공인 ip, right에는 각 터널에 해당하는 외부 ip 입력
- leftupdown에는 각 터널의 내부 ip와 사용하는 AWS의 VPC CIDR 입력
- /etc/ipsec.secrets에 사전 공유키(PSK) 설정을 통해 VPN 서버의 공인 ip와 터널의 공인 ip 연결

### NHN - 클라우드 간 RDS 동기화
- VPN 서버에서 NHN RDS 와 AWS RDS 연동 및 코드 실행
- crontab 과 스크립트 파일 활용하여 실시간 자동 배포
- NHN RDS의 백업 데이터 베이스를 AWS RDS로 실시간 적용
- AWS 서비스에서 데이터 발생시 스크립트를 활용하여 NHN RDS와 동기화

### Router 53
- AWS와 NHN 의 로드벨런서 웹 주소로 헬스 체크 ID 설정
- crontab과 스크립트 파일을 활용하여 실시간 헬스 체크
- NHN 웹 서비스를 기본으로 하고 NHN 서버 다운 시 AWS 서버 작동







  



</div>
</details>

## 5.결과 영상

[3차 프로젝트 결과](https://www.youtube.com/watch?v=RK5H21K5i-w)
[![3차프로젝트 결과](https://img.youtube.com/vi/RK5H21K5i-w/0.jpg)](https://www.youtube.com/watch?v=RK5H21K5i-w)






