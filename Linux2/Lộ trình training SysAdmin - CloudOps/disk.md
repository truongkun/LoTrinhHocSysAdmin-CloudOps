# Kiểm tra dung lượng disk

## DF

- Lệnh df viết tắt của “disk filesystem“, nó được dùng để lấy toàn bộ thông tin về lượng ổ cứng khả dụng và lượng ổ cứng đã dùng của các file hệ thống trên linux
    **Một số option quan trọng:**

    - `df -h` : hiển thị theo format dung lượng K,M,G

    - `df -i` : hiển thị theo format inodes

## DU

- Lệnh du là viết tắt của từ “disk usage” là một công cụ dòng lệnh được cung cấp bởi Linux, nhằm báo cáo dung lượng ổ đĩa được sử dụng bởi các thư mục và file. Đây là công cụ chính để phân tích không gian ổ đĩa trong dòng lệnh.
    
    **Một số option quan trọng:**

    - `du -h `: hiển thị theo format dung lượng K,M,G

    - `du -shc` : hiển thị tổng dung lượng

## So sánh `du` và `df`

|Chức năng       |du (Disk Usage)|df (Disk Free)|
|:---------------|:---------------|:------------|
|Mục đích        |Đo lường dung lượng thực sự của tệp và thư mục|Hiển thị thông tin về dung lượng của hệ thống tệp|
|Đơn vị đo       |Thường hiển thị dung lượng trong bytes hoặc các đơn vị khác (kilo, mega, giga)|Thường hiển thị dung lượng trong blocks hoặc các đơn vị tương tự|
|Phạm vi         |Dùng để đo lường dung lượng của các thư mục và tệp cụ thể|Hiển thị thông tin về dung lượng của toàn bộ hệ thống tệp|
|Thông tin cụ thể|Hiển thị dung lượng của các thư mục và tệp cụ thể|Hiển thị tổng dung lượng, dung lượng sử dụng, dung lượng còn trống và phân bổ trên các hệ thống tệp khác nhau|
|Ví dụ           |du -sh /<thư/mục>|	df -h|

## Điểm chính khác biệt giữa `du và df` là `mục đích sử dụng`.` 
- `du` được sử dụng để đo lường dung lượng của các thư mục và tệp cụ thể trong hệ thống tệp,
- `df` được sử dụng để hiển thị tổng quan về dung lượng, dung lượng sử dụng và dung lượng còn trống trên toàn bộ hệ thống tệp.

## LB2

### ktra ổ cứng

    C1. cat /proc/partitions

>

    C2. ls -l /dev/ | grep -i "sda*"

>

    C3. fdisk -l

>

## Chia ổ sdb

    sudo fdisk /dev/sdb

```
Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (1-4, default 1): 1   
First sector (2048-130023423, default 2048): 2048
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-130023423, default 130023423): +10G

Created a new partition 1 of type 'Linux' and of size 10 GiB. // ổ 1

Command (m for help): n
Partition type
   p   primary (1 primary, 0 extended, 3 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (2-4, default 2): 2
First sector (20973568-130023423, default 20973568): 20973568
Last sector, +/-sectors or +/-size{K,M,G,T,P} (20973568-130023423, default 130023423): +20G

Created a new partition 2 of type 'Linux' and of size 20 GiB. // ổ 2

Command (m for help): n
Partition type
   p   primary (2 primary, 0 extended, 2 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (3,4, default 3): 3
First sector (62916608-130023423, default 62916608): 
Last sector, +/-sectors or +/-size{K,M,G,T,P} (62916608-130023423, default 130023423): 

Created a new partition 3 of type 'Linux' and of size 32 GiB. // ổ 3

Command (m for help): m

Help:

  DOS (MBR)
   a   toggle a bootable flag
   b   edit nested BSD disklabel
   c   toggle the dos compatibility flag

  Generic
   d   delete a partition
   F   list free unpartitioned space
   l   list known partition types
   n   add a new partition
   p   print the partition table
   t   change a partition type
   v   verify the partition table
   i   print information about a partition

  Misc
   m   print this menu
   u   change display/entry units
   x   extra functionality (experts only)

  Script
   I   load disk layout from sfdisk script file
   O   dump disk layout to sfdisk script file

  Save & Exit
   w   write table to disk and exit
   q   quit without saving changes

  Create a new label
   g   create a new empty GPT partition table
   G   create a new empty SGI (IRIX) partition table
   o   create a new empty DOS partition table
   s   create a new empty Sun partition table


Command (m for help): w   // lưu lại các ổ vừa tạo
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.
```

