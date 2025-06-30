## qemu-org 

-[qemu ref](https://www.qemu.org/download/#source)

```shell
sudo apt install git gcc g++ make file wget gawk diffstat bzip2 cpio chrpath zstd lz4 bzip2 ninja-build libglib2.0-dev libpixman-1-dev python3 python3-pip flex
```

```shell
wget https://download.qemu.org/qemu-10.0.2.tar.xz
tar xvJf qemu-10.0.2.tar.xz
cd qemu-10.0.2
sudo apt-get install flex

./configure

./configure --target-list=arm-softmmu,arm-linux-user

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
