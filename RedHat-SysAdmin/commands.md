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