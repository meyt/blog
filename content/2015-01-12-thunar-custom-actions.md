title: اکشن های Thunar
date: 2015-01-12 00:10
tags: لینوکس, xfce, thunar, custom action
category: یادداشت ها
slug: thunar-custom-actions

فایل منیجر سبک و قوی مثل Thunar یه قابلیت خوبی داره همین Custom Action هست ، میشه باهاش در کلیک راست اکشن های مختلفی تعریف کرد. قبل اینکه من به فکر این پست باشم آرچ توی ویکیش یه لیست خفن گزاشته میتونید از اون هم استفاده کنید .
مسیر اکشن های Thunar : 


	~/.config/Thunar/uca.xml

### ارسال فایل با بلوتوث

	<action>
            <icon>preferences-system-bluetooth</icon>
            <name>Send to bluetooth</name>
            <unique-id>1420216921554080-6</unique-id>
            <command>blueman-sendto %F</command>
            <description></description>
            <patterns>*</patterns>
            <audio-files/>
            <image-files/>
            <other-files/>
            <text-files/>
            <video-files/>
	</action>



### تبدیل فایل png به jpg
درصد فشرده سازی فایل jpg رو هم میتونید از ۷۵ به میزان دلخواه تغییر بدید 

    <action>
        <icon>convertall</icon>
        <name>Convert To JPG</name>
        <unique-id>1420215126532639-1</unique-id>
        <command>convert %f -quality 75 %f.jpg</command>
        <description></description>
        <patterns>*.png</patterns>
        <image-files/>
    </action>

### مقایسه فایل های متنی توسط برنامه `Meld`


	<action>
		<icon>meld</icon>
		<name>Compare</name>
		<unique-id>1420215250239919-2</unique-id>
		<command>meld %F</command>
		<description></description>
		<patterns>*</patterns>
		<directories/>
		<text-files/>
	</action>


### نصب پکیج های `pacman` با پسوند .tar.gz و .tar.xz

	<action>
		<icon>system-software-install-symbolic</icon>
		<name>Install </name>
		<unique-id>1420088136910437-2</unique-id>
		<command>gksudo pacman -U %F</command>
		<description>install with Pacman</description>
		<patterns>*.tar.gz;*.tar.xz</patterns>
		<other-files/>
	</action>

### جستجو در فولدر با `Catfish`

	<action>
		<icon>system-search</icon>
		<name>Search</name>
		<unique-id>1367866030392913-3</unique-id>
		<command>catfish %f</command>
		<description>find files and folders</description>
		<patterns>*</patterns>
		<directories/>
	</action>

### باز کردن فولدر با دسترسی root

	<action>
		<icon>stock_folder</icon>
		<name>Thunar Root</name>
		<unique-id>1367866030392883-2</unique-id>
		<command>pkexec thunar %f</command>
		<description>Thunar Root</description>
		<patterns>*</patterns>
		<directories/>
	</action>

### بازکردن ترمینال از مسیر فعلی

	<action>
		<icon>Terminal</icon>
		<name>Terminal</name>
		<unique-id>1367866030392833-1</unique-id>
		<command>exo-open --working-directory %f --launch TerminalEmulator</command>
		<description></description>
		<patterns>*</patterns>
		<directories/>
	</action>

