# Red Hat System Administration I

Commands used  in my practice to course Red Hat System Administration I

## Instance ec2-aws
Red Hat Enterprise Linux 8 (HVM), SSD Volume Type

## Commands



```console
[ec2-user@ip-172-31-26-217 ~]$ whoami
ec2-user
```
```console
[ec2-user@ip-172-31-26-217 ~]$ sudo -i
[root@ip-172-31-26-217 ~]# whoami
root
[root@ip-172-31-26-217 ~]# exit
logout
```

```console
[ec2-user@ip-172-31-26-217 ~]$ ls
[ec2-user@ip-172-31-26-217 ~]$ date
Sat Jun 26 17:26:39 UTC 2021
[ec2-user@ip-172-31-26-217 ~]$ date +%R
17:28
[ec2-user@ip-172-31-26-217 ~]$ date %d
date: invalid date ‘%d’
[ec2-user@ip-172-31-26-217 ~]$ date +%d
26
[ec2-user@ip-172-31-26-217 ~]$ date +%x
06/26/21


[ec2-user@ip-172-31-26-217 ~]$ passwd
Changing password for user ec2-user.
```
Viewing the Contents of Files

```console
[ec2-user@ip-172-31-26-217 ~]$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
....
....

[ec2-user@ip-172-31-26-217 ~]$ cat file1 file2
file1!!
this is file2!!



[ec2-user@ip-172-31-26-217 ~]$ head /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin

[ec2-user@ip-172-31-26-217 ~]$ tail -n 3 /etc/passwd
chrony:x:995:992::/var/lib/chrony:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
ec2-user:x:1000:1000:Cloud User:/home/ec2-user:/bin/bash

[ec2-user@ip-172-31-26-217 ~]$ wc /etc/passwd
  23   43 1101 /etc/passwd
[ec2-user@ip-172-31-26-217 ~]$ wc -l /etc/passwd ; wc -l /etc/group
23 /etc/passwd
41 /etc/group
[ec2-user@ip-172-31-26-217 ~]$ wc -c /etc/group /etc/hosts
534 /etc/group
159 /etc/hosts
693 total

```
Continuing a Long Command on Another Line
```console
[ec2-user@ip-172-31-26-217 ~]$ head -n 3 \
> /home/ec2-user/file1 \
> /home/ec2-user/file2
==> /home/ec2-user/file1 <==
file1!!
second line file1
third line file2

==> /home/ec2-user/file2 <==
this is file2!!
second line file2
third line file3


[ec2-user@ip-172-31-26-217 ~]$ history
    1  ls
    2  ls -a
    3  exit
    4  ls
    5  ls -al
    6  cd ..
    7  ls
    8  cd ..
    9  ls
   10  cd home/
   11  cd ec2-user/
   12  ls
   13  whoami


[ec2-user@ip-172-31-26-217 ~]$ !ls
ls /home/ec2-user/
file1  file2
[ec2-user@ip-172-31-26-217 ~]$ !26
ls
file1  file2
[ec2-user@ip-172-31-26-217 ~]$ !13
whoami
ec2-user
[ec2-user@ip-172-31-26-217 ~]$



[ec2-user@ip-172-31-26-217 ~]$ cat file1
file1!!
second line file1
third line file2
[ec2-user@ip-172-31-26-217 ~]$ !!
cat file1
file1!!
second line file1
third line file2
```

