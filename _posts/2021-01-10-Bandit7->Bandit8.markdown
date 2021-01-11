---
layout: post
title:  "#Bandit Level 7 → Level 8"
date:   2021-01-10 17:06:00 +0830
categories: Linux Wargame Bandit
---

The password for the next level is stored in the file data.txt next to the word millionth

```
bandit7@bandit:~$ ls -al
total 4108
drwxr-xr-x  2 root    root       4096 May  7  2020 .
drwxr-xr-x 41 root    root       4096 May  7  2020 ..
-rw-r--r--  1 root    root        220 May 15  2017 .bash_logout
-rw-r--r--  1 root    root       3526 May 15  2017 .bashrc
-rw-r-----  1 bandit8 bandit7 4184396 May  7  2020 data.txt
-rw-r--r--  1 root    root        675 May 15  2017 .profile
bandit7@bandit:~$ file ./data.txt 
./data.txt: UTF-8 Unicode text
```
이번에는 Unicode 파일이다   
즉 한글 등 ASCII 코드에 없는 특수 문자가 포함돼 있다는 것이다

우리가 확인해 볼 data.txt 파일의 종류가 Unicode text 인데 사이즈가 약 4MB 인 것으로 보아 상당히 긴 길이의 텍스트 파일임을 알 수 있다   
그 내용들 중 millionth 단어를 일일이 찾기는 불가능해 보인다

여기서 우리는 파일의 내용에서 특정 문자열을 검색할 때 사용하는 grep 명령어를 사용할 것이다   
사용 방법은 다음과 같다
```
$ grep [특정 문자열] [파일 경로]
```
사용해보자
```
bandit7@bandit:~$ grep millionth data.txt 
millionth    cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```


flag 값의 발견으로 Level 7 → Level 8 은 끝난다



Link: [overthewire.org](https://overthewire.org/wargames/bandit/bandit8.html)
