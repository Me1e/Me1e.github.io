---
layout: post
title:  "#Bandit Level 4 → Level 5"
date:   2021-01-10 17:03:00 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command   

Level 4 접속   
```
% ssh -p 2220 bandit4@bandit.labs.overthewire.org
```
디렉토리 목록 확인   
```
bandit4@bandit:~$ ls -al
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
bandit4@bandit:~$ file ./inhere/
./inhere/: directory
```
inhere 디렉토리 이동
```
bandit4@bandit:~$ cd ./inhere/
bandit4@bandit:~/inhere$
```
디렉토리 목록 확인
```
bandit4@bandit:~/inhere$ ls -al
total 48
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file00
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file01
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file02
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file03
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file04
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file05
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file06
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file07
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file08
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file09
```
디렉토리 내의 파일 종류 확인
```
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```
-file07 파일만 텍스트 파일이고 나머지는 데이터 파일이다   
데이터 파일은 읽을 수 없고 만약 읽으려 하면 다음과 같이 의미없는 결과만 나온다   
```
bandit4@bandit:~/inhere$ cat ./-file00
?/`2ғ?%??rL~5?g??? ????
```
읽을 수 있는 -file07 파일을 읽어보자
```
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```



flag 값의 발견으로 Level 4 → Level 5 은 끝난다



Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit5.html)
