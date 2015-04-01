title: بارگزاری خودکار Swap 
date: 2015-01-11 02:30
tags: لینوکس, swap
category: یادداشت ها
slug: auto-mount-swap-on-linux

در بعضی توزیع ها یا به علت بعضی تغییرات ممکنه در حالت پیش‌فرض پارتیشن SWAP بارگزاری نشه برای اینکار مراحل زیر رو دنبال میکنیم .
 
- نکته : پارتیشن هایی که بصورت خودکار لود میشن در فایل `/etc/fstab`  تعریف شده‌.

با این دستور UUID پارتیشن مربوط به swap رو نمایش میده

    $ sudo blkid

حالا فایل fstab رو باز کرده 

	$ sudo gedit /etc/fstab

و خط زیر رو به انتهای فایل اضافه می‌کنیم :

	UUID=a40fae71-931f-44a0-80e4-ea1d10b0b68c none            swap    sw              0       0


`a40fae71-931f-44a0-80e4-ea1d10b0b68c` مربوط به شناسه swap هست که با شناسه پارتیشن خودتون عوض می‌کنید

منبع : 
[Arch wiki swap](https://wiki.archlinux.org/index.php/Swap)

