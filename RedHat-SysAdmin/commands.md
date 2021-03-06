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
date: invalid date ā%dā
[ec2-user@ip-172-31-26-217 ~]$ date +%d
26
[ec2-user@ip-172-31-26-217 ~]$ date +%x
06/26/21


[ec2-user@ip-172-31-26-217 ~]$ passwd
Changing password for user ec2-user.
```
* Viewing the Contents of Files

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
* Continuing a Long Command on Another Line
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

* Managing Files From the Command Line

| Location  | Purpose  |
|---|---|
| /usr  |  Installed software, shared libraries, include files, and read-only program data. Important subdirectories include: <ul><li>/usr/bin: User commands.</li><li>/usr/sbin: System administration commands.</li><li>/usr/local: Locally customized software.</li></ul> |
| /etc |  Configuration files specific to this system. |
| /var  | Variable data specific to this system that should persist between boots. Files that dynamically change, such as databases, cache directories, log files, printer-spooled documents, and website content may be found under /var.  |
| /run  | Runtime data for processes started since the last boot. This includes process ID files and lock files, among other things. The contents of this directory are recreated on reboot. This directory consolidates /var/run and /var/lock from earlier versions of Red Hat Enterprise Linux.  |
| /home  | Home directories are where regular users store their personal data and configuration files.  |
| /root  | Home directory for the administrative superuser, root.  |
| /tmp  | A world-writable space for temporary files. Files which have not been accessed, changed, or modified for 10 days are deleted from this directory automatically. Another temporary directory exists, /var/tmp, in which files that have not been accessed, changed, or modified in more than 30 days are deleted automatically.  |
| /boot  | Files needed in order to start the boot process.  |
| /dev  | 	Contains special device files that are used by the system to access hardware.  |

Important
In Red Hat Enterprise Linux 7 and later, four older directories in / have identical contents to their counterparts located in /usr:

/bin and /usr/bin

/sbin and /usr/sbin

/lib and /usr/lib

/lib64 and /usr/lib64

```console
[ec2-user@ip-172-31-26-217 ~]$ mkdir Videos
[ec2-user@ip-172-31-26-217 ~]$ touch Videos/blockbuster1.ogg
[ec2-user@ip-172-31-26-217 ~]$ mkdir Documents
[ec2-user@ip-172-31-26-217 ~]$ touch Videos/blockbuster2.ogg Documents/thesis_chapter1.odf
[ec2-user@ip-172-31-26-217 ~]$ ls
Documents  Videos  file1  file2
[ec2-user@ip-172-31-26-217 ~]$ ls Documents/
thesis_chapter1.odf
[ec2-user@ip-172-31-26-217 ~]$ touch Documents/thesis_chapter2.odf

```

The ls command has multiple options for displaying attributes on files. The most common and useful are -l (long listing format), -a (all files, including hidden files), and -R (recursive, to include the contents of all subdirectories).

The two special directories at the top of the listing refer to the current directory (.) and the parent directory (..). These special directories exist in every directory on the system
```console
[ec2-user@ip-172-31-26-217 ~]$ ls -l
total 8
drwxrwxr-x. 2 ec2-user ec2-user 60 Jun 27 02:16 Documents
drwxrwxr-x. 2 ec2-user ec2-user 54 Jun 27 02:16 Videos
-rw-rw-r--. 1 ec2-user ec2-user 43 Jun 26 18:25 file1
-rw-rw-r--. 1 ec2-user ec2-user 51 Jun 26 18:26 file2
[ec2-user@ip-172-31-26-217 ~]$ ls -al
total 24
drwx------. 5 ec2-user ec2-user 152 Jun 27 02:15 .
drwxr-xr-x. 3 root     root      22 Jun 26 17:13 ..
-rw-------. 1 ec2-user ec2-user 972 Jun 26 20:54 .bash_history
-rw-r--r--. 1 ec2-user ec2-user  18 Apr 21 14:04 .bash_logout
-rw-r--r--. 1 ec2-user ec2-user 141 Apr 21 14:04 .bash_profile
-rw-r--r--. 1 ec2-user ec2-user 376 Apr 21 14:04 .bashrc
drwx------. 2 ec2-user ec2-user  29 Jun 26 17:13 .ssh
drwxrwxr-x. 2 ec2-user ec2-user  60 Jun 27 02:16 Documents
drwxrwxr-x. 2 ec2-user ec2-user  54 Jun 27 02:16 Videos
-rw-rw-r--. 1 ec2-user ec2-user  43 Jun 26 18:25 file1
-rw-rw-r--. 1 ec2-user ec2-user  51 Jun 26 18:26 file2
[ec2-user@ip-172-31-26-217 ~]$ ls -R
.:
Documents  Videos  file1  file2

./Documents:
thesis_chapter1.odf  thesis_chapter2.odf

./Videos:
blockbuster1.ogg  blockbuster2.ogg
```
```console
[ec2-user@ip-172-31-26-217 ~]$ cd Videos/
[ec2-user@ip-172-31-26-217 Videos]$ pwd
/home/ec2-user/Videos
[ec2-user@ip-172-31-26-217 Videos]$ cd /home/ec2-user/Documents
[ec2-user@ip-172-31-26-217 Documents]$ pwd
/home/ec2-user/Documents
[ec2-user@ip-172-31-26-217 Documents]$ cd -
/home/ec2-user/Videos
[ec2-user@ip-172-31-26-217 Videos]$ pwd
/home/ec2-user/Videos
[ec2-user@ip-172-31-26-217 Videos]$ cd -
/home/ec2-user/Documents
[ec2-user@ip-172-31-26-217 Documents]$ pwd
/home/ec2-user/Documents
[ec2-user@ip-172-31-26-217 Documents]$ cd -
/home/ec2-user/Videos
[ec2-user@ip-172-31-26-217 Videos]$ pwd
/home/ec2-user/Videos
[ec2-user@ip-172-31-26-217 Videos]$ cd
[ec2-user@ip-172-31-26-217 ~]$
```
```console
[ec2-user@ip-172-31-26-217 Videos]$ pwd
/home/ec2-user/Videos
[ec2-user@ip-172-31-26-217 Videos]$ cd .
[ec2-user@ip-172-31-26-217 Videos]$ pwd
/home/ec2-user/Videos
[ec2-user@ip-172-31-26-217 Videos]$ cd ..
[ec2-user@ip-172-31-26-217 ~]$ pwd
/home/ec2-user
[ec2-user@ip-172-31-26-217 ~]$ cd ..
[ec2-user@ip-172-31-26-217 home]$ pwd
/home
[ec2-user@ip-172-31-26-217 home]$ cd ..
[ec2-user@ip-172-31-26-217 /]$ pwd
/
[ec2-user@ip-172-31-26-217 /]$ cd
[ec2-user@ip-172-31-26-217 ~]$ pwd
/home/ec2-user
[ec2-user@ip-172-31-26-217 ~]$
```
```console
[ec2-user@ip-172-31-26-217 ~]$ mkdir Videos/Watched
[ec2-user@ip-172-31-26-217 ~]$ ls -R Videos
Videos:
Watched  blockbuster1.ogg  blockbuster2.ogg