## Fomart ổ vừa tạo bằng `mkfs`

Xem các loại cấu hình

    mkfs + nút Tab*2 // danh sách cấu hình để fomart

>
Fomart cấu hình ext4 cho sdb1

    sudo mkfs -t ext4 /dev/sdb1

Fomart cấu hình xfs cho sdb2

    sudo mkfs -t xfs /dev/sdb2

Nếu HDH chưa hỗ trợ xfs thì hãy cài 

    sudo apt update
    sudo apt install xfsprogs

Fomart cấu hình ext3 cho sdb3

    sudo mkfs -t ext3 /dev/sdb3

**Kết quả**
```
truongpv@ubuntu:~$ sudo mkfs -t ext4 /dev/sdb1
[sudo] password for truongpv: 
mke2fs 1.45.5 (07-Jan-2020)
Creating filesystem with 2621440 4k blocks and 655360 inodes
Filesystem UUID: dee88177-04f8-4fdc-aa58-b0a3a2ea74fd
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information: done 

truongpv@ubuntu:~$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease           
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease                  
Get:3 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Hit:4 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease
Get:5 http://us.archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [780 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [1,175 kB]
Fetched 2,069 kB in 34s (60.6 kB/s)                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
248 packages can be upgraded. Run 'apt list --upgradable' to see them.

truongpv@ubuntu:~$ sudo apt install xfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libreadline5
Suggested packages:
  xfsdump attr quota
The following NEW packages will be installed:
  libreadline5 xfsprogs
0 upgraded, 2 newly installed, 0 to remove and 248 not upgraded.
Need to get 873 kB of archives.
After this operation, 3,076 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu focal/main amd64 libreadline5 amd64 5.2+dfsg-3build3 [100 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu focal/main amd64 xfsprogs amd64 5.3.0-1ubuntu2 [773 kB]
Fetched 873 kB in 33s (26.1 kB/s) 
Selecting previously unselected package libreadline5:amd64.
(Reading database ... 157237 files and directories currently installed.)
Preparing to unpack .../libreadline5_5.2+dfsg-3build3_amd64.deb ...
Unpacking libreadline5:amd64 (5.2+dfsg-3build3) ...
Selecting previously unselected package xfsprogs.
Preparing to unpack .../xfsprogs_5.3.0-1ubuntu2_amd64.deb ...
Unpacking xfsprogs (5.3.0-1ubuntu2) ...
Setting up libreadline5:amd64 (5.2+dfsg-3build3) ...
Setting up xfsprogs (5.3.0-1ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
Processing triggers for initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-100-generic

truongpv@ubuntu:~$ sudo mkfs -t xfs /dev/sdb2
meta-data=/dev/sdb2              isize=512    agcount=4, agsize=1310720 blks
         =                       sectsz=512   attr=2, projid32bit=1
         =                       crc=1        finobt=1, sparse=1, rmapbt=0
         =                       reflink=1
data     =                       bsize=4096   blocks=5242880, imaxpct=25
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0, ftype=1
log      =internal log           bsize=4096   blocks=2560, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0

truongpv@ubuntu:~$ sudo mkfs -t ext3 /dev/sdb3
mke2fs 1.45.5 (07-Jan-2020)
Creating filesystem with 8388352 4k blocks and 2097152 inodes
Filesystem UUID: afe84d97-9f73-42f2-b822-e72a7fc25b89
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done  
```

## Kết nối

Tạo 3 folder data1, data2, data3

    sudo mkdir /data1
    sudo mkdir /data2
    sudo mkdir /data3

## Cấu hình file /etc/fstab:

Mở file /etc/fstab với trình soạn thảo văn bản:

    sudo nano /etc/fstab

Thêm các dòng sau vào cuối file:

    /dev/sda1   /data1   ext4   defaults   0   0
    /dev/sda2   /data2   xfs    defaults   0   0
    /dev/sda3   /data3   ext3   defaults   0   0

Gắn kết các phân vùng:

  - Gắn kết tất cả các phân vùng:

        sudo mount -a
        
**kết quả**

![alt text](img/mount%20-ajpg)


![alt text](img/ktra%20mount1.jpg)


