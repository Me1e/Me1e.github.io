---
layout: post
title:  "#Bandit Level 0 → Level 1"
date:   2021-01-02 17:30:00 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.  

디렉토리 목록을 확인해보자    
디렉토리 하위 목록을 표시해 주는 명령어인 ls(list segments)에 디렉토리의 내용을 자세히 출력해주는 -l(long)과 숨겨진 파일, 디렉토리까지 볼 수 있는 -a를 합쳐   
```
$ ls -al
```
를 입력해보자   

```
bandit0@bandit:~$ ls -al
total 24
drwxr-xr-x  2 root    root    4096 May  7  2020 .
drwxr-xr-x 41 root    root    4096 May  7  2020 ..
-rw-r--r--  1 root    root     220 May 15  2017 .bash_logout
-rw-r--r--  1 root    root    3526 May 15  2017 .bashrc
-rw-r--r--  1 root    root     675 May 15  2017 .profile
-rw-r-----  1 bandit1 bandit0   33 May  7  2020 readme
```

readme를 읽어보자   
리눅스 시스템에서 파일을 읽는 명령어는
```
$ cat 파일이름
```
이다   


```
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```

다음 단계를 위한 flag 값의 발견으로 Level0은 끝난다



Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit0.html)