Videos/Watched:
[ec2-user@ip-172-31-26-217 ~]$ cd Documents
[ec2-user@ip-172-31-26-217 Documents]$ mkdir ProjectX ProjectY
[ec2-user@ip-172-31-26-217 Documents]$ ls
ProjectX  ProjectY  thesis_chapter1.odf  thesis_chapter2.odf
[ec2-user@ip-172-31-26-217 Documents]$ mkdir -p Thesis/Chapter1 Thesis/Chapter2 Thesis/Chapter3
[ec2-user@ip-172-31-26-217 Documents]$ cd
[ec2-user@ip-172-31-26-217 ~]$ ls -R Videos Documents
Documents:
ProjectX  ProjectY  Thesis  thesis_chapter1.odf  thesis_chapter2.odf

Documents/ProjectX:

Documents/ProjectY:

Documents/Thesis:
Chapter1  Chapter2  Chapter3

Documents/Thesis/Chapter1:

Documents/Thesis/Chapter2:

Documents/Thesis/Chapter3:

Videos:
Watched  blockbuster1.ogg  blockbuster2.ogg

Videos/Watched:


[ec2-user@ip-172-31-26-217 ~]$ cd Videos
[ec2-user@ip-172-31-26-217 Videos]$ cp blockbuster1.ogg blockbuster3.ogg
[ec2-user@ip-172-31-26-217 Videos]$ ls -a
.  ..  Watched  blockbuster1.ogg  blockbuster2.ogg  blockbuster3.ogg
[ec2-user@ip-172-31-26-217 Videos]$ ls -l
total 0
drwxrwxr-x. 2 ec2-user ec2-user 6 Jun 27 03:09 Watched
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 02:15 blockbuster1.ogg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 02:16 blockbuster2.ogg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 03:39 blockbuster3.ogg
```

When copying multiple files with one command, the last argument must be a directory. Copied files retain their original names in the new directory. If a file with the same name exists in the target directory, the existing file is overwritten. By default, the cp does not copy directories; it ignores them.

In the following example, two directories are listed, Thesis and ProjectX. Only the last argument, ProjectX is valid as a destination. The Thesis directory is ignored.

```console
[user@host Videos]$ cd ../Documents
[user@host Documents]$ cp thesis_chapter1.odf thesis_chapter2.odf Thesis ProjectX
cp: omitting directory `Thesis'
[user@host Documents]$ ls Thesis ProjectX
ProjectX:
thesis_chapter1.odf  thesis_chapter2.odf

Thesis:
Chapter1  Chapter2  Chapter3
```
```console
[ec2-user@ip-172-31-26-217 Documents]$ cp /etc/hostname .
[ec2-user@ip-172-31-26-217 Documents]$ cat hostname
ip-172-31-26-217.ec2.internal
[ec2-user@ip-172-31-26-217 Documents]$ ls
ProjectX  ProjectY  Thesis  hostname  thesis_chapter1.odf  thesis_chapter2.odf
```

```console
[ec2-user@ip-172-31-26-217 Documents]$ cd ../Documents
[ec2-user@ip-172-31-26-217 Documents]$ ls -l thesis*
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 02:16 thesis_chapter1.odf
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 02:16 thesis_chapter2.odf
[ec2-user@ip-172-31-26-217 Documents]$ mv thesis_chapter2.odf thesis_chapter2_reviewed.odf
[ec2-user@ip-172-31-26-217 Documents]$ ls -l thesis*
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 02:16 thesis_chapter1.odf
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 02:16 thesis_chapter2_reviewed.odf



[ec2-user@ip-172-31-26-217 Documents]$ ls Thesis/Chapter1
[ec2-user@ip-172-31-26-217 Documents]$ mv thesis_chapter1.odf Thesis/Chapter1
[ec2-user@ip-172-31-26-217 Documents]$ ls Thesis/Chapter1
thesis_chapter1.odf
[ec2-user@ip-172-31-26-217 Documents]$  ls -l thesis*
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 02:16 thesis_chapter2_reviewed.odf
```
```console
[ec2-user@ip-172-31-26-217 Documents]$ pwd
/home/ec2-user/Documents
[ec2-user@ip-172-31-26-217 Documents]$ ls -l thesis*
-rw-rw-r--. 1 ec2-user ec2-user 0 Jun 27 02:16 thesis_chapter2_reviewed.odf
[ec2-user@ip-172-31-26-217 Documents]$ rm thesis_chapter2_reviewed.odf
[ec2-user@ip-172-31-26-217 Documents]$ ls -l thesis*
ls: cannot access 'thesis*': No such file or directory


[ec2-user@ip-172-31-26-217 Documents]$ ls -R Thesis
Thesis:
Chapter1  Chapter2  Chapter3

Thesis/Chapter1:
thesis_chapter1.odf

Thesis/Chapter2:

Thesis/Chapter3:
[ec2-user@ip-172-31-26-217 Documents]$ rm -r Thesis/Chapter1
[ec2-user@ip-172-31-26-217 Documents]$ ls -l Thesis
total 0
drwxrwxr-x. 2 ec2-user ec2-user 6 Jun 27 03:10 Chapter2
drwxrwxr-x. 2 ec2-user ec2-user 6 Jun 27 03:10 Chapter3


[ec2-user@ip-172-31-26-217 Documents]$ rm -ri Thesis
rm: descend into directory 'Thesis'? y
rm: remove directory 'Thesis/Chapter2'? y
rm: remove directory 'Thesis/Chapter3'? y
rm: remove directory 'Thesis'? y
[ec2-user@ip-172-31-26-217 Documents]$


[ec2-user@ip-172-31-26-217 Documents]$ pwd
/home/ec2-user/Documents
[ec2-user@ip-172-31-26-217 Documents]$ rmdir ProjectY
[ec2-user@ip-172-31-26-217 Documents]$ rmdir ProjectX
rmdir: failed to remove 'ProjectX': Directory not empty
[ec2-user@ip-172-31-26-217 Documents]$ rm -r ProjectX
[ec2-user@ip-172-31-26-217 Documents]$ ls -lR
.:
total 4
-rw-r--r--. 1 ec2-user ec2-user 30 Jun 27 03:42 hostname
[ec2-user@ip-172-31-26-217 Documents]$
```


