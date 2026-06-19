# LFS-code
Most of the LFS code I had written and happened so far, I could not save that part where I booted from pendrive and so. Not just code.

[artix ~]# bash --version | head -n1  
ld --version | head -n1  
gcc --version | head -n1 
g++ --version | head -n1  
make --version | head -n1  
python3 --version  
bison --version | head -n1  
grep --version | head -n1  
tar --version | head -n1  
xz --version | head -n1  
GNU bash, version 5.3.9(1)-release (x86_64-pc-linux-gnu)  
GNU ld (GNU Binutils) 2.46.0  
gcc (GCC) 16.1.1 20260430  
g++ (GCC) 16.1.1 20260430  
GNU Make 4.4.1  
Python 3.14.5  
bison (GNU Bison) 3.8.2  
grep (GNU grep) 3.12-modified  
tar (GNU tar) 1.35  
xz (XZ Utils) 5.8.3  
[artix ~]# uname -a  
Linux artix 7.0.12-artix1-1 #1 SMP PREEMPT_DYNAMIC Wed, 10 Jun 2026 16:57:23 +0000 x86_64 GNU/Linux  
[artix ~]# /dev/sdb  
-bash: /dev/sdb: No such file or directory  
[artix ~]# /dev/nvme0n1p6  
-bash: /dev/nvme0n1p6: No such file or directory  
[artix ~]# /dev/sdb  
-bash: /dev/sdb: No such file or directory  
[artix ~]# lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINTS  
NAME          SIZE FSTYPE MOUNTPOINTS  
sda         931.5G           
|-sda1        512M ext4   /boot  
`-sda2        931G ext4   /  
nvme0n1     223.6G           
|-nvme0n1p1   200M vfat      
|-nvme0n1p2    16M           
|-nvme0n1p3 222.6G ntfs      
`-nvme0n1p4   777M ntfs      
[artix ~]# fdisk -l  
Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors  
Disk model: ST1000LM035-1RK1  
Units: sectors of 1 * 512 = 512 bytes  
Sector size (logical/physical): 512 bytes / 4096 bytes  
I/O size (minimum/optimal): 4096 bytes / 4096 bytes  
Disklabel type: dos  
Disk identifier: 0x27cfd468  
  
Device     Boot   Start        End    Sectors  Size Id Type  
/dev/sda1          2048    1050623    1048576  512M 83 Linux  
/dev/sda2       1050624 1953525167 1952474544  931G 83 Linux  
  
  
Disk /dev/nvme0n1: 223.57 GiB, 240057409536 bytes, 468862128 sectors  
Disk model: KINGSTON SA1000M8240G                      
Units: sectors of 1 * 512 = 512 bytes  
Sector size (logical/physical): 512 bytes / 512 bytes  
I/O size (minimum/optimal): 512 bytes / 512 bytes  
Disklabel type: gpt  
Disk identifier: 01696273-FCC8-4234-BB36-6B837976C894  
  
Device             Start       End   Sectors   Size Type  
/dev/nvme0n1p1      2048    411647    409600   200M EFI System  
/dev/nvme0n1p2    411648    444415     32768    16M Microsoft reserved  
/dev/nvme0n1p3    444416 467267583 466823168 222.6G Microsoft basic data  
/dev/nvme0n1p4 467267584 468858879   1591296   777M Windows recovery environment  
[artix ~]# sdb    100G  
-bash: sdb: command not found  
[artix ~]# sdb 100G  
-bash: sdb: command not found  
[artix ~]# nvme0n1p6  80G  
-bash: nvme0n1p6: command not found  
[artix ~]# grep -E 'CONFIG_USER_NS|CONFIG_FHANDLE' /boot/config-$(uname -r) 2>/dev/null  
[artix ~]# echo $LANG  
hu_HU.UTF-8  
[artix ~]# df -h /  
Filesystem      Size  Used Avail Use% Mounted on  
/dev/sda2       916G   24G  846G   3% /  
[artix ~]# free -h  
nproc  
              total        used        free      shared  buff/cache   available  
Mem:            15Gi       3.3Gi        10Gi       150Mi       2.2Gi        11Gi  
Swap:             0B          0B          0B  
8  
[artix ~]# cat /etc/artix-release 2>/dev/null  
  
[artix ~]# cat /etc/os-release  
NAME="Artix Linux"  
PRETTY_NAME="Artix Linux"  
ID=artix  
BUILD_ID=rolling  
ANSI_COLOR="38;2;23;147;209"  
HOME_URL="https://artixlinux.org/"  
DOCUMENTATION_URL="https://wiki.artixlinux.org/"  
SUPPORT_URL="https://forum.artixlinux.org/"  
BUG_REPORT_URL="https://bugs.artixlinux.org/"  
PRIVACY_POLICY_URL="https://terms.artixlinux.org/docs/privacy-policy/"  
LOGO=artixlinux-logo  
[artix ~]# ls /sys/firmware/efi  
ls: cannot access '/sys/firmware/efi': No such file or directory  
[artix ~]# ls /sys/firmware/efi  
ls: cannot access '/sys/firmware/efi': No such file or directory  
[artix ~]# parted -l  
Model: ATA ST1000LM035-1RK1 (scsi)  
Disk /dev/sda: 1000GB  
Sector size (logical/physical): 512B/4096B  
Partition Table: msdos  
Disk Flags:    
  
Number  Start   End     Size    Type     File system  Flags  
1      1049kB  538MB   537MB   primary  ext4  
2      538MB   1000GB  1000GB  primary  ext4  
  
  
Model: KINGSTON SA1000M8240G (nvme)  
Disk /dev/nvme0n1: 240GB  
Sector size (logical/physical): 512B/512B  
Partition Table: gpt  
Disk Flags:    
  
