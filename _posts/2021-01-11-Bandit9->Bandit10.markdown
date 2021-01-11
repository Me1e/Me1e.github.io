---
layout: post
title:  "#Bandit Level 9 → Level 10"
date:   2021-01-11 17:00:01 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters

```
bandit9@bandit:~$ ls -al
total 40
drwxr-xr-x  2 root     root     4096 May  7  2020 .
drwxr-xr-x 41 root     root     4096 May  7  2020 ..
-rw-r--r--  1 root     root      220 May 15  2017 .bash_logout
-rw-r--r--  1 root     root     3526 May 15  2017 .bashrc
-rw-r-----  1 bandit10 bandit9 19379 May  7  2020 data.txt
-rw-r--r--  1 root     root      675 May 15  2017 .profile
bandit9@bandit:~$ file ./data.txt 
./data.txt: data
```
data.txt 파일은 data 파일이다   
즉 사람이 읽을 수 없는 내용들이 많이 있을 것이다

strings 명령어를 통해 사람이 읽을 수 있는 문자열을 추출하고, grep 명령어를 통해 "=" 가 포함된 라인을 찾아보자
```
bandit9@bandit:~$ strings ./data.txt | grep =
========== the*2i"4
=:G e
========== password
<I=zsGi
Z)========== is
A=|t&E
Zdb=
c^ LAh=3G
*SF=s
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
S=A.H&^
```
평소 보던 flag 값이 있는 것으로 추정되는 라인을 찾았다

flag 값이 맞는지 테스트를 위해 위 값으로 다음 단계로 접속해 보았고 접속이 가능했다    
flag 값의 발견으로 Level 9 → Level 10 은 끝난다


Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit10.html)
