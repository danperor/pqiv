## 编译时需要安装以下库
```
apt-cache search libgtk
sudo apt-get install libgtkd-3-dev
sudo apt-get install libgtk-3-dev
```
### 解决安装特定库时报未满足的依赖关系错误
```
下列软件包有未满足的依赖关系：
 libgtk-3-dev : 依赖: libgtk-3-0 (= 3.22.5.2+4nfs4) 但是 3.22.5.2+4nfs6 正要被安装
                依赖: gir1.2-gtk-3.0 (= 3.22.5.2+4nfs4) 但是 3.22.5.2+4nfs6 正要被安装

```
解决办法：

• 什么冲突安装什么

1）.错误中出现 >=的情形，直接安装这个软件。
2).错误中出现了=，就直接安装这个特定版本
```
sudo apt install libgtk-3-0=3.22.5.2+4nfs4
sudo apt install  gir1.2-gtk-3.0=3.22.5.2+4nfs4
```
3).最后再回头安装目标软件
先安装特定版本的库：libgtk-3-0和gir1.2-gtk-3.0

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
## pqiv 执行的时候报权限不足的问题
 将pqiv拷贝到制定目录之后，要给pqiv执行权限
 ```
 chmod +x pqiv
 ```
 ## pqiv添加不在任务栏显示程序图标功能
 2个函数；
 gtk_window_set_skip_taskbar

 ```
 void
gtk_window_set_skip_taskbar_hint (
  GtkWindow* window,
  gboolean setting
)
 ```
 ## pqiv 编译过程中，git窗口的几种类型
 ```
 GDK_WINDOW_TYPE_HINT_NORMAL	---可以穿透和最上，但显示在任务栏中
Normal toplevel window.

GDK_WINDOW_TYPE_HINT_DIALOG	 ---可以穿透和最上，不会现在在任务栏中，但右键弹出的菜单会遮盖
Dialog window.

GDK_WINDOW_TYPE_HINT_MENU	   ---可以穿透和最上，不会现在在任务栏中，但右键弹出的菜单会遮盖
Window used to implement a menu; GTK+ uses this hint only for torn-off menus, see GtkTearoffMenuItem.

GDK_WINDOW_TYPE_HINT_TOOLBAR	---可以穿透和最上，不会现在在任务栏中，但右键弹出的菜单会遮盖
Window used to implement toolbars.

GDK_WINDOW_TYPE_HINT_SPLASHSCREEN	
Window used to display a splash screen during application startup.

GDK_WINDOW_TYPE_HINT_UTILITY	
Utility windows which are not detached toolbars or dialogs.

GDK_WINDOW_TYPE_HINT_DOCK	
Used for creating dock or panel windows.

GDK_WINDOW_TYPE_HINT_DESKTOP	---不可以在最上
Used for creating the desktop background window.

GDK_WINDOW_TYPE_HINT_DROPDOWN_MENU	
A menu that belongs to a menubar.

GDK_WINDOW_TYPE_HINT_POPUP_MENU	
A menu that does not belong to a menubar, e.g. a context menu.

GDK_WINDOW_TYPE_HINT_TOOLTIP	
A tooltip.

GDK_WINDOW_TYPE_HINT_NOTIFICATION	
A notification - typically a “bubble” that belongs to a status icon.

GDK_WINDOW_TYPE_HINT_COMBO	
A popup from a combo box.

GDK_WINDOW_TYPE_HINT_DND	
A window that is used to implement a DND cursor.
 ```