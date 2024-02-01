# Installation

###### Log into the oracle user.

```sh
DISPLAY=oradbwu:0.0; export DISPLAY
```

###### เข้าไปใน directory ORACLE_HOME


###### เตรียม directory.

```sh
export SOFTWARE_DIR=/u01/software
export OPATCH_FILE="p6880880_190000_Linux-x86-64.zip"
export PATCH_FILE="p35742413_190000_Linux-x86-64.zip"
export PATCH_TOP=${SOFTWARE_DIR}/35742413
export PATCH_PATH1=${PATCH_TOP}/35643107
export PATCH_PATH2=${PATCH_TOP}/35648110
```

###### Unzip software.

```sh
cd $ORACLE_HOME
unzip -oq ${SOFTWARE_DIR}/LINUX.X64_193000_db_home.zip
unzip -oq ${SOFTWARE_DIR}/${OPATCH_FILE}

export CV_ASSUME_DISTID=OL8
```

###### install
```sh
# Interactive mode.
./runInstaller

# Silent mode. Includes application of patch.
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
