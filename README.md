## qemu-org 

-[qemu ref](https://www.qemu.org/download/#source)

```shell
wget https://download.qemu.org/qemu-10.0.2.tar.xz
tar xvJf qemu-10.0.2.tar.xz
cd qemu-10.0.2
sudo apt-get install flex

./configure

./configure --target-list=arm-softmmu,arm-linux-user

make

make -j 2

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

make -j 2

sudo make install

qemu-system-arm --version

```
