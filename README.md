This is Prebuilt Ubuntu Root File System for BeagleBoneBlack.

uEnv.txt file SD card Partition BeagleBoneBlack
uEnv.txt

loadaddr=0x82000000

fdtaddr=0x88000000

rdaddr=0x88080000

initrd_high=0xffffffff

fdt_high=0xffffffff

#for single partitions:

mmcroot=/dev/mmcblk0p1

loadximage=load mmc 0:1 ${loadaddr} /boot/vmlinuz-${uname_r}

loadxfdt=load mmc 0:1 ${fdtaddr} /boot/dtbs/${uname_r}/${fdtfile}

loadxrd=load mmc 0:1 ${rdaddr} /boot/initrd.img-${uname_r}; setenv rdsize ${filesize}

loaduEnvtxt=load mmc 0:1 ${loadaddr} /boot/uEnv.txt ; env import -t ${loadaddr} ${filesize};

loadall=run loaduEnvtxt; run loadximage; run loadxfdt;

mmcargs=setenv bootargs console=tty0 console=${console} ${optargs} ${cape_disable} ${cape_enable} root=${mmcroot} rootfstype=${mmcrootfstype} ${cmdline}

uenvcmd=run loadall; run mmcargs; bootz ${loadaddr} - ${fdtaddr};





































