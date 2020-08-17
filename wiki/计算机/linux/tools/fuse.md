

---



FUSE文件系统，即filesystem in userspace，是linux kernel提供的一个功能模块，支持用户态程序实现文件系统。`lsmod | grep fuse`能看到这个内核模块。

配置文件在`/etc/fuse.conf`。

帮助文档：`$ man fuse`，有一些通用选项（OPTIONS），在mount时指定以改变FUSE的行为，如：

```
user_allow_other
              Allow non-root users to specify the allow_other or allow_root mount options (see below).
              允许非root用户在mount时指定"-o allow_other"或"-o allow_root"
```

例如通过sshfs，可以将ssh目标的目录mount到本地，允许root用户访问，先给fuse.conf添加`user_allow_other`选项，然后mount：

```
$ sshfs r@r-lc:/home/r/proj/sk02/skpi_root /home/pi/skpi_root -o allow_root
```


