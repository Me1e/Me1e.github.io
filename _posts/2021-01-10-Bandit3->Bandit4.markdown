---
layout: post
title:  "#Bandit Level 3 → Level 4"
date:   2021-01-10 17:02:00 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored in a hidden file in the inhere directory

Level 3 접속   
```
% ssh -p 2220 bandit3@bandit.labs.overthewire.org
```
디렉토리 목록 확인   
```
bandit3@bandit:~$ ls -al
total 24
drwxr-xr-x  3 root root 4096 May  7  2020 .
drwxr-xr-x 41 root root 4096 May  7  2020 ..
-rw-r--r--  1 root root  220 May 15  2017 .bash_logout
-rw-r--r--  1 root root 3526 May 15  2017 .bashrc
drwxr-xr-x  2 root root 4096 May  7  2020 inhere
-rw-r--r--  1 root root  675 May 15  2017 .profile
```
inhere 파일 종류 확인
```
bandit3@bandit:~$ file ./inhere/
inhere/: directory
```
디렉토리 파일 이므로 그 파일 경로로 이동해야 한다   
리눅스 시스템에서 디렉토리 이동 명령어는
```
$ cd [디렉토리 경로]
```
이다
```
bandit3@bandit:~$ cd ./inhere/
bandit3@bandit:~/inhere$
```
디렉토리 목록 확인
```
bandit3@bandit:~/inhere$ ls -al
total 12
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit4 bandit3   33 May  7  2020 .hidden
```
숨김 파일은 파일명이 "."으로 시작하며 기본적인 디렉토리 목록 확인 명령어로는 보이지 않는다   
하지만 우리는 숨겨진 파일까지 보여주는 -a 옵션을 사용하고 있었기 때문에 .hidden 파일이 보인다   
.hidden 파일 종류 확인
```
bandit3@bandit:~/inhere$ file ./.hidden 
./.hidden: ASCII text
```
.hidden 파일 확인
```
bandit3@bandit:~/inhere$ cat ./.hidden 
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

flag 값의 발견으로 Level 3 → Level 4 은 끝난다



Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit4.html)