```console
[ec2-user@ip-172-31-17-137 ~]$ mkdir Music Pictures Videos
[ec2-user@ip-172-31-17-137 ~]$ ls
Music  Pictures  Videos
[ec2-user@ip-172-31-17-137 ~]$  touch song1.mp3 song2.mp3 song3.mp3 song4.mp3 \
> song5.mp3 song6.mp3
[ec2-user@ip-172-31-17-137 ~]$ ls
Music  Pictures  Videos  song1.mp3  song2.mp3  song3.mp3  song4.mp3  song5.mp3  song6.mp3
[ec2-user@ip-172-31-17-137 ~]$ touch snap1.jpg snap2.jpg snap3.jpg snap4.jpg \
> snap5.jpg snap6.jpg
[ec2-user@ip-172-31-17-137 ~]$ touch film1.avi film2.avi film3.avi film4.avi \
> film5.avi film6.avi
[ec2-user@ip-172-31-17-137 ~]$ ls
Music     Videos     film2.avi  film4.avi  film6.avi  snap2.jpg  snap4.jpg  snap6.jpg  song2.mp3  song4.mp3  song6.mp3
Pictures  film1.avi  film3.avi  film5.avi  snap1.jpg  snap3.jpg  snap5.jpg  song1.mp3  song3.mp3  song5.mp3
[ec2-user@ip-172-31-17-137 ~]$ ls -l
total 0
drwxrwxr-x. 2 ec2-user ec2-user 6 Jul  2 00:07 Music
drwxrwxr-x. 2 ec2-user ec2-user 6 Jul  2 00:07 Pictures
drwxrwxr-x. 2 ec2-user ec2-user 6 Jul  2 00:07 Videos
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film1.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film2.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film3.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film4.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film5.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film6.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap1.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap2.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap3.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap4.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap5.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap6.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song1.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song2.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song3.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song4.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song5.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song6.mp3
```

```console
[ec2-user@ip-172-31-17-137 ~]$ mv song1.mp3 song2.mp3 song3.mp3 song4.mp3 \
> song5.mp3 song6.mp3 Music
[ec2-user@ip-172-31-17-137 ~]$ mv snap1.jpg snap2.jpg snap3.jpg snap4.jpg \
> snap5.jpg snap6.jpg Pictures
[ec2-user@ip-172-31-17-137 ~]$ mv film1.avi film2.avi film3.avi film4.avi \
> film5.avi film6.avi Videos
[ec2-user@ip-172-31-17-137 ~]$ ls -l Music Pictures Videos
Music:
total 0
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song1.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song2.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song3.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song4.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song5.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 song6.mp3

Pictures:
total 0
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap1.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap2.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap3.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap4.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap5.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:07 snap6.jpg

Videos:
total 0
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film1.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film2.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film3.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film4.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film5.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:08 film6.avi
[ec2-user@ip-172-31-17-137 ~]$ mkdir friends family work
[ec2-user@ip-172-31-17-137 ~]$ ls -l
total 0
drwxrwxr-x. 2 ec2-user ec2-user 108 Jul  2 00:13 Music
drwxrwxr-x. 2 ec2-user ec2-user 108 Jul  2 00:13 Pictures
drwxrwxr-x. 2 ec2-user ec2-user 108 Jul  2 00:13 Videos
drwxrwxr-x. 2 ec2-user ec2-user   6 Jul  2 00:15 family
drwxrwxr-x. 2 ec2-user ec2-user   6 Jul  2 00:15 friends
drwxrwxr-x. 2 ec2-user ec2-user   6 Jul  2 00:15 work
```

```console
[ec2-user@ip-172-31-17-137 ~]$ cd friends/
[ec2-user@ip-172-31-17-137 friends]$ cp ~/Music/song1.mp3 ~/Music/song2.mp3 \
> ~/Pictures/snap1.jpg ~/Pictures/snap2.jpg ~/Videos/film1.avi \
> ~/Videos/film2.avi .
[ec2-user@ip-172-31-17-137 friends]$ cd ../family
[ec2-user@ip-172-31-17-137 family]$ cp ~/Music/song3.mp3 ~/Music/song4.mp3 \
> ~/Pictures/snap3.jpg ~/Pictures/snap4.jpg ~/Videos/film3.avi \
> ~/Videos/film4.avi .
[ec2-user@ip-172-31-17-137 family]$ cd ../work/
[ec2-user@ip-172-31-17-137 work]$ cp ~/Music/song5.mp3 ~/Music/song6.mp3 \
> ~/Pictures/snap5.jpg ~/Pictures/snap6.jpg \
> ~/Videos/film5.avi ~/Videos/film6.avi .
[ec2-user@ip-172-31-17-137 work]$ ls -l
total 0
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:22 film5.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:22 film6.avi
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:22 snap5.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:22 snap6.jpg
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:22 song5.mp3
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 00:22 song6.mp3
ls -l Music/ Pictures/ Videos/


[ec2-user@ip-172-31-17-137 ~]$ rm -r family friends
[ec2-user@ip-172-31-17-137 ~]$ cd work
[ec2-user@ip-172-31-17-137 work]$ rm song5.mp3 song6.mp3 snap5.jpg snap6.jpg \
> film5.avi film6.avi
[ec2-user@ip-172-31-17-137 work]$ ls -l
total 0
[ec2-user@ip-172-31-17-137 work]$ cd
[ec2-user@ip-172-31-17-137 ~]$ rmdir work
[ec2-user@ip-172-31-17-137 ~]$ ls -l
total 0
drwxrwxr-x. 2 ec2-user ec2-user 108 Jul  2 00:13 Music
drwxrwxr-x. 2 ec2-user ec2-user 108 Jul  2 00:13 Pictures
drwxrwxr-x. 2 ec2-user ec2-user 108 Jul  2 00:13 Videos

```

You can use the ln command to create a new hard link (another name) that points to an existing file. The command needs at least two arguments, a path to the existing file, and the path to the hard link that you want to create.

The following example creates a hard link named newfile-link2.txt for the existing file newfile.txt in the /tmp directory.

If you want to find out whether two files are hard links of each other, one way is to use the -i option with the ls command to list the files' inode number. If the files are on the same file system (discussed in a moment) and their inode numbers are the same, the files are hard links pointing to the same data.

```console
[ec2-user@ip-172-31-17-137 ~]$ touch file1.txt
[ec2-user@ip-172-31-17-137 ~]$ ls
Music  Pictures  Videos  file1.txt
[ec2-user@ip-172-31-17-137 ~]$ ln file1.txt /tmp/newfile-klink.txt
[ec2-user@ip-172-31-17-137 ~]$ ls -l file1.txt /tmp/newfile-klink.txt
-rw-rw-r--. 2 ec2-user ec2-user 0 Jul  2 01:03 /tmp/newfile-klink.txt
-rw-rw-r--. 2 ec2-user ec2-user 0 Jul  2 01:03 file1.txt
[ec2-user@ip-172-31-17-137 ~]$
[ec2-user@ip-172-31-17-137 ~]$
[ec2-user@ip-172-31-17-137 ~]$ ls -il file1.txt /tmp/newfile-klink.txt
8412550 -rw-rw-r--. 2 ec2-user ec2-user 0 Jul  2 01:03 /tmp/newfile-klink.txt
8412550 -rw-rw-r--. 2 ec2-user ec2-user 0 Jul  2 01:03 file1.txt
```

