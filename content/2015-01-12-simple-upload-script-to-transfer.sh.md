title: اسکریپت اپلود در Transfer.sh
date: 2015-01-12 00:13
tags: لینوکس, transfer.sh, آپلود, bash
category: یادداشت ها
slug: simple-upload-script-to-transfer.sh

قبلن [جادی](http://jadi.net) یه سرویسی معرفی کرد به اسم [Transfer.sh](http://transfer.sh) که برای اپلود سریع و راحت فایل (از طریق bash ) استفاده میشه . بر طبق نیازی که داشتم واسه ارسال فایل برای دوستام این اسکریپ رو نوشتم که ادرس فایل رو میگیره اپلود میکنه لینک میده :)

*البته سرویس transfer.sh مدت زمان محدودی میزبان فایل شماست (الان که 14روز)*

#### اسکریپت

    #!/bin/bash
    # easy upload to transfer.sh / By: MeyT-GHG
    echo -e "\x1B[01;93m Enter file address : \x1B[0m"
    read -p "" address
    address0="$(echo "$address" | tr -d "[='=]")"
    name="${address0##*/}"
    echo -e "\x1B[01;93m Start Uploading ... \x1B[0m"
    echo -e "\x1B[01;93m \n Finish! Download link : \x1B[0m" $(curl --upload-file "$address0" 'https://transfer.sh/'"$name"'') 


