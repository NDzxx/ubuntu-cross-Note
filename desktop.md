# win7远程链接ubuntu桌面

##LXDE桌面 
sudo apt-get install xrdp
sudo apt-get install vnc4server
建议采用这种，占资源比较小

安装LXDE TightVNC桌面  
apt-get install xorg lxde-core tightvncserver 
启动VNC且设置密码  
tightvncserver :1  
然后输入2次密码  
停止VNC服务修改配置  
tightvncserver -kill :1  
修改配置  
lubuntu下  
sudo leafpad ~/.vnc/xstartup  
ubuntu下  
sudo gedit ~/.vnc/xstartup  
在最后一行加上下面脚本。  
lxterminal &
/usr/bin/lxsession -s LXDE &  
启动VNC设置分辨率  
vncserver :1 -geometry 1024x768 -depth 16 -pixelformat rgb565  



##Windows下的操作：

　　打开“运行”，输入mstsc，回车后填上你要连接的Ubuntu的IP地址即可。在Ubuntu下可以通过“ifconfig”获得本机网络连接的概况，其中包括IP地址。

　　填上正确的IP地址回车，会出现一个登陆框，我们选择“sessman-xvnc”这个，然后输入你的Ubuntu的用户名和密码，OK！ 