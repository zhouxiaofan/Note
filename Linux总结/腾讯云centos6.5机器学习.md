### 腾讯云centos6.5 安装zlib+python2.7+机器学习常用库

1.安装zlib 编译安装会因为gcc编译条件苛刻报错，不管他了，直接yum

```bash
$yum instal gcc zlib-devel
```

2.下载Python2.7.3
```bash
$wget http://python.org/ftp/python/2.7.3/Python-2.7.3.tar.bz2
```

3.解压
```bash
$tar -jxvf Python-2.7.3.tar.bz2  
```

4.更改工作目录
```bash
$cd Python-2.7.3  
```
5.安装Python2.7.3
```bash
$./configure  
$make all
$make install 
$make clean 
$make disclean
```

5.建立软连接
```bash
$mv /usr/bin/python /usr/bin/python2.6.6
$ln -s /usr/local/bin/python2.7 /usr/bin/python
```
6.查询Python
```bash
$python -V
```

7.解决yum不支持python2.7的问题
```bash
$vi /usr/bin/yum  
```

