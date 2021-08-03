# Linux 基础命令



## 1 查看版本：

```
cat /proc/version
# Linux version 3.10.0-123.el7.x86_64 (mockbuild@x86-017.build.eng.bos.redhat.com) (gcc version 4.8.2 20140120 (Red Hat 4.8.2-16) (GCC) ) #1 SMP Mon May 5 11:16:57 EDT 2014
```

## 2 查看位数

```
uname -a
# Linux localhost.localdomain 3.10.0-123.el7.x86_64 #1 SMP Mon May 5 11:16:57 EDT 2014 x86_64 x86_64 x86_64 GNU/Linux

getconf LONG_BIT
# 64
```