```console
ec2-user@ip-172-31-17-137 ~]$ vi file1.txt
[ec2-user@ip-172-31-17-137 ~]$
[ec2-user@ip-172-31-17-137 ~]$ rm -f file1.txt
[ec2-user@ip-172-31-17-137 ~]$ ls -l /tmp/newfile-klink.txt
-rw-rw-r--. 1 ec2-user ec2-user 17 Jul  2 01:09 /tmp/newfile-klink.txt
[ec2-user@ip-172-31-17-137 ~]$ cat /tmp/newfile-klink.txt
Hi, How are you?
[ec2-user@ip-172-31-17-137 ~]$



[ec2-user@ip-172-31-17-137 ~]$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
devtmpfs          385740       0    385740   0% /dev
tmpfs             412872       0    412872   0% /dev/shm
tmpfs             412872   10740    402132   3% /run
tmpfs             412872       0    412872   0% /sys/fs/cgroup
/dev/xvda2      10473452 1302428   9171024  13% /
tmpfs              82572       0     82572   0% /run/user/1000
[ec2-user@ip-172-31-17-137 ~]$
```

###Limitations of Hard Links

Hard links have some limitations. Firstly, hard links can only be used with regular files. You cannot use ln to create a hard link to a directory or special file.

Secondly, hard links can only be used if both files are on the same file system. The file-system hierarchy can be made up of multiple storage devices. Depending on the configuration of your system, when you change into a new directory, that directory and its contents may be stored on a different file system.

Files in two different "Mounted on" directories and their subdirectories are on different file systems. (The most specific match wins.) So, the system in this example, you can create a hard link between /var/tmp/link1 and /home/user/file because they are both subdirectories of / but not any other directory on the list. But you cannot create a hard link between /boot/test/badlink and /home/user/file because the first file is in a subdirectory of /boot (on the "Mounted on" list) and the second file is not.


```console
[ec2-user@ip-172-31-17-137 ~]$ touch file2.txt
[ec2-user@ip-172-31-17-137 ~]$ vi file2.txt
[ec2-user@ip-172-31-17-137 ~]$
[ec2-user@ip-172-31-17-137 ~]$ ln -s /home/ec2-user/file2.txt /tmp/file2-symlink.txt

[ec2-user@ip-172-31-17-137 ~]$ ls -l file2.txt /tmp/file2-symlink.txt
lrwxrwxrwx. 1 ec2-user ec2-user 24 Jul  2 01:17 /tmp/file2-symlink.txt -> /home/ec2-user/file2.txt
-rw-rw-r--. 1 ec2-user ec2-user 27 Jul  2 01:16 file2.txt
[ec2-user@ip-172-31-17-137 ~]$ cat /tmp/file2-symlink.txt
Soft link!! with this file

[ec2-user@ip-172-31-17-137 ~]$ ls -il file2.txt /tmp/file2-symlink.txt
5401455 lrwxrwxrwx. 1 ec2-user ec2-user 24 Jul  2 01:17 /tmp/file2-symlink.txt -> /home/ec2-user/file2.txt
8412560 -rw-rw-r--. 1 ec2-user ec2-user 27 Jul  2 01:16 file2.txt

[ec2-user@ip-172-31-17-137 ~]$ rm -f file2.txt
[ec2-user@ip-172-31-17-137 ~]$ ls -l /tmp/file2-symlink.txt
lrwxrwxrwx. 1 ec2-user ec2-user 24 Jul  2 01:17 /tmp/file2-symlink.txt -> /home/ec2-user/file2.txt
[ec2-user@ip-172-31-17-137 ~]$ cat /tmp/file2-symlink.txt
cat: /tmp/file2-symlink.txt: No such file or directory


[ec2-user@ip-172-31-17-137 ~]$ ln -s /etc /home/ec2-user/configfiles
[ec2-user@ip-172-31-17-137 ~]$ cd /home/ec2-user/configfiles
[ec2-user@ip-172-31-17-137 configfiles]$ pwd
/home/ec2-user/configfiles
[ec2-user@ip-172-31-17-137 configfiles]$ ls
etc
```

```console
[ec2-user@ip-172-31-20-80 ~]$ mkdir glob; cd glob
[ec2-user@ip-172-31-20-80 glob]$ touch alfa bravo charlie delta echo able baker cast dog easy
[ec2-user@ip-172-31-20-80 glob]$ ls
able  alfa  baker  bravo  cast  charlie  delta  dog  easy  echo
[ec2-user@ip-172-31-20-80 glob]$ ls a*
able  alfa
[ec2-user@ip-172-31-20-80 glob]$ ls *a*
able  alfa  baker  bravo  cast  charlie  delta  easy
[ec2-user@ip-172-31-20-80 glob]$ ls [ac]*
able  alfa  cast  charlie
[ec2-user@ip-172-31-20-80 glob]$ ls ????
able  alfa  cast  easy  echo
[ec2-user@ip-172-31-20-80 glob]$ ls ?????
baker  bravo  delta
[ec2-user@ip-172-31-20-80 glob]$


[ec2-user@ip-172-31-20-80 glob]$ echo ~root
/root
[ec2-user@ip-172-31-20-80 glob]$ echo ~user
~user
[ec2-user@ip-172-31-20-80 glob]$ echo ~ec2-user
/home/ec2-user
[ec2-user@ip-172-31-20-80 glob]$ echo ~/glob
/home/ec2-user/glob
[ec2-user@ip-172-31-20-80 glob]$


[ec2-user@ip-172-31-20-80 glob]$ echo {Sunday,Monday,Tuesday,Wenesday}.log
Sunday.log Monday.log Tuesday.log Wenesday.log
[ec2-user@ip-172-31-20-80 glob]$ echo file{1..3}.txt
file1.txt file2.txt file3.txt
[ec2-user@ip-172-31-20-80 glob]$ echo file{a.c}.txt
file{a.c}.txt
[ec2-user@ip-172-31-20-80 glob]$ echo file{a..c}.txt
filea.txt fileb.txt filec.txt
[ec2-user@ip-172-31-20-80 glob]$ echo file{a,b}{1,2}.txt
filea1.txt filea2.txt fileb1.txt fileb2.txt
[ec2-user@ip-172-31-20-80 glob]$ echo file{a{1,2},b,c}.txt
filea1.txt filea2.txt fileb.txt filec.txt

[ec2-user@ip-172-31-20-80 glob]$ mkdir ../RHEL{6,7,8}
[ec2-user@ip-172-31-20-80 glob]$ ls ../RHEL*
../RHEL6:

../RHEL7:

../RHEL8:

[ec2-user@ip-172-31-20-80 glob]$ USERNAME=operator
[ec2-user@ip-172-31-20-80 glob]$ echo ${USERNAME}
operator
[ec2-user@ip-172-31-20-80 glob]$
[ec2-user@ip-172-31-20-80 glob]$ echo $USERNAME
operator


[ec2-user@ip-172-31-20-80 glob]$ echo Today is $(date +%A).
Today is Friday.
[ec2-user@ip-172-31-20-80 glob]$ echo Today is $(date).
Today is Fri Jul 2 11:39:46 UTC 2021.
[ec2-user@ip-172-31-20-80 glob]$
[ec2-user@ip-172-31-20-80 glob]$ echo The time is $(data +%M) minutes past $(date +%1%p).
-bash: data: command not found
The time is minutes past %p.
[ec2-user@ip-172-31-20-80 glob]$ echo The time is $(date +%M) minutes past $(date +%1%p).
The time is 40 minutes past %p.
// With character l, not number 1
[ec2-user@ip-172-31-20-80 glob]$ echo The time is $(date +%M) minutes past $(date +%l%p).
The time is 41 minutes past 11AM.
[ec2-user@ip-172-31-20-80 glob]$


[ec2-user@ip-172-31-20-80 glob]$ echo The value of $HOME is your home directory.
The value of /home/ec2-user is your home directory.
[ec2-user@ip-172-31-20-80 glob]$ echo The value of \$HOME is your home directory.
The value of $HOME is your home directory.

[ec2-user@ip-172-31-20-80 glob]$ myhost=$(hostname -s); echo $myhost
ip-172-31-20-80
[ec2-user@ip-172-31-20-80 glob]$ echo "***** hostname is ${myhost} *****"
***** hostname is ip-172-31-20-80 *****
[ec2-user@ip-172-31-20-80 glob]$

[ec2-user@ip-172-31-20-80 glob]$ echo "Will variable $myhost evaluate to $(hostname -s)?"
Will variable ip-172-31-20-80 evaluate to ip-172-31-20-80?
[ec2-user@ip-172-31-20-80 glob]$ echo 'Will variable $myhost evaluate to $(hostname -s)?'
Will variable $myhost evaluate to $(hostname -s)?
[ec2-user@ip-172-31-20-80 glob]$
```

