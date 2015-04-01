title: فعال کردن Hibernate 
date: 2015-01-12 23:02
tags: لینوکس, swap, hibernate, grub
category: یادداشت ها
slug: enable-hibernate-linux

اگه توضیعی مثل [مانجارو](http://manjaro.org) واسه hibernate شدن ادا در آورد یا کلن مشکلی پیش اومد...

در مرحله اول ببنید پارتیشن swap وجود داره؟! اگه نبود که باید بسازید.

بعد ببینید پارتیشن swap به صورت خودکار بالا میاد یا نه ؟!

    $ free -h 

اگه چیزی شناسایی نشد پس [فعال‌اش کنید]({tag}swap)

فایل کانفیگ grub رو باز کنید :

    $ sudo gedit /etc/default/grub

خط زیر رو با یه فاصله به ادامه `GRUB_CMDLINE_LINUX_DEFAULT` اضافه کنید :

    resume=/dev/sda8
    
*نکته : `/dev/sda8` مسیر پارتیشن swap سیستم شماس که میتونید با دستور `sudo blkid` پیدا کنید‌.*

درنهایت تغییرات به این شکل میشه : 

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=/dev/sda8"

حالا فایل رو ذخیره کنید بعد با دستور زیر تنظیمات grub دوباره با اعمال تغییرات ساخته میشه.

    $ grub-mkconfig -o /boot/grub/grub.cfg
