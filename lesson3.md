#lesson3笔记

##修改文件或目录的访问权限

		psjicfh@ubuntu:~$ cd work/lesson3
		psjicfh@ubuntu:~/work/lesson3$ touch aaa
		psjicfh@ubuntu:~/work/lesson3$ ls -l aaa
		-rw-r--r-- 1 psjicfh psjicfh 0 2011-07-19 20:54 aaa
		psjicfh@ubuntu:~/work/lesson3$ chmod -w aaa
		psjicfh@ubuntu:~/work/lesson3$ ls -l aaa
		-r--r--r-- 1 psjicfh psjicfh 0 2011-07-19 20:54 aaa
		psjicfh@ubuntu:~/work/lesson3$ rm -r aaa
		rm：是否删除有写保护的普通空文件 "aaa"？ y  //删除成功

		psjicfh@ubuntu:~/work/lesson3$  cd ..
		psjicfh@ubuntu:~/work$ cd lesson3
		psjicfh@ubuntu:~/work/lesson3$ touch aa
		psjicfh@ubuntu:~/work/lesson3$ cd ..
		psjicfh@ubuntu:~/work$ chmod -w lesson3  //此处改的是文件夹的属性文件在此文件夹中
		psjicfh@ubuntu:~/work$ ls -l lesson3
		总用量 20
		-rw-r--r-- 1 psjicfh psjicfh    0 2011-07-19 21:06 aa
		drwxr-xr-x 3 psjicfh psjicfh 4096 2011-07-17 10:29 ggg
		-rw-r--r-- 1 psjicfh psjicfh   26 2011-07-17 08:47 h1.c
		-rw-r--r-- 1 psjicfh psjicfh   26 2011-07-17 09:02 h.c
		-rw-r--r-- 1 psjicfh psjicfh  141 2011-07-17 08:52 h.diff
		-rw-r--r-- 1 psjicfh psjicfh  507 2011-07-17 09:06 笔记
		psjicfh@ubuntu:~/work$ cd lesson3
		psjicfh@ubuntu:~/work/lesson3$ rm -r aa
		rm: 无法删除"aa": 权限不够
		psjicfh@ubuntu:~/work/lesson3$ rm -rf aa
		rm: 无法删除"aa": 权限不够               //上两方法均无法删除
		psjicfh@ubuntu:~/work/lesson3$ cd ..
		psjicfh@ubuntu:~/work$ chmod +w lesson3
		psjicfh@ubuntu:~/work$ ls -l lesson3
		总用量 20
		-rw-r--r-- 1 psjicfh psjicfh    0 2011-07-19 21:06 aa
		drwxr-xr-x 3 psjicfh psjicfh 4096 2011-07-17 10:29 ggg
		-rw-r--r-- 1 psjicfh psjicfh   26 2011-07-17 08:47 h1.c
		-rw-r--r-- 1 psjicfh psjicfh   26 2011-07-17 09:02 h.c
		-rw-r--r-- 1 psjicfh psjicfh  141 2011-07-17 08:52 h.diff
		-rw-r--r-- 1 psjicfh psjicfh  507 2011-07-17 09:06 笔记
		psjicfh@ubuntu:~/work$ cd lesson3
		psjicfh@ubuntu:~/work/lesson3$ rm -r aa   //删除成功
		psjicfh@ubuntu:~/work/lesson3$ 
### r w x
    r 读 w 写 x 执行

	psjicfh@ubuntu:~/work/lesson3$ ls -l aaa
	-rw-r--r-- 1 psjicfh psjicfh 0 2011-07-19 20:54 aaa
###	可以看出 以上由三组八进制数组成 所以有另一种更改权限的方法
### chmod 666 aa   即 rw-rw-rw-
    其余详见课本第十六页

##查看两个文件的不同之处

		akaedu@akaedu-desktop:~/work$ vim h.c
		akaedu@akaedu-desktop:~/work$ cp h.c h1.c
		akaedu@akaedu-desktop:~/work$ vim h1.c
		akaedu@akaedu-desktop:~/work$ diff -u h.c h1.c >h.diff
							  (也可diff h.c h1.c直接打印)
		akaedu@akaedu-desktop:~/work$ vim h.diff

		--- h.c 2011-07-17 08:46:19.790055706 +0800
		+++ h1.c        2011-07-17 08:47:15.435058419 +0800
		@@ -1,3 +1,3 @@
		 line1
		-line2
		+this is line2
		 line3

##打补丁
	akaedu@akaedu-desktop:~/work$ patch h.c <h.diff
    此时执行 diff h.c h1.c后显示为空
    去除补丁patch -R h.c <h.diff   (R:reverse)

##解压缩
### 解压：tar zxvf dir.tar.gz
### 压缩：tar zcvf dir.tar.gz dir
###例如：

		psjicfh@ubuntu:~$ mkdir yasuo
		psjicfh@ubuntu:~$ tar zcvf yasuo.tar.gz yasuo //压缩
		yasuo/
		psjicfh@ubuntu:~$ cp yasuo.tar.gz ./work/lesson3
		psjicfh@ubuntu:~$ cd work/lesson3
		psjicfh@ubuntu:~/work/lesson3$ ls
		ggg  h1.c  h.c  h.diff  yasuo.tar.gz  笔记
		psjicfh@ubuntu:~/work/lesson3$ tar zxvf yasuo.tar.gz //解压
		yasuo/
		psjicfh@ubuntu:~/work/lesson3$ 
###其余详见课本第十九页
