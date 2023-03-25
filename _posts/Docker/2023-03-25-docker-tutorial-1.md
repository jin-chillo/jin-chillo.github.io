---
title: Docker 사용법 (1) - 도커 설치, 도커로 프로그램 설치
categories: [BE, Docker]
tags: [docker]
date: 2023-03-25 16:00
---

![Docker Image](https://raw.githubusercontent.com/docker-library/docs/c350af05d3fac7b5c3f6327ac82fe4d990d8729c/docker/logo.png)

## 도커 설치 및 설치 확인

---

1. [공식 홈페이지](https://www.docker.com/products/docker-desktop/)에서 다운로드 및 설치하기
2. 정상적으로 설치되었는지 확인해 보기
   ```zsh
   $ docker -v
   ```
   ###### 결과
   > Docker version 20.10.23, build 7155243
3. 설치한 도커 프로그램 실행


## 도커로 Ubuntu(이하 우분투) 설치해 보기

---

1. 우분투 `이미지` 내려받기
   ```zsh
   $ docker pull ubuntu  # 가장 최신 버전의 ubuntu 이미지를 받는다.
   # ...
   ```
   > docker pull ubuntu와 docker pull ubuntu:latest는 같은 명령을 실행한다. (가장 최신 버전의 우분투 이미지를 받는다.)
2. 내려받은 우분투 이미지 확인
   ```zsh
   $ docker images
   ```
   ###### 결과
   > REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
   >
   > ubuntu       latest    08d22c0ceb15   2 weeks ago   77.8MB
3. 우분투 이미지로 `컨테이너` 만들기
   ```zsh
   $ docker create -it ubuntu  # -it: Interactive Terminal mode
   ```
   ###### 결과
   > 0562d8be3f83cd95fd67307dbb4d7cd89248faaab9cc0b2feb3b15b39df3489e
4. 우분투가 정상적으로 컨테이너화 됐는지 확인하기
   ```zsh
   $ docker ps -a  # ps: Process Status, -a(--all): Show all
   ```
   ###### 결과
   > CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS    PORTS     NAMES
   > 0562d8be3f83   ubuntu    "/bin/bash"   32 seconds ago   Created             nifty_dijkstra

## 도커로 설치한 우분투 실행해 보기

---

1. 우분투 컨테이너 실행하기
   ```zsh
   $ docker start nifty_dijkstra
   ```
   ###### 결과
   > nifty_dijkstra
2. 실행 중인 컨테이너 확인
   ```zsh
   $ docker ps
   ```
   ###### 결과
   > CONTAINER ID   IMAGE     COMMAND       CREATED              STATUS          PORTS     NAMES
   > 0562d8be3f83   ubuntu    "/bin/bash"   About a minute ago   Up 47 seconds             nifty_dijkstra
3. 우분투 컨테이너의 bash 실행
   ```zsh
   $ docker exec -it nifty_dijkstra /bin/bash
   ```
   ###### 결과
   > root@0562d8be3f83:/#

> 도커를 사용해서 내 PC에 리눅스 계열의 OS인 Ubuntu(우분투)를 설치하고 실행하는 것까지 진행해 봤다.
>
> 많은 부분이 생략되어 있지만 한 번에 너무 많은 양을 포스트하기 보다 조금씩 찍먹하면서 앞으로 조금 더 촘촘하게 도커에 대해 포스트 해 볼 예정이다.
{:.prompt-info}

