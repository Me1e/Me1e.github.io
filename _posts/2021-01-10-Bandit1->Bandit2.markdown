---
layout: post
title:  "#Bandit Level 1 → Level 2"
date:   2021-01-10 17:00:00 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored in a file called - located in the home directory     

Level 1 접속   
```
% ssh -p 2220 bandit1@bandit.labs.overthewire.org
```

디렉토리 목록 확인   
```
bandit1@bandit:~$ ls -al
total 24
-rw-r-----  1 bandit2 bandit1   33 May  7  2020 -
drwxr-xr-x  2 root    root    4096 May  7  2020 .
drwxr-xr-x 41 root    root    4096 May  7  2020 ..
-rw-r--r--  1 root    root     220 May 15  2017 .bash_logout
-rw-r--r--  1 root    root    3526 May 15  2017 .bashrc
-rw-r--r--  1 root    root     675 May 15  2017 .profile
```

리눅스에서 -는 옵션을 부여하는 것으로 간주하기 때문에 "-"가 이름인 파일을 열기 위해선 "./"와 같이 그 경로를 나타내거나, "/home/bandit1/-"처럼 절대경로를 나타내 줘야 한다. (혹은 현재 위치의 모든 파일을 나타내는 "./*"를 이용하여 이름이 "-"인 파일을 여는 방법도 있다)   
```
bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
bandit1@bandit:~$ cat /home/bandit1/-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
bandit1@bandit:~$ cat ./*
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
flag 값의 발견으로 Level 1 → Level 2 은 끝난다



Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit2.html)