```console
[ec2-user@ip-172-31-20-80 ~]$ mkdir -p ~/Documents/project_plans
[ec2-user@ip-172-31-20-80 ~]$ touch \
> ~/Documents/project_plans/{season1,season2}_project_plan.odf
[ec2-user@ip-172-31-20-80 ~]$ ls -lR Documents/
Documents/:
total 0
drwxrwxr-x. 2 ec2-user ec2-user 70 Jul  2 12:21 project_plans

Documents/project_plans:
total 0
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:21 season1_project_plan.odf
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:21 season2_project_plan.odf
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$ touch tv_season{1..2}_episode{1..6}.ogg
[ec2-user@ip-172-31-20-80 ~]$ ls tv*
tv_season1_episode1.ogg  tv_season1_episode5.ogg  tv_season2_episode3.ogg
tv_season1_episode2.ogg  tv_season1_episode6.ogg  tv_season2_episode4.ogg
tv_season1_episode3.ogg  tv_season2_episode1.ogg  tv_season2_episode5.ogg
tv_season1_episode4.ogg  tv_season2_episode2.ogg  tv_season2_episode6.ogg
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$ touch mystery_chapter{1..8}.odf
[ec2-user@ip-172-31-20-80 ~]$ ls mys*
mystery_chapter1.odf  mystery_chapter3.odf  mystery_chapter5.odf  mystery_chapter7.odf
mystery_chapter2.odf  mystery_chapter4.odf  mystery_chapter6.odf  mystery_chapter8.odf
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$ mkdir -p Videos/season{1..2}
[ec2-user@ip-172-31-20-80 ~]$ ls Videos
season1  season2
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$ mv tv_season1* Videos/season1
[ec2-user@ip-172-31-20-80 ~]$ mv tv_season2* Videos/season2
[ec2-user@ip-172-31-20-80 ~]$ ls -R Videos
Videos:
season1  season2

Videos/season1:
tv_season1_episode1.ogg  tv_season1_episode3.ogg  tv_season1_episode5.ogg
tv_season1_episode2.ogg  tv_season1_episode4.ogg  tv_season1_episode6.ogg

Videos/season2:
tv_season2_episode1.ogg  tv_season2_episode3.ogg  tv_season2_episode5.ogg
tv_season2_episode2.ogg  tv_season2_episode4.ogg  tv_season2_episode6.ogg
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$ mkdir -p Documents/my_bestseller/chapters
[ec2-user@ip-172-31-20-80 ~]$ ls -R Documents
Documents:
my_bestseller  project_plans

Documents/my_bestseller:
chapters

Documents/my_bestseller/chapters:

Documents/project_plans:
season1_project_plan.odf  season2_project_plan.odf
[ec2-user@ip-172-31-20-80 ~]$ mkdir Documents/my_bestseller/{editor,changes,vacation}
[ec2-user@ip-172-31-20-80 ~]$ ls -R Documents
Documents:
my_bestseller  project_plans

Documents/my_bestseller:
changes  chapters  editor  vacation

Documents/my_bestseller/changes:

Documents/my_bestseller/chapters:

Documents/my_bestseller/editor:

Documents/my_bestseller/vacation:

Documents/project_plans:
season1_project_plan.odf  season2_project_plan.odf
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$ cd Documents/my_bestseller/chapters
[ec2-user@ip-172-31-20-80 chapters]$ mv ~/mystery_chapter* .
[ec2-user@ip-172-31-20-80 chapters]$ ls
mystery_chapter1.odf  mystery_chapter3.odf  mystery_chapter5.odf  mystery_chapter7.odf
mystery_chapter2.odf  mystery_chapter4.odf  mystery_chapter6.odf  mystery_chapter8.odf
[ec2-user@ip-172-31-20-80 chapters]$
[ec2-user@ip-172-31-20-80 chapters]$ mv mystery_chapter{1..2}.odf ../editor
[ec2-user@ip-172-31-20-80 chapters]$ ls
mystery_chapter3.odf  mystery_chapter5.odf  mystery_chapter7.odf
mystery_chapter4.odf  mystery_chapter6.odf  mystery_chapter8.odf
[ec2-user@ip-172-31-20-80 chapters]$ ls ../editor
mystery_chapter1.odf  mystery_chapter2.odf
[ec2-user@ip-172-31-20-80 chapters]$
[ec2-user@ip-172-31-20-80 chapters]$
[ec2-user@ip-172-31-20-80 chapters]$ mv mystery_chapter{7,8}.odf ../vacation
[ec2-user@ip-172-31-20-80 chapters]$ ls
mystery_chapter3.odf  mystery_chapter4.odf  mystery_chapter5.odf  mystery_chapter6.odf
[ec2-user@ip-172-31-20-80 chapters]$ ls ../vacation
mystery_chapter7.odf  mystery_chapter8.odf
[ec2-user@ip-172-31-20-80 chapters]$ cd ~/Videos/season2
[ec2-user@ip-172-31-20-80 season2]$ cp *episode1.ogg ~/Documents/my_bestseller/vacation
[ec2-user@ip-172-31-20-80 season2]$
[ec2-user@ip-172-31-20-80 season2]$ cd ~/Documents/my_bestseller/vacation
[ec2-user@ip-172-31-20-80 vacation]$ ls
mystery_chapter7.odf  mystery_chapter8.odf  tv_season2_episode1.ogg
[ec2-user@ip-172-31-20-80 vacation]$ cd -
/home/ec2-user/Videos/season2
[ec2-user@ip-172-31-20-80 season2]$ cp *episode2.ogg ~/Documents/my_bestseller/vacation
[ec2-user@ip-172-31-20-80 season2]$ cd -
/home/ec2-user/Documents/my_bestseller/vacation
[ec2-user@ip-172-31-20-80 vacation]$ ls
mystery_chapter7.odf  mystery_chapter8.odf  tv_season2_episode1.ogg  tv_season2_episode2.ogg
[ec2-user@ip-172-31-20-80 vacation]$
[ec2-user@ip-172-31-20-80 vacation]$
[ec2-user@ip-172-31-20-80 vacation]$ cd ~/Documents/my_bestseller
[ec2-user@ip-172-31-20-80 my_bestseller]$ cp chapters/mystery_chapter[56].odf changes
[ec2-user@ip-172-31-20-80 my_bestseller]$ ls chapters
mystery_chapter3.odf  mystery_chapter4.odf  mystery_chapter5.odf  mystery_chapter6.odf
[ec2-user@ip-172-31-20-80 my_bestseller]$ ls changes
mystery_chapter5.odf  mystery_chapter6.odf
[ec2-user@ip-172-31-20-80 my_bestseller]$
[ec2-user@ip-172-31-20-80 my_bestseller]$
[ec2-user@ip-172-31-20-80 my_bestseller]$ cd changes
[ec2-user@ip-172-31-20-80 changes]$ cp mystery_chapter5.odf \
> mystery_chapter5_$(date +%F).odf
[ec2-user@ip-172-31-20-80 changes]$ cp mystery_chapter5.odf \
> mystery_chapter5_$(date +%s).odf
[ec2-user@ip-172-31-20-80 changes]$ ls
mystery_chapter5.odf             mystery_chapter5_2021-07-02.odf
mystery_chapter5_1625229312.odf  mystery_chapter6.odf
[ec2-user@ip-172-31-20-80 changes]$ rm mystery*
[ec2-user@ip-172-31-20-80 changes]$ cd ..
[ec2-user@ip-172-31-20-80 my_bestseller]$ rm changes
rm: cannot remove 'changes': Is a directory
[ec2-user@ip-172-31-20-80 my_bestseller]$ rmdir changes
[ec2-user@ip-172-31-20-80 my_bestseller]$ ls
chapters  editor  vacation
[ec2-user@ip-172-31-20-80 my_bestseller]$
[ec2-user@ip-172-31-20-80 my_bestseller]$
[ec2-user@ip-172-31-20-80 my_bestseller]$ rm -r vacation
[ec2-user@ip-172-31-20-80 my_bestseller]$ ls
chapters  editor
[ec2-user@ip-172-31-20-80 my_bestseller]$ cd
[ec2-user@ip-172-31-20-80 ~]$ mkdir ~/Documents/backups
[ec2-user@ip-172-31-20-80 ~]$ ln ~/Documents/project_plans/season2_project_plan.odf \
> ~/Documents/backups/season2_project_plan.odf.back
[ec2-user@ip-172-31-20-80 ~]$ ls -lR ~/Documents/
/home/ec2-user/Documents/:
total 0
drwxrwxr-x. 2 ec2-user ec2-user 43 Jul  2 12:41 backups
drwxrwxr-x. 4 ec2-user ec2-user 36 Jul  2 12:40 my_bestseller
drwxrwxr-x. 2 ec2-user ec2-user 70 Jul  2 12:21 project_plans

/home/ec2-user/Documents/backups:
total 0
-rw-rw-r--. 2 ec2-user ec2-user 0 Jul  2 12:21 season2_project_plan.odf.back

/home/ec2-user/Documents/my_bestseller:
total 0
drwxrwxr-x. 2 ec2-user ec2-user 118 Jul  2 12:28 chapters
drwxrwxr-x. 2 ec2-user ec2-user  62 Jul  2 12:27 editor

/home/ec2-user/Documents/my_bestseller/chapters:
total 0
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:22 mystery_chapter3.odf
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:22 mystery_chapter4.odf
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:22 mystery_chapter5.odf
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:22 mystery_chapter6.odf

/home/ec2-user/Documents/my_bestseller/editor:
total 0
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:22 mystery_chapter1.odf
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:22 mystery_chapter2.odf

/home/ec2-user/Documents/project_plans:
total 0
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 12:21 season1_project_plan.odf
-rw-rw-r--. 2 ec2-user ec2-user 0 Jul  2 12:21 season2_project_plan.odf
[ec2-user@ip-172-31-20-80 ~]$
```

