title: ساختن Wifi - Hotspot در لینوکس 
date: 2015-01-11 02:20
tags: وای‌فای, لینوکس, آرچ,نقطه دستیابی 
category: یادداشت ها
slug: create-wifi-hotspot-linux-arch

اشتراک گزاری اینترنت یا ایجاد شبکه محلی با دستگاه های دارای وای‌فای
- توزیع انتخابی Arch
- برنامه مورد نیاز create_ap 

1) تشخیص دستگاهی که از AP پشتیبانی میکنه


	$ iw list
 

خروجی مثل این رو میبینین که اگه AP جز لیست بود میریم مرحله بعدی ...

 
	Wiphy phy1
	...
	Supported interface modes:
	* IBSS
	* managed
	* AP
	* AP/VLAN
	* WDS
	* monitor
	* mesh point
	...


۲) نصب برنامه 
 
	$yaourt -S create_ap

یا
https://github.com/oblique/create_ap

۳) تشخیص اینترفیس 

	$ iw dev

خروجی مثل این رو میبینید که نشون میده اینترفیس شبکه دستگاه phy0 برابر wlp2s0

	phy#0
	Interface wlp2s0
	ifindex 3
	wdev 0x1
	addr 24:0a:64:83:f0:e9
	type managed
	channel 6 (2437 MHz), width: 20 MHz, center1: 2437 MHz

 ۳ ) ایجاد hotspot یا access point

	$ sudo create_ap wlp2s0 wlp2s0 MyAccessPoint MyPassword

	:: MyAccessPoint = نام نقطه دستیابی
	:: MyPassword = کلمه عبور 

 این دستور در حالت رمزگزاری WPA + WPA2 بود برای استفاده از حالت‌های دیگه از رفرنس خود برنامه میتونید استفاده کنید : https://github.com/oblique/create_ap

	Examples
	No passphrase (open network):
	create_ap wlan0 eth0 MyAccessPoint

	WPA + WPA2 passphrase:
	create_ap wlan0 eth0 MyAccessPoint MyPassPhrase

	AP without Internet sharing:
	create_ap -n wlan0 MyAccessPoint MyPassPhrase

	Bridged Internet sharing:
	create_ap -m bridge wlan0 eth0 MyAccessPoint MyPassPhrase

	Bridged Internet sharing (pre-configured bridge interface):
	create_ap -m bridge wlan0 br0 MyAccessPoint MyPassPhrase

	Internet sharing from the same WiFi interface:
	create_ap wlan0 wlan0 MyAccessPoint MyPassPhrase

	Choose a different WiFi adapter driver
	create_ap --driver rtl871xdrv wlan0 eth0 MyAccessPoint MyPassPhrase

	No passphrase (open network) using pipe:
	echo -e "MyAccessPoint" | create_ap wlan0 eth0

	WPA + WPA2 passphrase using pipe:
	echo -e "MyAccessPoint\nMyPassPhrase" | create_ap wlan0 eth0

	Enable IEEE 802.11n
	create_ap --ieee80211n --ht_capab '[HT40+]' wlan0 eth0 MyAccessPoint MyPassPhrase