Number  Start   End    Size    File system  Name                          Flags  
1      1049kB  211MB  210MB   fat32        Basic data partition          boot, esp, no_automount  
2      211MB   228MB  16.8MB               Microsoft reserved partition  msftres, no_automount  
3      228MB   239GB  239GB   ntfs         Basic data partition          msftdata  
4      239GB   240GB  815MB   ntfs                                       hidden, diag, no_automount
[artix sda sda       
├─sda1 512M ext4 /boot  
└─sda2 931G ext4 /  
-bash: sda: command not found  
-bash: $'\342\224\234\342\224\200sda1': command not found  
-bash: $'\342\224\224\342\224\200sda2': command not found  
[artix ~]# tune2fs -l /dev/sda2 | grep 'Filesystem state'  
Filesystem state:         clean  
[artix ~]# pacman -S smartmontools  
warning: smartmontools-7.5-1.1 is up to date -- reinstalling  
resolving dependencies...  
looking for conflicting packages...  
  
Packages (1) smartmontools-7.5-1.1  
  
Total Installed Size:  2.07 MiB  
Net Upgrade Size:      0.00 MiB  
  
:: Proceed with installation? [Y/n] y  
(1/1) checking keys in keyring                                        [#######################################] 100%  
(1/1) checking package integrity                                      [#######################################] 100%  
(1/1) loading package files                                           [#######################################] 100%  
(1/1) checking for file conflicts                                     [#######################################] 100%  
(1/1) checking available disk space                                   [#######################################] 100%  
:: Processing package changes...  
(1/1) reinstalling smartmontools                                      [#######################################] 100%  
[artix ~]# smartctl -H /dev/sda  
smartctl 7.5 2025-04-30 r5714 [x86_64-linux-7.0.12-artix1-1] (local build)  
Copyright (C) 2002-25, Bruce Allen, Christian Franke, www.smartmontools.org  
  
=== START OF READ SMART DATA SECTION ===  
SMART overall-health self-assessment test result: PASSED  
  
[artix ~]# ls /sys/firmware/efi  
ls: cannot access '/sys/firmware/efi': No such file or directory  
[artix ~]# parted -l  
Model: ATA ST1000LM035-1RK1 (scsi)  
Disk /dev/sda: 1000GB  
Sector size (logical/physical): 512B/4096B  
Partition Table: msdos  
Disk Flags:    
  
Number  Start   End     Size    Type     File system  Flags  
1      1049kB  538MB   537MB   primary  ext4  
2      538MB   1000GB  1000GB  primary  ext4  
  
  
Model: KINGSTON SA1000M8240G (nvme)  
Disk /dev/nvme0n1: 240GB  
Sector size (logical/physical): 512B/512B  
Partition Table: gpt  
Disk Flags:    
  
Number  Start   End    Size    File system  Name                          Flags  
1      1049kB  211MB  210MB   fat32        Basic data partition          boot, esp, no_automount  
2      211MB   228MB  16.8MB               Microsoft reserved partition  msftres, no_automount  
3      228MB   239GB  239GB   ntfs         Basic data partition          msftdata  
4      239GB   240GB  815MB   ntfs                                       hidden, diag, no_automount
[artix ~]# smartctl -H /dev/sda  
smartctl 7.5 2025-04-30 r5714 [x86_64-linux-7.0.12-artix1-1] (local build)  
Copyright (C) 2002-25, Bruce Allen, Christian Franke, www.smartmontools.org  
  
=== START OF READ SMART DATA SECTION ===  
SMART overall-health self-assessment test result: PASSED  
  
[artix ~]# ls /sys/firmware/efi  
ls: cannot access '/sys/firmware/efi': No such file or directory  
[artix ~]# parted -l  
Model: ATA ST1000LM035-1RK1 (scsi)  
Disk /dev/sda: 1000GB  
Sector size (logical/physical): 512B/4096B  
Partition Table: msdos  
Disk Flags:    
  
Number  Start   End     Size    Type     File system  Flags  
1      1049kB  538MB   537MB   primary  ext4  
2      538MB   1000GB  1000GB  primary  ext4  
  
  
Model: KINGSTON SA1000M8240G (nvme)  
Disk /dev/nvme0n1: 240GB  
Sector size (logical/physical): 512B/512B  
Partition Table: gpt  
Disk Flags:    
  
Number  Start   End    Size    File system  Name                          Flags  
1      1049kB  211MB  210MB   fat32        Basic data partition          boot, esp, no_automount  
2      211MB   228MB  16.8MB               Microsoft reserved partition  msftres, no_automount  
3      228MB   239GB  239GB   ntfs         Basic data partition          msftdata  
4      239GB   240GB  815MB   ntfs                                       hidden, diag, no_automount  
  
  
[artix ~]# resize2fs -P /dev/sda2  
resize2fs 1.47.4 (6-Mar-2025)  
Estimated minimum size of the filesystem: 7297636  
[artix ~]# dumpe2fs -h /dev/sda2 | grep 'Block count\|Block size'  
dumpe2fs 1.47.4 (6-Mar-2025)  
Block count:              244059318  
Block size:               4096
  
[artix ~]# resize2fs -P /dev/sda2  
resize2fs 1.47.4 (6-Mar-2025)  
Estimated minimum size of the filesystem: 7297636  
[artix ~]# dumpe2fs -h /dev/sda2 | grep 'Block count\|Block size'  
dumpe2fs 1.47.4 (6-Mar-2025)  
Block count:              244059318  
Block size:               4096  
[artix ~]# man resize2fs  
-bash: man: command not found  
[artix ~]# resize2fs  
resize2fs 1.47.4 (6-Mar-2025)  
Usage: resize2fs [-d debug_flags] [-f] [-F] [-M] [-P] [-p] device [-b|-s|new_size] [-S RAID-stride] [-z undo_file] 

I couldn't save the booting from pendrive part.

[Zsupsz@artix ~]$ lsblk  
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS  
sda           8:0    0 931.5G  0 disk    
|-sda1        8:1    0   512M  0 part /boot  
|-sda2        8:2    0   830G  0 part /  
`-sda3        8:3    0   100G  0 part    
nvme0n1     259:0    0 223.6G  0 disk    
|-nvme0n1p1 259:1    0   200M  0 part    
|-nvme0n1p2 259:2    0    16M  0 part    
|-nvme0n1p3 259:3    0 222.6G  0 part    
`-nvme0n1p4 259:4    0   777M  0 part    
[artix ~]# sudo mkfs.ext4 /dev/sda3  
mke2fs 1.47.4 (6-Mar-2025)  
Creating filesystem with 26214400 4k blocks and 6553600 inodes  
Filesystem UUID: a030d025-2563-4862-8263-068b34fa6a25  
Superblock backups stored on blocks:    
       32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,    
       4096000, 7962624, 11239424, 20480000, 23887872  
  
Allocating group tables: done                               
Writing inode tables: done                               
Creating journal (131072 blocks): done  
Writing superblocks and filesystem accounting information: done      
  
[artix ~]# sudo mkdir /data  
[artix ~]# sudo mount /dev/sda3 /data  
[artix ~]# df -h  
Filesystem      Size  Used Avail Use% Mounted on  
dev              10M     0   10M   0% /dev  
run             7.6G  2.2M  7.6G   1% /run  
/dev/sda2       816G   24G  751G   4% /  
shm             7.6G     0  7.6G   0% /dev/shm  
/dev/sda1       488M  180M  273M  40% /boot  
tmpfs           1.6G  100K  1.6G   1% /run/user/1000  
/dev/sda3        98G   32K   93G   1% /data  
[artix ~]# sudo blkid /dev/sda3  
/dev/sda3: UUID="a030d025-2563-4862-8263-068b34fa6a25" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="27cfd468-03"  
[artix ~]# sudo cp /etc/fstab /etc/fstab.bak  
[artix ~]# sudo nano /etc/fstab  
[artix ~]# sudo umount /data  
sudo mount -a  
[artix ~]# df -h  
Filesystem      Size  Used Avail Use% Mounted on  
dev              10M     0   10M   0% /dev  
run             7.6G  2.2M  7.6G   1% /run  
/dev/sda2       816G   24G  751G   4% /  
shm             7.6G     0  7.6G   0% /dev/shm  
/dev/sda1       488M  180M  273M  40% /boot  
tmpfs           1.6G  100K  1.6G   1% /run/user/1000
[artix ~]# ls -l /etc/fstab  
-rw-r--r-- 1 root root 312 May 24 10:37 /etc/fstab  
[artix ~]# file /etc/fstab  
/etc/fstab: ASCII text  
[artix ~]# echo 'UUID=a030d025-2563-4862-8263-068b34fa6a25 /data ext4 defaults 0 2' | sudo tee -a /etc/fstab  
UUID=a030d025-2563-4862-8263-068b34fa6a25 /data ext4 defaults 0 2  
[artix ~]# cat /etc/fstab  
# Static information about the filesystems.  
# See fstab(5) for details.  
  
# <file system> <dir> <type> <options> <dump> <pass>  
# /dev/sda2  
UUID=0744ccef-a565-47fb-bd90-65a293a769a1       /               ext4            rw,relatime     0 1  
  
# /dev/sda1  
UUID=3d317915-7e8d-4438-a138-a7840655f152       /boot           ext4            rw,relatime     0 2  
  
UUID=a030d025-2563-4862-8263-068b34fa6a25 /data ext4 defaults 0 2  
[artix ~]# sudo mount -a  
[artix ~]# findmnt /data  
TARGET SOURCE    FSTYPE OPTIONS  
/data  /dev/sda3 ext4   rw,relatime  
[artix ~]#
[artix ~]# sudo mkdir -pv /mnt/lfs  
mkdir: created directory '/mnt/lfs'  
[artix ~]# sudo umount /data    
sudo mount /dev/sda3 /mnt/lfs  
[artix ~]# findmnt /mnt/lfs  
TARGET   SOURCE    FSTYPE OPTIONS  
/mnt/lfs /dev/sda3 ext4   rw,relatime  
[artix ~]# UUID=a030d025-2563-4862-8263-068b34fa6a25 /data ext4 defaults 0 2  
-bash: /data: Is a directory  
[artix ~]# UUID=a030d025-2563-4862-8263-068b34fa6a25 /mnt/lfs ext4 defaults 0 2  
-bash: /mnt/lfs: Is a directory  
[artix ~]# sudo mount -a  
[artix ~]# findmnt /mnt/lfs  
TARGET   SOURCE    FSTYPE OPTIONS  
/mnt/lfs /dev/sda3 ext4   rw,relatime  
[artix ~]# export LFS=/mnt/lfs    
  
sudo mkdir -pv $LFS/sources  
sudo chmod -v a+wt $LFS/sources  
mkdir: created directory '/mnt/lfs/sources'  
mode of '/mnt/lfs/sources' changed from 0755 (rwxr-xr-x) to 1777 (rwxrwxrwt)  
[artix ~]#

✓ sda3 exists  
✓ ext4 filesystem created  
✓ mounted at /mnt/lfs  
✓ /mnt/lfs/sources exists  
✓ sticky bit set correctly (1777)  
✓ host system healthy  
✓ ready for LFS Chapter 3
[artix ~]# grep sda3 /etc/fstab  
grep lfs /etc/fstab  
[artix ~]# sudo groupadd lfs  
sudo useradd -s /bin/bash -g lfs -m -k /dev/null lfs  
sudo passwd lfs  
New password:    
Retype new password:    
passwd: password updated successfully  
[artix ~]# sudo chown -v lfs $LFS/{usr{,/*},lib,var,etc,bin,sbin,tools}  
chown: cannot access '/mnt/lfs/usr': No such file or directory  
failed to change ownership of '/mnt/lfs/usr' to lfs  
chown: cannot access '/mnt/lfs/usr/*': No such file or directory  
failed to change ownership of '/mnt/lfs/usr/*' to lfs  
chown: cannot access '/mnt/lfs/lib': No such file or directory  
failed to change ownership of '/mnt/lfs/lib' to lfs  
chown: cannot access '/mnt/lfs/var': No such file or directory  
failed to change ownership of '/mnt/lfs/var' to lfs  
chown: cannot access '/mnt/lfs/etc': No such file or directory  
failed to change ownership of '/mnt/lfs/etc' to lfs  
chown: cannot access '/mnt/lfs/bin': No such file or directory  
failed to change ownership of '/mnt/lfs/bin' to lfs  
chown: cannot access '/mnt/lfs/sbin': No such file or directory  
failed to change ownership of '/mnt/lfs/sbin' to lfs  
chown: cannot access '/mnt/lfs/tools': No such file or directory  
failed to change ownership of '/mnt/lfs/tools' to lfs  
[artix ~]# ls -la /mnt/lfs  
total 28  
drwxr-xr-x 4 root root  4096 Jun 18 23:17 .  
drwxr-xr-x 4 root root  4096 Jun 18 23:16 ..  
drwx------ 2 root root 16384 Jun 18 23:03 lost+found  
drwxrwxrwt 2 root root  4096 Jun 18 23:17 sources  
[artix ~]# sudo mkdir -pv $LFS/{etc,var} $LFS/usr/{bin,lib,sbin}  
sudo mkdir -pv $LFS/tools  
mkdir: created directory '/mnt/lfs/etc'  
mkdir: created directory '/mnt/lfs/var'  
mkdir: created directory '/mnt/lfs/usr'  
mkdir: created directory '/mnt/lfs/usr/bin'  
mkdir: created directory '/mnt/lfs/usr/lib'  
mkdir: created directory '/mnt/lfs/usr/sbin'  
mkdir: created directory '/mnt/lfs/tools'  
[artix ~]# sudo ln -sv usr/bin $LFS/bin  
sudo ln -sv usr/lib $LFS/lib  
sudo ln -sv usr/sbin $LFS/sbin  
'/mnt/lfs/bin' -> 'usr/bin'  
'/mnt/lfs/lib' -> 'usr/lib'  
'/mnt/lfs/sbin' -> 'usr/sbin'  
[artix ~]# sudo chown -v lfs $LFS/{usr{,/*},var,etc,tools}  
changed ownership of '/mnt/lfs/usr' from root to lfs  
changed ownership of '/mnt/lfs/usr/bin' from root to lfs  
changed ownership of '/mnt/lfs/usr/lib' from root to lfs  
changed ownership of '/mnt/lfs/usr/sbin' from root to lfs  
changed ownership of '/mnt/lfs/var' from root to lfs  
changed ownership of '/mnt/lfs/etc' from root to lfs  
changed ownership of '/mnt/lfs/tools' from root to lfs  
[artix ~]# sudo chown -v lfs $LFS/{usr{,/*},var,etc,tools}  
ownership of '/mnt/lfs/usr' retained as lfs  
ownership of '/mnt/lfs/usr/bin' retained as lfs  
ownership of '/mnt/lfs/usr/lib' retained as lfs  
ownership of '/mnt/lfs/usr/sbin' retained as lfs  
ownership of '/mnt/lfs/var' retained as lfs  
ownership of '/mnt/lfs/etc' retained as lfs  
ownership of '/mnt/lfs/tools' retained as lfs  
[artix ~]# sudo chown -v lfs:lfs $LFS/{usr{,/*},var,etc,tools}  
changed ownership of '/mnt/lfs/usr' from lfs:root to lfs:lfs  
changed ownership of '/mnt/lfs/usr/bin' from lfs:root to lfs:lfs  
changed ownership of '/mnt/lfs/usr/lib' from lfs:root to lfs:lfs  
changed ownership of '/mnt/lfs/usr/sbin' from lfs:root to lfs:lfs  
changed ownership of '/mnt/lfs/var' from lfs:root to lfs:lfs  
changed ownership of '/mnt/lfs/etc' from lfs:root to lfs:lfs  
changed ownership of '/mnt/lfs/tools' from lfs:root to lfs:lfs  
[artix ~]# grep data /etc/fstab  
grep lfs /etc/fstab  
UUID=a030d025-2563-4862-8263-068b34fa6a25 /data ext4 defaults 0 2  
[artix ~]#
[artix ~]# grep data /etc/fstab  
grep lfs /etc/fstab  
UUID=a030d025-2563-4862-8263-068b34fa6a25 /data ext4 defaults 0 2  
[artix ~]# sudo nano /etc/fstab  
[artix ~]# sudo nano /etc/fstab  
[artix ~]# sudo mount -a  
findmnt /mnt/lfs  
TARGET   SOURCE    FSTYPE OPTIONS  
/mnt/lfs /dev/sda3 ext4   rw,relatime  
[artix ~]# su - lfs  
[lfs@artix ~]$ echo $LFS  
  
[lfs@artix ~]$ su - lfs  
echo $HOME  
echo $USER  
Password:    
[lfs@artix ~]$
[lfs@artix ~]$ echo $LFS  
  
[lfs@artix ~]$ su - lfs  
echo $HOME  
echo $USER  
Password:    
[lfs@artix ~]$ whoami  
pwd  
echo $HOME  
echo $USER  
lfs  
/home/lfs  
/home/lfs  
lfs  
[lfs@artix ~]$ cat > ~/.bash_profile << "EOF"  
exec env -i HOME=$HOME TERM=$TERM PS1='\u:\w\$ ' /bin/bash  
EOF  
[lfs@artix ~]$ cat > ~/.bashrc << "EOF"  
set +h  
umask 022  
LFS=/mnt/lfs  
LC_ALL=POSIX  
LFS_TGT=$(uname -m)-lfs-linux-gnu  
PATH=/usr/bin  
if [ ! -L /bin ]; then PATH=/bin:$PATH; fi  
PATH=$LFS/tools/bin:$PATH  
CONFIG_SITE=$LFS/usr/share/config.site  
export LFS LC_ALL LFS_TGT PATH CONFIG_SITE  
export MAKEFLAGS=-j8  
EOF  
[lfs@artix ~]$ source ~/.bash_profile  
[lfs@artix ~]$ echo $LFS  
echo $LFS_TGT  
echo $PATH  
/mnt/lfs  
x86_64-lfs-linux-gnu  
/mnt/lfs/tools/bin:/usr/bin  
[lfs@artix ~]$
[lfs@artix ~]$ source ~/.bash_profile  
[lfs@artix ~]$ echo $LFS  
echo $LFS_TGT  
echo $PATH  
/mnt/lfs  
x86_64-lfs-linux-gnu  
/mnt/lfs/tools/bin:/usr/bin  
[lfs@artix ~]$ cd $LFS/sources  
[lfs@artix sources]$ wget https://www.linuxfromscratch.org/lfs/view/12.4/wget-list-sysv  
bash: wget: command not found  
[lfs@artix sources]$ which wget  
ls -l /usr/bin/wget  
which: no wget in (/mnt/lfs/tools/bin:/usr/bin)  
ls: cannot access '/usr/bin/wget': No such file or directory  
[lfs@artix sources]$
[artix ~]# pacman -Qs wget  
which wget  
which: no wget in (/usr/local/sbin:/usr/local/bin:/usr/bin:/var/lib/flatpak/exports/bin:/usr/bin/site_perl:/usr/bin/  
vendor_perl:/usr/bin/core_perl)  
[artix ~]# sudo pacman -S wget  
resolving dependencies...  
looking for conflicting packages...  
  
Packages (1) wget-1.25.0-5  
  
Total Download Size:   0.69 MiB  
Total Installed Size:  5.70 MiB  
  
:: Proceed with installation? [Y/n] y  
:: Retrieving packages...  
wget-1.25.0-5-x86_64                     705.0 KiB   340 KiB/s 00:02 [#######################################] 100%  
(1/1) checking keys in keyring                                        [#######################################] 100%  
(1/1) checking package integrity                                      [#######################################] 100%  
(1/1) loading package files                                           [#######################################] 100%  
(1/1) checking for file conflicts                                     [#######################################] 100%  
(1/1) checking available disk space                                   [#######################################] 100%  
:: Processing package changes...  
(1/1) installing wget                                                 [#######################################] 100%  
Optional dependencies for wget  
   ca-certificates: HTTPS downloads [installed]  
:: Running post-transaction hooks...  
(1/1) Updating the info directory file...  
[artix ~]# su - lfs      
source ~/.bash_profile  
[lfs@artix ~]$ which wget  
/usr/bin/wget  
[lfs@artix ~]$ which wget  
which curl  
/usr/bin/wget  
/usr/bin/curl  
[lfs@artix ~]$
[Zsupsz@artix ~]$ md5sum -c md5sums  
md5sum: md5sums: No such file or directory  
[Zsupsz@artix ~]$ wget https://www.linuxfromscratch.org/lfs/view/12.4/md5sums  
--2026-06-19 07:23:43--  https://www.linuxfromscratch.org/lfs/view/12.4/md5sums  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving www.linuxfromscratch.org (www.linuxfromscratch.org)... 208.118.68.85  
Connecting to www.linuxfromscratch.org (www.linuxfromscratch.org)|208.118.68.85|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 5179 (5.1K)  
Saving to: 'md5sums'  
  
md5sums                      100%[==============================================>]   5.06K  --.-KB/s    in 0s         
  
2026-06-19 07:23:45 (59.0 MB/s) - 'md5sums' saved [5179/5179]  
  
[Zsupsz@artix ~]$ wget --input-file=wget-list-sysv --continue --directory-prefix=$LFS/sources  
wget-list-sysv: No such file or directory  
No URLs found in wget-list-sysv.  
[Zsupsz@artix ~]$ wget https://www.linuxfromscratch.org/lfs/view/12.4/wget-list-sysv  
--2026-06-19 07:24:39--  https://www.linuxfromscratch.org/lfs/view/12.4/wget-list-sysv  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving www.linuxfromscratch.org (www.linuxfromscratch.org)... 208.118.68.85  
Connecting to www.linuxfromscratch.org (www.linuxfromscratch.org)|208.118.68.85|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 6107 (6.0K)  
Saving to: 'wget-list-sysv'  
  
wget-list-sysv               100%[==============================================>]   5.96K  --.-KB/s    in 0s         
  
2026-06-19 07:24:42 (101 MB/s) - 'wget-list-sysv' saved [6107/6107]  
  
[Zsupsz@artix ~]$ wget https://www.linuxfromscratch.org/lfs/view/12.4/wget-list-sysv  
--2026-06-19 07:24:50--  https://www.linuxfromscratch.org/lfs/view/12.4/wget-list-sysv  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving www.linuxfromscratch.org (www.linuxfromscratch.org)... 208.118.68.85  
Connecting to www.linuxfromscratch.org (www.linuxfromscratch.org)|208.118.68.85|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 6107 (6.0K)  
Saving to: 'wget-list-sysv.1'  
  
wget-list-sysv.1             100%[==============================================>]   5.96K  --.-KB/s    in 0s         
  
2026-06-19 07:24:52 (80.0 MB/s) - 'wget-list-sysv.1' saved [6107/6107]  
  
[Zsupsz@artix ~]$ wget --input-file=wget-list-sysv --continue --directory-prefix=$LFS/sources  
--2026-06-19 07:25:46--  https://download.savannah.gnu.org/releases/acl/acl-2.3.2.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving download.savannah.gnu.org (download.savannah.gnu.org)... 2001:470:142:5::200, 209.51.188.200  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|2001:470:142:5::200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://fosszone.csd.auth.gr/nongnu/acl/acl-2.3.2.tar.xz [following]  
--2026-06-19 07:25:47--  https://fosszone.csd.auth.gr/nongnu/acl/acl-2.3.2.tar.xz  
Resolving fosszone.csd.auth.gr (fosszone.csd.auth.gr)... 155.207.200.222  
Connecting to fosszone.csd.auth.gr (fosszone.csd.auth.gr)|155.207.200.222|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 371680 (363K) [application/x-xz]  
/sources: Permission denied  
/sources/acl-2.3.2.tar.xz: No such file or directory  
  
Cannot write to '/sources/acl-2.3.2.tar.xz' (No such file or directory).  
--2026-06-19 07:25:48--  https://download.savannah.gnu.org/releases/attr/attr-2.5.2.tar.gz  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|2001:470:142:5::200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirror.accum.se/mirror/gnu.org/savannah/attr/attr-2.5.2.tar.gz [following]  
--2026-06-19 07:25:49--  https://mirror.accum.se/mirror/gnu.org/savannah/attr/attr-2.5.2.tar.gz  
Resolving mirror.accum.se (mirror.accum.se)... 2001:6b0:19::165, 2001:6b0:19::163, 2001:6b0:19::173, ...  
Connecting to mirror.accum.se (mirror.accum.se)|2001:6b0:19::165|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 492539 (481K) [application/x-gzip]  
/sources: Permission denied  
/sources/attr-2.5.2.tar.gz: No such file or directory  
  
Cannot write to '/sources/attr-2.5.2.tar.gz' (No such file or directory).  
--2026-06-19 07:25:49--  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Resolving ftp.gnu.org (ftp.gnu.org)... 2001:470:142:3::b, 209.51.188.20  
Connecting to ftp.gnu.org (ftp.gnu.org)|2001:470:142:3::b|:443... failed: Connection timed out.  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... failed: Connection timed out.  
Retrying.  
  
--2026-06-19 07:30:20--  (try: 2)  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|2001:470:142:3::b|:443... failed: Connection timed out.  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443...
[lfs@artix sources]$ wget --input-file=wget-list-sysv --continue --directory-prefix=$LFS/sources  
--2026-06-19 07:19:33--  https://download.savannah.gnu.org/releases/acl/acl-2.3.2.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving download.savannah.gnu.org (download.savannah.gnu.org)... 2001:470:142:5::200, 209.51.188.200  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|2001:470:142:5::200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://nongnu.niranjan.co/acl/acl-2.3.2.tar.xz [following]  
--2026-06-19 07:19:43--  https://nongnu.niranjan.co/acl/acl-2.3.2.tar.xz  
Resolving nongnu.niranjan.co (nongnu.niranjan.co)... 2001:bc8:304d::1, 51.158.149.147  
Connecting to nongnu.niranjan.co (nongnu.niranjan.co)|2001:bc8:304d::1|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:19:43--  https://download.savannah.gnu.org/releases/attr/attr-2.5.2.tar.gz  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|2001:470:142:5::200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://ftp.cc.uoc.gr/mirrors/nongnu.org/attr/attr-2.5.2.tar.gz [following]  
--2026-06-19 07:19:49--  https://ftp.cc.uoc.gr/mirrors/nongnu.org/attr/attr-2.5.2.tar.gz  
Resolving ftp.cc.uoc.gr (ftp.cc.uoc.gr)... 2001:648:2c00:6c08::2, 147.52.159.50  
Connecting to ftp.cc.uoc.gr (ftp.cc.uoc.gr)|2001:648:2c00:6c08::2|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:19:50--  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Resolving ftp.gnu.org (ftp.gnu.org)... 2001:470:142:3::b, 209.51.188.20  
Connecting to ftp.gnu.org (ftp.gnu.org)|2001:470:142:3::b|:443... failed: Connection timed out.  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:04--  https://ftp.gnu.org/gnu/automake/automake-1.18.1.tar.xz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:04--  https://ftp.gnu.org/gnu/bash/bash-5.3.tar.gz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:05--  https://github.com/gavinhoward/bc/releases/download/7.0.3/bc-7.0.3.tar.xz  
Resolving github.com (github.com)... 140.82.121.3  
Connecting to github.com (github.com)|140.82.121.3|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/146616613/381a6f4b-d33c-4bf2-  
ace0-cdad4b590d2b?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A16%3A18Z&rscd=attachment%3B+filename%3Dbc-7.0  
.3.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-9  
515b896b4de&skt=2026-06-19T05%3A16%3A07Z&ske=2026-06-19T06%3A16%3A18Z&sks=b&skv=2018-11-09&sig=UwHQ7d99N%2FvXpaDegvg  
MXx4UWVZUP4CQhrBLM3Uur9s%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZS1  
hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0NjgyOSwibmJmIjoxNzgxODQ2NTI5LCJwYXRoIjoicmV  
sZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.Ns1eWcUeLGaZKs-A3W3ooeqLX_NU7zPLKZ4l6vAEd50&response-con  
tent-disposition=attachment%3B%20filename%3Dbc-7.0.3.tar.xz&response-content-type=application%2Foctet-stream [follow  
ing]  
--2026-06-19 07:22:05--  https://release-assets.githubusercontent.com/github-production-release-asset/146616613/381a  
6f4b-d33c-4bf2-ace0-cdad4b590d2b?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A16%3A18Z&rscd=attachment%3B+fi  
lename%3Dbc-7.0.3.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-9  
97b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A16%3A07Z&ske=2026-06-19T06%3A16%3A18Z&sks=b&skv=2018-11-09&sig=UwHQ7d  
99N%2FvXpaDegvgMXx4UWVZUP4CQhrBLM3Uur9s%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVk  
IjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0NjgyOSwibmJmIjoxNzgxODQ2NTI5  
LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.Ns1eWcUeLGaZKs-A3W3ooeqLX_NU7zPLKZ4l6vAEd  
50&response-content-disposition=attachment%3B%20filename%3Dbc-7.0.3.tar.xz&response-content-type=application%2Foctet  
-stream  
Resolving release-assets.githubusercontent.com (release-assets.githubusercontent.com)... 185.199.109.133, 185.199.10  
8.133, 185.199.110.133, ...  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.109.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 416 Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:05--  https://sourceware.org/pub/binutils/releases/binutils-2.45.tar.xz  
Resolving sourceware.org (sourceware.org)... 2620:52:6:3111::32, 38.145.34.32  
Connecting to sourceware.org (sourceware.org)|2620:52:6:3111::32|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:06--  https://ftp.gnu.org/gnu/bison/bison-3.8.2.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:07--  https://www.sourceware.org/pub/bzip2/bzip2-1.0.8.tar.gz  
Resolving www.sourceware.org (www.sourceware.org)... 2620:52:6:3111::32, 38.145.34.32  
Connecting to www.sourceware.org (www.sourceware.org)|2620:52:6:3111::32|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:09--  https://ftp.gnu.org/gnu/coreutils/coreutils-9.7.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:10--  https://ftp.gnu.org/gnu/dejagnu/dejagnu-1.6.3.tar.gz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:10--  https://ftp.gnu.org/gnu/diffutils/diffutils-3.12.tar.xz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:11--  https://downloads.sourceforge.net/project/e2fsprogs/e2fsprogs/v1.47.3/e2fsprogs-1.47.3.tar.  
gz  
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 2606:4700::6812:c95, 2606:4700::6812:d95, 104.18.  
13.149, ...  
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|2606:4700::6812:c95|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://sf-eu-introserv-1.dl.sourceforge.net/project/e2fsprogs/e2fsprogs/v1.47.3/e2fsprogs-1.47.3.tar.gz?v  
iasf=1&fid=8e0f2d4a72e3c880 [following]  
--2026-06-19 07:22:11--  https://sf-eu-introserv-1.dl.sourceforge.net/project/e2fsprogs/e2fsprogs/v1.47.3/e2fsprogs-  
1.47.3.tar.gz?viasf=1&fid=8e0f2d4a72e3c880  
Resolving sf-eu-introserv-1.dl.sourceforge.net (sf-eu-introserv-1.dl.sourceforge.net)... 141.95.66.71  
Connecting to sf-eu-introserv-1.dl.sourceforge.net (sf-eu-introserv-1.dl.sourceforge.net)|141.95.66.71|:443... conne  
cted.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:12--  https://sourceware.org/ftp/elfutils/0.193/elfutils-0.193.tar.bz2  
Connecting to sourceware.org (sourceware.org)|2620:52:6:3111::32|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:13--  https://github.com/libexpat/libexpat/releases/download/R_2_7_1/expat-2.7.1.tar.xz  
Connecting to github.com (github.com)|140.82.121.3|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/80314213/4d96344b-919f-488a-8  
b1f-31a18456a4ff?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A16%3A02Z&rscd=attachment%3B+filename%3Dexpat-2  
.7.1.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b  
-9515b896b4de&skt=2026-06-19T05%3A15%3A38Z&ske=2026-06-19T06%3A16%3A02Z&sks=b&skv=2018-11-09&sig=6rRdh26Ryx%2BlV%2BD  
fJskS4jgoV3pd4A9Ki%2BFkDcPmuTA%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZ  
WFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0NjgzNywibmJmIjoxNzgxODQ2NTM3LCJwYXRoI  
joicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.UKpot2AgOpKsv9Kg0-TTonjbPIUbvkJeEpAhARvfDSg&respon  
se-content-disposition=attachment%3B%20filename%3Dexpat-2.7.1.tar.xz&response-content-type=application%2Foctet-strea  
m [following]  
--2026-06-19 07:22:13--  https://release-assets.githubusercontent.com/github-production-release-asset/80314213/4d963  
44b-919f-488a-8b1f-31a18456a4ff?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A16%3A02Z&rscd=attachment%3B+fil  
ename%3Dexpat-2.7.1.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654  
-997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A15%3A38Z&ske=2026-06-19T06%3A16%3A02Z&sks=b&skv=2018-11-09&sig=6rRd  
h26Ryx%2BlV%2BDfJskS4jgoV3pd4A9Ki%2BFkDcPmuTA%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIi  
wiYXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0NjgzNywibmJmIjoxNzgxOD  
Q2NTM3LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.UKpot2AgOpKsv9Kg0-TTonjbPIUbvkJeEpA  
hARvfDSg&response-content-disposition=attachment%3B%20filename%3Dexpat-2.7.1.tar.xz&response-content-type=applicatio  
n%2Foctet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.109.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 416 Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:14--  https://prdownloads.sourceforge.net/expect/expect5.45.4.tar.gz  
Resolving prdownloads.sourceforge.net (prdownloads.sourceforge.net)... 2606:4700::6812:c95, 2606:4700::6812:d95, 104  
.18.12.149, ...  
Connecting to prdownloads.sourceforge.net (prdownloads.sourceforge.net)|2606:4700::6812:c95|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://downloads.sourceforge.net/project/expect/Expect/5.45.4/expect5.45.4.tar.gz [following]  
--2026-06-19 07:22:14--  https://downloads.sourceforge.net/project/expect/Expect/5.45.4/expect5.45.4.tar.gz  
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|2606:4700::6812:c95|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://unlimited.dl.sourceforge.net/project/expect/Expect/5.45.4/expect5.45.4.tar.gz?viasf=1&fid=dc54e74a  
7cc4cf5f [following]  
--2026-06-19 07:22:15--  https://unlimited.dl.sourceforge.net/project/expect/Expect/5.45.4/expect5.45.4.tar.gz?viasf  
=1&fid=dc54e74a7cc4cf5f  
Resolving unlimited.dl.sourceforge.net (unlimited.dl.sourceforge.net)... 185.119.90.247  
Connecting to unlimited.dl.sourceforge.net (unlimited.dl.sourceforge.net)|185.119.90.247|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:15--  https://astron.com/pub/file/file-5.46.tar.gz  
Resolving astron.com (astron.com)... 2620:106:3003:1f00:9e8e:99ff:fe15:cae4, 38.117.134.17  
Connecting to astron.com (astron.com)|2620:106:3003:1f00:9e8e:99ff:fe15:cae4|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:17--  https://ftp.gnu.org/gnu/findutils/findutils-4.10.0.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:18--  https://github.com/westes/flex/releases/download/v2.6.4/flex-2.6.4.tar.gz  
Connecting to github.com (github.com)|140.82.121.3|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/14521001/23794388-327c-11e7-8  
219-c41432b94acf?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A07%3A37Z&rscd=attachment%3B+filename%3Dflex-2.  
6.4.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-  
9515b896b4de&skt=2026-06-19T05%3A06%3A58Z&ske=2026-06-19T06%3A07%3A37Z&sks=b&skv=2018-11-09&sig=ZAwm8ycth5%2BsMrsfmf  
uVdKGZsqBsFkHyNIu4d8ju%2B8Q%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFz  
ZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0Njg0MiwibmJmIjoxNzgxODQ2NTQyLCJwYXRoIjoi  
cmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.5BLYR0f-zdTjqYZj7RsIqg8umaX2W8xoFRTA99nTUvI&response-  
content-disposition=attachment%3B%20filename%3Dflex-2.6.4.tar.gz&response-content-type=application%2Foctet-stream [f  
ollowing]  
--2026-06-19 07:22:18--  https://release-assets.githubusercontent.com/github-production-release-asset/14521001/23794  
388-327c-11e7-8219-c41432b94acf?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A07%3A37Z&rscd=attachment%3B+fil  
ename%3Dflex-2.6.4.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-  
997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A06%3A58Z&ske=2026-06-19T06%3A07%3A37Z&sks=b&skv=2018-11-09&sig=ZAwm8  
ycth5%2BsMrsfmfuVdKGZsqBsFkHyNIu4d8ju%2B8Q%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiY  
XVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0Njg0MiwibmJmIjoxNzgxODQ2N  
TQyLCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.5BLYR0f-zdTjqYZj7RsIqg8umaX2W8xoFRTA99  
nTUvI&response-content-disposition=attachment%3B%20filename%3Dflex-2.6.4.tar.gz&response-content-type=application%2F  
octet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.109.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 416 Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:19--  https://pypi.org/packages/source/f/flit-core/flit_core-3.12.0.tar.gz  
Resolving pypi.org (pypi.org)... 2a04:4e42::223, 2a04:4e42:200::223, 2a04:4e42:600::223, ...  
Connecting to pypi.org (pypi.org)|2a04:4e42::223|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://files.pythonhosted.org/packages/source/f/flit-core/flit_core-3.12.0.tar.gz [following]  
--2026-06-19 07:22:19--  https://files.pythonhosted.org/packages/source/f/flit-core/flit_core-3.12.0.tar.gz  
Resolving files.pythonhosted.org (files.pythonhosted.org)... 2a04:4e42:600::223, 2a04:4e42::223, 2a04:4e42:200::223,  
...  
Connecting to files.pythonhosted.org (files.pythonhosted.org)|2a04:4e42:600::223|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://files.pythonhosted.org/packages/69/59/b6fc2188dfc7ea4f936cd12b49d707f66a1cb7a1d2c16172963534db741b  
/flit_core-3.12.0.tar.gz [following]  
--2026-06-19 07:22:19--  https://files.pythonhosted.org/packages/69/59/b6fc2188dfc7ea4f936cd12b49d707f66a1cb7a1d2c16  
172963534db741b/flit_core-3.12.0.tar.gz  
Reusing existing connection to [files.pythonhosted.org]:443.  
HTTP request sent, awaiting response... 416 Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:22:19--  https://ftp.gnu.org/gnu/gawk/gawk-5.3.2.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... connected.  
HTTP request sent, awaiting response... 206 Partial Content  
Length: 3749260 (3.6M), 2093821 (2.0M) remaining [application/x-xz]  
Saving to: '/mnt/lfs/sources/gawk-5.3.2.tar.xz'  
  
gawk-5.3.2.tar.xz            100%[++++++++++++++++++++==========================>]   3.58M  1.99MB/s    in 1.0s       
  
2026-06-19 07:22:21 (1.99 MB/s) - '/mnt/lfs/sources/gawk-5.3.2.tar.xz' saved [3749260/3749260]  
  
--2026-06-19 07:22:21--  https://ftp.gnu.org/gnu/gcc/gcc-15.2.0/gcc-15.2.0.tar.xz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 101056276 (96M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/gcc-15.2.0.tar.xz'  
  
gcc-15.2.0.tar.xz            100%[==============================================>]  96.37M  7.83MB/s    in 14s        
  
2026-06-19 07:22:35 (6.95 MB/s) - '/mnt/lfs/sources/gcc-15.2.0.tar.xz' saved [101056276/101056276]  
  
--2026-06-19 07:22:35--  https://ftp.gnu.org/gnu/gdbm/gdbm-1.26.tar.gz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 1226591 (1.2M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/gdbm-1.26.tar.gz'  
  
gdbm-1.26.tar.gz             100%[==============================================>]   1.17M  7.77MB/s    in 0.2s       
  
2026-06-19 07:22:35 (7.77 MB/s) - '/mnt/lfs/sources/gdbm-1.26.tar.gz' saved [1226591/1226591]  
  
--2026-06-19 07:22:35--  https://ftp.gnu.org/gnu/gettext/gettext-0.26.tar.xz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 10061740 (9.6M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/gettext-0.26.tar.xz'  
  
gettext-0.26.tar.xz          100%[==============================================>]   9.59M  6.47MB/s    in 1.5s       
  
2026-06-19 07:22:37 (6.47 MB/s) - '/mnt/lfs/sources/gettext-0.26.tar.xz' saved [10061740/10061740]  
  
--2026-06-19 07:22:37--  https://ftp.gnu.org/gnu/glibc/glibc-2.42.tar.xz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 19930508 (19M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/glibc-2.42.tar.xz'  
  
glibc-2.42.tar.xz            100%[==============================================>]  19.01M  8.51MB/s    in 2.2s       
  
2026-06-19 07:22:39 (8.51 MB/s) - '/mnt/lfs/sources/glibc-2.42.tar.xz' saved [19930508/19930508]  
  
--2026-06-19 07:22:39--  https://ftp.gnu.org/gnu/gmp/gmp-6.3.0.tar.xz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 2094196 (2.0M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/gmp-6.3.0.tar.xz'  
  
gmp-6.3.0.tar.xz             100%[==============================================>]   2.00M  8.95MB/s    in 0.2s       
  
2026-06-19 07:22:40 (8.95 MB/s) - '/mnt/lfs/sources/gmp-6.3.0.tar.xz' saved [2094196/2094196]  
  
--2026-06-19 07:22:40--  https://ftp.gnu.org/gnu/gperf/gperf-3.3.tar.gz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 1831294 (1.7M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/gperf-3.3.tar.gz'  
  
gperf-3.3.tar.gz             100%[==============================================>]   1.75M  8.29MB/s    in 0.2s       
  
2026-06-19 07:22:40 (8.29 MB/s) - '/mnt/lfs/sources/gperf-3.3.tar.gz' saved [1831294/1831294]  
  
--2026-06-19 07:22:40--  https://ftp.gnu.org/gnu/grep/grep-3.12.tar.xz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 1918448 (1.8M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/grep-3.12.tar.xz'  
  
grep-3.12.tar.xz             100%[==============================================>]   1.83M  8.46MB/s    in 0.2s       
  
2026-06-19 07:22:40 (8.46 MB/s) - '/mnt/lfs/sources/grep-3.12.tar.xz' saved [1918448/1918448]  
  
--2026-06-19 07:22:40--  https://ftp.gnu.org/gnu/groff/groff-1.23.0.tar.gz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 7433031 (7.1M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/groff-1.23.0.tar.gz'  
  
groff-1.23.0.tar.gz          100%[==============================================>]   7.09M  7.78MB/s    in 0.9s       
  
2026-06-19 07:22:41 (7.78 MB/s) - '/mnt/lfs/sources/groff-1.23.0.tar.gz' saved [7433031/7433031]  
  
--2026-06-19 07:22:41--  https://ftp.gnu.org/gnu/grub/grub-2.12.tar.xz  
Reusing existing connection to ftp.gnu.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 6675608 (6.4M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/grub-2.12.tar.xz'  
  
grub-2.12.tar.xz              87%[========================================>      ]   5.60M  --.-KB/s    eta 70s    ^  
C  
[lfs@artix sources]$ wget --input-file=wget-list-sysv --continue --directory-prefix=$LFS/sources  
--2026-06-19 07:31:17--  https://download.savannah.gnu.org/releases/acl/acl-2.3.2.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving download.savannah.gnu.org (download.savannah.gnu.org)... 2001:470:142:5::200, 209.51.188.200  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|2001:470:142:5::200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://ftp.cc.uoc.gr/mirrors/nongnu.org/acl/acl-2.3.2.tar.xz [following]  
--2026-06-19 07:31:18--  https://ftp.cc.uoc.gr/mirrors/nongnu.org/acl/acl-2.3.2.tar.xz  
Resolving ftp.cc.uoc.gr (ftp.cc.uoc.gr)... 2001:648:2c00:6c08::2, 147.52.159.50  
Connecting to ftp.cc.uoc.gr (ftp.cc.uoc.gr)|2001:648:2c00:6c08::2|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:31:18--  https://download.savannah.gnu.org/releases/attr/attr-2.5.2.tar.gz  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|2001:470:142:5::200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirror.rabisu.com/mirrors/savannah/attr/attr-2.5.2.tar.gz [following]  
--2026-06-19 07:31:19--  https://mirror.rabisu.com/mirrors/savannah/attr/attr-2.5.2.tar.gz  
Resolving mirror.rabisu.com (mirror.rabisu.com)... 162.55.247.53  
Connecting to mirror.rabisu.com (mirror.rabisu.com)|162.55.247.53|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:31:20--  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Resolving ftp.gnu.org (ftp.gnu.org)... 2001:470:142:3::b, 209.51.188.20  
Connecting to ftp.gnu.org (ftp.gnu.org)|2001:470:142:3::b|:443...
[Zsupsz@artix ~]$ su - lfs  
source ~/.bash_profile  
Password:    
[lfs@artix ~]$ whoami  
echo "$LFS"  
lfs  
/mnt/lfs  
[lfs@artix ~]$ cd $LFS/sources  
pwd  
/mnt/lfs/sources  
[lfs@artix sources]$ wget --input-file=$HOME/wget-list-sysv \  
    --continue \  
    --directory-prefix=$LFS/sources  
/home/lfs/wget-list-sysv: No such file or directory  
No URLs found in /home/lfs/wget-list-sysv.  
[lfs@artix sources]$ wget --input-file=wget-list-sysv \  
    --continue \  
    --directory-prefix=$LFS/sources  
--2026-06-19 07:35:59--  https://download.savannah.gnu.org/releases/acl/acl-2.3.2.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving download.savannah.gnu.org (download.savannah.gnu.org)... 2001:470:142:5::200, 209.51.188.200  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|2001:470:142:5::200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://nongnu.niranjan.co/acl/acl-2.3.2.tar.xz [following]  
--2026-06-19 07:36:00--  https://nongnu.niranjan.co/acl/acl-2.3.2.tar.xz  
Resolving nongnu.niranjan.co (nongnu.niranjan.co)... 2001:bc8:304d::1, 51.158.149.147  
Connecting to nongnu.niranjan.co (nongnu.niranjan.co)|2001:bc8:304d::1|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:36:01--  https://download.savannah.gnu.org/releases/attr/attr-2.5.2.tar.gz  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|2001:470:142:5::200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://fosszone.csd.auth.gr/nongnu/attr/attr-2.5.2.tar.gz [following]  
--2026-06-19 07:36:02--  https://fosszone.csd.auth.gr/nongnu/attr/attr-2.5.2.tar.gz  
Resolving fosszone.csd.auth.gr (fosszone.csd.auth.gr)... 155.207.200.222  
Connecting to fosszone.csd.auth.gr (fosszone.csd.auth.gr)|155.207.200.222|:443... connected.  
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable  
  
   The file is already fully retrieved; nothing to do.  
  
--2026-06-19 07:36:02--  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Resolving ftp.gnu.org (ftp.gnu.org)... 2001:470:142:3::b, 209.51.188.20  
Connecting to ftp.gnu.org (ftp.gnu.org)|2001:470:142:3::b|:443... ^C  
[lfs@artix sources]$ whoami  
echo "$LFS"  
pwd  
ls -ld /mnt/lfs/sources  
lfs  
/mnt/lfs  
/mnt/lfs/sources  
drwxrwxrwt 2 root root 4096 Jun 19 07:22 /mnt/lfs/sources  
[lfs@artix sources]$ ^C
[lfs@artix sources]$ ls -lh $LFS/sources | head  
ls $LFS/sources | wc -l  
total 229M  
-rw-r--r-- 1 lfs lfs 363K Jan 24  2024 acl-2.3.2.tar.xz  
-rw-r--r-- 1 lfs lfs 481K Jan 14  2024 attr-2.5.2.tar.gz  
-rw-r--r-- 1 lfs lfs 1.4M Dec 22  2023 autoconf-2.72.tar.xz  
-rw-r--r-- 1 lfs lfs 1.6M Jun 26  2025 automake-1.18.1.tar.xz  
-rw-r--r-- 1 lfs lfs  11M Jul 30  2025 bash-5.3.tar.gz  
-rw-r--r-- 1 lfs lfs 464K Sep 24  2024 bc-7.0.3.tar.xz  
-rw-r--r-- 1 lfs lfs  27M Jul 27  2025 binutils-2.45.tar.xz  
-rw-r--r-- 1 lfs lfs 2.7M Sep 25  2021 bison-3.8.2.tar.xz  
-rw-r--r-- 1 lfs lfs 792K Jul 13  2019 bzip2-1.0.8.tar.gz  
31  
[lfs@artix sources]$ wget -4 https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
--2026-06-19 07:42:36--  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving ftp.gnu.org (ftp.gnu.org)... 209.51.188.20  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... failed: Connection timed out.  
Retrying.  
  
--2026-06-19 07:44:53--  (try: 2)  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... ^C  
[lfs@artix sources]$
31  
[lfs@artix sources]$ wget -4 https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
--2026-06-19 07:42:36--  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving ftp.gnu.org (ftp.gnu.org)... 209.51.188.20  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... failed: Connection timed out.  
Retrying.  
  
--2026-06-19 07:44:53--  (try: 2)  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... ^C  
[lfs@artix sources]$ curl -4 -I https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
curl: (28) Failed to connect to ftp.gnu.org port 443 after 135485 ms: Could not connect to server  
[lfs@artix sources]$
[lfs@artix sources]$ wget -4 https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
--2026-06-19 07:42:36--  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving ftp.gnu.org (ftp.gnu.org)... 209.51.188.20  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... failed: Connection timed out.  
Retrying.  
  
--2026-06-19 07:44:53--  (try: 2)  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... ^C  
[lfs@artix sources]$ curl -4 -I https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
curl: (28) Failed to connect to ftp.gnu.org port 443 after 135485 ms: Could not connect to server  
[lfs@artix sources]$ ls $LFS/sources | wc -l  
du -sh $LFS/sources  
31  
229M    /mnt/lfs/sources  
[lfs@artix sources]$ wget -4 https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
--2026-06-19 07:48:59--  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving ftp.gnu.org (ftp.gnu.org)... 209.51.188.20  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... failed: Connection timed out.  
Retrying.  
  
--2026-06-19 07:51:13--  (try: 2)  https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:443... ^C  
[lfs@artix sources]$
[lfs@artix sources]$ curl -4 -I https://www.google.com                                    
curl -4 -I https://www.kernel.org  
curl -4 -I https://mirrors.kernel.org  
HTTP/2 200    
content-type: text/html; charset=ISO-8859-1  
content-security-policy-report-only: object-src 'none';base-uri 'self';script-src 'nonce-oTziXAW0qKcnA8EL7xzweg' 'st  
rict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/g  
ws/other-hp  
accept-ch: Sec-CH-Prefers-Color-Scheme  
p3p: CP="This is not a P3P policy! See g.co/p3phelp for more info."  
date: Fri, 19 Jun 2026 05:53:39 GMT  
server: gws  
x-xss-protection: 0  
x-frame-options: SAMEORIGIN  
expires: Fri, 19 Jun 2026 05:53:39 GMT  
cache-control: private  
set-cookie: AEC=AaJma5uhXtigcIj1dnxQTeTs-pihpF8kGgg-fhTg8tt7BP0EefVX_CbDjXY; expires=Wed, 16-Dec-2026 05:53:39 GMT;  
path=/; domain=.google.com; Secure; HttpOnly; SameSite=lax  
set-cookie: __Secure-ENID=34.SE=ckS2zrEDU-MyTYERog6udQ632E7h8tfRan1Mee_yW_Co3wjWVAPWhtaD3OjnrxW_MOnGR4Y4krn2tG9KDl6V  
ZpHYqyzcz7g4LL9rRjmFt23H4hDHDxPb78zl9xs5jWmhXv4am1guuJHDBCrPrqbBPMUR-OfBfrV0zmb4FcezAMJji7lRiRUBekrZgk3aeXI5g2d6c95a  
0bxd9YRmxn54gx164foZFZN7HaftsM94atEf3CS2I093_CJL; expires=Mon, 19-Jul-2027 22:11:57 GMT; path=/; domain=.google.com;  
Secure; HttpOnly; SameSite=lax  
set-cookie: __Secure-BUCKET=CJEB; expires=Wed, 16-Dec-2026 05:53:39 GMT; path=/; domain=.google.com; Secure; HttpOnl  
y  
alt-svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000  
  
HTTP/2 200    
server: nginx  
content-type: text/html; charset=utf-8  
last-modified: Thu, 18 Jun 2026 14:07:00 GMT  
x-frame-options: DENY  
x-content-type-options: nosniff  
referrer-policy: same-origin  
content-security-policy: default-src 'self' *.kernel.org; img-src https: data:  
accept-ranges: bytes  
date: Fri, 19 Jun 2026 05:53:39 GMT  
via: 1.1 varnish  
age: 130  
x-served-by: cache-muc13978-MUC  
x-cache: HIT  
x-cache-hits: 2  
x-timer: S1781848420.517739,VS0,VE0  
vary: Accept-Encoding  
strict-transport-security: max-age=31557600  
alt-svc: h3=":443";ma=86400,h3-29=":443";ma=86400,h3-27=":443";ma=86400  
content-length: 16927  
  
HTTP/2 200    
server: nginx  
date: Fri, 19 Jun 2026 05:53:40 GMT  
content-type: text/html; charset=utf-8  
content-length: 8427  
last-modified: Tue, 02 Sep 2025 19:53:43 GMT  
vary: Accept-Encoding  
x-frame-options: DENY  
x-content-type-options: nosniff  
x-xss-protection: 1; mode=block  
strict-transport-security: max-age=15768001  
accept-ranges: bytes  
  
[lfs@artix sources]$ curl -4 -I https://ftpmirror.gnu.org/autoconf/autoconf-2.72.tar.xz  
HTTP/1.1 302 Moved Temporarily  
Server: nginx  
Date: Fri, 19 Jun 2026 05:53:45 GMT  
Connection: keep-alive  
Location: https://mirror.kumi.systems/gnu/autoconf/autoconf-2.72.tar.xz  
X-Frame-Options: DENY  
X-Content-Type-Options: nosniff  
  
[lfs@artix sources]$ wget -4 https://ftpmirror.gnu.org/autoconf/autoconf-2.72.tar.xz  
--2026-06-19 07:53:46--  https://ftpmirror.gnu.org/autoconf/autoconf-2.72.tar.xz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving ftpmirror.gnu.org (ftpmirror.gnu.org)... 209.51.188.200  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirrors.nav.ro/gnu/autoconf/autoconf-2.72.tar.xz [following]  
--2026-06-19 07:53:47--  https://mirrors.nav.ro/gnu/autoconf/autoconf-2.72.tar.xz  
Resolving mirrors.nav.ro (mirrors.nav.ro)... 5.154.224.26  
Connecting to mirrors.nav.ro (mirrors.nav.ro)|5.154.224.26|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1389680 (1.3M) [application/x-xz]  
Saving to: 'autoconf-2.72.tar.xz.1'  
  
autoconf-2.72.tar.xz.1       100%[==============================================>]   1.33M  2.10MB/s    in 0.6s       
  
2026-06-19 07:53:48 (2.10 MB/s) - 'autoconf-2.72.tar.xz.1' saved [1389680/1389680]  
  
[lfs@artix sources]$ grep autoconf wget-list-sysv  
https://ftp.gnu.org/gnu/autoconf/autoconf-2.72.tar.xz  
[lfs@artix sources]$ ls $LFS/sources | head  
ls $LFS/sources | tail  
acl-2.3.2.tar.xz  
attr-2.5.2.tar.gz  
autoconf-2.72.tar.xz  
autoconf-2.72.tar.xz.1  
automake-1.18.1.tar.xz  
bash-5.3.tar.gz  
bc-7.0.3.tar.xz  
binutils-2.45.tar.xz  
bison-3.8.2.tar.xz  
bzip2-1.0.8.tar.gz  
gcc-15.2.0.tar.xz  
gdbm-1.26.tar.gz  
gettext-0.26.tar.xz  
glibc-2.42.tar.xz  
gmp-6.3.0.tar.xz  
gperf-3.3.tar.gz  
grep-3.12.tar.xz  
groff-1.23.0.tar.gz  
grub-2.12.tar.xz  
wget-list-sysv  
[lfs@artix sources]$
Length: 1764528 (1.7M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/inetutils-2.6.tar.xz'  
  
inetutils-2.6.tar.xz         100%[==============================================>]   1.68M  4.01MB/s    in 0.4s       
  
2026-06-19 07:56:15 (4.01 MB/s) - '/mnt/lfs/sources/inetutils-2.6.tar.xz' saved [1764528/1764528]  
  
--2026-06-19 07:56:15--  https://launchpad.net/intltool/trunk/0.51.0/+download/intltool-0.51.0.tar.gz  
Resolving launchpad.net (launchpad.net)... 185.125.189.222, 185.125.189.223  
Connecting to launchpad.net (launchpad.net)|185.125.189.222|:443... connected.  
HTTP request sent, awaiting response... 303 See Other  
Location: https://launchpadlibrarian.net/199705878/intltool-0.51.0.tar.gz [following]  
--2026-06-19 07:56:15--  https://launchpadlibrarian.net/199705878/intltool-0.51.0.tar.gz  
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 185.125.189.228, 185.125.189.229  
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|185.125.189.228|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 162286 (158K) [application/x-tar]  
Saving to: '/mnt/lfs/sources/intltool-0.51.0.tar.gz'  
  
intltool-0.51.0.tar.gz       100%[==============================================>] 158.48K   830KB/s    in 0.2s       
  
2026-06-19 07:56:16 (830 KB/s) - '/mnt/lfs/sources/intltool-0.51.0.tar.gz' saved [162286/162286]  
  
--2026-06-19 07:56:16--  https://www.kernel.org/pub/linux/utils/net/iproute2/iproute2-6.16.0.tar.xz  
Resolving www.kernel.org (www.kernel.org)... 146.75.117.55  
Connecting to www.kernel.org (www.kernel.org)|146.75.117.55|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 931124 (909K) [application/x-xz]  
Saving to: '/mnt/lfs/sources/iproute2-6.16.0.tar.xz'  
  
iproute2-6.16.0.tar.xz       100%[==============================================>] 909.30K  4.14MB/s    in 0.2s       
  
2026-06-19 07:56:16 (4.14 MB/s) - '/mnt/lfs/sources/iproute2-6.16.0.tar.xz' saved [931124/931124]  
  
--2026-06-19 07:56:16--  https://pypi.org/packages/source/J/Jinja2/jinja2-3.1.6.tar.gz  
Connecting to pypi.org (pypi.org)|151.101.64.223|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://files.pythonhosted.org/packages/source/J/Jinja2/jinja2-3.1.6.tar.gz [following]  
--2026-06-19 07:56:16--  https://files.pythonhosted.org/packages/source/J/Jinja2/jinja2-3.1.6.tar.gz  
Connecting to files.pythonhosted.org (files.pythonhosted.org)|151.101.192.223|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://files.pythonhosted.org/packages/df/bf/f7da0350254c0ed7c72f3e33cef02e048281fec7ecec5f032d4aac52226b  
/jinja2-3.1.6.tar.gz [following]  
--2026-06-19 07:56:17--  https://files.pythonhosted.org/packages/df/bf/f7da0350254c0ed7c72f3e33cef02e048281fec7ecec5  
f032d4aac52226b/jinja2-3.1.6.tar.gz  
Reusing existing connection to files.pythonhosted.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 245115 (239K) [binary/octet-stream]  
Saving to: '/mnt/lfs/sources/jinja2-3.1.6.tar.gz'  
  
jinja2-3.1.6.tar.gz          100%[==============================================>] 239.37K  --.-KB/s    in 0.07s      
  
2026-06-19 07:56:17 (3.14 MB/s) - '/mnt/lfs/sources/jinja2-3.1.6.tar.gz' saved [245115/245115]  
  
--2026-06-19 07:56:17--  https://www.kernel.org/pub/linux/utils/kbd/kbd-2.8.0.tar.xz  
Connecting to www.kernel.org (www.kernel.org)|146.75.117.55|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1482152 (1.4M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/kbd-2.8.0.tar.xz'  
  
kbd-2.8.0.tar.xz             100%[==============================================>]   1.41M  4.67MB/s    in 0.3s       
  
2026-06-19 07:56:17 (4.67 MB/s) - '/mnt/lfs/sources/kbd-2.8.0.tar.xz' saved [1482152/1482152]  
  
--2026-06-19 07:56:17--  https://www.kernel.org/pub/linux/utils/kernel/kmod/kmod-34.2.tar.xz  
Reusing existing connection to www.kernel.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 443748 (433K) [application/x-xz]  
Saving to: '/mnt/lfs/sources/kmod-34.2.tar.xz'  
  
kmod-34.2.tar.xz             100%[==============================================>] 433.35K  --.-KB/s    in 0.07s      
  
2026-06-19 07:56:17 (6.38 MB/s) - '/mnt/lfs/sources/kmod-34.2.tar.xz' saved [443748/443748]  
  
--2026-06-19 07:56:17--  https://www.greenwoodsoftware.com/less/less-679.tar.gz  
Resolving www.greenwoodsoftware.com (www.greenwoodsoftware.com)... 104.200.21.227  
Connecting to www.greenwoodsoftware.com (www.greenwoodsoftware.com)|104.200.21.227|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 877094 (857K) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/less-679.tar.gz'  
  
less-679.tar.gz              100%[==============================================>] 856.54K   985KB/s    in 0.9s       
  
2026-06-19 07:56:19 (985 KB/s) - '/mnt/lfs/sources/less-679.tar.gz' saved [877094/877094]  
  
--2026-06-19 07:56:19--  https://www.linuxfromscratch.org/lfs/downloads/12.4/lfs-bootscripts-20250827.tar.xz  
Resolving www.linuxfromscratch.org (www.linuxfromscratch.org)... 208.118.68.85  
Connecting to www.linuxfromscratch.org (www.linuxfromscratch.org)|208.118.68.85|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 34196 (33K) [application/x-xz]  
Saving to: '/mnt/lfs/sources/lfs-bootscripts-20250827.tar.xz'  
  
lfs-bootscripts-20250827.tar 100%[==============================================>]  33.39K   161KB/s    in 0.2s       
  
2026-06-19 07:56:21 (161 KB/s) - '/mnt/lfs/sources/lfs-bootscripts-20250827.tar.xz' saved [34196/34196]  
  
--2026-06-19 07:56:21--  https://www.kernel.org/pub/linux/libs/security/linux-privs/libcap2/libcap-2.76.tar.xz  
Connecting to www.kernel.org (www.kernel.org)|146.75.117.55|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 199200 (195K) [application/x-xz]  
Saving to: '/mnt/lfs/sources/libcap-2.76.tar.xz'  
  
libcap-2.76.tar.xz           100%[==============================================>] 194.53K  --.-KB/s    in 0.09s      
  
2026-06-19 07:56:21 (2.11 MB/s) - '/mnt/lfs/sources/libcap-2.76.tar.xz' saved [199200/199200]  
  
--2026-06-19 07:56:21--  https://github.com/libffi/libffi/releases/download/v3.5.2/libffi-3.5.2.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/321154/a7ac1470-95d7-4036-973  
5-36099626d83e?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A47%3A31Z&rscd=attachment%3B+filename%3Dlibffi-3.  
5.2.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-  
9515b896b4de&skt=2026-06-19T05%3A46%3A43Z&ske=2026-06-19T06%3A47%3A31Z&sks=b&skv=2018-11-09&sig=c%2BxYDS9bZHfGtBkCSc  
k7GE%2FWXn56JptaGdNRAmGt7fY%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFz  
ZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODg4NSwibmJmIjoxNzgxODQ4NTg1LCJwYXRoIjoi  
cmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.99HQsfMvdJuOZ9abjrq821Pj7-ZOdiieW14dIgVGaKo&response-  
content-disposition=attachment%3B%20filename%3Dlibffi-3.5.2.tar.gz&response-content-type=application%2Foctet-stream  
[following]  
--2026-06-19 07:56:21--  https://release-assets.githubusercontent.com/github-production-release-asset/321154/a7ac147  
0-95d7-4036-9735-36099626d83e?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A47%3A31Z&rscd=attachment%3B+filen  
ame%3Dlibffi-3.5.2.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-  
997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A46%3A43Z&ske=2026-06-19T06%3A47%3A31Z&sks=b&skv=2018-11-09&sig=c%2Bx  
YDS9bZHfGtBkCSck7GE%2FWXn56JptaGdNRAmGt7fY%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiY  
XVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODg4NSwibmJmIjoxNzgxODQ4N  
Tg1LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.99HQsfMvdJuOZ9abjrq821Pj7-ZOdiieW14dIg  
VGaKo&response-content-disposition=attachment%3B%20filename%3Dlibffi-3.5.2.tar.gz&response-content-type=application%  
2Foctet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1423124 (1.4M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/libffi-3.5.2.tar.gz'  
  
libffi-3.5.2.tar.gz          100%[==============================================>]   1.36M  4.16MB/s    in 0.3s       
  
2026-06-19 07:56:22 (4.16 MB/s) - '/mnt/lfs/sources/libffi-3.5.2.tar.gz' saved [1423124/1423124]  
  
--2026-06-19 07:56:22--  https://download.savannah.gnu.org/releases/libpipeline/libpipeline-1.5.8.tar.gz  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://fosszone.csd.auth.gr/nongnu/libpipeline/libpipeline-1.5.8.tar.gz [following]  
--2026-06-19 07:56:22--  https://fosszone.csd.auth.gr/nongnu/libpipeline/libpipeline-1.5.8.tar.gz  
Resolving fosszone.csd.auth.gr (fosszone.csd.auth.gr)... 155.207.200.222  
Connecting to fosszone.csd.auth.gr (fosszone.csd.auth.gr)|155.207.200.222|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1070254 (1.0M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/libpipeline-1.5.8.tar.gz'  
  
libpipeline-1.5.8.tar.gz     100%[==============================================>]   1.02M  2.59MB/s    in 0.4s       
  
2026-06-19 07:56:23 (2.59 MB/s) - '/mnt/lfs/sources/libpipeline-1.5.8.tar.gz' saved [1070254/1070254]  
  
--2026-06-19 07:56:23--  https://ftpmirror.gnu.org/libtool/libtool-2.5.4.tar.xz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://ftp.man.poznan.pl/gnu/libtool/libtool-2.5.4.tar.xz [following]  
--2026-06-19 07:56:24--  https://ftp.man.poznan.pl/gnu/libtool/libtool-2.5.4.tar.xz  
Connecting to ftp.man.poznan.pl (ftp.man.poznan.pl)|150.254.173.17|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1056924 (1.0M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/libtool-2.5.4.tar.xz'  
  
libtool-2.5.4.tar.xz         100%[==============================================>]   1.01M  3.54MB/s    in 0.3s       
  
2026-06-19 07:56:24 (3.54 MB/s) - '/mnt/lfs/sources/libtool-2.5.4.tar.xz' saved [1056924/1056924]  
  
--2026-06-19 07:56:24--  https://github.com/besser82/libxcrypt/releases/download/v4.4.38/libxcrypt-4.4.38.tar.xz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/35503965/00fec067-6b89-42f6-b  
a82-02f2997ff738?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A38%3A33Z&rscd=attachment%3B+filename%3Dlibxcry  
pt-4.4.38.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9  
-b12b-9515b896b4de&skt=2026-06-19T05%3A37%3A47Z&ske=2026-06-19T06%3A38%3A33Z&sks=b&skv=2018-11-09&sig=SeWHmVHBb%2FOR  
EcDzWl0bVuXQwb6s5VZw%2BIglJgc%2FQO0%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoi  
cmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODg4OCwibmJmIjoxNzgxODQ4NTg4LCJw  
YXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.R4VV6H3nbdeQKkfRyOsV-XfyWxSWhVD-schfA6Kca7o&r  
esponse-content-disposition=attachment%3B%20filename%3Dlibxcrypt-4.4.38.tar.xz&response-content-type=application%2Fo  
ctet-stream [following]  
--2026-06-19 07:56:25--  https://release-assets.githubusercontent.com/github-production-release-asset/35503965/00fec  
067-6b89-42f6-ba82-02f2997ff738?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A38%3A33Z&rscd=attachment%3B+fil  
ename%3Dlibxcrypt-4.4.38.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398  
a6654-997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A37%3A47Z&ske=2026-06-19T06%3A38%3A33Z&sks=b&skv=2018-11-09&sig  
=SeWHmVHBb%2FOREcDzWl0bVuXQwb6s5VZw%2BIglJgc%2FQO0%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY  
29tIiwiYXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODg4OCwibmJmIjoxN  
zgxODQ4NTg4LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.R4VV6H3nbdeQKkfRyOsV-XfyWxSWhV  
D-schfA6Kca7o&response-content-disposition=attachment%3B%20filename%3Dlibxcrypt-4.4.38.tar.xz&response-content-type=  
application%2Foctet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 625756 (611K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/libxcrypt-4.4.38.tar.xz'  
  
libxcrypt-4.4.38.tar.xz      100%[==============================================>] 611.09K  --.-KB/s    in 0.1s       
  
2026-06-19 07:56:25 (4.24 MB/s) - '/mnt/lfs/sources/libxcrypt-4.4.38.tar.xz' saved [625756/625756]  
  
--2026-06-19 07:56:25--  https://www.kernel.org/pub/linux/kernel/v6.x/linux-6.16.1.tar.xz  
Connecting to www.kernel.org (www.kernel.org)|146.75.117.55|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 152618660 (146M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/linux-6.16.1.tar.xz'  
  
linux-6.16.1.tar.xz          100%[==============================================>] 145.55M  5.83MB/s    in 24s        
  
2026-06-19 07:56:50 (5.98 MB/s) - '/mnt/lfs/sources/linux-6.16.1.tar.xz' saved [152618660/152618660]  
  
--2026-06-19 07:56:50--  https://github.com/lz4/lz4/releases/download/v1.10.0/lz4-1.10.0.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/18106269/26ca634c-7a27-4a9c-b  
280-60db44f8a9eb?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A54%3A03Z&rscd=attachment%3B+filename%3Dlz4-1.1  
0.0.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-  
9515b896b4de&skt=2026-06-19T05%3A53%3A42Z&ske=2026-06-19T06%3A54%3A03Z&sks=b&skv=2018-11-09&sig=gPV2XHuCnwXs1c5U0E2m  
H1jOZleFjivpSB%2BqCTPtioQ%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZS  
1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODkxNCwibmJmIjoxNzgxODQ4NjE0LCJwYXRoIjoicm  
VsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.zx0tYJ34-BHRuWVGLqZBfrGG6AJTddYE9kyzoU6vnac&response-co  
ntent-disposition=attachment%3B%20filename%3Dlz4-1.10.0.tar.gz&response-content-type=application%2Foctet-stream [fol  
lowing]  
--2026-06-19 07:56:51--  https://release-assets.githubusercontent.com/github-production-release-asset/18106269/26ca6  
34c-7a27-4a9c-b280-60db44f8a9eb?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A54%3A03Z&rscd=attachment%3B+fil  
ename%3Dlz4-1.10.0.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-  
997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A53%3A42Z&ske=2026-06-19T06%3A54%3A03Z&sks=b&skv=2018-11-09&sig=gPV2X  
HuCnwXs1c5U0E2mH1jOZleFjivpSB%2BqCTPtioQ%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXV  
kIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODkxNCwibmJmIjoxNzgxODQ4NjE  
0LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.zx0tYJ34-BHRuWVGLqZBfrGG6AJTddYE9kyzoU6v  
nac&response-content-disposition=attachment%3B%20filename%3Dlz4-1.10.0.tar.gz&response-content-type=application%2Foc  
tet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 387114 (378K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/lz4-1.10.0.tar.gz'  
  
lz4-1.10.0.tar.gz            100%[==============================================>] 378.04K  --.-KB/s    in 0.1s       
  
2026-06-19 07:56:51 (2.47 MB/s) - '/mnt/lfs/sources/lz4-1.10.0.tar.gz' saved [387114/387114]  
  
--2026-06-19 07:56:51--  https://ftpmirror.gnu.org/m4/m4-1.4.20.tar.xz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirror.easyname.at/gnu/m4/m4-1.4.20.tar.xz [following]  
--2026-06-19 07:56:52--  https://mirror.easyname.at/gnu/m4/m4-1.4.20.tar.xz  
Connecting to mirror.easyname.at (mirror.easyname.at)|77.244.244.134|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2044756 (1.9M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/m4-1.4.20.tar.xz'  
  
m4-1.4.20.tar.xz             100%[==============================================>]   1.95M  5.12MB/s    in 0.4s       
  
2026-06-19 07:56:52 (5.12 MB/s) - '/mnt/lfs/sources/m4-1.4.20.tar.xz' saved [2044756/2044756]  
  
--2026-06-19 07:56:52--  https://ftpmirror.gnu.org/make/make-4.4.1.tar.gz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://sunsite.icm.edu.pl/pub/gnu/make/make-4.4.1.tar.gz [following]  
--2026-06-19 07:56:53--  https://sunsite.icm.edu.pl/pub/gnu/make/make-4.4.1.tar.gz  
Connecting to sunsite.icm.edu.pl (sunsite.icm.edu.pl)|193.219.28.2|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2348200 (2.2M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/make-4.4.1.tar.gz'  
  
make-4.4.1.tar.gz            100%[==============================================>]   2.24M  3.99MB/s    in 0.6s       
  
2026-06-19 07:56:54 (3.99 MB/s) - '/mnt/lfs/sources/make-4.4.1.tar.gz' saved [2348200/2348200]  
  
--2026-06-19 07:56:54--  https://download.savannah.gnu.org/releases/man-db/man-db-2.13.1.tar.xz  
Connecting to download.savannah.gnu.org (download.savannah.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://nongnu.niranjan.co/man-db/man-db-2.13.1.tar.xz [following]  
--2026-06-19 07:56:55--  https://nongnu.niranjan.co/man-db/man-db-2.13.1.tar.xz  
Resolving nongnu.niranjan.co (nongnu.niranjan.co)... 51.158.149.147  
Connecting to nongnu.niranjan.co (nongnu.niranjan.co)|51.158.149.147|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2110328 (2.0M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/man-db-2.13.1.tar.xz'  
  
man-db-2.13.1.tar.xz         100%[==============================================>]   2.01M  3.78MB/s    in 0.5s       
  
2026-06-19 07:56:55 (3.78 MB/s) - '/mnt/lfs/sources/man-db-2.13.1.tar.xz' saved [2110328/2110328]  
  
--2026-06-19 07:56:55--  https://www.kernel.org/pub/linux/docs/man-pages/man-pages-6.15.tar.xz  
Connecting to www.kernel.org (www.kernel.org)|146.75.117.55|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1860208 (1.8M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/man-pages-6.15.tar.xz'  
  
man-pages-6.15.tar.xz        100%[==============================================>]   1.77M  4.97MB/s    in 0.4s       
  
2026-06-19 07:56:56 (4.97 MB/s) - '/mnt/lfs/sources/man-pages-6.15.tar.xz' saved [1860208/1860208]  
  
--2026-06-19 07:56:56--  https://pypi.org/packages/source/M/MarkupSafe/markupsafe-3.0.2.tar.gz  
Connecting to pypi.org (pypi.org)|151.101.64.223|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://files.pythonhosted.org/packages/source/M/MarkupSafe/markupsafe-3.0.2.tar.gz [following]  
--2026-06-19 07:56:56--  https://files.pythonhosted.org/packages/source/M/MarkupSafe/markupsafe-3.0.2.tar.gz  
Connecting to files.pythonhosted.org (files.pythonhosted.org)|151.101.192.223|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://files.pythonhosted.org/packages/b2/97/5d42485e71dfc078108a86d6de8fa46db44a1a9295e89c5d6d4a06e23a62  
/markupsafe-3.0.2.tar.gz [following]  
--2026-06-19 07:56:56--  https://files.pythonhosted.org/packages/b2/97/5d42485e71dfc078108a86d6de8fa46db44a1a9295e89  
c5d6d4a06e23a62/markupsafe-3.0.2.tar.gz  
Reusing existing connection to files.pythonhosted.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 20537 (20K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/markupsafe-3.0.2.tar.gz'  
  
markupsafe-3.0.2.tar.gz      100%[==============================================>]  20.06K  --.-KB/s    in 0.002s     
  
2026-06-19 07:56:56 (8.99 MB/s) - '/mnt/lfs/sources/markupsafe-3.0.2.tar.gz' saved [20537/20537]  
  
--2026-06-19 07:56:56--  https://github.com/mesonbuild/meson/releases/download/1.8.3/meson-1.8.3.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/19784232/4a5b9d80-645d-4cda-b  
b5f-974af3f0e17c?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A55%3A45Z&rscd=attachment%3B+filename%3Dmeson-1  
.8.3.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b  
-9515b896b4de&skt=2026-06-19T05%3A55%3A32Z&ske=2026-06-19T06%3A55%3A45Z&sks=b&skv=2018-11-09&sig=7mxyDwlTfJQNlix5eFU  
C%2Bh1I1N9%2BVPSslqmpNsuE6P8%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWF  
zZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODkyMCwibmJmIjoxNzgxODQ4NjIwLCJwYXRoIjo  
icmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.IjZVUEq-1IfeNq-XI2jLexO8y6A2n_W-49ih15tPex4&response  
-content-disposition=attachment%3B%20filename%3Dmeson-1.8.3.tar.gz&response-content-type=application%2Foctet-stream  
[following]  
--2026-06-19 07:56:57--  https://release-assets.githubusercontent.com/github-production-release-asset/19784232/4a5b9  
d80-645d-4cda-bb5f-974af3f0e17c?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A55%3A45Z&rscd=attachment%3B+fil  
ename%3Dmeson-1.8.3.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654  
-997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A55%3A32Z&ske=2026-06-19T06%3A55%3A45Z&sks=b&skv=2018-11-09&sig=7mxy  
DwlTfJQNlix5eFUC%2Bh1I1N9%2BVPSslqmpNsuE6P8%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwi  
YXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODkyMCwibmJmIjoxNzgxODQ4  
NjIwLCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.IjZVUEq-1IfeNq-XI2jLexO8y6A2n_W-49ih1  
5tPex4&response-content-disposition=attachment%3B%20filename%3Dmeson-1.8.3.tar.gz&response-content-type=application%  
2Foctet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2335924 (2.2M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/meson-1.8.3.tar.gz'  
  
meson-1.8.3.tar.gz           100%[==============================================>]   2.23M  5.61MB/s    in 0.4s       
  
2026-06-19 07:56:58 (5.61 MB/s) - '/mnt/lfs/sources/meson-1.8.3.tar.gz' saved [2335924/2335924]  
  
--2026-06-19 07:56:58--  https://ftpmirror.gnu.org/mpc/mpc-1.3.1.tar.gz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirrors.nav.ro/gnu/mpc/mpc-1.3.1.tar.gz [following]  
--2026-06-19 07:56:59--  https://mirrors.nav.ro/gnu/mpc/mpc-1.3.1.tar.gz  
Connecting to mirrors.nav.ro (mirrors.nav.ro)|5.154.224.26|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 773573 (755K) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/mpc-1.3.1.tar.gz'  
  
mpc-1.3.1.tar.gz             100%[==============================================>] 755.44K  2.67MB/s    in 0.3s       
  
2026-06-19 07:56:59 (2.67 MB/s) - '/mnt/lfs/sources/mpc-1.3.1.tar.gz' saved [773573/773573]  
  
--2026-06-19 07:56:59--  https://ftpmirror.gnu.org/mpfr/mpfr-4.2.2.tar.xz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://sunsite.icm.edu.pl/pub/gnu/mpfr/mpfr-4.2.2.tar.xz [following]  
--2026-06-19 07:57:00--  https://sunsite.icm.edu.pl/pub/gnu/mpfr/mpfr-4.2.2.tar.xz  
Connecting to sunsite.icm.edu.pl (sunsite.icm.edu.pl)|193.219.28.2|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1505596 (1.4M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/mpfr-4.2.2.tar.xz'  
  
mpfr-4.2.2.tar.xz            100%[==============================================>]   1.44M  3.11MB/s    in 0.5s       
  
2026-06-19 07:57:01 (3.11 MB/s) - '/mnt/lfs/sources/mpfr-4.2.2.tar.xz' saved [1505596/1505596]  
  
--2026-06-19 07:57:01--  https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
Resolving invisible-mirror.net (invisible-mirror.net)... 107.180.113.177  
Connecting to invisible-mirror.net (invisible-mirror.net)|107.180.113.177|:443... connected.  
HTTP request sent, awaiting response... 404 Not Found  
2026-06-19 07:57:02 ERROR 404: Not Found.  
  
--2026-06-19 07:57:02--  https://github.com/ninja-build/ninja/archive/v1.13.1/ninja-1.13.1.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://codeload.github.com/ninja-build/ninja/tar.gz/refs/tags/v1.13.1 [following]  
--2026-06-19 07:57:02--  https://codeload.github.com/ninja-build/ninja/tar.gz/refs/tags/v1.13.1  
Resolving codeload.github.com (codeload.github.com)... 140.82.121.10  
Connecting to codeload.github.com (codeload.github.com)|140.82.121.10|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 292098 (285K) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/ninja-1.13.1.tar.gz'  
  
ninja-1.13.1.tar.gz          100%[==============================================>] 285.25K  1.72MB/s    in 0.2s       
  
2026-06-19 07:57:02 (1.72 MB/s) - '/mnt/lfs/sources/ninja-1.13.1.tar.gz' saved [292098/292098]  
  
--2026-06-19 07:57:02--  https://github.com/openssl/openssl/releases/download/openssl-3.5.2/openssl-3.5.2.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/7634677/de48a7fc-93b5-47ca-9b  
00-ec7d9ee86a60?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A37%3A20Z&rscd=attachment%3B+filename%3Dopenssl-  
3.5.2.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12  
b-9515b896b4de&skt=2026-06-19T05%3A37%3A07Z&ske=2026-06-19T06%3A37%3A20Z&sks=b&skv=2018-11-09&sig=GyE3UYVpMe1J9jUwtd  
9NmdJSdaBK%2BTflxz0HWS5W8f8%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFz  
ZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg1MDQyNiwibmJmIjoxNzgxODQ4NjI2LCJwYXRoIjoi  
cmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.P-q5ypxieA6wQvv7gah78wmgoCInWnTTiSNiLRBrFSY&response-  
content-disposition=attachment%3B%20filename%3Dopenssl-3.5.2.tar.gz&response-content-type=application%2Foctet-stream  
[following]  
--2026-06-19 07:57:03--  https://release-assets.githubusercontent.com/github-production-release-asset/7634677/de48a7  
fc-93b5-47ca-9b00-ec7d9ee86a60?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A37%3A20Z&rscd=attachment%3B+file  
name%3Dopenssl-3.5.2.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a665  
4-997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A37%3A07Z&ske=2026-06-19T06%3A37%3A20Z&sks=b&skv=2018-11-09&sig=GyE  
3UYVpMe1J9jUwtd9NmdJSdaBK%2BTflxz0HWS5W8f8%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiY  
XVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg1MDQyNiwibmJmIjoxNzgxODQ4N  
jI2LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.P-q5ypxieA6wQvv7gah78wmgoCInWnTTiSNiLR  
BrFSY&response-content-disposition=attachment%3B%20filename%3Dopenssl-3.5.2.tar.gz&response-content-type=application  
%2Foctet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 53180161 (51M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/openssl-3.5.2.tar.gz'  
  
openssl-3.5.2.tar.gz         100%[==============================================>]  50.72M  6.02MB/s    in 9.0s       
  
2026-06-19 07:57:12 (5.63 MB/s) - '/mnt/lfs/sources/openssl-3.5.2.tar.gz' saved [53180161/53180161]  
  
--2026-06-19 07:57:12--  https://files.pythonhosted.org/packages/source/p/packaging/packaging-25.0.tar.gz  
Connecting to files.pythonhosted.org (files.pythonhosted.org)|151.101.192.223|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://files.pythonhosted.org/packages/a1/d4/1fc4078c65507b51b96ca8f8c3ba19e6a61c8253c72794544580a7b6c24d  
/packaging-25.0.tar.gz [following]  
--2026-06-19 07:57:12--  https://files.pythonhosted.org/packages/a1/d4/1fc4078c65507b51b96ca8f8c3ba19e6a61c8253c7279  
4544580a7b6c24d/packaging-25.0.tar.gz  
Reusing existing connection to files.pythonhosted.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 165727 (162K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/packaging-25.0.tar.gz'  
  
packaging-25.0.tar.gz        100%[==============================================>] 161.84K  --.-KB/s    in 0.06s      
  
2026-06-19 07:57:12 (2.58 MB/s) - '/mnt/lfs/sources/packaging-25.0.tar.gz' saved [165727/165727]  
  
--2026-06-19 07:57:12--  https://ftpmirror.gnu.org/patch/patch-2.8.tar.xz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirror.kumi.systems/gnu/patch/patch-2.8.tar.xz [following]  
--2026-06-19 07:57:13--  https://mirror.kumi.systems/gnu/patch/patch-2.8.tar.xz  
Connecting to mirror.kumi.systems (mirror.kumi.systems)|110.172.148.96|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 907208 (886K) [application/x-xz]  
Saving to: '/mnt/lfs/sources/patch-2.8.tar.xz'  
  
patch-2.8.tar.xz             100%[==============================================>] 885.95K  2.31MB/s    in 0.4s       
  
2026-06-19 07:57:14 (2.31 MB/s) - '/mnt/lfs/sources/patch-2.8.tar.xz' saved [907208/907208]  
  
--2026-06-19 07:57:14--  https://www.cpan.org/src/5.0/perl-5.42.0.tar.xz  
Resolving www.cpan.org (www.cpan.org)... 199.232.189.55  
Connecting to www.cpan.org (www.cpan.org)|199.232.189.55|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 14400988 (14M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/perl-5.42.0.tar.xz'  
  
perl-5.42.0.tar.xz           100%[==============================================>]  13.73M  5.64MB/s    in 2.4s       
  
2026-06-19 07:57:17 (5.64 MB/s) - '/mnt/lfs/sources/perl-5.42.0.tar.xz' saved [14400988/14400988]  
  
--2026-06-19 07:57:17--  https://distfiles.ariadne.space/pkgconf/pkgconf-2.5.1.tar.xz  
Resolving distfiles.ariadne.space (distfiles.ariadne.space)... 199.255.18.183  
Connecting to distfiles.ariadne.space (distfiles.ariadne.space)|199.255.18.183|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 328064 (320K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/pkgconf-2.5.1.tar.xz'  
  
pkgconf-2.5.1.tar.xz         100%[==============================================>] 320.38K   375KB/s    in 0.9s       
  
2026-06-19 07:57:19 (375 KB/s) - '/mnt/lfs/sources/pkgconf-2.5.1.tar.xz' saved [328064/328064]  
  
--2026-06-19 07:57:19--  https://sourceforge.net/projects/procps-ng/files/Production/procps-ng-4.0.5.tar.xz  
Resolving sourceforge.net (sourceforge.net)... 104.18.13.149, 104.18.12.149  
Connecting to sourceforge.net (sourceforge.net)|104.18.13.149|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://sourceforge.net/projects/procps-ng/files/Production/procps-ng-4.0.5.tar.xz/ [following]  
--2026-06-19 07:57:19--  https://sourceforge.net/projects/procps-ng/files/Production/procps-ng-4.0.5.tar.xz/  
Reusing existing connection to sourceforge.net:443.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://sourceforge.net/projects/procps-ng/files/Production/procps-ng-4.0.5.tar.xz/download [following]  
--2026-06-19 07:57:19--  https://sourceforge.net/projects/procps-ng/files/Production/procps-ng-4.0.5.tar.xz/download  
Reusing existing connection to sourceforge.net:443.  
HTTP request sent, awaiting response... 302 Found  
Location: https://downloads.sourceforge.net/project/procps-ng/Production/procps-ng-4.0.5.tar.xz?ts=gAAAAABqNNpDRMoU_  
s2ANQnAxARgRlGI9dQXeNN0MMMzjltrW1OocQUteLhmvH5WTf-Gy6Kn2zdFCDCy54gXAnna1QovbDo9ZQ%3D%3D&use_mirror=netix&r= [followi  
ng]  
--2026-06-19 07:57:20--  https://downloads.sourceforge.net/project/procps-ng/Production/procps-ng-4.0.5.tar.xz?ts=gA  
AAAABqNNpDRMoU_s2ANQnAxARgRlGI9dQXeNN0MMMzjltrW1OocQUteLhmvH5WTf-Gy6Kn2zdFCDCy54gXAnna1QovbDo9ZQ%3D%3D&use_mirror=ne  
tix&r=  
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|104.18.13.149|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://netix.dl.sourceforge.net/project/procps-ng/Production/procps-ng-4.0.5.tar.xz?viasf=1&fid=bd5366f16  
66fd393 [following]  
--2026-06-19 07:57:20--  https://netix.dl.sourceforge.net/project/procps-ng/Production/procps-ng-4.0.5.tar.xz?viasf=  
1&fid=bd5366f1666fd393  
Resolving netix.dl.sourceforge.net (netix.dl.sourceforge.net)... 87.121.121.2  
Connecting to netix.dl.sourceforge.net (netix.dl.sourceforge.net)|87.121.121.2|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1517672 (1.4M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/procps-ng-4.0.5.tar.xz'  
  
procps-ng-4.0.5.tar.xz       100%[==============================================>]   1.45M  3.19MB/s    in 0.5s       
  
2026-06-19 07:57:21 (3.19 MB/s) - '/mnt/lfs/sources/procps-ng-4.0.5.tar.xz' saved [1517672/1517672]  
  
--2026-06-19 07:57:21--  https://sourceforge.net/projects/psmisc/files/psmisc/psmisc-23.7.tar.xz  
Connecting to sourceforge.net (sourceforge.net)|104.18.13.149|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://sourceforge.net/projects/psmisc/files/psmisc/psmisc-23.7.tar.xz/ [following]  
--2026-06-19 07:57:21--  https://sourceforge.net/projects/psmisc/files/psmisc/psmisc-23.7.tar.xz/  
Reusing existing connection to sourceforge.net:443.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://sourceforge.net/projects/psmisc/files/psmisc/psmisc-23.7.tar.xz/download [following]  
--2026-06-19 07:57:21--  https://sourceforge.net/projects/psmisc/files/psmisc/psmisc-23.7.tar.xz/download  
Reusing existing connection to sourceforge.net:443.  
HTTP request sent, awaiting response... 302 Found  
Location: https://downloads.sourceforge.net/project/psmisc/psmisc/psmisc-23.7.tar.xz?ts=gAAAAABqNNpF_3WOQQi-Xvpy0058  
7WZiRCS0gVGhM5Ead43fyaWQnwrzQWrNzZRpC9gppslxuoIWWUeSDCYVU_0MZr846aYZ4g%3D%3D&use_mirror=sf-eu-introserv-2&r= [follow  
ing]  
--2026-06-19 07:57:22--  https://downloads.sourceforge.net/project/psmisc/psmisc/psmisc-23.7.tar.xz?ts=gAAAAABqNNpF_  
3WOQQi-Xvpy00587WZiRCS0gVGhM5Ead43fyaWQnwrzQWrNzZRpC9gppslxuoIWWUeSDCYVU_0MZr846aYZ4g%3D%3D&use_mirror=sf-eu-introse  
rv-2&r=  
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|104.18.13.149|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://sf-eu-introserv-2.dl.sourceforge.net/project/psmisc/psmisc/psmisc-23.7.tar.xz?viasf=1&fid=b8b41677  
20078fbd [following]  
--2026-06-19 07:57:22--  https://sf-eu-introserv-2.dl.sourceforge.net/project/psmisc/psmisc/psmisc-23.7.tar.xz?viasf  
=1&fid=b8b4167720078fbd  
Resolving sf-eu-introserv-2.dl.sourceforge.net (sf-eu-introserv-2.dl.sourceforge.net)... 51.91.221.175  
Connecting to sf-eu-introserv-2.dl.sourceforge.net (sf-eu-introserv-2.dl.sourceforge.net)|51.91.221.175|:443... conn  
ected.  
HTTP request sent, awaiting response... 200 OK  
Length: 432208 (422K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/psmisc-23.7.tar.xz'  
  
psmisc-23.7.tar.xz           100%[==============================================>] 422.08K  2.42MB/s    in 0.2s       
  
2026-06-19 07:57:22 (2.42 MB/s) - '/mnt/lfs/sources/psmisc-23.7.tar.xz' saved [432208/432208]  
  
--2026-06-19 07:57:22--  https://www.python.org/ftp/python/3.13.7/Python-3.13.7.tar.xz  
Resolving www.python.org (www.python.org)... 151.101.0.223, 151.101.64.223, 151.101.128.223, ...  
Connecting to www.python.org (www.python.org)|151.101.0.223|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 22769492 (22M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/Python-3.13.7.tar.xz'  
  
Python-3.13.7.tar.xz         100%[==============================================>]  21.71M  6.01MB/s    in 3.7s       
  
2026-06-19 07:57:27 (5.92 MB/s) - '/mnt/lfs/sources/Python-3.13.7.tar.xz' saved [22769492/22769492]  
  
--2026-06-19 07:57:27--  https://www.python.org/ftp/python/doc/3.13.7/python-3.13.7-docs-html.tar.bz2  
Reusing existing connection to www.python.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 10426777 (9.9M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/python-3.13.7-docs-html.tar.bz2'  
  
python-3.13.7-docs-html.tar. 100%[==============================================>]   9.94M  6.06MB/s    in 1.6s       
  
2026-06-19 07:57:29 (6.06 MB/s) - '/mnt/lfs/sources/python-3.13.7-docs-html.tar.bz2' saved [10426777/10426777]  
  
--2026-06-19 07:57:29--  https://ftpmirror.gnu.org/readline/readline-8.3.tar.gz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirrors.nav.ro/gnu/readline/readline-8.3.tar.gz [following]  
--2026-06-19 07:57:30--  https://mirrors.nav.ro/gnu/readline/readline-8.3.tar.gz  
Connecting to mirrors.nav.ro (mirrors.nav.ro)|5.154.224.26|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 3419642 (3.3M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/readline-8.3.tar.gz'  
  
readline-8.3.tar.gz          100%[==============================================>]   3.26M   607KB/s    in 4.1s       
  
2026-06-19 07:57:34 (824 KB/s) - '/mnt/lfs/sources/readline-8.3.tar.gz' saved [3419642/3419642]  
  
--2026-06-19 07:57:34--  https://ftpmirror.gnu.org/sed/sed-4.9.tar.xz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirror.easyname.at/gnu/sed/sed-4.9.tar.xz [following]  
--2026-06-19 07:57:37--  https://mirror.easyname.at/gnu/sed/sed-4.9.tar.xz  
Connecting to mirror.easyname.at (mirror.easyname.at)|77.244.244.134|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1397092 (1.3M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/sed-4.9.tar.xz'  
  
sed-4.9.tar.xz               100%[==============================================>]   1.33M  2.65MB/s    in 0.5s       
  
2026-06-19 07:57:38 (2.65 MB/s) - '/mnt/lfs/sources/sed-4.9.tar.xz' saved [1397092/1397092]  
  
--2026-06-19 07:57:38--  https://pypi.org/packages/source/s/setuptools/setuptools-80.9.0.tar.gz  
Connecting to pypi.org (pypi.org)|151.101.64.223|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://files.pythonhosted.org/packages/source/s/setuptools/setuptools-80.9.0.tar.gz [following]  
--2026-06-19 07:57:39--  https://files.pythonhosted.org/packages/source/s/setuptools/setuptools-80.9.0.tar.gz  
Connecting to files.pythonhosted.org (files.pythonhosted.org)|151.101.192.223|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://files.pythonhosted.org/packages/18/5d/3bf57dcd21979b887f014ea83c24ae194cfcd12b9e0fda66b957c69d1fca  
/setuptools-80.9.0.tar.gz [following]  
--2026-06-19 07:57:39--  https://files.pythonhosted.org/packages/18/5d/3bf57dcd21979b887f014ea83c24ae194cfcd12b9e0fd  
a66b957c69d1fca/setuptools-80.9.0.tar.gz  
Reusing existing connection to files.pythonhosted.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 1319958 (1.3M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/setuptools-80.9.0.tar.gz'  
  
setuptools-80.9.0.tar.gz     100%[==============================================>]   1.26M  2.83MB/s    in 0.4s       
  
2026-06-19 07:57:39 (2.83 MB/s) - '/mnt/lfs/sources/setuptools-80.9.0.tar.gz' saved [1319958/1319958]  
  
--2026-06-19 07:57:39--  https://github.com/shadow-maint/shadow/releases/download/4.18.0/shadow-4.18.0.tar.xz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/10508169/cdc1c3d0-eba2-4c6b-b  
b55-fb0515435d5c?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A49%3A28Z&rscd=attachment%3B+filename%3Dshadow-  
4.18.0.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b1  
2b-9515b896b4de&skt=2026-06-19T05%3A49%3A22Z&ske=2026-06-19T06%3A49%3A28Z&sks=b&skv=2018-11-09&sig=66G4wFRqel2GAXshd  
02ThGWmbhdJfLV6xMwMTGYqE9A%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZ  
S1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk2MywibmJmIjoxNzgxODQ4NjYzLCJwYXRoIjoic  
mVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.pS8HmE7XOJrh0ho6mLWwEmJEnk_NMssa21-yaYN9BO0&response-c  
ontent-disposition=attachment%3B%20filename%3Dshadow-4.18.0.tar.xz&response-content-type=application%2Foctet-stream  
[following]  
--2026-06-19 07:57:40--  https://release-assets.githubusercontent.com/github-production-release-asset/10508169/cdc1c  
3d0-eba2-4c6b-bb55-fb0515435d5c?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A49%3A28Z&rscd=attachment%3B+fil  
ename%3Dshadow-4.18.0.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a66  
54-997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A49%3A22Z&ske=2026-06-19T06%3A49%3A28Z&sks=b&skv=2018-11-09&sig=66  
G4wFRqel2GAXshd02ThGWmbhdJfLV6xMwMTGYqE9A%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYX  
VkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk2MywibmJmIjoxNzgxODQ4Nj  
YzLCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.pS8HmE7XOJrh0ho6mLWwEmJEnk_NMssa21-yaYN  
9BO0&response-content-disposition=attachment%3B%20filename%3Dshadow-4.18.0.tar.xz&response-content-type=application%  
2Foctet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2347912 (2.2M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/shadow-4.18.0.tar.xz'  
  
shadow-4.18.0.tar.xz         100%[==============================================>]   2.24M  3.71MB/s    in 0.6s       
  
2026-06-19 07:57:41 (3.71 MB/s) - '/mnt/lfs/sources/shadow-4.18.0.tar.xz' saved [2347912/2347912]  
  
--2026-06-19 07:57:41--  https://github.com/troglobit/sysklogd/releases/download/v2.7.2/sysklogd-2.7.2.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/143292860/c92abd31-c7b7-471a-  
b909-74016da574bd?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A50%3A28Z&rscd=attachment%3B+filename%3Dsysklo  
gd-2.7.2.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-  
b12b-9515b896b4de&skt=2026-06-19T05%3A50%3A11Z&ske=2026-06-19T06%3A50%3A28Z&sks=b&skv=2018-11-09&sig=BH%2BSn%2B7XB%2  
FtzKNCokIhPsWx5FqzwE5qUv6KfAleJif8%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoic  
mVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk2NSwibmJmIjoxNzgxODQ4NjY1LCJwY  
XRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.jEpnhFB2OLXmoE3Igb1DjMFEsZ0RspYm_-aFRNR025Q&re  
sponse-content-disposition=attachment%3B%20filename%3Dsysklogd-2.7.2.tar.gz&response-content-type=application%2Focte  
t-stream [following]  
--2026-06-19 07:57:41--  https://release-assets.githubusercontent.com/github-production-release-asset/143292860/c92a  
bd31-c7b7-471a-b909-74016da574bd?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A50%3A28Z&rscd=attachment%3B+fi  
lename%3Dsysklogd-2.7.2.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a  
6654-997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A50%3A11Z&ske=2026-06-19T06%3A50%3A28Z&sks=b&skv=2018-11-09&sig=  
BH%2BSn%2B7XB%2FtzKNCokIhPsWx5FqzwE5qUv6KfAleJif8%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY2  
9tIiwiYXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk2NSwibmJmIjoxNz  
gxODQ4NjY1LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.jEpnhFB2OLXmoE3Igb1DjMFEsZ0RspY  
m_-aFRNR025Q&response-content-disposition=attachment%3B%20filename%3Dsysklogd-2.7.2.tar.gz&response-content-type=app  
lication%2Foctet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 484398 (473K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/sysklogd-2.7.2.tar.gz'  
  
sysklogd-2.7.2.tar.gz        100%[==============================================>] 473.04K  --.-KB/s    in 0.1s       
  
2026-06-19 07:57:41 (3.28 MB/s) - '/mnt/lfs/sources/sysklogd-2.7.2.tar.gz' saved [484398/484398]  
  
--2026-06-19 07:57:41--  https://github.com/systemd/systemd/archive/v257.8/systemd-257.8.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://codeload.github.com/systemd/systemd/tar.gz/refs/tags/v257.8 [following]  
--2026-06-19 07:57:42--  https://codeload.github.com/systemd/systemd/tar.gz/refs/tags/v257.8  
Connecting to codeload.github.com (codeload.github.com)|140.82.121.10|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: unspecified [application/x-gzip]  
Saving to: '/mnt/lfs/sources/systemd-257.8.tar.gz'  
  
systemd-257.8.tar.gz             [               <=>                             ]  15.63M  5.48MB/s    in 2.8s       
  
2026-06-19 07:57:45 (5.48 MB/s) - '/mnt/lfs/sources/systemd-257.8.tar.gz' saved [16385060]  
  
--2026-06-19 07:57:45--  https://anduin.linuxfromscratch.org/LFS/systemd-man-pages-257.8.tar.xz  
Resolving anduin.linuxfromscratch.org (anduin.linuxfromscratch.org)... 104.200.30.157  
Connecting to anduin.linuxfromscratch.org (anduin.linuxfromscratch.org)|104.200.30.157|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 753608 (736K) [application/x-xz]  
Saving to: '/mnt/lfs/sources/systemd-man-pages-257.8.tar.xz'  
  
systemd-man-pages-257.8.tar. 100%[==============================================>] 735.95K   955KB/s    in 0.8s       
  
2026-06-19 07:57:47 (955 KB/s) - '/mnt/lfs/sources/systemd-man-pages-257.8.tar.xz' saved [753608/753608]  
  
--2026-06-19 07:57:47--  https://github.com/slicer69/sysvinit/releases/download/3.14/sysvinit-3.14.tar.xz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/457063710/41bdb838-4caf-467f-  
b86a-71694cc509a2?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A43%3A40Z&rscd=attachment%3B+filename%3Dsysvin  
it-3.14.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b  
12b-9515b896b4de&skt=2026-06-19T05%3A42%3A41Z&ske=2026-06-19T06%3A43%3A40Z&sks=b&skv=2018-11-09&sig=etZqfQgtHOl%2BNk  
ntDqm0QPtQKWB3zgOqqdESi9dtrzY%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZW  
FzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk3MSwibmJmIjoxNzgxODQ4NjcxLCJwYXRoIj  
oicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.BuJ9XcSdwX4ySXbj2ynRwChdtWqldepzgBYL4pS1oNA&respons  
e-content-disposition=attachment%3B%20filename%3Dsysvinit-3.14.tar.xz&response-content-type=application%2Foctet-stre  
am [following]  
--2026-06-19 07:57:47--  https://release-assets.githubusercontent.com/github-production-release-asset/457063710/41bd  
b838-4caf-467f-b86a-71694cc509a2?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A43%3A40Z&rscd=attachment%3B+fi  
lename%3Dsysvinit-3.14.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6  
654-997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A42%3A41Z&ske=2026-06-19T06%3A43%3A40Z&sks=b&skv=2018-11-09&sig=e  
tZqfQgtHOl%2BNkntDqm0QPtQKWB3zgOqqdESi9dtrzY%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiw  
iYXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk3MSwibmJmIjoxNzgxODQ  
4NjcxLCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.BuJ9XcSdwX4ySXbj2ynRwChdtWqldepzgBYL  
4pS1oNA&response-content-disposition=attachment%3B%20filename%3Dsysvinit-3.14.tar.xz&response-content-type=applicati  
on%2Foctet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 241536 (236K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/sysvinit-3.14.tar.xz'  
  
sysvinit-3.14.tar.xz         100%[==============================================>] 235.88K  --.-KB/s    in 0.09s      
  
2026-06-19 07:57:47 (2.68 MB/s) - '/mnt/lfs/sources/sysvinit-3.14.tar.xz' saved [241536/241536]  
  
--2026-06-19 07:57:47--  https://ftpmirror.gnu.org/tar/tar-1.35.tar.xz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://mirrors.nav.ro/gnu/tar/tar-1.35.tar.xz [following]  
--2026-06-19 07:57:48--  https://mirrors.nav.ro/gnu/tar/tar-1.35.tar.xz  
Connecting to mirrors.nav.ro (mirrors.nav.ro)|5.154.224.26|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2317208 (2.2M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/tar-1.35.tar.xz'  
  
tar-1.35.tar.xz              100%[==============================================>]   2.21M   618KB/s    in 3.7s       
  
2026-06-19 07:57:52 (619 KB/s) - '/mnt/lfs/sources/tar-1.35.tar.xz' saved [2317208/2317208]  
  
--2026-06-19 07:57:52--  https://downloads.sourceforge.net/tcl/tcl8.6.16-src.tar.gz  
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|104.18.13.149|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://downloads.sourceforge.net/project/tcl/Tcl/8.6.16/tcl8.6.16-src.tar.gz [following]  
--2026-06-19 07:57:52--  https://downloads.sourceforge.net/project/tcl/Tcl/8.6.16/tcl8.6.16-src.tar.gz  
Reusing existing connection to downloads.sourceforge.net:443.  
HTTP request sent, awaiting response... 302 Found  
Location: https://altushost-swe.dl.sourceforge.net/project/tcl/Tcl/8.6.16/tcl8.6.16-src.tar.gz?viasf=1&fid=49e0a8079  
2bf6f08 [following]  
--2026-06-19 07:57:52--  https://altushost-swe.dl.sourceforge.net/project/tcl/Tcl/8.6.16/tcl8.6.16-src.tar.gz?viasf=  
1&fid=49e0a80792bf6f08  
Resolving altushost-swe.dl.sourceforge.net (altushost-swe.dl.sourceforge.net)... 79.142.76.130  
Connecting to altushost-swe.dl.sourceforge.net (altushost-swe.dl.sourceforge.net)|79.142.76.130|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 11678979 (11M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/tcl8.6.16-src.tar.gz'  
  
tcl8.6.16-src.tar.gz         100%[==============================================>]  11.14M  5.59MB/s    in 2.0s       
  
2026-06-19 07:57:55 (5.59 MB/s) - '/mnt/lfs/sources/tcl8.6.16-src.tar.gz' saved [11678979/11678979]  
  
--2026-06-19 07:57:55--  https://downloads.sourceforge.net/tcl/tcl8.6.16-html.tar.gz  
Reusing existing connection to downloads.sourceforge.net:443.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://downloads.sourceforge.net/project/tcl/Tcl/8.6.16/tcl8.6.16-html.tar.gz [following]  
--2026-06-19 07:57:55--  https://downloads.sourceforge.net/project/tcl/Tcl/8.6.16/tcl8.6.16-html.tar.gz  
Reusing existing connection to downloads.sourceforge.net:443.  
HTTP request sent, awaiting response... 302 Found  
Location: https://sf-eu-introserv-3.dl.sourceforge.net/project/tcl/Tcl/8.6.16/tcl8.6.16-html.tar.gz?viasf=1&fid=8c10  
02ca1066f2bf [following]  
--2026-06-19 07:57:55--  https://sf-eu-introserv-3.dl.sourceforge.net/project/tcl/Tcl/8.6.16/tcl8.6.16-html.tar.gz?v  
iasf=1&fid=8c1002ca1066f2bf  
Resolving sf-eu-introserv-3.dl.sourceforge.net (sf-eu-introserv-3.dl.sourceforge.net)... 51.83.96.195  
Connecting to sf-eu-introserv-3.dl.sourceforge.net (sf-eu-introserv-3.dl.sourceforge.net)|51.83.96.195|:443... conne  
cted.  
HTTP request sent, awaiting response... 200 OK  
Length: 1196445 (1.1M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/tcl8.6.16-html.tar.gz'  
  
tcl8.6.16-html.tar.gz        100%[==============================================>]   1.14M  4.03MB/s    in 0.3s       
  
2026-06-19 07:57:56 (4.03 MB/s) - '/mnt/lfs/sources/tcl8.6.16-html.tar.gz' saved [1196445/1196445]  
  
--2026-06-19 07:57:56--  https://ftpmirror.gnu.org/texinfo/texinfo-7.2.tar.xz  
Connecting to ftpmirror.gnu.org (ftpmirror.gnu.org)|209.51.188.200|:443... connected.  
HTTP request sent, awaiting response... 302 Moved Temporarily  
Location: https://sunsite.icm.edu.pl/pub/gnu/texinfo/texinfo-7.2.tar.xz [following]  
--2026-06-19 07:57:57--  https://sunsite.icm.edu.pl/pub/gnu/texinfo/texinfo-7.2.tar.xz  
Connecting to sunsite.icm.edu.pl (sunsite.icm.edu.pl)|193.219.28.2|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 6408432 (6.1M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/texinfo-7.2.tar.xz'  
  
texinfo-7.2.tar.xz           100%[==============================================>]   6.11M  5.12MB/s    in 1.2s       
  
2026-06-19 07:57:58 (5.12 MB/s) - '/mnt/lfs/sources/texinfo-7.2.tar.xz' saved [6408432/6408432]  
  
--2026-06-19 07:57:58--  https://www.iana.org/time-zones/repository/releases/tzdata2025b.tar.gz  
Resolving www.iana.org (www.iana.org)... 192.0.46.8  
Connecting to www.iana.org (www.iana.org)|192.0.46.8|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://data.iana.org/time-zones/releases/tzdata2025b.tar.gz [following]  
--2026-06-19 07:57:59--  https://data.iana.org/time-zones/releases/tzdata2025b.tar.gz  
Resolving data.iana.org (data.iana.org)... 104.18.24.232, 104.18.25.232  
Connecting to data.iana.org (data.iana.org)|104.18.24.232|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 464295 (453K) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/tzdata2025b.tar.gz'  
  
tzdata2025b.tar.gz           100%[==============================================>] 453.41K  --.-KB/s    in 0.1s       
  
2026-06-19 07:57:59 (4.51 MB/s) - '/mnt/lfs/sources/tzdata2025b.tar.gz' saved [464295/464295]  
  
--2026-06-19 07:57:59--  https://anduin.linuxfromscratch.org/LFS/udev-lfs-20230818.tar.xz  
Connecting to anduin.linuxfromscratch.org (anduin.linuxfromscratch.org)|104.200.30.157|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 10180 (9.9K) [application/x-xz]  
Saving to: '/mnt/lfs/sources/udev-lfs-20230818.tar.xz'  
  
udev-lfs-20230818.tar.xz     100%[==============================================>]   9.94K  --.-KB/s    in 0s         
  
2026-06-19 07:58:00 (81.8 MB/s) - '/mnt/lfs/sources/udev-lfs-20230818.tar.xz' saved [10180/10180]  
  
--2026-06-19 07:58:00--  https://www.kernel.org/pub/linux/utils/util-linux/v2.41/util-linux-2.41.1.tar.xz  
Connecting to www.kernel.org (www.kernel.org)|146.75.117.55|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 9606156 (9.2M) [application/x-xz]  
Saving to: '/mnt/lfs/sources/util-linux-2.41.1.tar.xz'  
  
util-linux-2.41.1.tar.xz     100%[==============================================>]   9.16M  4.17MB/s    in 2.2s       
  
2026-06-19 07:58:02 (4.17 MB/s) - '/mnt/lfs/sources/util-linux-2.41.1.tar.xz' saved [9606156/9606156]  
  
--2026-06-19 07:58:02--  https://github.com/vim/vim/archive/v9.1.1629/vim-9.1.1629.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://codeload.github.com/vim/vim/tar.gz/refs/tags/v9.1.1629 [following]  
--2026-06-19 07:58:03--  https://codeload.github.com/vim/vim/tar.gz/refs/tags/v9.1.1629  
Connecting to codeload.github.com (codeload.github.com)|140.82.121.10|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: unspecified [application/x-gzip]  
Saving to: '/mnt/lfs/sources/vim-9.1.1629.tar.gz'  
  
vim-9.1.1629.tar.gz              [                 <=>                           ]  17.89M  5.67MB/s    in 3.4s       
  
2026-06-19 07:58:07 (5.29 MB/s) - '/mnt/lfs/sources/vim-9.1.1629.tar.gz' saved [18756124]  
  
--2026-06-19 07:58:07--  https://pypi.org/packages/source/w/wheel/wheel-0.46.1.tar.gz  
Connecting to pypi.org (pypi.org)|151.101.64.223|:443... connected.  
HTTP request sent, awaiting response... 301 Moved Permanently  
Location: https://files.pythonhosted.org/packages/source/w/wheel/wheel-0.46.1.tar.gz [following]  
--2026-06-19 07:58:07--  https://files.pythonhosted.org/packages/source/w/wheel/wheel-0.46.1.tar.gz  
Connecting to files.pythonhosted.org (files.pythonhosted.org)|151.101.192.223|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://files.pythonhosted.org/packages/fb/62/e90918c4558b002726ab930863c0cbd3e7cf9a7befa1d4a1a240cecdb379  
/wheel-0.46.1.tar.gz [following]  
--2026-06-19 07:58:07--  https://files.pythonhosted.org/packages/fb/62/e90918c4558b002726ab930863c0cbd3e7cf9a7befa1d  
4a1a240cecdb379/wheel-0.46.1.tar.gz  
Reusing existing connection to files.pythonhosted.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 54400 (53K) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/wheel-0.46.1.tar.gz'  
  
wheel-0.46.1.tar.gz          100%[==============================================>]  53.12K  --.-KB/s    in 0.03s      
  
2026-06-19 07:58:08 (1.93 MB/s) - '/mnt/lfs/sources/wheel-0.46.1.tar.gz' saved [54400/54400]  
  
--2026-06-19 07:58:08--  https://cpan.metacpan.org/authors/id/T/TO/TODDR/XML-Parser-2.47.tar.gz  
Resolving cpan.metacpan.org (cpan.metacpan.org)... 199.232.190.217  
Connecting to cpan.metacpan.org (cpan.metacpan.org)|199.232.190.217|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 279029 (272K) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/XML-Parser-2.47.tar.gz'  
  
XML-Parser-2.47.tar.gz       100%[==============================================>] 272.49K  --.-KB/s    in 0.1s       
  
2026-06-19 07:58:08 (2.29 MB/s) - '/mnt/lfs/sources/XML-Parser-2.47.tar.gz' saved [279029/279029]  
  
--2026-06-19 07:58:08--  https://github.com//tukaani-project/xz/releases/download/v5.8.1/xz-5.8.1.tar.xz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/553665726/81f49e1b-3583-44ed-  
855f-87d88de3c4e9?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A56%3A50Z&rscd=attachment%3B+filename%3Dxz-5.8  
.1.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-9  
515b896b4de&skt=2026-06-19T05%3A56%3A38Z&ske=2026-06-19T06%3A56%3A50Z&sks=b&skv=2018-11-09&sig=4NAbZwTTI4eAzY08Av5MT  
Eo0zhlb%2BTOP8CrFvCY3ldE%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZS1  
hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk5MiwibmJmIjoxNzgxODQ4NjkyLCJwYXRoIjoicmV  
sZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.jA_L4jgE74X0UgSPZuzMkYLPvvr0so_ziPQatyn5Z-Q&response-con  
tent-disposition=attachment%3B%20filename%3Dxz-5.8.1.tar.xz&response-content-type=application%2Foctet-stream [follow  
ing]  
--2026-06-19 07:58:08--  https://release-assets.githubusercontent.com/github-production-release-asset/553665726/81f4  
9e1b-3583-44ed-855f-87d88de3c4e9?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A56%3A50Z&rscd=attachment%3B+fi  
lename%3Dxz-5.8.1.tar.xz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-9  
97b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A56%3A38Z&ske=2026-06-19T06%3A56%3A50Z&sks=b&skv=2018-11-09&sig=4NAbZw  
TTI4eAzY08Av5MTEo0zhlb%2BTOP8CrFvCY3ldE%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVk  
IjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk5MiwibmJmIjoxNzgxODQ4Njky  
LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.jA_L4jgE74X0UgSPZuzMkYLPvvr0so_ziPQatyn5Z  
-Q&response-content-disposition=attachment%3B%20filename%3Dxz-5.8.1.tar.xz&response-content-type=application%2Foctet  
-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1461872 (1.4M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/xz-5.8.1.tar.xz'  
  
xz-5.8.1.tar.xz              100%[==============================================>]   1.39M  3.01MB/s    in 0.5s       
  
2026-06-19 07:58:09 (3.01 MB/s) - '/mnt/lfs/sources/xz-5.8.1.tar.xz' saved [1461872/1461872]  
  
--2026-06-19 07:58:09--  https://zlib.net/fossils/zlib-1.3.1.tar.gz  
Resolving zlib.net (zlib.net)... 85.187.148.2  
Connecting to zlib.net (zlib.net)|85.187.148.2|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1512791 (1.4M) [application/x-gzip]  
Saving to: '/mnt/lfs/sources/zlib-1.3.1.tar.gz'  
  
zlib-1.3.1.tar.gz            100%[==============================================>]   1.44M   342KB/s    in 4.5s       
  
2026-06-19 07:58:14 (330 KB/s) - '/mnt/lfs/sources/zlib-1.3.1.tar.gz' saved [1512791/1512791]  
  
--2026-06-19 07:58:14--  https://github.com/facebook/zstd/releases/download/v1.5.7/zstd-1.5.7.tar.gz  
Connecting to github.com (github.com)|140.82.121.4|:443... connected.  
HTTP request sent, awaiting response... 302 Found  
Location: https://release-assets.githubusercontent.com/github-production-release-asset/29759715/99c899ba-527a-4d01-9  
4e1-4b246cc9b551?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A42%3A01Z&rscd=attachment%3B+filename%3Dzstd-1.  
5.7.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-  
9515b896b4de&skt=2026-06-19T05%3A41%3A55Z&ske=2026-06-19T06%3A42%3A01Z&sks=b&skv=2018-11-09&sig=pN27bzdX2fApZwstUOMo  
SzjSIvrJTHfcLFwJrw%2FCQJY%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZS  
1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk5OCwibmJmIjoxNzgxODQ4Njk4LCJwYXRoIjoicm  
VsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.SVurNPW5NT3SiLZW2t1HOoPVa9Jv2pRqYeGoG3rkOA4&response-co  
ntent-disposition=attachment%3B%20filename%3Dzstd-1.5.7.tar.gz&response-content-type=application%2Foctet-stream [fol  
lowing]  
--2026-06-19 07:58:15--  https://release-assets.githubusercontent.com/github-production-release-asset/29759715/99c89  
9ba-527a-4d01-94e1-4b246cc9b551?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-06-19T06%3A42%3A01Z&rscd=attachment%3B+fil  
ename%3Dzstd-1.5.7.tar.gz&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-  
997b-47e9-b12b-9515b896b4de&skt=2026-06-19T05%3A41%3A55Z&ske=2026-06-19T06%3A42%3A01Z&sks=b&skv=2018-11-09&sig=pN27b  
zdX2fApZwstUOMoSzjSIvrJTHfcLFwJrw%2FCQJY%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXV  
kIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc4MTg0ODk5OCwibmJmIjoxNzgxODQ4Njk  
4LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.SVurNPW5NT3SiLZW2t1HOoPVa9Jv2pRqYeGoG3rk  
OA4&response-content-disposition=attachment%3B%20filename%3Dzstd-1.5.7.tar.gz&response-content-type=application%2Foc  
tet-stream  
Connecting to release-assets.githubusercontent.com (release-assets.githubusercontent.com)|185.199.108.133|:443... co  
nnected.  
HTTP request sent, awaiting response... 200 OK  
Length: 2434947 (2.3M) [application/octet-stream]  
Saving to: '/mnt/lfs/sources/zstd-1.5.7.tar.gz'  
  
zstd-1.5.7.tar.gz            100%[==============================================>]   2.32M  5.49MB/s    in 0.4s       
  
2026-06-19 07:58:15 (5.49 MB/s) - '/mnt/lfs/sources/zstd-1.5.7.tar.gz' saved [2434947/2434947]  
  
--2026-06-19 07:58:15--  https://www.linuxfromscratch.org/patches/lfs/12.4/bzip2-1.0.8-install_docs-1.patch  
Connecting to www.linuxfromscratch.org (www.linuxfromscratch.org)|208.118.68.85|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1684 (1.6K)  
Saving to: '/mnt/lfs/sources/bzip2-1.0.8-install_docs-1.patch'  
  
bzip2-1.0.8-install_docs-1.p 100%[==============================================>]   1.64K  --.-KB/s    in 0s         
  
2026-06-19 07:58:16 (18.6 MB/s) - '/mnt/lfs/sources/bzip2-1.0.8-install_docs-1.patch' saved [1684/1684]  
  
--2026-06-19 07:58:16--  https://www.linuxfromscratch.org/patches/lfs/12.4/coreutils-9.7-upstream_fix-1.patch  
Reusing existing connection to www.linuxfromscratch.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 4130 (4.0K)  
Saving to: '/mnt/lfs/sources/coreutils-9.7-upstream_fix-1.patch'  
  
coreutils-9.7-upstream_fix-1 100%[==============================================>]   4.03K  --.-KB/s    in 0s         
  
2026-06-19 07:58:16 (77.3 MB/s) - '/mnt/lfs/sources/coreutils-9.7-upstream_fix-1.patch' saved [4130/4130]  
  
--2026-06-19 07:58:16--  https://www.linuxfromscratch.org/patches/lfs/12.4/coreutils-9.7-i18n-1.patch  
Reusing existing connection to www.linuxfromscratch.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 162555 (159K)  
Saving to: '/mnt/lfs/sources/coreutils-9.7-i18n-1.patch'  
  
coreutils-9.7-i18n-1.patch   100%[==============================================>] 158.75K  57.4KB/s    in 2.8s       
  
2026-06-19 07:58:19 (57.4 KB/s) - '/mnt/lfs/sources/coreutils-9.7-i18n-1.patch' saved [162555/162555]  
  
--2026-06-19 07:58:19--  https://www.linuxfromscratch.org/patches/lfs/12.4/expect-5.45.4-gcc15-1.patch  
Reusing existing connection to www.linuxfromscratch.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 12155 (12K)  
Saving to: '/mnt/lfs/sources/expect-5.45.4-gcc15-1.patch'  
  
expect-5.45.4-gcc15-1.patch  100%[==============================================>]  11.87K  --.-KB/s    in 0s         
  
2026-06-19 07:58:20 (97.4 MB/s) - '/mnt/lfs/sources/expect-5.45.4-gcc15-1.patch' saved [12155/12155]  
  
--2026-06-19 07:58:20--  https://www.linuxfromscratch.org/patches/lfs/12.4/glibc-2.42-fhs-1.patch  
Reusing existing connection to www.linuxfromscratch.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 2804 (2.7K)  
Saving to: '/mnt/lfs/sources/glibc-2.42-fhs-1.patch'  
  
glibc-2.42-fhs-1.patch       100%[==============================================>]   2.74K  --.-KB/s    in 0.002s     
  
2026-06-19 07:58:20 (1.32 MB/s) - '/mnt/lfs/sources/glibc-2.42-fhs-1.patch' saved [2804/2804]  
  
--2026-06-19 07:58:20--  https://www.linuxfromscratch.org/patches/lfs/12.4/kbd-2.8.0-backspace-1.patch  
Reusing existing connection to www.linuxfromscratch.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 12640 (12K)  
Saving to: '/mnt/lfs/sources/kbd-2.8.0-backspace-1.patch'  
  
kbd-2.8.0-backspace-1.patch  100%[==============================================>]  12.34K  --.-KB/s    in 0s         
  
2026-06-19 07:58:20 (94.6 MB/s) - '/mnt/lfs/sources/kbd-2.8.0-backspace-1.patch' saved [12640/12640]  
  
--2026-06-19 07:58:20--  https://www.linuxfromscratch.org/patches/lfs/12.4/sysvinit-3.14-consolidated-1.patch  
Reusing existing connection to www.linuxfromscratch.org:443.  
HTTP request sent, awaiting response... 200 OK  
Length: 2644 (2.6K)  
Saving to: '/mnt/lfs/sources/sysvinit-3.14-consolidated-1.patch'  
  
sysvinit-3.14-consolidated-1 100%[==============================================>]   2.58K  --.-KB/s    in 0s         
  
2026-06-19 07:58:20 (50.8 MB/s) - '/mnt/lfs/sources/sysvinit-3.14-consolidated-1.patch' saved [2644/2644]  
  
FINISHED --2026-06-19 07:58:20--  
Total wall clock time: 2m 57s  
Downloaded: 64 files, 349M in 1m 22s (4.27 MB/s)  
[lfs@artix sources]$
[lfs@artix sources]$ ls | wc -l  
du -sh .  
95  
578M    .  
[lfs@artix sources]$ wget https://www.linuxfromscratch.org/lfs/view/12.4/md5sums  
  
md5sum -c md5sums  
--2026-06-19 08:02:55--  https://www.linuxfromscratch.org/lfs/view/12.4/md5sums  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving www.linuxfromscratch.org (www.linuxfromscratch.org)... 208.118.68.85  
Connecting to www.linuxfromscratch.org (www.linuxfromscratch.org)|208.118.68.85|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 5179 (5.1K)  
Saving to: 'md5sums'  
  
md5sums                      100%[==============================================>]   5.06K  --.-KB/s    in 0s         
  
2026-06-19 08:02:57 (82.9 MB/s) - 'md5sums' saved [5179/5179]  
  
acl-2.3.2.tar.xz: OK  
attr-2.5.2.tar.gz: OK  
autoconf-2.72.tar.xz: OK  
automake-1.18.1.tar.xz: OK  
bash-5.3.tar.gz: OK  
bc-7.0.3.tar.xz: OK  
binutils-2.45.tar.xz: OK  
bison-3.8.2.tar.xz: OK  
bzip2-1.0.8.tar.gz: OK  
coreutils-9.7.tar.xz: OK  
dejagnu-1.6.3.tar.gz: OK  
diffutils-3.12.tar.xz: OK  
e2fsprogs-1.47.3.tar.gz: OK  
elfutils-0.193.tar.bz2: OK  
expat-2.7.1.tar.xz: OK  
expect5.45.4.tar.gz: OK  
file-5.46.tar.gz: OK  
findutils-4.10.0.tar.xz: OK  
flex-2.6.4.tar.gz: OK  
flit_core-3.12.0.tar.gz: OK  
gawk-5.3.2.tar.xz: OK  
gcc-15.2.0.tar.xz: OK  
gdbm-1.26.tar.gz: OK  
gettext-0.26.tar.xz: OK  
glibc-2.42.tar.xz: OK  
gmp-6.3.0.tar.xz: OK  
gperf-3.3.tar.gz: OK  
grep-3.12.tar.xz: OK  
groff-1.23.0.tar.gz: OK  
grub-2.12.tar.xz: OK  
gzip-1.14.tar.xz: OK  
iana-etc-20250807.tar.gz: OK  
inetutils-2.6.tar.xz: OK  
intltool-0.51.0.tar.gz: OK  
iproute2-6.16.0.tar.xz: OK  
jinja2-3.1.6.tar.gz: OK  
kbd-2.8.0.tar.xz: OK  
kmod-34.2.tar.xz: OK  
less-679.tar.gz: OK  
lfs-bootscripts-20250827.tar.xz: OK  
libcap-2.76.tar.xz: OK  
libffi-3.5.2.tar.gz: OK  
libpipeline-1.5.8.tar.gz: OK  
libtool-2.5.4.tar.xz: OK  
libxcrypt-4.4.38.tar.xz: OK  
linux-6.16.1.tar.xz: OK  
lz4-1.10.0.tar.gz: OK  
m4-1.4.20.tar.xz: OK  
make-4.4.1.tar.gz: OK  
man-db-2.13.1.tar.xz: OK  
man-pages-6.15.tar.xz: OK  
markupsafe-3.0.2.tar.gz: OK  
meson-1.8.3.tar.gz: OK  
mpc-1.3.1.tar.gz: OK  
mpfr-4.2.2.tar.xz: OK  
md5sum: ncurses-6.5-20250809.tgz: No such file or directory  
ncurses-6.5-20250809.tgz: FAILED open or read  
ninja-1.13.1.tar.gz: OK  
openssl-3.5.2.tar.gz: OK  
packaging-25.0.tar.gz: OK  
patch-2.8.tar.xz: OK  
perl-5.42.0.tar.xz: OK  
pkgconf-2.5.1.tar.xz: OK  
procps-ng-4.0.5.tar.xz: OK  
psmisc-23.7.tar.xz: OK  
Python-3.13.7.tar.xz: OK  
python-3.13.7-docs-html.tar.bz2: OK  
readline-8.3.tar.gz: OK  
sed-4.9.tar.xz: OK  
setuptools-80.9.0.tar.gz: OK  
shadow-4.18.0.tar.xz: OK  
sysklogd-2.7.2.tar.gz: OK  
systemd-257.8.tar.gz: OK  
systemd-man-pages-257.8.tar.xz: OK  
sysvinit-3.14.tar.xz: OK  
tar-1.35.tar.xz: OK  
tcl8.6.16-src.tar.gz: OK  
tcl8.6.16-html.tar.gz: OK  
texinfo-7.2.tar.xz: OK  
tzdata2025b.tar.gz: OK  
udev-lfs-20230818.tar.xz: OK  
util-linux-2.41.1.tar.xz: OK  
vim-9.1.1629.tar.gz: OK  
wheel-0.46.1.tar.gz: OK  
XML-Parser-2.47.tar.gz: OK  
xz-5.8.1.tar.xz: OK  
zlib-1.3.1.tar.gz: OK  
zstd-1.5.7.tar.gz: OK  
bzip2-1.0.8-install_docs-1.patch: OK  
coreutils-9.7-upstream_fix-1.patch: OK  
coreutils-9.7-i18n-1.patch: OK  
expect-5.45.4-gcc15-1.patch: OK  
glibc-2.42-fhs-1.patch: OK  
kbd-2.8.0-backspace-1.patch: OK  
sysvinit-3.14-consolidated-1.patch: OK  
md5sum: WARNING: 1 listed file could not be read  
[lfs@artix sources]$
[lfs@artix sources]$ cd $LFS/sources  
  
ls ncurses*  
ls: cannot access 'ncurses*': No such file or directory  
[lfs@artix sources]$ wget https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
--2026-06-19 08:05:20--  https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving invisible-mirror.net (invisible-mirror.net)... 107.180.113.177  
Connecting to invisible-mirror.net (invisible-mirror.net)|107.180.113.177|:443... connected.  
HTTP request sent, awaiting response... 404 Not Found  
2026-06-19 08:05:21 ERROR 404: Not Found.  
  
[lfs@artix sources]$ grep ncurses md5sums  
md5sum ncurses-6.5-20250809.tgz  
679987405412f970561cc85e1e6428a2  ncurses-6.5-20250809.tgz  
md5sum: ncurses-6.5-20250809.tgz: No such file or directory  
[lfs@artix sources]$ md5sum -c md5sums  
acl-2.3.2.tar.xz: OK  
attr-2.5.2.tar.gz: OK  
autoconf-2.72.tar.xz: OK  
automake-1.18.1.tar.xz: OK  
bash-5.3.tar.gz: OK  
bc-7.0.3.tar.xz: OK  
binutils-2.45.tar.xz: OK  
bison-3.8.2.tar.xz: OK  
bzip2-1.0.8.tar.gz: OK  
coreutils-9.7.tar.xz: OK  
dejagnu-1.6.3.tar.gz: OK  
diffutils-3.12.tar.xz: OK  
e2fsprogs-1.47.3.tar.gz: OK  
elfutils-0.193.tar.bz2: OK  
expat-2.7.1.tar.xz: OK  
expect5.45.4.tar.gz: OK  
file-5.46.tar.gz: OK  
findutils-4.10.0.tar.xz: OK  
flex-2.6.4.tar.gz: OK  
flit_core-3.12.0.tar.gz: OK  
gawk-5.3.2.tar.xz: OK  
gcc-15.2.0.tar.xz: OK  
gdbm-1.26.tar.gz: OK  
gettext-0.26.tar.xz: OK  
glibc-2.42.tar.xz: OK  
gmp-6.3.0.tar.xz: OK  
gperf-3.3.tar.gz: OK  
grep-3.12.tar.xz: OK  
groff-1.23.0.tar.gz: OK  
grub-2.12.tar.xz: OK  
gzip-1.14.tar.xz: OK  
iana-etc-20250807.tar.gz: OK  
inetutils-2.6.tar.xz: OK  
intltool-0.51.0.tar.gz: OK  
iproute2-6.16.0.tar.xz: OK  
jinja2-3.1.6.tar.gz: OK  
kbd-2.8.0.tar.xz: OK  
kmod-34.2.tar.xz: OK  
less-679.tar.gz: OK  
lfs-bootscripts-20250827.tar.xz: OK  
libcap-2.76.tar.xz: OK  
libffi-3.5.2.tar.gz: OK  
libpipeline-1.5.8.tar.gz: OK  
libtool-2.5.4.tar.xz: OK  
libxcrypt-4.4.38.tar.xz: OK  
linux-6.16.1.tar.xz: OK  
lz4-1.10.0.tar.gz: OK  
m4-1.4.20.tar.xz: OK  
make-4.4.1.tar.gz: OK  
man-db-2.13.1.tar.xz: OK  
man-pages-6.15.tar.xz: OK  
markupsafe-3.0.2.tar.gz: OK  
meson-1.8.3.tar.gz: OK  
mpc-1.3.1.tar.gz: OK  
mpfr-4.2.2.tar.xz: OK  
md5sum: ncurses-6.5-20250809.tgz: No such file or directory  
ncurses-6.5-20250809.tgz: FAILED open or read  
ninja-1.13.1.tar.gz: OK  
openssl-3.5.2.tar.gz: OK  
packaging-25.0.tar.gz: OK  
patch-2.8.tar.xz: OK  
perl-5.42.0.tar.xz: OK  
pkgconf-2.5.1.tar.xz: OK  
procps-ng-4.0.5.tar.xz: OK  
psmisc-23.7.tar.xz: OK  
Python-3.13.7.tar.xz: OK  
python-3.13.7-docs-html.tar.bz2: OK  
readline-8.3.tar.gz: OK  
sed-4.9.tar.xz: OK  
setuptools-80.9.0.tar.gz: OK  
shadow-4.18.0.tar.xz: OK  
sysklogd-2.7.2.tar.gz: OK  
systemd-257.8.tar.gz: OK  
systemd-man-pages-257.8.tar.xz: OK  
sysvinit-3.14.tar.xz: OK  
tar-1.35.tar.xz: OK  
tcl8.6.16-src.tar.gz: OK  
tcl8.6.16-html.tar.gz: OK  
texinfo-7.2.tar.xz: OK  
tzdata2025b.tar.gz: OK  
udev-lfs-20230818.tar.xz: OK  
util-linux-2.41.1.tar.xz: OK  
vim-9.1.1629.tar.gz: OK  
wheel-0.46.1.tar.gz: OK  
XML-Parser-2.47.tar.gz: OK  
xz-5.8.1.tar.xz: OK  
zlib-1.3.1.tar.gz: OK  
zstd-1.5.7.tar.gz: OK  
bzip2-1.0.8-install_docs-1.patch: OK  
coreutils-9.7-upstream_fix-1.patch: OK  
coreutils-9.7-i18n-1.patch: OK  
expect-5.45.4-gcc15-1.patch: OK  
glibc-2.42-fhs-1.patch: OK  
kbd-2.8.0-backspace-1.patch: OK  
sysvinit-3.14-consolidated-1.patch: OK  
md5sum: WARNING: 1 listed file could not be read  
[lfs@artix sources]$ ls ncurses*  
ls: cannot access 'ncurses*': No such file or directory  
[lfs@artix sources]$
[lfs@artix sources]$ ls ncurses*  
ls: cannot access 'ncurses*': No such file or directory  
[lfs@artix sources]$ grep ncurses wget-list-sysv  
https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
[lfs@artix sources]$ grep -i ncurses wget-list-sysv  
https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
[lfs@artix sources]$ wget "<the-url-from-wget-list-sysv>"  
Prepended http:// to '<the-url-from-wget-list-sysv>'  
--2026-06-19 08:06:50--  http://%3Cthe-url-from-wget-list-sysv%3E/  
Resolving <the-url-from-wget-list-sysv> (<the-url-from-wget-list-sysv>)... failed: Name or service not known.  
wget: unable to resolve host address '<the-url-from-wget-list-sysv>'  
[lfs@artix sources]$ grep -c '^' md5sums  
ls | wc -l  
94  
96  
[lfs@artix sources]$
[lfs@artix sources]$ wget -O - https://invisible-mirror.net/archives/ncurses/current/ | head -50  
--2026-06-19 08:08:14--  https://invisible-mirror.net/archives/ncurses/current/  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving invisible-mirror.net (invisible-mirror.net)... 107.180.113.177  
Connecting to invisible-mirror.net (invisible-mirror.net)|107.180.113.177|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: unspecified [text/html]  
Saving to: 'STDOUT'  
  
-                                [<=>                                            ]       0  --.-KB/s               <  
!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">  
<html>  
<head>  
 <title>Index of /archives/ncurses/current</title>  
</head>  
<body>  
<h1>Index of /archives/ncurses/current</h1>  
 <table>  
  <tr><th valign="top">&nbsp;</th><th><a href="?C=N;O=D">Name</a></th><th><a href="?C=M;O=A">Last modified</a></th>  
<th><a href="?C=S;O=A">Size</a></th><th><a href="?C=D;O=A">Description</a></th></tr>  
  <tr><th colspan="5"><hr></th></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="/archives/ncurses/">Parent Directory</a>       </td><td>&nbsp;</td><td  
align="right">  - </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20251230.tgz">ncurses-6.6-20251230..&gt;</a></td><td align=  
"right">2025-12-30 18:05  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20251230.tgz.asc">ncurses-6.6-20251230..&gt;</a></td><td al  
ign="right">2025-12-30 18:05  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20251231.tgz">ncurses-6.6-20251231..&gt;</a></td><td align=  
"right">2025-12-31 11:47  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20251231.tgz.asc">ncurses-6.6-20251231..&gt;</a></td><td al  
ign="right">2025-12-31 11:47  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260103.tgz">ncurses-6.6-20260103..&gt;</a></td><td align=  
"right">2026-01-03 18:54  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260103.tgz.asc">ncurses-6.6-20260103..&gt;</a></td><td al  
ign="right">2026-01-03 18:54  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260117.tgz">ncurses-6.6-20260117..&gt;</a></td><td align=  
"right">2026-01-17 18:35  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260117.tgz.asc">ncurses-6.6-20260117..&gt;</a></td><td al  
ign="right">2026-01-17 18:35  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260124.tgz">ncurses-6.6-20260124..&gt;</a></td><td align=  
"right">2026-01-24 19:06  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260124.tgz.asc">ncurses-6.6-20260124..&gt;</a></td><td al  
ign="right">2026-01-24 19:06  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260131.tgz">ncurses-6.6-20260131..&gt;</a></td><td align=  
"right">2026-01-31 15:51  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260131.tgz.asc">ncurses-6.6-20260131..&gt;</a></td><td al  
ign="right">2026-01-31 15:51  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260207.tgz">ncurses-6.6-20260207..&gt;</a></td><td align=  
"right">2026-02-07 17:16  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260207.tgz.asc">ncurses-6.6-20260207..&gt;</a></td><td al  
ign="right">2026-02-07 17:16  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260214.tgz">ncurses-6.6-20260214..&gt;</a></td><td align=  
"right">2026-02-14 18:41  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260214.tgz.asc">ncurses-6.6-20260214..&gt;</a></td><td al  
ign="right">2026-02-14 18:41  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260221.tgz">ncurses-6.6-20260221..&gt;</a></td><td align=  
"right">2026-02-21 19:22  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260221.tgz.asc">ncurses-6.6-20260221..&gt;</a></td><td al  
ign="right">2026-02-21 19:22  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260301.tgz">ncurses-6.6-20260301..&gt;</a></td><td align=  
"right">2026-03-01 17:26  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260301.tgz.asc">ncurses-6.6-20260301..&gt;</a></td><td al  
ign="right">2026-03-01 17:26  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260307.tgz">ncurses-6.6-20260307..&gt;</a></td><td align=  
"right">2026-03-07 17:35  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260307.tgz.asc">ncurses-6.6-20260307..&gt;</a></td><td al  
ign="right">2026-03-07 17:36  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260314.tgz">ncurses-6.6-20260314..&gt;</a></td><td align=  
"right">2026-03-14 16:35  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260314.tgz.asc">ncurses-6.6-20260314..&gt;</a></td><td al  
ign="right">2026-03-14 16:35  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260321.tgz">ncurses-6.6-20260321..&gt;</a></td><td align=  
"right">2026-03-21 16:57  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260321.tgz.asc">ncurses-6.6-20260321..&gt;</a></td><td al  
ign="right">2026-03-21 16:57  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260328.tgz">ncurses-6.6-20260328..&gt;</a></td><td align=  
"right">2026-03-28 17:42  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260328.tgz.asc">ncurses-6.6-20260328..&gt;</a></td><td al  
ign="right">2026-03-28 17:42  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260404.tgz">ncurses-6.6-20260404..&gt;</a></td><td align=  
"right">2026-04-04 16:10  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260404.tgz.asc">ncurses-6.6-20260404..&gt;</a></td><td al  
ign="right">2026-04-04 16:10  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260411.tgz">ncurses-6.6-20260411..&gt;</a></td><td align=  
"right">2026-04-11 17:16  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260411.tgz.asc">ncurses-6.6-20260411..&gt;</a></td><td al  
ign="right">2026-04-11 17:16  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260418.tgz">ncurses-6.6-20260418..&gt;</a></td><td align=  
"right">2026-04-18 17:07  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260418.tgz.asc">ncurses-6.6-20260418..&gt;</a></td><td al  
ign="right">2026-04-18 17:07  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260425.tgz">ncurses-6.6-20260425..&gt;</a></td><td align=  
"right">2026-04-25 17:52  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260425.tgz.asc">ncurses-6.6-20260425..&gt;</a></td><td al  
ign="right">2026-04-25 17:52  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260502.tgz">ncurses-6.6-20260502..&gt;</a></td><td align=  
"right">2026-05-02 16:34  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260502.tgz.asc">ncurses-6.6-20260502..&gt;</a></td><td al  
ign="right">2026-05-02 16:34  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
-                                [ <=>                                           ]   7.95K  39.0KB/s               <  
tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260509.tgz">ncurses-6.6-20260509..&gt;</a></td><td align="  
right">2026-05-09 17:58  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
-                                [  <=>                                          ]  15.82K  77.5KB/s    in 0.2s       
  
  
Cannot write to '-' (Broken pipe).  
[lfs@artix sources]$ curl https://invisible-mirror.net/archives/ncurses/current/ | grep ncurses  
 % Total    % Received % Xferd  Average Speed  Time    Time    Time   Current  
                                Dload  Upload  Total   Spent   Left   Speed  
100  18659   0  18659   0    <title>Index of /archives/ncurses/current</title>  
 <h1>Index of /archives/ncurses/current</h1>  
 <tr><td valign="top">&nbsp;</td><td><a href="/archives/ncurses/">Parent Directory</a>       </td><td>&nbsp;</td><t  
d align="right">  - </td><td>&nbsp;</td></tr>  
0  <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20251230.tgz">ncurses-6.6-20251230..&gt;</a></td><td ali  
gn="right">2025-12-30 18:05  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
170<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20251230.tgz.asc">ncurses-6.6-20251230..&gt;</a></td><td  
align="right">2025-12-30 18:05  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
90 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20251231.tgz">ncurses-6.6-20251231..&gt;</a></td><td ali  
gn="right">2025-12-31 11:47  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
  <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20251231.tgz.asc">ncurses-6.6-20251231..&gt;</a></td><td  
align="right">2025-12-31 11:47  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260103.tgz">ncurses-6.6-20260103..&gt;</a></td><td ali  
gn="right">2026-01-03 18:54  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
  <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260103.tgz.asc">ncurses-6.6-20260103..&gt;</a></td><td  
align="right">2026-01-03 18:54  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
  <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260117.tgz">ncurses-6.6-20260117..&gt;</a></td><td ali  
gn="right">2026-01-17 18:35  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
  <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260117.tgz.asc">ncurses-6.6-20260117..&gt;</a></td><td  
align="right">2026-01-17 18:35  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260124.tgz">ncurses-6.6-20260124..&gt;</a></td><td ali  
gn="right">2026-01-24 19:06  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
0:0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260124.tgz.asc">ncurses-6.6-20260124..&gt;</a></td><td  
align="right">2026-01-24 19:06  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
1 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260131.tgz">ncurses-6.6-20260131..&gt;</a></td><td alig  
n="right">2026-01-31 15:51  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260131.tgz.asc">ncurses-6.6-20260131..&gt;</a></td><td  
align="right">2026-01-31 15:51  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260207.tgz">ncurses-6.6-20260207..&gt;</a></td><td alig  
n="right">2026-02-07 17:16  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260207.tgz.asc">ncurses-6.6-20260207..&gt;</a></td><td  
align="right">2026-02-07 17:16  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260214.tgz">ncurses-6.6-20260214..&gt;</a></td><td alig  
n="right">2026-02-14 18:41  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260214.tgz.asc">ncurses-6.6-20260214..&gt;</a></td><td  
align="right">2026-02-14 18:41  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260221.tgz">ncurses-6.6-20260221..&gt;</a></td><td alig  
n="right">2026-02-21 19:22  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260221.tgz.asc">ncurses-6.6-20260221..&gt;</a></td><td  
align="right">2026-02-21 19:22  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260301.tgz">ncurses-6.6-20260301..&gt;</a></td><td align=  
"right">2026-03-01 17:26  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
1<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260301.tgz.asc">ncurses-6.6-20260301..&gt;</a></td><td a  
lign="right">2026-03-01 17:26  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
00<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260307.tgz">ncurses-6.6-20260307..&gt;</a></td><td alig  
n="right">2026-03-07 17:35  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260307.tgz.asc">ncurses-6.6-20260307..&gt;</a></td><td  
align="right">2026-03-07 17:36  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
186<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260314.tgz">ncurses-6.6-20260314..&gt;</a></td><td ali  
gn="right">2026-03-14 16:35  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
59<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260314.tgz.asc">ncurses-6.6-20260314..&gt;</a></td><td  
align="right">2026-03-14 16:35  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260321.tgz">ncurses-6.6-20260321..&gt;</a></td><td alig  
n="right">2026-03-21 16:57  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260321.tgz.asc">ncurses-6.6-20260321..&gt;</a></td><td  
align="right">2026-03-21 16:57  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260328.tgz">ncurses-6.6-20260328..&gt;</a></td><td alig  
n="right">2026-03-28 17:42  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
18<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260328.tgz.asc">ncurses-6.6-20260328..&gt;</a></td><td  
align="right">2026-03-28 17:42  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
65<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260404.tgz">ncurses-6.6-20260404..&gt;</a></td><td alig  
n="right">2026-04-04 16:10  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
9 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260404.tgz.asc">ncurses-6.6-20260404..&gt;</a></td><td  
align="right">2026-04-04 16:10  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260411.tgz">ncurses-6.6-20260411..&gt;</a></td><td align  
="right">2026-04-11 17:16  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260411.tgz.asc">ncurses-6.6-20260411..&gt;</a></td><td a  
lign="right">2026-04-11 17:16  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
0 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260418.tgz">ncurses-6.6-20260418..&gt;</a></td><td alig  
n="right">2026-04-18 17:07  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260418.tgz.asc">ncurses-6.6-20260418..&gt;</a></td><td  
align="right">2026-04-18 17:07  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260425.tgz">ncurses-6.6-20260425..&gt;</a></td><td alig  
n="right">2026-04-25 17:52  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260425.tgz.asc">ncurses-6.6-20260425..&gt;</a></td><td  
align="right">2026-04-25 17:52  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260502.tgz">ncurses-6.6-20260502..&gt;</a></td><td alig  
n="right">2026-05-02 16:34  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
17<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260502.tgz.asc">ncurses-6.6-20260502..&gt;</a></td><td  
align="right">2026-05-02 16:34  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
08<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260509.tgz">ncurses-6.6-20260509..&gt;</a></td><td alig  
n="right">2026-05-09 17:58  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
2 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260509.tgz.asc">ncurses-6.6-20260509..&gt;</a></td><td  
align="right">2026-05-09 17:58  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260516.tgz">ncurses-6.6-20260516..&gt;</a></td><td alig  
n="right">2026-05-16 18:15  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260516.tgz.asc">ncurses-6.6-20260516..&gt;</a></td><td  
align="right">2026-05-16 18:15  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260523.tgz">ncurses-6.6-20260523..&gt;</a></td><td alig  
n="right">2026-05-23 17:08  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260523.tgz.asc">ncurses-6.6-20260523..&gt;</a></td><td  
align="right">2026-05-23 17:08  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260530.tgz">ncurses-6.6-20260530..&gt;</a></td><td alig  
n="right">2026-05-30 18:12  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260530.tgz.asc">ncurses-6.6-20260530..&gt;</a></td><td a  
lign="right">2026-05-30 18:12  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260606.tgz">ncurses-6.6-20260606..&gt;</a></td><td alig  
n="right">2026-06-06 17:51  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260606.tgz.asc">ncurses-6.6-20260606..&gt;</a></td><td  
align="right">2026-06-06 17:51  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260607.tgz">ncurses-6.6-20260607..&gt;</a></td><td align  
="right">2026-06-07 02:11  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260607.tgz.asc">ncurses-6.6-20260607..&gt;</a></td><td  
align="right">2026-06-07 02:11  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
0:<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260608.tgz">ncurses-6.6-20260608..&gt;</a></td><td alig  
n="right">2026-06-08 17:37  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
01<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260608.tgz.asc">ncurses-6.6-20260608..&gt;</a></td><td  
align="right">2026-06-08 17:37  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260613.tgz">ncurses-6.6-20260613..&gt;</a></td><td alig  
n="right">2026-06-13 18:06  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6-20260613.tgz.asc">ncurses-6.6-20260613..&gt;</a></td><td  
align="right">2026-06-13 18:06  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
 <tr><td valign="top">&nbsp;</td><td><a href="ncurses.tar.gz">ncurses.tar.gz</a>         </td><td align="right">202  
6-06-13 18:06  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
100  18659   0  18659   0      0  17073      0           00:01              0  
[lfs@artix sources]$ wget https://invisible-mirror.net/archives/ncurses/current/ncurses.tar.gz  
--2026-06-19 08:08:30--  https://invisible-mirror.net/archives/ncurses/current/ncurses.tar.gz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving invisible-mirror.net (invisible-mirror.net)... 107.180.113.177  
Connecting to invisible-mirror.net (invisible-mirror.net)|107.180.113.177|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 3806741 (3.6M) [application/x-gzip]  
Saving to: 'ncurses.tar.gz'  
  
ncurses.tar.gz               100%[==============================================>]   3.63M   914KB/s    in 4.8s       
  
2026-06-19 08:08:36 (782 KB/s) - 'ncurses.tar.gz' saved [3806741/3806741]  
  
[lfs@artix sources]$ wget https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5.tar.gz  
--2026-06-19 08:08:41--  https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5.tar.gz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving invisible-mirror.net (invisible-mirror.net)... 107.180.113.177  
Connecting to invisible-mirror.net (invisible-mirror.net)|107.180.113.177|:443... connected.  
HTTP request sent, awaiting response... 404 Not Found  
2026-06-19 08:08:42 ERROR 404: Not Found.  
  
[lfs@artix sources]$ wget https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5.tar.gz  
--2026-06-19 08:08:57--  https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5.tar.gz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving invisible-mirror.net (invisible-mirror.net)... 107.180.113.177  
Connecting to invisible-mirror.net (invisible-mirror.net)|107.180.113.177|:443... connected.  
HTTP request sent, awaiting response... 404 Not Found  
2026-06-19 08:08:58 ERROR 404: Not Found.  
  
[lfs@artix sources]$ ls -lh ncurses*  
-rw-r--r-- 1 lfs lfs 3.7M Jun 14 03:06 ncurses.tar.gz  
[lfs@artix sources]$
[lfs@artix sources]$ ls -lh ncurses*  
-rw-r--r-- 1 lfs lfs 3.7M Jun 14 03:06 ncurses.tar.gz  
[lfs@artix sources]$ md5sum -c md5sums 2>&1 | grep FAILED  
ncurses-6.5-20250809.tgz: FAILED open or read  
[lfs@artix sources]$ comm -23 \  
 <(awk '{print $2}' md5sums | sort) \  
 <(ls | sort)  
ncurses-6.5-20250809.tgz  
[lfs@artix sources]$ comm -23 \  
 <(awk '{print $2}' md5sums | sort) \  
 <(ls | sort)  
ncurses-6.5-20250809.tgz  
[lfs@artix sources]$
[lfs@artix sources]$ mv ncurses.tar.gz ncurses-6.6-20250809.tgz  
[lfs@artix sources]$ md5sum ncurses-6.6-20250809.tgz  
b68bc977902f398198a55dc7366f7ffd  ncurses-6.6-20250809.tgz  
[lfs@artix sources]$ md5sum -c md5sums 2>&1 | grep FAILED  
ncurses-6.5-20250809.tgz: FAILED open or read  
[lfs@artix sources]$ md5sum -c md5sums 2>&1 | grep FAILEDcomm -23 \  
 <(awk '{print $2}' md5sums | sort) \  
 <(ls | sort)  
[lfs@artix sources]$[lfs@artix sources]$ tar -tf ncurses-6.6-20250809.tgz | head  
ncurses-6.6-20260613/  
ncurses-6.6-20260613/Ada95/  
ncurses-6.6-20260613/Ada95/make-tar.sh  
ncurses-6.6-20260613/Ada95/configure.in  
ncurses-6.6-20260613/Ada95/mk-1st.awk  
ncurses-6.6-20260613/Ada95/doc/  
ncurses-6.6-20260613/Ada95/doc/Makefile.in  
ncurses-6.6-20260613/Ada95/mk-pkg.awk  
ncurses-6.6-20260613/Ada95/TODO  
ncurses-6.6-20260613/Ada95/package/  
[lfs@artix sources]$ grep ncurses wget-list-sysv  
https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
[lfs@artix sources]$ curl -L -O https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
 % Total    % Received % Xferd  Average Speed  Time    Time    Time   Current  
                                Dload  Upload  Total   Spent   Left   Speed  
100    355 100    355   0      0    399      0                              0  
[lfs@artix sources]$
[lfs@artix sources]$ ls -lh ncurses-6.5-20250809.tgz  
file ncurses-6.5-20250809.tgz  
head ncurses-6.5-20250809.tgz  
-rw-r--r-- 1 lfs lfs 355 Jun 19 08:15 ncurses-6.5-20250809.tgz  
ncurses-6.5-20250809.tgz: HTML document, ASCII text  
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">  
<html><head>  
<title>404 Not Found</title>  
</head><body>  
<h1>Not Found</h1>  
<p>The requested URL was not found on this server.</p>  
<p>Additionally, a 404 Not Found  
error was encountered while trying to use an ErrorDocument to handle the request.</p>  
</body></html>  
[lfs@artix sources]$ curl -I https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
HTTP/2 404    
content-type: text/html; charset=iso-8859-1  
date: Fri, 19 Jun 2026 06:16:38 GMT  
server: Apache  
  
[lfs@artix sources]$ curl -I https://invisible-mirror.net/archives/ncurses/  
HTTP/2 200    
content-type: text/html;charset=ISO-8859-1  
date: Fri, 19 Jun 2026 06:16:48 GMT  
server: Apache  
  
[lfs@artix sources]$ ls -lh ncurses-6.5-20250809.tgz  
-rw-r--r-- 1 lfs lfs 355 Jun 19 08:15 ncurses-6.5-20250809.tgz  
[lfs@artix sources]$
[lfs@artix sources]$ ls -lh ncurses-6.5-20250809.tgz  
file ncurses-6.5-20250809.tgz  
head ncurses-6.5-20250809.tgz  
-rw-r--r-- 1 lfs lfs 355 Jun 19 08:15 ncurses-6.5-20250809.tgz  
ncurses-6.5-20250809.tgz: HTML document, ASCII text  
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">  
<html><head>  
<title>404 Not Found</title>  
</head><body>  
<h1>Not Found</h1>  
<p>The requested URL was not found on this server.</p>  
<p>Additionally, a 404 Not Found  
error was encountered while trying to use an ErrorDocument to handle the request.</p>  
</body></html>  
[lfs@artix sources]$ curl -I https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
HTTP/2 404    
content-type: text/html; charset=iso-8859-1  
date: Fri, 19 Jun 2026 06:16:38 GMT  
server: Apache  
  
[lfs@artix sources]$ curl -I https://invisible-mirror.net/archives/ncurses/  
HTTP/2 200    
content-type: text/html;charset=ISO-8859-1  
date: Fri, 19 Jun 2026 06:16:48 GMT  
server: Apache  
  
[lfs@artix sources]$ ls -lh ncurses-6.5-20250809.tgz  
-rw-r--r-- 1 lfs lfs 355 Jun 19 08:15 ncurses-6.5-20250809.tgz  
[lfs@artix sources]$ curl https://invisible-mirror.net/archives/ncurses/ | grep 20250809  
 % Total    % Received % Xferd  Average Speed  Time    Time    Time   Current  
                                Dload  Upload  Total   Spent   Left   Speed  
100  11418   0  11418   0      0  12410      0                              0  
[lfs@artix sources]$ curl https://invisible-mirror.net/archives/ncurses/ | grep ncurses-6.5 | tail  
 % Total    % Received % Xferd  Average Speed  Time    Time    Time   Current  
                                Dload  Upload  Total   Spent   Left   Speed  
100  11418   0  11418   0      0  11252      0           00:01              0  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5.tar.gz">ncurses-6.5.tar.gz</a>     </td><td align="right">2  
024-04-27 14:31  </td><td align="right">3.5M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5.tar.gz.asc">ncurses-6.5.tar.gz.asc</a> </td><td align="righ  
t">2024-04-27 14:42  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
[lfs@artix sources]$ curl https://invisible-mirror.net/archives/ncurses/ | grep 2025  
 % Total    % Received % Xferd  Average Speed  Time    Time    Time   Current  
                                Dload  Upload  Total   Spent   Left   Speed  
100  11418   0  11418  <tr><td valign="top">&nbsp;</td><td><a href="6.5/">6.5/</a>                   </td><td align=  
"right">2025-12-27 18:41  </td><td align="right">  - </td><td>&nbsp;</td></tr>  
0<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6.tar.gz">ncurses-6.6.tar.gz</a>     </td><td align="right"  
>2025-12-30 16:24  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.6.tar.gz.asc">ncurses-6.6.tar.gz.asc</a> </td><td align="rig  
ht">2025-12-31 02:49  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses.tar.gz">ncurses.tar.gz</a>         </td><td align="right">2025  
-12-30 16:24  </td><td align="right">3.6M</td><td>&nbsp;</td></tr>  
100  11418   0  11418   0      0   6108      0           00:01              0  
<tr><td valign="top">&nbsp;</td><td><a href="tack-1.11.tgz">tack-1.11.tgz</a>          </td><td align="right">2025-0  
5-03 15:52  </td><td align="right">257K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="tack-1.11.tgz.asc">tack-1.11.tgz.asc</a>      </td><td align="right">20  
25-05-03 15:52  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="tack.tar.gz">tack.tar.gz</a>            </td><td align="right">2025-05-  
03 15:52  </td><td align="right">257K</td><td>&nbsp;</td></tr>  
[lfs@artix sources]$ rm ncurses-6.5-20250809.tgz  
[lfs@artix sources]$ mv ncurses-6.6-20250809.tgz ncurses-6.6-20260613.tgz  
[lfs@artix sources]$[lfs@artix sources]$ rm ncurses-6.5-20250809.tgz  
[lfs@artix sources]$ mv ncurses-6.6-20250809.tgz ncurses-6.6-20260613.tgz  
[lfs@artix sources]$ curl https://invisible-mirror.net/archives/ncurses/6.5/ | grep 20250809  
 % Total    % Received % Xferd  Average Speed  Time    Time    Time   Current  
                                Dload  Upload  Total   Spent   Left   Speed  
 0      0   0      0   0      0      0      0                              0<tr><td valign="top">&nbsp;</td><td><a  
href="ncurses-6.5-20250809.patch.gz">ncurses-6.5-20250809..&gt;</a></td><td align="right">2025-08-09 17:46  </td><td  
align="right"> 46K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20250809.patch.gz.asc">ncurses-6.5-20250809..&gt;</a></td><  
td align="right">2025-08-09 17:46  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
100  34976   0  34976   0      0  31121      0           00:01              0  
[lfs@artix sources]$ curl https://invisible-mirror.net/archives/ncurses/6.5/ | tail -30  
 % Total    % Received % Xferd  Average Speed  Time    Time    Time   Current  
                                Dload  Upload  Total   Spent   Left   Speed  
100  34976   0  34976   0      0  32218      0           00:01              0  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20250927.patch.gz.asc">ncurses-6.5-20250927..&gt;</a></td><  
td align="right">2025-09-27 18:19  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251004.patch.gz">ncurses-6.5-20251004..&gt;</a></td><td a  
lign="right">2025-10-04 16:58  </td><td align="right">199K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251004.patch.gz.asc">ncurses-6.5-20251004..&gt;</a></td><  
td align="right">2025-10-04 16:58  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251010.patch.gz">ncurses-6.5-20251010..&gt;</a></td><td a  
lign="right">2025-10-10 03:15  </td><td align="right">202K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251010.patch.gz.asc">ncurses-6.5-20251010..&gt;</a></td><  
td align="right">2025-10-10 03:17  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251018.patch.gz">ncurses-6.5-20251018..&gt;</a></td><td a  
lign="right">2025-10-18 17:58  </td><td align="right">158K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251018.patch.gz.asc">ncurses-6.5-20251018..&gt;</a></td><  
td align="right">2025-10-18 17:59  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251025.patch.gz">ncurses-6.5-20251025..&gt;</a></td><td a  
lign="right">2025-10-25 17:38  </td><td align="right"> 14K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251025.patch.gz.asc">ncurses-6.5-20251025..&gt;</a></td><  
td align="right">2025-10-25 17:38  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251101.patch.gz">ncurses-6.5-20251101..&gt;</a></td><td a  
lign="right">2025-11-01 18:30  </td><td align="right"> 17K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251101.patch.gz.asc">ncurses-6.5-20251101..&gt;</a></td><  
td align="right">2025-11-01 18:30  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251115.patch.gz">ncurses-6.5-20251115..&gt;</a></td><td a  
lign="right">2025-11-15 19:23  </td><td align="right"> 42K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251115.patch.gz.asc">ncurses-6.5-20251115..&gt;</a></td><  
td align="right">2025-11-15 19:23  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251122.patch.gz">ncurses-6.5-20251122..&gt;</a></td><td a  
lign="right">2025-11-22 17:33  </td><td align="right">4.9K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251122.patch.gz.asc">ncurses-6.5-20251122..&gt;</a></td><  
td align="right">2025-11-22 17:33  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251123.patch.gz">ncurses-6.5-20251123..&gt;</a></td><td a  
lign="right">2025-11-23 15:17  </td><td align="right">3.5K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251123.patch.gz.asc">ncurses-6.5-20251123..&gt;</a></td><  
td align="right">2025-11-23 15:17  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251129.patch.gz">ncurses-6.5-20251129..&gt;</a></td><td a  
lign="right">2025-11-29 17:54  </td><td align="right">3.4K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251129.patch.gz.asc">ncurses-6.5-20251129..&gt;</a></td><  
td align="right">2025-11-29 17:54  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251206.patch.gz">ncurses-6.5-20251206..&gt;</a></td><td a  
lign="right">2025-12-06 18:10  </td><td align="right"> 19K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251206.patch.gz.asc">ncurses-6.5-20251206..&gt;</a></td><  
td align="right">2025-12-06 18:10  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251213.patch.gz">ncurses-6.5-20251213..&gt;</a></td><td a  
lign="right">2025-12-13 18:28  </td><td align="right">3.4K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251213.patch.gz.asc">ncurses-6.5-20251213..&gt;</a></td><  
td align="right">2025-12-13 18:28  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251220.patch.gz">ncurses-6.5-20251220..&gt;</a></td><td a  
lign="right">2025-12-20 19:05  </td><td align="right"> 46K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251220.patch.gz.asc">ncurses-6.5-20251220..&gt;</a></td><  
td align="right">2025-12-20 19:06  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251227.patch.gz">ncurses-6.5-20251227..&gt;</a></td><td a  
lign="right">2025-12-27 18:41  </td><td align="right">223K</td><td>&nbsp;</td></tr>  
<tr><td valign="top">&nbsp;</td><td><a href="ncurses-6.5-20251227.patch.gz.asc">ncurses-6.5-20251227..&gt;</a></td><  
td align="right">2025-12-27 18:41  </td><td align="right">729 </td><td>&nbsp;</td></tr>  
  <tr><th colspan="5"><hr></th></tr>  
</table>  
</body></html>  
[lfs@artix sources]$ wget https://invisible-mirror.net/archives/ncurses/ncurses-6.5.tar.gz  
--2026-06-19 08:24:07--  https://invisible-mirror.net/archives/ncurses/ncurses-6.5.tar.gz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving invisible-mirror.net (invisible-mirror.net)... 107.180.113.177  
Connecting to invisible-mirror.net (invisible-mirror.net)|107.180.113.177|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 3688489 (3.5M) [application/x-gzip]  
Saving to: 'ncurses-6.5.tar.gz'  
  
ncurses-6.5.tar.gz           100%[==============================================>]   3.52M  2.20MB/s    in 1.6s       
  
2026-06-19 08:24:10 (2.20 MB/s) - 'ncurses-6.5.tar.gz' saved [3688489/3688489]  
  
[lfs@artix sources]$
[lfs@artix sources]$ tar -tf ncurses-6.5.tar.gz | head  
ncurses-6.5/  
ncurses-6.5/announce.html.in  
ncurses-6.5/misc/  
ncurses-6.5/configure  
ncurses-6.5/package/  
ncurses-6.5/dist.mk  
ncurses-6.5/AUTHORS  
ncurses-6.5/NEWS  
ncurses-6.5/README  
ncurses-6.5/README.emx  
[lfs@artix sources]$ rm ncurses-6.6-20260613.tgz  
rm ncurses-6.5-20250809.tgz  
rm: cannot remove 'ncurses-6.5-20250809.tgz': No such file or directory  
[lfs@artix sources]$ ncurses-6.5.tar.gz  
bash: ncurses-6.5.tar.gz: command not found  
[lfs@artix sources]$ grep -R "20250809" .  
./md5sums:679987405412f970561cc85e1e6428a2  ncurses-6.5-20250809.tgz  
./wget-list-sysv:https://invisible-mirror.net/archives/ncurses/current/ncurses-6.5-20250809.tgz  
./wget-list-sysv.bak:htt

[lfs@artix sources]$ cd $LFS/sources  
  
rm -f ncurses-6.5-20250809.tgz  
  
wget https://ftp.lfs-matrix.net/pub/lfs/lfs-packages/12.4/ncurses-6.5-20250809.tgz  
--2026-06-19 08:38:33--  https://ftp.lfs-matrix.net/pub/lfs/lfs-packages/12.4/ncurses-6.5-20250809.tgz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving ftp.lfs-matrix.net (ftp.lfs-matrix.net)... 208.113.130.205  
Connecting to ftp.lfs-matrix.net (ftp.lfs-matrix.net)|208.113.130.205|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 3790967 (3.6M) [application/x-gzip]  
Saving to: 'ncurses-6.5-20250809.tgz'  
  
ncurses-6.5-20250809.tgz     100%[==============================================>]   3.62M  2.56MB/s    in 1.4s       
  
2026-06-19 08:38:36 (2.56 MB/s) - 'ncurses-6.5-20250809.tgz' saved [3790967/3790967]  
  
[lfs@artix sources]$
[lfs@artix sources]$ rm ncurses-6.5-20250809.tgz  
rm: cannot remove 'ncurses-6.5-20250809.tgz': No such file or directory  
[lfs@artix sources]$ cd $LFS/sources  
  
rm -f ncurses-6.5-20250809.tgz  
  
wget https://ftp.lfs-matrix.net/pub/lfs/lfs-packages/12.4/ncurses-6.5-20250809.tgz  
--2026-06-19 08:38:33--  https://ftp.lfs-matrix.net/pub/lfs/lfs-packages/12.4/ncurses-6.5-20250809.tgz  
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'  
Resolving ftp.lfs-matrix.net (ftp.lfs-matrix.net)... 208.113.130.205  
Connecting to ftp.lfs-matrix.net (ftp.lfs-matrix.net)|208.113.130.205|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 3790967 (3.6M) [application/x-gzip]  
Saving to: 'ncurses-6.5-20250809.tgz'  
  
ncurses-6.5-20250809.tgz     100%[==============================================>]   3.62M  2.56MB/s    in 1.4s       
  
2026-06-19 08:38:36 (2.56 MB/s) - 'ncurses-6.5-20250809.tgz' saved [3790967/3790967]  
  
[lfs@artix sources]$ md5sum ncurses-6.5-20250809.tgz  
679987405412f970561cc85e1e6428a2  ncurses-6.5-20250809.tgz  
[lfs@artix sources]$ md5sum -c md5sums  
acl-2.3.2.tar.xz: OK  
attr-2.5.2.tar.gz: OK  
autoconf-2.72.tar.xz: OK  
automake-1.18.1.tar.xz: OK  
bash-5.3.tar.gz: OK  
bc-7.0.3.tar.xz: OK  
binutils-2.45.tar.xz: OK  
bison-3.8.2.tar.xz: OK  
bzip2-1.0.8.tar.gz: OK  
coreutils-9.7.tar.xz: OK  
dejagnu-1.6.3.tar.gz: OK  
diffutils-3.12.tar.xz: OK  
e2fsprogs-1.47.3.tar.gz: OK  
elfutils-0.193.tar.bz2: OK  
expat-2.7.1.tar.xz: OK  
expect5.45.4.tar.gz: OK  
file-5.46.tar.gz: OK  
findutils-4.10.0.tar.xz: OK  
flex-2.6.4.tar.gz: OK  
flit_core-3.12.0.tar.gz: OK  
gawk-5.3.2.tar.xz: OK  
gcc-15.2.0.tar.xz: OK  
gdbm-1.26.tar.gz: OK  
gettext-0.26.tar.xz: OK  
glibc-2.42.tar.xz: OK  
gmp-6.3.0.tar.xz: OK  
gperf-3.3.tar.gz: OK  
grep-3.12.tar.xz: OK  
groff-1.23.0.tar.gz: OK  
grub-2.12.tar.xz: OK  
gzip-1.14.tar.xz: OK  
iana-etc-20250807.tar.gz: OK  
inetutils-2.6.tar.xz: OK  
intltool-0.51.0.tar.gz: OK  
iproute2-6.16.0.tar.xz: OK  
jinja2-3.1.6.tar.gz: OK  
kbd-2.8.0.tar.xz: OK  
kmod-34.2.tar.xz: OK  
less-679.tar.gz: OK  
lfs-bootscripts-20250827.tar.xz: OK  
libcap-2.76.tar.xz: OK  
libffi-3.5.2.tar.gz: OK  
libpipeline-1.5.8.tar.gz: OK  
libtool-2.5.4.tar.xz: OK  
libxcrypt-4.4.38.tar.xz: OK  
linux-6.16.1.tar.xz: OK  
lz4-1.10.0.tar.gz: OK  
m4-1.4.20.tar.xz: OK  
make-4.4.1.tar.gz: OK  
man-db-2.13.1.tar.xz: OK  
man-pages-6.15.tar.xz: OK  
markupsafe-3.0.2.tar.gz: OK  
meson-1.8.3.tar.gz: OK  
mpc-1.3.1.tar.gz: OK  
mpfr-4.2.2.tar.xz: OK  
ncurses-6.5-20250809.tgz: OK  
ninja-1.13.1.tar.gz: OK  
openssl-3.5.2.tar.gz: OK  
packaging-25.0.tar.gz: OK  
patch-2.8.tar.xz: OK  
perl-5.42.0.tar.xz: OK  
pkgconf-2.5.1.tar.xz: OK  
procps-ng-4.0.5.tar.xz: OK  
psmisc-23.7.tar.xz: OK  
Python-3.13.7.tar.xz: OK  
python-3.13.7-docs-html.tar.bz2: OK  
readline-8.3.tar.gz: OK  
sed-4.9.tar.xz: OK  
setuptools-80.9.0.tar.gz: OK  
shadow-4.18.0.tar.xz: OK  
sysklogd-2.7.2.tar.gz: OK  
systemd-257.8.tar.gz: OK  
systemd-man-pages-257.8.tar.xz: OK  
sysvinit-3.14.tar.xz: OK  
tar-1.35.tar.xz: OK  
tcl8.6.16-src.tar.gz: OK  
tcl8.6.16-html.tar.gz: OK  
texinfo-7.2.tar.xz: OK  
tzdata2025b.tar.gz: OK  
udev-lfs-20230818.tar.xz: OK  
util-linux-2.41.1.tar.xz: OK  
vim-9.1.1629.tar.gz: OK  
wheel-0.46.1.tar.gz: OK  
XML-Parser-2.47.tar.gz: OK  
xz-5.8.1.tar.xz: OK  
zlib-1.3.1.tar.gz: OK  
zstd-1.5.7.tar.gz: OK  
bzip2-1.0.8-install_docs-1.patch: OK  
coreutils-9.7-upstream_fix-1.patch: OK  
coreutils-9.7-i18n-1.patch: OK  
expect-5.45.4-gcc15-1.patch: OK  
glibc-2.42-fhs-1.patch: OK  
kbd-2.8.0-backspace-1.patch: OK  
sysvinit-3.14-consolidated-1.patch: OK  
[lfs@artix sources]$

What happened is wonderfully typical of LFS: the book referenced a file that disappeared from the upstream ncurses site, because it was a specific snapshot tarball. The URL in `wget-list-sysv` became stale, so you spent a while chasing ghosts through mirrors, HTML 404 pages disguised as downloads, and a completely unrelated ncurses 6.6 snapshot.

[lfs@artix sources]$ md5sum -c md5sums | grep -v OK  
[lfs@artix sources]$
[lfs@artix sources]$ pwd  
ls $LFS  
/mnt/lfs/sources  
bin  etc  lib  lost+found  sbin  sources  tools  usr  var  
[lfs@artix sources]$ echo $LFS  
whoami  
/mnt/lfs  
lfs  
[lfs@artix sources]$
[lfs@artix sources]$ pwd  
ls $LFS  
/mnt/lfs/sources  
bin  etc  lib  lost+found  sbin  sources  tools  usr  var  
[lfs@artix sources]$ echo $LFS  
whoami  
/mnt/lfs  
lfs  
[lfs@artix sources]$ mkdir -pv $LFS/{etc,var} $LFS/usr/{bin,lib,sbin}  
  
for i in bin lib sbin; do  
   ln -sv usr/$i $LFS/$i  
done  
  
case $(uname -m) in  
   x86_64) mkdir -pv $LFS/lib64 ;;  
esac  
  
mkdir -pv $LFS/tools  
'/mnt/lfs/bin/bin' -> 'usr/bin'  
'/mnt/lfs/lib/lib' -> 'usr/lib'  
'/mnt/lfs/sbin/sbin' -> 'usr/sbin'  
mkdir: cannot create directory '/mnt/lfs/lib64': Permission denied  
[lfs@artix sources]$ chown -v lfs $LFS/{usr{,/*},var,etc,tools}  
  
case $(uname -m) in  
   x86_64) chown -v lfs $LFS/lib64 ;;  
esac  
ownership of '/mnt/lfs/usr' retained as lfs  
ownership of '/mnt/lfs/usr/bin' retained as lfs  
ownership of '/mnt/lfs/usr/lib' retained as lfs  
ownership of '/mnt/lfs/usr/sbin' retained as lfs  
ownership of '/mnt/lfs/var' retained as lfs  
ownership of '/mnt/lfs/etc' retained as lfs  
ownership of '/mnt/lfs/tools' retained as lfs  
chown: cannot access '/mnt/lfs/lib64': No such file or directory  
failed to change ownership of '/mnt/lfs/lib64' to lfs  
[lfs@artix sources]$ su - lfs  
Password:    
[lfs@artix ~]$ export MAKEFLAGS=-j$(nproc)  
[lfs@artix ~]$ ls /etc/bash.bashrc  
ls: cannot access '/etc/bash.bashrc': No such file or directory  
[lfs@artix ~]$ mv -v /etc/bash.bashrc /etc/bash.bashrc.NOUSE  
mv: cannot stat '/etc/bash.bashrc': No such file or directory  
[lfs@artix ~]$ source ~/.bash_profile  
[lfs@artix ~]$ echo $LFS  
echo $LFS_TGT  
echo $PATH  
/mnt/lfs  
x86_64-lfs-linux-gnu  
/mnt/lfs/tools/bin:/usr/bin  
[lfs@artix ~]$ whoami  
echo $LFS  
echo $LFS_TGT  
echo $PATH  
lfs  
/mnt/lfs  
x86_64-lfs-linux-gnu  
/mnt/lfs/tools/bin:/usr/bin  
[lfs@artix ~]$
[lfs@artix sources]$ su - lfs  
Password:    
[lfs@artix ~]$ export MAKEFLAGS=-j$(nproc)  
[lfs@artix ~]$ ls /etc/bash.bashrc  
ls: cannot access '/etc/bash.bashrc': No such file or directory  
[lfs@artix ~]$ mv -v /etc/bash.bashrc /etc/bash.bashrc.NOUSE  
mv: cannot stat '/etc/bash.bashrc': No such file or directory  
[lfs@artix ~]$ source ~/.bash_profile  
[lfs@artix ~]$ echo $LFS  
echo $LFS_TGT  
echo $PATH  
/mnt/lfs  
x86_64-lfs-linux-gnu  
/mnt/lfs/tools/bin:/usr/bin  
[lfs@artix ~]$ whoami  
echo $LFS  
echo $LFS_TGT  
echo $PATH  
lfs  
/mnt/lfs  
x86_64-lfs-linux-gnu  
/mnt/lfs/tools/bin:/usr/bin  
[lfs@artix ~]$ ls -ld /mnt/lfs/bin  
ls -ld /mnt/lfs/lib  
ls -ld /mnt/lfs/sbin  
  
ls -l /mnt/lfs/bin  
ls -l /mnt/lfs/lib  
ls -l /mnt/lfs/sbin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/bin -> usr/bin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/lib -> usr/lib  
lrwxrwxrwx 1 root root 8 Jun 18 23:21 /mnt/lfs/sbin -> usr/sbin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/bin -> usr/bin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/lib -> usr/lib  
lrwxrwxrwx 1 root root 8 Jun 18 23:21 /mnt/lfs/sbin -> usr/sbin  
[lfs@artix ~]$ mkdir: cannot create directory '/mnt/lfs/lib64': Permission denied  
bash: mkdir:: command not found  
[lfs@artix ~]$ whoami         
lfs  
  
echo $LFS  
/mnt/lfs  
  
echo $LFS_TGT  
x86_64-lfs-linux-gnu  
  
echo $PATH  
/mnt/lfs/tools/bin:/usr/bin  
lfs  
bash: lfs: command not found  
/mnt/lfs  
bash: /mnt/lfs: Is a directory  
x86_64-lfs-linux-gnu  
bash: x86_64-lfs-linux-gnu: command not found  
/mnt/lfs/tools/bin:/usr/bin  
bash: /mnt/lfs/tools/bin:/usr/bin: No such file or directory  
[lfs@artix ~]$ ls -ld /mnt/lfs/bin /mnt/lfs/lib /mnt/lfs/sbin  
ls -l /mnt/lfs/bin /mnt/lfs/lib /mnt/lfs/sbin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/bin -> usr/bin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/lib -> usr/lib  
lrwxrwxrwx 1 root root 8 Jun 18 23:21 /mnt/lfs/sbin -> usr/sbin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/bin -> usr/bin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/lib -> usr/lib  
lrwxrwxrwx 1 root root 8 Jun 18 23:21 /mnt/lfs/sbin -> usr/sbin  
[lfs@artix ~]$
[Zsupsz@artix ~]$ su -  
Password:    
[artix ~]# ls -ld /mnt/lfs/bin  
ls -ld /mnt/lfs/lib  
ls -ld /mnt/lfs/sbin  
  
ls -l /mnt/lfs/bin  
ls -l /mnt/lfs/lib  
ls -l /mnt/lfs/sbin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/bin -> usr/bin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/lib -> usr/lib  
lrwxrwxrwx 1 root root 8 Jun 18 23:21 /mnt/lfs/sbin -> usr/sbin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/bin -> usr/bin  
lrwxrwxrwx 1 root root 7 Jun 18 23:21 /mnt/lfs/lib -> usr/lib  
lrwxrwxrwx 1 root root 8 Jun 18 23:21 /mnt/lfs/sbin -> usr/sbin  
[artix ~]# mkdir: cannot create directory '/mnt/lfs/lib64': Permission denied  
-bash: mkdir:: command not found  
[artix ~]# whoami             
lfs  
  
echo $LFS  
/mnt/lfs  
  
echo $LFS_TGT  
x86_64-lfs-linux-gnu  
  
echo $PATH  
/mnt/lfs/tools/bin:/usr/bin  
root  
-bash: lfs: command not found  
  
-bash: /mnt/lfs: Is a directory  
  
-bash: x86_64-lfs-linux-gnu: command not found  
/usr/local/sbin:/usr/local/bin:/usr/bin:/var/lib/flatpak/exports/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bi  
n/core_perl  
-bash: /mnt/lfs/tools/bin:/usr/bin: No such file or directory  
[artix ~]# [artix ~]# ls -ld /mnt/lfs/lib64  
ls: cannot access '/mnt/lfs/lib64': No such file or directory  
[artix ~]# mkdir -pv /mnt/lfs/lib64  
chown lfs:lfs /mnt/lfs/lib64  
mkdir: created directory '/mnt/lfs/lib64'  
[artix ~]# ls -ld /mnt/lfs/lib64  
drwxr-xr-x 2 lfs lfs 4096 Jun 19 08:58 /mnt/lfs/lib64  
[artix ~]#
[artix ~]# whoami  
echo $LFS  
echo $LFS_TGT  
echo $PATH  
root  
  
  
/usr/local/sbin:/usr/local/bin:/usr/bin:/var/lib/flatpak/exports/bin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bi  
n/core_perl  
[artix ~]# [lfs@artix ~]$ whoami  
echo $LFS  
echo $LFS_TGT  
echo $PATH  
lfs  
/mnt/lfs  
x86_64-lfs-linux-gnu  
/mnt/lfs/tools/bin:/usr/bin  
