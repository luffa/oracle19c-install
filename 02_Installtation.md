# Installation

###### Log into the oracle user.

```sh
DISPLAY=oradbwu:0; export DISPLAY
```

###### เข้าไปใน directory ORACLE_HOME


###### เตรียม directory.

```sh
export SOFTWARE_DIR=/u01/software
```

###### Unzip software.

```sh
cd $ORACLE_HOME
unzip -oq ${SOFTWARE_DIR}/LINUX.X64_193000_db_home.zip

```
```sh
dnf config-manager --enable ol8_codeready_builder
dnf install xorg-x11-apps xorg-x11-xauth
```



###### install

การติดตั้งมี 2 แบบ

###### แบบที่ 1

```sh
./runInstaller
```

###### แบบที่ 2

```sh
./runInstaller -ignorePrereq -waitforcompletion -silent                        \
    -applyRU ${PATCH_PATH1}                                                    \
    -responseFile ${ORACLE_HOME}/install/response/db_install.rsp               \
    oracle.install.option=INSTALL_DB_SWONLY                                    \
    ORACLE_HOSTNAME=${ORACLE_HOSTNAME}                                         \
    UNIX_GROUP_NAME=oinstall                                                   \
    INVENTORY_LOCATION=${ORA_INVENTORY}                                        \
    SELECTED_LANGUAGES=en,en_GB                                                \
    ORACLE_HOME=${ORACLE_HOME}                                                 \
    ORACLE_BASE=${ORACLE_BASE}                                                 \
    oracle.install.db.InstallEdition=EE                                        \
    oracle.install.db.OSDBA_GROUP=dba                                          \
    oracle.install.db.OSBACKUPDBA_GROUP=dba                                    \
    oracle.install.db.OSDGDBA_GROUP=dba                                        \
    oracle.install.db.OSKMDBA_GROUP=dba                                        \
    oracle.install.db.OSRACDBA_GROUP=dba                                       \
    SECURITY_UPDATES_VIA_MYORACLESUPPORT=false                                 \
    DECLINE_SECURITY_UPDATES=true
```
