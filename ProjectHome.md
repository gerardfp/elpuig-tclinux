## ElPuig - Remastered Tiny Core Linux LiveCD. ##

Minimal LiveCD based on Core Linux 5.2. Modules included:
  * iproute2
  * iptables
  * openssh
  * nmap
  * ntfs-3g-dev
  * lynx
  * nano

  * es.kmap



### Download ###

  * link: http://elpuig-tclinux.googlecode.com/git/ElPuig-TCLinux.iso (23 MB)

  * mirror: https://drive.google.com/file/d/0Bxy87ucpLMaBRlNZOHVnaXNhR0k

  * Tiny Core Linux: http://www.tinycorelinux.net/downloads.html

### Remastering ###

**tclinux.iso**

  * _Unpack_

`mount tclinux.iso iso/`

  * _Pack_

`mkisofs -l -J -V TC-custom -no-emul-boot -boot-load-size 4 -boot-info-table -b boot/isolinux/isolinux.bin -c boot/isolinux/boot.cat -o TC-remastered.iso iso/`



**core.gz**

  * _Unpack_

`cd extract/`

`zcat /tmp/newiso/boot/core.gz | sudo cpio -i -H newc -d`

  * _Pack_

`cd extract/`

`find | cpio -o -H newc | gzip -2 > ../core.gz`


**extension.tcz**

_(Get extensions with_ `tce-ab` _command_. _Install them and copy "tcz" files from_ `/tmp/tce/optional`_)_

  * _Unpack_

`mount extension.tcz extension/`

  * _Pack_

`mksquashfs extension/ extension.tcz`

`md5sum extension.tcz > extension.tcz.md5.txt`

`cp extension.tcz* extract/tmp/tce/optional/`

`echo -n "extension.tcz" >> extract/tmp/tce/onboot.lst`