title: کامپایل کد های پایتون
date: 2015-01-11 02:25
tags: پایتون, لینوکس ,سایتون, cython
category: یادداشت ها
slug: compile-cython-code-python

با استفاده از برنامه cython کد های پایتون رو میشه به c تغییر داد و کامپایل کرد و در نهایت در پروژه import !
.


	$ sudo pip install cython

فایلی که قصد کامپایل کردن‌اش رو دارید به این صورت وارد کنید تا تبدیل به کد c  بشه ::

	$ cython -a mytest.pyx

محتوای فایل mytest.pyx 


	def fib(n):
	    """Print the Fibonacci series up to n."""
	    a, b = 0, 1
	    while b < n:
		print b,
		a, b = b, a + b


واما کامپایل :) 

	$ gcc -shared -pthread -fPIC -fwrapv -O2 -Wall -fno-strict-aliasing -I/usr/include/python2.7 -o mytest.so mytest.c


