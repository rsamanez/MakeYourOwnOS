# Commands to compile the kernel
```
nasm -f elf32 loader.s   
ld -T link.ld -melf_i386 loader.o -o kernel.elf   
```   

## Bulding the ISO
```
mkdir -p iso/boot/grub
cp stage2_eltorito iso/boot/grub/
cp kernel.elf iso/boot/
cp menu.lst iso/boot/grub/
```
Get the GRUB image from:
```
wget http://littleosbook.github.com/files/stage2_eltorito
```

ISO image can be generated with the following command:
```
genisoimage -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -A os -input-charset utf8 -quiet -boot-info-table -o os.iso iso
```
