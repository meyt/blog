title: تبدیل دسته‌ای فایل‌ها گرافیکی در ترمینال لینوکس
date: 2015-01-10 00:05
tags: لینوکس, bash, تبدیل فایل, inkscape
category: یادداشت ها
slug: multiple-png-to-svg-convert-bash

یه دسته فایل svg داشتم که ترجیح دادم به جای جستجوی فرمت png اونارو خودم تبدیل کنم برای اینکار برنامه معروف گرافیکی inkscape رو نصب کنید و اسکریپت bash زیر رو با نام (دلخواه) convert توی فولدر محتوی فایل هاتون قرار بدید و اجرا کنید .

#### اسکریپت


    #!/bin/bash
    for i in *.svg; do
        inkscape --without-gui --export-png="$(basename $i .svg).png" $i
    done


#### اجرا

    $ ./convert
  

