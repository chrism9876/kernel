## MakeFile
```
EXTRAVERSION = -BlueBird-LTS
```
## Build

```
kernelVersion=$(cat Makefile|grep "^VERSION = " | awk -F'= ' '{ print $2}').$(cat Makefile|grep "^PATCHLEVEL = " | awk -F'= ' '{ print $2}').$(cat Makefile|grep "^SUBLEVEL = " | awk -F'= ' '{ print $2}')
kernelFullString=$kernelVersion"-BlueBird-LTS"
sed -i '/^EXTRAVERSION/c\EXTRAVERSION = -BlueBird-LTS' Makefile
make -j16
make modules

mkdir modules
modinstalldir=$(pwd)/modules
make INSTALL_MOD_PATH=$modinstalldir modules_install
tar cjvf $kernelFullString-modules.tar.gz -C modules/lib/modules .
cp arch/x86_64/boot/bzImage vmlinuz-$kernelFullString

```
