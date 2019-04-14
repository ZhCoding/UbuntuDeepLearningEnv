# 系统安装
* [硬盘分区](https://blog.csdn.net/u012052268/article/details/77145427)

# 驱动安装

* NVIDIA显卡驱动的安装
1. 从官网下载驱动的.run文件
2. 禁止集成的nouveau驱动
```
# 查看属性
sudo ls -lh /etc/modprobe.d/blacklist.conf

# 修改属性
sudo chmod 666 /etc/modprobe.d/blacklist.conf

# 用编辑器打开, 这里展示用vim编辑器, 也可以用别的编辑器
sudo vim /etc/modprobe.d/blacklist.conf

# 在该文件后添加以下几行
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist rivatv
blacklist nvidiafb

# 保存后执行
sudo update-initramfs -u

# 重启后执行以下命令, 若没有输出, 则说明已经禁用nouveau驱动
lsmod | grep nouveau
```