## Chapter 4. Getting Help in Red Hat Enterprise Linux

```console
[ec2-user@ip-172-31-20-80 ~]$ man 1 su
[ec2-user@ip-172-31-20-80 ~]$ man man
[ec2-user@ip-172-31-20-80 ~]$ whereis man
man: /usr/bin/man /usr/share/man /usr/share/man/man1/man.1.gz

[student@workstation ~]$ man -k zip
...output omitted...
zipinfo (1)          - list detailed information about a ZIP archive
zipnote (1)          - write the comments in zipfile to stdout, edit comments and rename files in zipfile
zipsplit (1)         - split a zipfile into smaller zipfiles

[student@workstation ~]$ man -k boot
...output omitted...
bootctl (1)          - Control the firmware and boot manager settings
bootparam (7)        - introduction to boot time parameters of the Linux kernel
bootup (7)           - System bootup process
...output omitted...

[student@workstation ~]$ man -k ext4
...output omitted...
resize2fs (8)        - ext2/ext3/ext4 file system resizer
tune2fs (8)          - adjust tunable filesystem parameters on ext2/ext3/ext4 filesystems

[ec2-user@ip-172-31-20-80 ~]$ man tar
[ec2-user@ip-172-31-20-80 ~]$ pinfo tar

[ec2-user@ip-172-31-20-80 ~]$ man -t passwd > passwd.ps
[ec2-user@ip-172-31-20-80 ~]$ ls -al
total 32
drwx------. 3 ec2-user ec2-user    91 Jul  2 13:22 .
drwxr-xr-x. 3 root     root        22 Jul  2 11:15 ..
-rw-r--r--. 1 ec2-user ec2-user    18 Apr 21 14:04 .bash_logout
-rw-r--r--. 1 ec2-user ec2-user   141 Apr 21 14:04 .bash_profile
-rw-r--r--. 1 ec2-user ec2-user   376 Apr 21 14:04 .bashrc
drwx------. 2 ec2-user ec2-user    29 Jul  2 11:15 .ssh
-rw-rw-r--. 1 ec2-user ec2-user 20142 Jul  2 13:22 passwd.ps
[ec2-user@ip-172-31-20-80 ~]$ file passwd.ps
passwd.ps: PostScript document text conforming DSC level 3.0
[ec2-user@ip-172-31-20-80 ~]$ less passwd.ps

```

