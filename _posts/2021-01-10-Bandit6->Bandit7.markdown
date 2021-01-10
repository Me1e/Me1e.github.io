---
layout: post
title:  "#Bandit Level 6 → Level 7"
date:   2021-01-10 17:05:00 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, 33 bytes in size

```
bandit6@bandit:~$ ls -al
total 20
drwxr-xr-x  2 root root 4096 May  7  2020 .
drwxr-xr-x 41 root root 4096 May  7  2020 ..
-rw-r--r--  1 root root  220 May 15  2017 .bash_logout
-rw-r--r--  1 root root 3526 May 15  2017 .bashrc
-rw-r--r--  1 root root  675 May 15  2017 .profile
```
앞서 사용했던 find 명령어에 파일의 소유자를 찾을때 사용하는 -user 와 파일의 소유그룹을 찾을때 사용하는 -group 옵션을 추가해서 사용해보자

```
bandit6@bandit:~$ find / -size 33c -user bandit7 -group bandit6
find: ‘/root’: Permission denied
find: ‘/etc/polkit-1/localauthority’: Permission denied
find: ‘/proc/29968/task/29968/fdinfo/6’: No such file or directory
find: ‘/proc/29968/fd/5’: No such file or directory
find: ‘/run/lvm’: Permission denied
find: ‘/run/screen/S-bandit0’: Permission denied
중략..
```
찾으려는 파일의 조건에 해당하지만 읽을 권한이 없거나, 파일의 위치가 존재하지 않아 발생하는 에러들로 인해 내가 읽을 수 있는 파일을 구별하기 힘들다   

에러들을 걸러낼 필요가 있다   
그러기 위해서 명령어 뒤에
```
2> /dev/null
```
를 붙여보자   
2는 표준 에러 자료들을 뜻하고(0은 표준 입력, 1은 표준 출력 자료이다)  
/dev/null 은 항상 비어있으며, 해당 위치로 전송된 데이터는 버려지는 특성이 있는 경로이다      

따라서 위 명령어는 표준 에러 자료들을 늘 비어있는 위치로 전송하는 것이다   
즉 표준 출력 자료들만 나타내게 만드는 명령어인 것이다
```
bandit6@bandit:~$ find / -size 33c -user bandit7 -group bandit6 2> /dev/null
/var/lib/dpkg/info/bandit7.password
```
에러들은 모두 사라지고 읽을 수 있는 파일 하나가 검색된다
```
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```


flag 값의 발견으로 Level 6 → Level 7 은 끝난다



Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit6.html)
