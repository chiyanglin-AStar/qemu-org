## qemu-org 

-[qemu ref](https://www.qemu.org/download/#source)

```shell
sudo apt install git gcc g++ make file wget gawk diffstat bzip2 cpio chrpath zstd lz4 bzip2 ninja-build libglib2.0-dev libpixman-1-dev python3 python3-pip flex meson bison
pip3 install tomli
pip3 install meson==0.63
```

```shell
wget https://download.qemu.org/qemu-10.0.2.tar.xz
tar xvJf qemu-10.0.2.tar.xz
cd qemu-10.0.2
sudo apt-get install flex

./configure

./configure --target-list=arm-softmmu,arm-linux-user
```
if still not work , get source :
```shell 
wget https://download.gnome.org/sources/glib/2.66/glib-2.66.7.tar.xz

tar xf glib-2.66.7.tar.xz

cd glib-@GLIB_VERSION@

meson _build

ninja -C _build

sudo ninja -C _build install

```
```
make

make -j 4

sudo make install

qemu-system-arm --version
```

or 
```shell
git clone https://gitlab.com/qemu-project/qemu.git
cd qemu

sudo apt-get install flex

./configure

./configure --target-list=arm-softmmu,arm-linux-user

make

make -j 4

sudo make install

qemu-system-arm --version

```

```shell
wget https://jenkins.openbmc.org/job/ci-openbmc/lastSuccessfulBuild/distro=ubuntu,label=docker-builder,target=romulus/artifact/openbmc/build/tmp/deploy/images/romulus/obmc-phosphor-image-romulus-20250624191223.static.mtd

qemu-system-arm -M romulus-bmc -nic user -drive file=obmc-phosphor-image-romulus.static.mtd,format=raw,if=mtd -nographic

```
### use redfish or webui need 
```shell
qemu-system-arm -m 256 -M romulus-bmc -nographic -drive file=obmc-phosphor-image-romulus-20250630004344.static.mtd,format=raw,if=mtd -net nic -net user,hostfwd=:127.0.0.1:2222-:22,hostfwd=:127.0.0.1:2443-:443,hostname=qemu
```
### if show ***network backend 'user' is not compiled into this binary***  ref : https://stackoverflow.com/questions/75641274/network-backend-user-is-not-compiled-into-this-binary

```shell
git clone https://gitlab.freedesktop.org/slirp/libslirp.git

cd libslirp

meson build

ninja -C build install

use
./configure --enable-slirp --enable-debug

```

### aspeed sdk image
[the operation ref of qemu on aspeed](https://www.qemu.org/docs/master/system/arm/aspeed.html)


```shell
wget https://github.com/AspeedTech-BMC/openbmc/releases/ast2600-default-ncsi-obmc.tar.gz

sudo chmod u+x ast2600-default-obmc.tar.gz

tar -xvzf ast2600-default-obmc.tar.gz

cd ast2600-default

qemu-system-arm -M ast2600-evb -drive file=obmc-phosphor-image-ast2600-default.static.mtd,format=raw,if=mtd -nographic
```
## Qemu_IBM 
-[Qemu IBM](https://github.com/legoater/qemu.git)

```shell
git clone https://github.com/legoater/qemu.git qemu-ibm
cd qemu-ibm

sudo apt-get install flex

./configure

./configure --target-list=arm-softmmu,arm-linux-user

make

make -j 4

sudo make install

qemu-system-arm --version

wget https://jenkins.openbmc.org/job/ci-openbmc/lastSuccessfulBuild/distro=ubuntu,label=docker-builder,target=romulus/artifact/openbmc/build/tmp/deploy/images/romulus/obmc-phosphor-image-romulus-20250625062256.static.mtd

qemu-system-arm -M romulus-bmc -nic user -drive file=obmc-phosphor-image-romulus-20250625062256.static.mtd,format=raw,if=mtd -nographic


wget https://github.com/AspeedTech-BMC/openbmc/releases/download/v09.06/ast2600-default-obmc-sdk.tar.gz

sudo chmod u+x ast2600-default-obmc-sdk.tar.gz

tar -xvzf ast2600-default-obmc-sdk.tar.gz

cd ast2600-default-sdk/

qemu-system-arm -M ast2600-evb -drive file=obmc-phosphor-image-ast2600-default.static.mtd,format=raw,if=mtd -nographic
```
