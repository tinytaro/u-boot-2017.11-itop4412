# u-boot-2017.11-itop4412
Port U-boot-2017.11 to TOPEET iTOP-4412 board

## Usage
```
tar -jxf u-boot-2017.11.tar.bz2
cd u-boot-2017.11
patch -p1 < ../u-boot-2017.11.diff
make itop4412_defconfig
make -j4 CROSS_COMPILE=arm-linux-gnueabi-
dd if=/dev/zero of=env.bin bs=8192 count=1
cat E4412_N.bl1.bin spl/itop4412-spl.bin env.bin u-boot.bin > u-boot-itop4412.bin
dd iflag=dsync oflag=dsync if=u-boot-itop4412.bin of=/dev/sdb seek=1
```