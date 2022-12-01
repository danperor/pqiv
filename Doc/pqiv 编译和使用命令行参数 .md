## 编译时需要安装以下库
sudo apt-get install libgtkd-3-dev
apt-cache search libgtk
## 编译错误解决：
报错：
对‘gdk_x11_window_get_xid’未定义的引用
collect2: error: ld returned 1 exit status

改为如下配置后重新make
./configure --gtk-version=3 --prefix=/home/dp/code/dependlib

## 使用命令行参数： 
### 一般使用：
pqiv --click-through --transparent-background --hide-info-box --keep-above  alphatest.png 
### Wayland下报错的话使用如下配置：
GDK_BACKEND=x11 pqiv --click-through --transparent-background --hide-info-box --keep-above  alphatest.png 
