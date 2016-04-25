# win7远程链接ubuntu桌面

##LXDE桌面 
注意：只适合lubuntu和服务器版，据说ubuntu会有unity兼容问题必须使用xfce

安装LXDE TightVNC桌面  
apt-get install xorg lxde-core tightvncserver  
启动VNC且设置密码  
tightvncserver :1  
然后输入2次密码  
停止VNC服务修改配置  
tightvncserver -kill :1  
修改配置  
sudo leafpad ~/.vnc/xstartup  
在最后一行加上下面脚本。  
lxterminal &
/usr/bin/lxsession -s LXDE &  
启动VNC设置分辨率  
vncserver :1 -geometry 1024x768 -depth 16 -pixelformat rgb565  

win7下运行输入mstsc
输入ip 后填写入用户名密码就可以看到桌面了

##ubuntu 使用XFCE4桌面
安装远程桌面服务器

sudo apt-get install xrdp 
sudo apt-get install vnc4server tightvncserver 
