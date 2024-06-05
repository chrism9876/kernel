## MakeFile
```
EXTRAVERSION = -BlueBird-LTS
```
## Build

```

make -j16
make modules

mkdir modules
modinstalldir=$(pwd)/modules
make INSTALL_MOD_PATH=$modinstalldir modules_install
tar cf modules.tar.gz modules/lib/*

```
