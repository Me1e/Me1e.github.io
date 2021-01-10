---
layout: post
title:  "#Bandit Level 5 → Level 6"
date:   2021-01-10 17:04:00 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable, 1033 bytes in size, not executable   

이 포스트부터 이미 설명했던 명령어를 활용한 접근은 따로 설명하지 않을 것이다
```
bandit5@bandit:~$ ls -al
total 24
drwxr-xr-x  3 root root    4096 May  7  2020 .
drwxr-xr-x 41 root root    4096 May  7  2020 ..
-rw-r--r--  1 root root     220 May 15  2017 .bash_logout
-rw-r--r--  1 root root    3526 May 15  2017 .bashrc
drwxr-x--- 22 root bandit5 4096 May  7  2020 inhere
-rw-r--r--  1 root root     675 May 15  2017 .profile
bandit5@bandit:~$ file ./inhere/
./inhere/: directory
bandit5@bandit:~$ cd ./inhere/
bandit5@bandit:~/inhere$ ls -al
total 88
drwxr-x--- 22 root bandit5 4096 May  7  2020 .
drwxr-xr-x  3 root root    4096 May  7  2020 ..
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere00
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere01
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere02
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere03
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere04
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere05
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere06
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere07
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere08
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere09
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere10
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere11
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere12
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere13
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere14
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere15
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere16
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere17
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere18
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere19
```
여러 가지 디렉토리들이 있다   
이 디렉토리 안의 모든 파일을 일일이 확인하며 flag 값을 찾기는 불가능해 보인다
따라서 우리는 리눅스 시스템에서 파일 및 디렉토리를 검색할 때 사용하는 명령어인 find 를 사용할 것이다   

find 명령어는 정말 다양한 옵션이 있다   
하지만 모든 옵션을 활용하지 않고 문제에 주어진 1033 bytes 사이즈를 이용한 문제풀이를 할 것이다   
파일의 사이즈를 기준으로 파일을 찾는 명령어는
```
$ find [디렉토리 경로] -size [파일 사이즈]
```
이다   
파일 사이즈에 + 기호를 붙이면 초과의 크기, - 기호를 붙이면 미만의 크기로 검색해준다   
find 명령어는 해당 디렉토리와 하위 디렉토리의 모든 파일에서 검색을 하기 때문에 상당히 유용하다

find 명령어를 사용해보자   
.은 현재 디렉토리를 나타낸다
```
bandit5@bandit:~/inhere$ find . -size 1033c
./maybehere07/.file2
```
Byte 단위로 검색하기 위해 사이즈 뒤에 c 를 붙여주었다

```
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```



flag 값의 발견으로 Level 5 → Level 6 은 끝난다



Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit5.html)
