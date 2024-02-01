# Oracle Database 19c Install

##### 1.Hosts File

แก้ไขไฟล์ "/etc/hosts"

```sh
sudo -i
nano /etc/hosts
```

For example.
```sh
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
192.168.56.107  oradbwu.localdomain  oradbwu
```

##### 2. Hostname

แก้ไขไฟล์ hostname

```sh
nano /etc/hostname
```

```sh
oradbwu.localdomain
```

### Oracle Installation Prerequisites

##### 3. Automatic Setup

```sh
dnf install -y oracle-database-preinstall-19c
dnf update -y


dnf install -y bc
dnf install -y binutils
dnf install -y compat-openssl11
dnf install -y elfutils-libelf
dnf install -y fontconfig
dnf install -y glibc
dnf install -y glibc-devel
dnf install -y ksh
dnf install -y libaio
dnf install -y libasan
dnf install -y liblsan
dnf install -y libX11
dnf install -y libXau
dnf install -y libXi
dnf install -y libXrender
dnf install -y libXtst
dnf install -y libxcrypt-compat
dnf install -y libgcc
dnf install -y libibverbs
dnf install -y libnsl
dnf install -y librdmacm
dnf install -y libstdc++
dnf install -y libxcb
dnf install -y libvirt-libs
dnf install -y make
dnf install -y policycoreutils
dnf install -y policycoreutils-python-utils
dnf install -y smartmontools
dnf install -y sysstat

dnf install -y glibc-headers
dnf install -y ipmiutil
dnf install -y libnsl2
dnf install -y libnsl2-devel
dnf install -y net-tools
dnf install -y nfs-utils 

dnf install -y gcc
dnf install -y unixODBC
```

##### 4. Create the new groups and users.

```sh
groupadd -g 54321 oinstall
groupadd -g 54322 dba
groupadd -g 54323 oper 
#groupadd -g 54324 backupdba
#groupadd -g 54325 dgdba
#groupadd -g 54326 kmdba
#groupadd -g 54327 asmdba
#groupadd -g 54328 asmoper
#groupadd -g 54329 asmadmin
#groupadd -g 54330 racdba

useradd -u 54321 -g oinstall -G dba,oper oracle
```

##### 5. Additional Setup

###### Set the password for the "oracle" user.

```sh
passwd oracle
```

###### Set secure Linux to permissive by editing the "/etc/selinux/config"
```sh
SELINUX=permissive
setenforce Permissive
```

##### 6. Disable firewall

```sh
systemctl stop firewalld
systemctl disable firewalld
```

##### 7. Create the oracle directories 

```sh
mkdir -p /u01/app/oracle/product/19.0.0/dbhome_1
mkdir -p /u02/oradata
mkdir -p /u01/software
cp ~/Downloads/LINUX.X64_193000_db_home.zip /u01/software/LINUX.X64_193000_db_home.zip
chown -R oracle:oinstall /u01 /u02
chown -R oracle:oinstall /u01/software/LINUX.X64_193000_db_home.zip
chmod -R 775 /u01 /u02
```

##### 8. Create a "scripts" directory.

```sh
mkdir /home/oracle/scripts

cat > /home/oracle/scripts/setEnv.sh <<EOF
# Oracle Settings
export TMP=/tmp
export TMPDIR=\$TMP

export ORACLE_HOSTNAME=ol9-19.localdomain
export ORACLE_UNQNAME=cdb1
export ORACLE_BASE=/u01/app/oracle
export ORACLE_HOME=\$ORACLE_BASE/product/19.0.0/dbhome_1
export ORA_INVENTORY=/u01/app/oraInventory
export ORACLE_SID=cdb1
export PDB_NAME=pdb1
export DATA_DIR=/u02/oradata

export PATH=/usr/sbin:/usr/local/bin:\$PATH
export PATH=\$ORACLE_HOME/bin:\$PATH

export LD_LIBRARY_PATH=\$ORACLE_HOME/lib:/lib:/usr/lib
export CLASSPATH=\$ORACLE_HOME/jlib:\$ORACLE_HOME/rdbms/jlib
EOF

echo ". /home/oracle/scripts/setEnv.sh" >> /home/oracle/.bash_profile
```

##### 9. Create a "start_all.sh" and "stop_all.sh" 

```sh
cat > /home/oracle/scripts/start_all.sh <<EOF
#!/bin/bash
. /home/oracle/scripts/setEnv.sh

export ORAENV_ASK=NO
. oraenv
export ORAENV_ASK=YES

dbstart \$ORACLE_HOME
EOF


cat > /home/oracle/scripts/stop_all.sh <<EOF
#!/bin/bash
. /home/oracle/scripts/setEnv.sh

export ORAENV_ASK=NO
. oraenv
export ORAENV_ASK=YES

dbshut \$ORACLE_HOME
EOF

chown -R oracle:oinstall /home/oracle/scripts
chmod u+x /home/oracle/scripts/*.sh
```

###### ใช้ start stop database ต้อง login ด้วย user oracle
```sh
~/scripts/start_all.sh
~/scripts/stop_all.sh
```





