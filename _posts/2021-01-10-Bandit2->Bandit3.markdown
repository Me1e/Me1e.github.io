---
layout: post
title:  "#Bandit Level 2 → Level 3"
date:   2021-01-10 17:01:00 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored in a file called spaces in this filename located in the home directory

Level 2 접속   
```
% ssh -p 2220 bandit2@bandit.labs.overthewire.org
```
디렉토리 목록 확인   
```
bandit2@bandit:~$ ls -al
total 24
drwxr-xr-x  2 root    root    4096 May  7  2020 .
drwxr-xr-x 41 root    root    4096 May  7  2020 ..
-rw-r--r--  1 root    root     220 May 15  2017 .bash_logout
-rw-r--r--  1 root    root    3526 May 15  2017 .bashrc
-rw-r--r--  1 root    root     675 May 15  2017 .profile
-rw-r-----  1 bandit3 bandit2   33 May  7  2020 spaces in this filename
```
우리가 확인하려는 파일의 종류를 확인해봐야 한다   
리눅스 시스템에서 파일의 종류를 확인하는 명령어는  
```
$ file ./파일이름
```
이다

```
bandit1@bandit:~$ file ./*
./spaces in this filename: ASCII text
```
텍스트 파일이다   



평소처럼 "spaces in this filename" 을 읽으려 하면 문제가 발생한다
```
bandit2@bandit:~$ cat ./spaces in this filename
cat: ./spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory
```
cat 은 "spaces", "in", "this", "filename" 이라는 4개의 파일을 읽으려 하기 때문이다    
따라서 공백문자 처리를 하기 위해선 공백문자 좌측에 "\\"을 입력하여 공백 문자임을 표현하거나, 따옴표로 파일 이름을 정확하게 표시, "./*"이용 또는 파일을 구별할 수 있는 정도까지 입력 후 tab 키 자동완성을 이용해야 한다

```
bandit2@bandit:~$ cat ./spaces\ in\ this\ filename 
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
bandit2@bandit:~$ cat ./*
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
bandit2@bandit:~$ cat ./"spaces in this filename" 
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```


flag 값의 발견으로 Level 2 → Level 3 은 끝난다



Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit3.html)