## Chapter 5. Creating, Viewing, and Editing Text Files

```console
[ec2-user@ip-172-31-20-80 ~]$ date > /tmp/saved-timestamp
[ec2-user@ip-172-31-20-80 ~]$ cat /tmp/saved-timestamp
Fri Jul  2 15:51:54 UTC 2021



[user@host ~]$ tail -n 100 /var/log/dmesg > /tmp/last-100-boot-messages
[user@host ~]$ cat file1 file2 file3 file4 > /tmp/all-four-in-one
[user@host ~]$ ls -a > /tmp/my-file-names
[user@host ~]$ echo "new line of information" >> /tmp/many-lines-of-information
[user@host ~]$ diff previous-file current-file >> /tmp/tracking-changes-made


[user@host ~]$ find /etc -name passwd 2> /tmp/errors
[user@host ~]$ find /etc -name passwd > /tmp/output 2> /tmp/errors
[user@host ~]$ find /etc -name passwd > /tmp/output 2> /dev/null
[user@host ~]$ find /etc -name passwd &> /tmp/save-both
[user@host ~]$ find /etc -name passwd >> /tmp/save-both 2>&1

[ec2-user@ip-172-31-20-80 ~]$ ls -l /usr/bin | less

[ec2-user@ip-172-31-20-80 ~]$ touch filee
[ec2-user@ip-172-31-20-80 ~]$ ls | wc -l
1
[ec2-user@ip-172-31-20-80 ~]$

[ec2-user@ip-172-31-20-80 ~]$ ls -t | head -n 10 > /tmp/ten-last-changed-files
[ec2-user@ip-172-31-20-80 ~]$ cat /tmp/ten-last-changed-files
filee

[ec2-user@ip-172-31-20-80 ~]$ ls -l | tee /tmp/saved-output | less
[ec2-user@ip-172-31-20-80 ~]$ ls -t | head -n 10 | tee /tmp/ten-last-changed-files
filee



[ec2-user@ip-172-31-20-80 ~]$ set | less
[ec2-user@ip-172-31-20-80 ~]$ COUNT=40
[ec2-user@ip-172-31-20-80 ~]$ echo $COUNT
40

[ec2-user@ip-172-31-20-80 ~]$ file1=/tmp/tmp.z9pXW0HqcC
[ec2-user@ip-172-31-20-80 ~]$ ls -l $file1
-rw-rw-r--. 1 ec2-user ec2-user 0 Jul  2 16:41 /tmp/tmp.z9pXW0HqcC
```

```console
[ec2-user@ip-172-31-20-80 ~]$ PS1="bash\$ "
bash$
bash$ PS1="[\u@\h \W]\$ "
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$
```

```console
[ec2-user@ip-172-31-20-80 ~]$ echo $PATH
/home/ec2-user/.local/bin:/home/ec2-user/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin
[ec2-user@ip-172-31-20-80 ~]$ export PATH=${PATH}:/home/user/sbin
[ec2-user@ip-172-31-20-80 ~]$ echo $PATH
/home/ec2-user/.local/bin:/home/ec2-user/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/home/user/sbin
[ec2-user@ip-172-31-20-80 ~]$
[ec2-user@ip-172-31-20-80 ~]$ env

[ec2-user@ip-172-31-20-80 ~]$ echo $file1
/tmp/tmp.z9pXW0HqcC
[ec2-user@ip-172-31-20-80 ~]$ unset file1
[ec2-user@ip-172-31-20-80 ~]$ echo $file1

```

## Chapter 6. Managing Local Users and Groups
```console
[ec2-user@ip-172-31-26-63 ~]$ id
uid=1000(ec2-user) gid=1000(ec2-user) groups=1000(ec2-user),4(adm),190(systemd-journal) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

[ec2-user@ip-172-31-26-63 ~]$ id user02
uid=1001(user02) gid=1001(user02) groups=1001(user02)

[user01@host ~]$ ls -l file1
-rw-rw-r--. 1 user01 user01 0 Feb  5 11:10 file1
[user01@host]$ ls -ld dir1
drwxrwxr-x. 2 user01 user01 6 Feb  5 11:10 dir1

[ec2-user@ip-172-31-26-63 ~]$ ps -au
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root        1095  0.0  0.1  13656  1596 tty1     Ss+  23:19   0:00 /sbin/agetty -o -p -- \u --noclear tty1 linux
root        1096  0.0  0.2  16224  2112 ttyS0    Ss+  23:19   0:00 /sbin/agetty -o -p -- \u --keep-baud 115200,38400,960
ec2-user    4683  0.0  0.5  31280  4408 pts/0    Ss   23:20   0:00 -bash
ec2-user    4851  0.0  0.4  62988  3932 pts/0    R+   23:22   0:00 ps -au

[ec2-user@ip-172-31-26-63 etc]$ cat passwd
[ec2-user@ip-172-31-26-63 etc]$ cat group
[ec2-user@ip-172-31-26-63 etc]$ sudo cat /etc/shadow

[user02@host ~]$ sudo tail /var/log/secure

[ec2-user@ip-172-31-26-63 ~]$ sudo -i
```

```console
[student@servera ~]$ sudo su -
[sudo] password for student: student
[root@servera ~]# 

[root@servera ~]# useradd operator1
[root@servera ~]# tail /etc/passwd
...output omitted...
operator1:x:1002:1002::/home/operator1:/bin/bash

[root@servera ~]# passwd operator1
Changing password for user operator1.
New password: redhat
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: redhat
passwd: all authentication tokens updated successfully.

[root@servera ~]# passwd operator1
Changing password for user operator1.
New password: redhat
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: redhat
passwd: all authentication tokens updated successfully.

[root@servera ~]# useradd operator3
[root@servera ~]# passwd operator3
Changing password for user operator3.
New password: redhat
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: redhat
passwd: all authentication tokens updated successfully.
[root@servera ~]# usermod -c "Operator One" operator1
[root@servera ~]# usermod -c "Operator Two" operator2
[root@servera ~]# tail /etc/passwd

[root@servera ~]# userdel -r operator3
[root@servera ~]# tail /etc/passwd
...output omitted...
operator1:x:1002:1002:Operator One:/home/operator1:/bin/bash
operator2:x:1003:1003:Operator Two:/home/operator2:/bin/bash

[root@servera ~]# exit
logout
[student@servera ~]$ 


[ec2-user@ip-172-31-22-184 ~]$ sudo groupadd -g 10000 group01
[ec2-user@ip-172-31-22-184 ~]$ tail /etc/group
tss:x:59:
polkitd:x:996:
ssh_keys:x:995:
unbound:x:994:
sssd:x:993:
chrony:x:992:
sshd:x:74:
ec2-user:x:1000:
operator3:x:1001:
group01:x:10000:

[ec2-user@ip-172-31-22-184 ~]$ sudo groupadd -r group02
[ec2-user@ip-172-31-22-184 ~]$ tail /etc/group
polkitd:x:996:
ssh_keys:x:995:
unbound:x:994:
sssd:x:993:
chrony:x:992:
sshd:x:74:
ec2-user:x:1000:
operator3:x:1001:
group01:x:10000:
group02:x:991:

[ec2-user@ip-172-31-22-184 ~]$ sudo groupmod -n group0022 group02
[ec2-user@ip-172-31-22-184 ~]$ tail /etc/group
polkitd:x:996:
ssh_keys:x:995:
unbound:x:994:
sssd:x:993:
chrony:x:992:
sshd:x:74:
ec2-user:x:1000:
operator3:x:1001:
group01:x:10000:
group0022:x:991:

[ec2-user@ip-172-31-22-184 ~]$ sudo groupdel group0022

[ec2-user@ip-172-31-22-184 ~]$ sudo useradd user02
[ec2-user@ip-172-31-22-184 ~]$ id user02
uid=1002(user02) gid=1002(user02) groups=1002(user02)
[ec2-user@ip-172-31-22-184 ~]$ sudo usermod -g group01 user02
[ec2-user@ip-172-31-22-184 ~]$ id user02
uid=1002(user02) gid=10000(group01) groups=10000(group01)

[ec2-user@ip-172-31-22-184 ~]$ sudo useradd user03
[ec2-user@ip-172-31-22-184 ~]$ sudo usermod -aG group01 user03
[ec2-user@ip-172-31-22-184 ~]$ id user03
uid=1003(user03) gid=1003(user03) groups=1003(user03),10000(group01)
```

