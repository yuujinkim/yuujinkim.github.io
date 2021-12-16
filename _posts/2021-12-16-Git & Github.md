---
layout: post
title: "Git & Github"
comments: true
---

## Git

### 깃이란?

**분산 버전관리 시스템**

1. 버전 관리
2. 백업하기
3. 협업하기

### 깃으로 버전 관리하기

- 깃 초기화
  현재 작업중인 디렉토리를 git 저장소로 지정
  `$ git init`

- 현재 깃 상태 확인
  `$ git status`

- 파일 스테이징
  `$ git add <파일명>`

- 파일 커밋
  `$ git commit -m "<커밋 메시지>"`

- 커밋 내용 확인
  `$ git log`

### 깃의 브랜치

나무가 가지에서 새 줄기를 뻗듯이 여러 갈래로 퍼지는 데이터 흐름

- 새 브랜치 만들기
  `$ git branch <branch 이름>`

- 브랜치 전환
  `$ git checkout <branch 이름>`

- 브랜치 병합
  `$ git merge <branch 이름>`

- 브랜치 삭제
  `$ git branch -d <branch 이름>`

## Github

- 원격 저장소에서 깃을 사용할 수 있다.
- 지역 저장소를 백업할 수 있다.
- 협업 프로젝트에 사용할 수 있다.
- 자신의 개발 이력을 남길 수 있다.
- 다른 사람의 소스를 살펴볼 수 있고, 오픈 소스에 참여할 수 있다.
