# rancher-vagrant

클라우드 종속적이지 않은 인프라 도커 친화적 인프라 구축

VM(virtual box)와 도커(rancher)를 활용하는 미니 개발 환경

구축환경:
- PROXY : http://proxy.dev.webnori.com/
- Rancher for Docker : http://docker.webnori.com/
- 인프라 코드관리 : https://github.com/psmon/rancher-vagrant
- 도커 이미지 관리 : https://hub.webnori.com

doc : http://wiki.webnori.com/display/rancher

# Vagrant명령

    vagrant up : vm을 구동시킨다.
    vagrant ssh : ssh접속
    vagrant halt : vm 중지
    vagrant reload : vm 재시작
    vagrant destroy : vm 삭제

# Vagrant 스냅샷

    vagrant snapshot list :현재 스냅샷 목록을 불려온다
    vagrant snapshot save [name] : 해당 스냅샷 이름으로 저장한다
    vagrant snapshot resotere [name] :해당 스냅샷 이름으로 복구한다

## VM 구조

-docker1 : RancherOS와 Agent 설치
-docker2 : Agent 설치
-docker3 : Agent 설치

# RancherOS 1.6 설치

    sudo docker run -d --restart=unless-stopped -p 8080:8080 rancher/server

# Rancher Agent 설치

    # Agent설치명령은 RancherOS 설치후 웹에서 명령어 제공됨
    sudo docker run --rm --privileged -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/rancher:/var/lib/rancher rancher/agent:v1.2.11 http://192.168.56.201/v1/scripts/8AD6C1A249259F7A715C:1546214400000:xR6wKh3ny8yQvIRxomDD6miSo

# 도커 컨테이너 추가

    Option 1: Add Container 를 통해 도커 레지트리 주소를 통해 구동가능
    Option 2: Add Stack명령으로 Dockercompose 파일베이스로 추가가능
    Option 3: 기본 환경이 Cattle이며 Swarm/Kuber 환경도 추가가능
    Option 4: 온프레미스 이지만, 다양한 클라우드 이용가능
    
[인프라 샘플](dockerinfra)


# node.js 자동 배포 실습

    docker build -t hub.webnori.com/node-web-app:latest .
    docker run -p 8080:8080 -d psmon/node-web-app:latest

    docker login hub.webnori.com
    docker push hub.webnori.com/node-web-app:latest

