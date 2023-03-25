---
title: Docker 사용법 (2) - Dockerfile 사용해 보기
categories: [BE, Docker]
tags: [docker]
date: 2023-03-26 03:00
---

![Docker Image](https://raw.githubusercontent.com/docker-library/docs/c350af05d3fac7b5c3f6327ac82fe4d990d8729c/docker/logo.png)

## Dockerfile이란?

---

> 사용자가 설정한 이미지 설정 파일을 의미한다.
{:.prompt-info}


## 왜 사용할까?

---

예시를 통해 Dockerfile을 왜 사용하는지 알아보자.
#### (Dockerfile 없이) **ubuntu(이하 우분투) 설치**, **설치한 우분투에 git을 설치**하기
> 1. `docker pull ubuntu` 명령으로 ubuntu 이미지를 다운로드 한다.
> 2. 다운로드한 이미지를 컨테이너화한다.
> 3. 우분투 컨테이너를 실행한다.
> 4. `apt update && apt install git -y` 명령어를 통해 우분투에 git을 설치한다.

#### Dockerfile을 사용해서 **우분투 설치**, **설치한 우분투에 git을 한 번에 설치**하기
> 1. `Dockerfile`(.txt와 같은 확장자 없이 Dockerfile)을 생성한다.
> 2. Dockerfile에 설정에 해당하는 내용을 작성한다.
> 3. Dockerfile을 빌드 해서 우분투를 설치하고, 설치한 우분투에 git을 설치한다.

## Dockerfile 사용해 보기

---

이번 포스트에서는 ubuntu 이미지를 다운로드 받고 동시에 git을 설치하는 설정 파일(Dockerfile)을 만들어서 위의 과정을 한 번에 처리해 보겠다.

1. 원하는 경로에서 `Dockerfile`을 생성한다.

2. 파일 생성 후 아래와 같이 Dockerfile의 내용을 채워준다.
	```dockerfile
	FROM ubuntu
	RUN apt update
	RUN apt install git -y
	```
	> FROM ubuntu: 우분투 이미지에서
	>
	> RUN apt update: 패키지 관리 도구 업데이트
	>
	> RUN apt install git -y: 패키지 관리 도구를 통해 git을 설치한다 (-y는 프로그램 설치 동의를 의미)

3. Dockerfile을 사용해 도커의 이미지를 만든다.
	```zsh
	$ docker build -t ubuntu_git .
	```
	> -t(tag): 이미지 이름을 지정하는 옵션
	>
	> ubuntu_git: 만들고자 하는 이미지 이름(예: test, abc, zzz)
	>
	> .의 의미: Dockerfile 파일이 있는 위치를 의미한다.
4. `ubuntu_git` 이미지를 컨테이너화하기
	```zsh
	$ docker run -it ubuntu_git /bin/bash
	```
	위 명령어는 아래 명령어들을 한 번에 실행하는 것과 같은 결과를 보여준다.
	> 1. docker create ubuntu_git
	> 2. docker start {CONTAINER_ID}
	> 3. docker exec -it {CONTAINER_ID} /bin/bash
5. 실행한 우분투에서 git 설치 확인해 보기
```zsh
root@0e37a27047cf:/# git -v
```

> Dockerfile을 사용해서 여러 과정을 상대적으로 쉽게 처리할 수 있는 방법을 간단히 알아봤다.
>
> 천천히, 조금씩 하지만 꾸준히 포스트 해볼 예정이다.
{:.prompt-info}