title: فشرده کردن کد های php 
date: 2015-04-1 02:05
tags: لینوکس, php, minify, script, python
category: یادداشت ها
slug: minify-php-codes


بخاطر دسترسی محدود اینترنت(یه چیزی تو مایه‌های 3KiB/s :| ) دیگه مجبور شدم کدهای پی‌اچ‌پی رو در این حد فشرده کنم تا بشه با ftp فرستاد.
با چند تا جستجو یه معجون آماده شد که پیش نیازش نصب بودن php  و python2.x ‌ـه.

کد :


    import os
    import shutil

    root_src_dir = os.path.join('.','scripts') 
    root_target_dir = os.path.join('.','scripts2') 

    for src_dir, dirs, files in os.walk(root_src_dir):
        dst_dir = src_dir.replace(root_src_dir, root_target_dir)
        if not os.path.exists(dst_dir):
            os.mkdir(dst_dir)
        for file_ in files:
            src_file = os.path.join(src_dir, file_)
            dst_file = os.path.join(dst_dir, file_)
            if os.path.exists(dst_file):
                os.remove(dst_file)
            
            
            if src_file.endswith(".php"):
                print "compress: "+src_file
                os.system("php -w '"+src_file+"' > '"+dst_file+"'")
                print " |---[ Done"
            else:
                print "copy: "+src_file
                shutil.copy(src_file, dst_dir)
                print " |---[ Done"

