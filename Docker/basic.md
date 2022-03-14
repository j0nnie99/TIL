# Docker란

도커는 **컨테이너 기반의 오픈소스 가상화 플랫폼**

버전이 다른 다양한 프로젝트를 관리하기 위해 각 프로젝트를 관리할 수 있는 공간(집)에 컨테이너(프로젝트 공간)을 할당하여 OS를 효율적으로 사용할 수 있도록 한 것

# Docker의 필요성

가상환경을 설치하여 버전을 구분하게 되면 컴퓨터의 자원을 각 프로젝트마다 일정 수치만큼 할당해야 하여 자원의 소모가 크기 때문에 공통으로 사용할 수 있는 OS 기능들을 제외한 나머지 부분만 컨테이너로 묶어서 사용한다.

# Docker Image

이미지: 리눅스 컴퓨터의 특정 상태를 캡쳐해서 저장해둔 것

도커는 우선 내 컴퓨터에서 이미지를 찾아본 뒤, 없으면 docker hub에 올라와 있는 이러한 이미지를 다운받아 환경이 설치되어 있지 않은 상황에서도 프로그램이 작동할 수 있게 만들어준다

# 명령어

## run

이미지가 없을 경우 다운로드한 뒤, 해당 이미지를 컴퓨터에 컨테이너로 만든다

- --name: 컨테이너 이름 지정
- -v: 볼륨. 컨테이너와 특정 폴더 공유.
- -p: 포트.

## -it

컨테이너를 연 뒤 그 환경 안에서 CLI를 사용

## exec

실행 

## ps

현재 작업이 진행 중인 컨테이너 표시

-a 옵션을 통해 현재 작업을 하지 않고 있는 컨테이너도 언제 중지했는지 등의 정보와 함께 확인 가능

### 이미지 삭제

```docker
docker stop $(docker ps -aq)
docker system prune -a
```

# Dockerfile

나만의 이미지를 만들기 위한 설계도

- 필요성 → nodejs + http-server가 있어야 실행할 수 있는데 docker hub의 이미지를 사용하면 매번 http-server를 설치해야 함. 따라서 둘을 같이 사용할 수 있는 상태를 이미지로 생성 필요

# Docker Compose
```docker
# 실행 명령어
docker-compose up
```