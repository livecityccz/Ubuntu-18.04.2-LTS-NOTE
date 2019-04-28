# Ubuntu 18.04.2 LTS NOTE :dart:


## :smile:解决亮度问题

```shell
sudo add-apt-repository ppa:apandada1/brightness-controller
sudo apt update
sudo apt install brightness-controller
```

------

## 双系统时间不同步问题

> :link:[参考网址](https://www.jianshu.com/p/cf445a2c55e8)

```shell
sudo timedatectl set-local-rtc 1
sudo hwclock --localtime --systohc 
```

------

## 安装福昕阅读器

```shell
gzip -d 'FoxitReader.enu.setup.2.4.4.0911.x64.run.tar.gz'
tar xvf 'FoxitReader.enu.setup.2.4.4.0911.x64.run.tar'
# 生成如下文件，再执行命令安装
# FoxitReader.enu.setup.2.4.4.0911(r057d814).x64.run
./'FoxitReader.enu.setup.2.4.4.0911(r057d814).x64.run'
```

------

## :muscle:安装Notepad++ 

```shell
snap install notepad-plus-plus
# 安装snap包后，通过命令安装一些插件
sudo snap connect notepad-plus-plus:process-control
sudo snap connect notepad-plus-plus:removable-media
sudo snap connect notepad-plus-plus:hardware-observe
sudo snap connect notepad-plus-plus:cups-contro
```

------

## :key:安装打印机驱动

```shell
sudo apt-get install hplip hplip-gui
# 必须加sudo
sudo hp-plugin
```

------

## :bulb:搭建深度学习环境——安装CUDA9.0等

> :link:[参考网址](https://blog.csdn.net/xd_wjc/article/details/83005148)

#### Tips:命令nvidia-smi 查看驱动安装情况

## 安装tensorflow

```shell
sudo apt-get install python-pip python-dev 
# 尽量用pip安装
pip install tensorflow-gpu==1.7
```

------

## 安装Typora

> :link:[参考网址](http://support.typora.io/Typora-on-Linux/)

```shell
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
# add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
# install typora
sudo apt-get install typora
```

------

## 安装、激活、配置PyCharm

> :link:[参考网址](https://www.cnblogs.com/huozf/p/9304396.html)

## 安装微信、TIM、百度网盘等

> :link:[参考github](https://github.com/wszqkzqk/deepin-wine-ubuntu)

## 安装Popcorn Time

> :link:[参考网址](https://linux.cn/article-10081-1.html)

------

## 卸载Anaconda3 

```shell
sudo rm -rf ~/anaconda3
sudo rm -rf ~/.conda*
sudo gedit .bashrc
source ~/.bashrc
```

------

------

## :eyes:Tips

-  网易云音乐——最小化退出问题

```shell
sudo killall -9 netease-cloud-music
```

- ### 若之前装了VLC播放器，卸载会影响网易云音乐的使用

```shell
# 检查命令
sudo apt-get check 
# 修复命令
sudo apt --fix-broken install
```

- ### PyCharm使用Anaconda环境中的tensorflow时

> 配置环境变量：LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH

- ### 安装WPS的字体存储路径

> /usr/share/fonts/wps_symbol_fonts/

- ### 微信、TIM、百度网盘、Pycharm等软件安装路径

> /opt/deepinwine/ 
>
> /opt/pycharm-2018.3.5/

- ### 使用anaconda、PyCharm

> 默认的spyder是不支持中文输入的，输入以下代码，重启spyder生效

```shell
sudo mv anaconda3/plugins/platforminputcontexts/libcomposeplatforminputcontextplugin.so anaconda3/plugins/platforminputcontexts/libcomposeplatforminputcontextplugin.so.bak
cp /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so anaconda3/plugins/platforminputcontexts/
```

> Conda更新源在~/.condarc文件中
>
> Spyder中的命令历史记录在~/.config/spyder-py3/history.py中

```shell
conda list
conda create --name new_environment python=3
source activate new_environment
```
> :pensive:Pycharm运行卡死时
>
 ```shell
ps -ef | grep pycharm | grep -v grep | cut -c 9-15 | xargs kill -s 9
 ```
> :pensive:apt-get install 软件，出现如下错误时
>
> E: 无法获得锁 /var/lib/dpkg/lock-frontend - open (11: 资源暂时不可用)
>
> E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?
>
``` shell
# 只需要杀死之前的进程，释放系统锁就可以了：
ps -e|grep apt-get
# 显示 28843 ?        00:00:00 apt-get
sudo kill 28843
```
> :pensive:安装软件出问题时
>
> E: 无法打开锁文件 /var/lib/dpkg/lock-frontend - open (13: 权限不够)
>
> E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
```shell
sudo -i
apt-get -f install
```
> 其他用户创建，删除文件等操作时
>
> 错误信息：sudo 提示XXX不在 sudoers 文件中，此事将被报告
>
```shell
sudo su
chmod 740 /etc/sudoers
vi /etc/sudoers
# 打开sudoers后，点击“i”进行编辑加上自己的用户名
# root ALL=(ALL:ALL) ALL
# xxx ALL=(ALL:ALL) ALL //xxx为用户名
```
- ### 录屏

```shell
# 快捷键：使用默认的录屏
# Ctrl + Alt + Shift + R
# 修改默认时长
gsettings set org.gnome.settings-daemon.plugins.media-keys max-screencast-length 60
```

```shell
# 或者安装录屏软件
sudo add-apt-repository ppa:obsproject/obs-studio
sudo apt update
sudo apt install obs-studio
```
- ### 默认背景图片路径

```shell
# /usr/share/backgrounds/
```
> :link:[壁纸网站](https://wallpaperscraft.com/)

- ### Remote Desktop with VNC Viewer

```shell
# 如果设置使用密码登录，可能需要运行：
gsettings set org.gnome.Vino require-encryption false
# 允许所有网络连接：
gsettings reset org.gnome.Vino network-interface
# 设置用户为自动登录，重启计算机，使用VNC Viewer即可正常访问
```
- ###### sudo systemctl edit apt-daily.timer

```shell
# apt-daily timer configuration override
[Timer]
OnBootSec=15min
OnUnitActiveSec=1d
AccuracySec=1h
RandomizedDelaySec=30min
```
## :sob:Uninstall ubuntu clearly

> [EFI分区](https://blog.csdn.net/qq_28057541/article/details/51723914)
>
> [删除grub引导](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)

```powershell
# 删除Linux分区（此时EFI分区删除不了）
# 在win10命令行下，删除ubuntu的EFI分区
# cmd 中输入 Diskpart
list disk
select disk 1
list partition
select partition 6
# 必须加override（强制），否则不能删除
delete partition override
# 再到powershell中卸载ubuntu的grub引导项 
diskpart
list disk
sel disk
list vol
sel vol 3
assign letter=Y
exit
cd Y:
ls
cd .\EFI\
rmdir .\ubuntu\
```

> [**去除在开机BIOS启动菜单（uefi菜单中）出现的ubuntu启动项**](https://blog.csdn.net/Vanepin/article/details/8927771)

```shell
# via a Live Ubuntu CD.
sudo apt-get install efibootmgr
sudo modprobe efivars
# then run sudo efibootmgr to check your boot entries.
sudo efibootmgr
# Then delete the option you dont want.In this example, Ubuntu is entry 2.
sudo efibootmgr -b 2 -B 
```
