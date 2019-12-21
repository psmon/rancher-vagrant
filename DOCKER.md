# 기본 도커 명령

 개발레벨에 필요한 핵심적인 도커명령으를 정리

## 도커 빌드

    docker build -t hub.webnori.com/node-web-app:latest .    

## 도커 실행

    docker run -p 8080:8080 -d hub.webnori.com/node-web-app:latest

    환경주입 : -e env=prod   -컨테이너 레벨에서 사용되는 환경변수를 셋팅합니다.

## 도커 배포

    docker login hub.webnori.com
    docker push hub.webnori.com/node-web-app:latest


## 도커 실행중인것 리스트업

    docker ps

## 도커 실행중인것 중지

    docker stop {도커인스턴스 ID}   - 중복이 없으면 앞자리만 사용가능 


## 로컬 한꺼번에 삭제 : 자신의 로컬에서만 사용할것

    # 전체 초기화 할때 이용 (리눅스용)    
    docker stop $(docker ps -a -q)
    docker start $(docker ps -a -q)
    docker rm $(docker ps -a -q)
    docker rmi $(docker images -q)

    # 이미지 정리
    docker image prune -a


# 도커 활용하기