```console
[root@ip-172-31-22-184 ~]# chage -l user03
Last password change                                    : Jul 07, 2021
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
[root@ip-172-31-22-184 ~]#
[user01@host ~]$ sudo chage -m 0 -M 90 -W 7 -I 14 user03
[user01@host ~]$ date -d "+45 days" -u
Thu May 23 17:01:20 UTC 2019
[user01@host ~]$ sudo usermod -L user03
[user01@host ~]$ su - user03
Password: redhat
su: Authentication failure
[user01@host ~]$ sudo usermod -L -e 2019-10-05 user03
[user01@host ~]$ usermod -s /sbin/nologin user03
[user01@host ~]$ su - user03
Last login: Wed Feb  6 17:03:06 IST 2019 on pts/0
This account is currently not available.

[student@servera ~]$ sudo chage -M 90 operator1
[student@servera ~]$ sudo chage -l operator1
Last password change      : Jan 25, 2019
Password expires          : Apr 25, 2019
Password inactive         : never
Account expires           : never
Minimum number of days between password change    : 0
Maximum number of days between password change    : 90
Number of days of warning before password expires : 7


[student@servera ~]$ sudo chage -d 0 operator1
[student@servera ~]$ date -d "+180 days" +%F
2019-07-24
[student@servera ~]$ sudo chage -E 2019-07-24 operator1
[student@servera ~]$ sudo chage -l operator1
Last password change      : Jan 25, 2019
Password expires          : Apr 25, 2019
Password inactive         : never
Account expires           : Jul 24, 2019
Minimum number of days between password change    : 0
Maximum number of days between password change    : 90
Number of days of warning before password expires : 7


 /etc/login.defs.

 ...output omitted...
# Password aging controls:
#
#       PASS_MAX_DAYS   Maximum number of days a password may be
#       used.
#       PASS_MIN_DAYS   Minimum number of days allowed between
#       password changes.
#       PASS_MIN_LEN    Minimum acceptable password length.
#       PASS_WARN_AGE   Number of days warning given before a
#       password expires.
#
PASS_MAX_DAYS   30
PASS_MIN_DAYS   0
PASS_MIN_LEN    5
PASS_WARN_AGE   7
...output omitted...

[student@serverb ~]$ sudo groupadd -g 35000 consultants

/etc/sudoers.d/consultants
%consultants  ALL=(ALL) ALL

[student@serverb ~]$ sudo useradd -G consultants consultant1
[student@serverb ~]$ sudo useradd -G consultants consultant2
[student@serverb ~]$ sudo useradd -G consultants consultant3

Determine the date 90 days in the future.
[student@serverb ~]$ date -d "+90 days" +%F
2019-04-28

Set the account to expire on the date displayed in the preceding step.
[student@serverb ~]$ sudo chage -E 2019-04-28 consultant1
[student@serverb ~]$ sudo chage -E 2019-04-28 consultant2
[student@serverb ~]$ sudo chage -E 2019-04-28 consultant3

Change the password policy for the consultant2 account to require a new password every 15 days

[student@serverb ~]$ sudo chage -M 15 consultant2

Set the last day of th epassword change to 0 so that the users are forced to chance the password whenever they log in to the system for the first time
[student@serverb ~]$ sudo chage -d 0 consultant1
[student@serverb ~]$ sudo chage -d 0 consultant2
[student@serverb ~]$ sudo chage -d 0 consultant3
```

## Chapter 7. Controlling Access to Files

```console
The -l option of the ls command shows detailed information about permissions and ownership:
[user@host~]$ ls -l test
-rw-rw-r--. 1 student student 0 Feb  8 17:36 test

Use the -d option to show detailed information about a directory itself, and not its contents.
[user@host ~]$ ls -ld /home
drwxr-xr-x. 5 root root 4096 Jan 31 22:00 /home

The first character of the long listing is the file type, interpreted like this:

- is a regular file.

d is a directory.

l is a soft link.

Other characters represent hardware devices (b and c) or other special-purpose files (p and s).

The next nine characters are the file permissions. These are in three sets of three characters: permissions that apply to the user that owns the file, the group that owns the file, and all other users. 
If the set shows rwx, that category has all three permissions, read, write, and execute. If a letter has been replaced by -, then that category does not have that permission.

------
Use the chown command to change the group ownership of the consultants directory to consultants.
[root@servera ~]# chown :consultants /home/consultants

Use the ls command to confirm that the permissions of the consultants group allow 
its group members to create files in, and delete files from the /home/consultants directory.
[root@servera ~]# ls -ld /home/consultants
drwxr-xr-x.  2 root    consultants       6 Feb  1 12:08 /home/consultants

[root@servera ~]# chmod g+w /home/consultants
[root@servera ~]# ls -ld /home/consultants
drwxrwxr-x. 2 root consultants 6 Feb  1 13:21 /home/consultants 


Use the chmod command to forbid others from accessing files in the /home/consultants directory.
[root@servera ~]# chmod 770 /home/consultants
[root@servera ~]# ls -ld /home/consultants
drwxrwx---. 2 root consultants 6 Feb  1 12:08 /home/consultants/

------
Use the chown command to change the group ownership of the consultant1.txt file to consultants.
[consultant1@servera consultants]$ chown :consultants consultant1.txt
[consultant1@servera consultants]$ ls -l consultant1.txt
-rw-rw-r--. 1 consultant1 consultants 0 Feb  1 12:53 consultant1.txt



```