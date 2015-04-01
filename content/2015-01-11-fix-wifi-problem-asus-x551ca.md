title: حل مشکل کار نکردن وای‌فای در لپ‌تاپ Asus سری x
date: 2015-01-11 02:40
tags: لینوکس, وای‌فای, asus
category: یادداشت ها
slug: fix-wifi-problem-asus-x551ca



	$ sudo nano /etc/modprobe.d/asus-wifi.conf

و خط زیر رو بهش اضافه کنید 



	options asus_nb_wmi wapf=1


و بعد یه Restart  


####  آپدیت 

در کرنل 3.19 این مشکل حل شده !
