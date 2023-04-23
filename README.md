# Sockd
**Dante socks5 server (v1.3.2/v1.4.2) auto-install and management script**


## Update

> #### 2022/11/26
> Upgrade default version for Debian as 1.4.2

> #### 2022/12/22
> Upgrade default version for Debian as 1.4.3

说明
Socks5属于明文代理，不要用于科学上网，否则会被阻断端口，可用于正常的跳板使用；
比如SSH转发加速国外VPS的连接速度，特别是一些延迟高或者丢包高的VPS；
使用Socks5转发后SSH就可以快速稳定的连接了，解决高丢包SSH断开的问题；

支持
支持系统
Debian7+ Ubuntu14.04+ CentOS6+

安装
下载脚本

wget --no-check-certificate https://raw.github.com/Lozy/danted/master/install.sh -O install.sh
安装脚本

bash install.sh  --port=端口 --user=用户名 --passwd=密码
其中的端口 用户名 密码自行修改后粘贴到SSH里运行安装即可；
完成后会提示Dante Server Install Successfuly即表示安装成功；
安装后如果连接不上，检查设置的端口是否已经放行；
说明：安装完成后会显示内网IP地址，但在实际使用的时候需要用外网IP地址；

使用
一般使用IP和用户名密码即可使用
如果需要固定IP或IP段，可以修改配置文件设置白名单

vi /etc/danted/sockd.conf
修改以下代码，改成你需要设置的白名单IP或IP段即可，然后重启使其生效；

client pass {
        from: 0.0.0.0/0  to: 0.0.0.0/0
}
卸载
bash install.sh --uninstall
命令
命令	或者	说明
service sockd start	/etc/init.d/sockd start	启动socks5服务器守护进程
service sockd stop	/etc/init.d/sockd stop	停止socks5服务器守护进程
service sockd restart	/etc/init.d/sockd restart	重新启动socks5服务器守护进程
service sockd reload	/etc/init.d/sockd reload	重新加载socks5服务器守护进程
service sockd status	/	系统进程状态
service sockd state	/etc/init.d/sockd state	运行状态
service sockd tail	/etc/init.d/sockd tail	sock 日志
service sockd adduser	/etc/init.d/sockd adduser	添加pam-auth用户：service sockd adduser NAME PASSWORD
service sockd deluser	/etc/init.d/sockd deluser	删除pam-auth用户：service sockd deluser NAME
