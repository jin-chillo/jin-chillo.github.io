---
title: Docker란?
categories: [BE, Docker]
tags: [docker]
date: 2023-03-23 21:04
last_modified_at: 2023-03-25 15:35
---

![Docker Image](https://raw.githubusercontent.com/docker-library/docs/c350af05d3fac7b5c3f6327ac82fe4d990d8729c/docker/logo.png)

## **도커란 무엇일까?**

---

> 도커는 컨테이너 기반의 가상화 플랫폼이다.
{:.prompt-info}

- [`컨테이너(container)`](https://docs.docker.com/get-started/#what-is-a-container)란 호스트 os의 기능을 그대로 사용하면서 프로세스를 격리함으로, 독립된 환경을 만드는 기술이다.

- [`가상화(virtualization)`](https://aws.amazon.com/ko/what-is/virtualization/)란 물리적 자원인 하드웨어를 효율적으로 활용하기 위해 하드웨어 공간 위에 가상의 머신을 만드는 기술이다.

## **도커의 장점**

---

> 도커의 핵심 개념 중 하나인 컨테이너는 애플리케이션을 환경에 구애받지 않고 실행할 수 있게 도와준다.
{:.prompt-info}

일단 우리는 리눅스 계열 OS에 `A`라는 프로그램을 설치한다고 가정해 보겠다.

```zsh
# 우분투에서 A를 설치하는 방법
$ apt-get install A
```

```zsh
# 센트OS에서 A를 설치하는 방법
$ yum install A
```

```zsh
# 페도라에서 A를 설치하는 방법
$ dnf install A
```

우분투(Ubuntu), 센트OS(CentOS), 페도라(Fedora)는 전부 리눅스 계열 OS임에도 불구하고 프로그램을 설치하는 방법이 조금씩 다름을 알 수 있다.

**하지만, 도커를 사용하면 환경에 구애받지 않고 A와 같은 프로그램을 설치할 수 있다.(=우분투이든 센트OS이든 페도라이든 같은 코드로 A프로그램을 설치할 수 있음)**

> 도커란 무엇이고 도커의 장점이 무엇인지에 대해 간략히 알아보았다.
>
> 다음 포스트에는 도커를 설치하고 사용하는 방법에 대해 작성해 볼 예정이다.
{:.prompt-info}
