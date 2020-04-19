# 在vultr上面搭建ssr
# 选择vps类型
1,目前vultr上面的产品大部分都已经是5$/m,只有少数几个地区有2.5$/m,但是尽量不要选，因为只支持ipv6,不支持ipv4;而剩下的3.5$/m的只有美国的New Jersey地区有，RAM:512M,Storage:10G,我只是用来搭建ssr，所以足够了。<br>
<a href="https://www.vultr.com/?ref=8541841"><img src="https://www.vultr.com/media/banners/banner_728x90.png" width="728" height="90"></a><br>
2,操作系统选择centos7,不要选择centos8，不支持的，而且默认也没装python <br>
3,如果不想使用密码登录，这个时候就要选择ssh key，其他都默认就可以

# 安装shadowsocks
1,使用putty远程连接后执行<br>
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssrmu.sh && chmod +x ssrmu.sh && bash ssrmu.sh

加密方式： aes-256-cfb ;
协议：origin ;
其他都默认就可以

2,安装完成可以随时使用以下命令来修改或者查看shadowsocks信息.<br>
<b>bash ssrmu.sh</b>

3,防火墙设置，可以在控制面板也可直接通过命令行执行，推荐命令行很方便 <br>
<b>firewall-cmd --zone=public --add-port=5688/tcp --permanent # 开通刚才shadowsocks设置的端口 <br>
firewall-cmd --reload  #重启防火墙

firewall-cmd --zone=public --list-ports  #查看设置的端口是否开启</b>

# 安装bbr加速
wget -N --no-check-certificate https://raw.githubusercontent.com/FunctionClub/YankeeBBR/master/bbr.sh && bash bbr.sh install

重启之后开启bbr<br>
<b>bash bbr.sh start </b>

# 查看ip端口被墙
国内： http://port.ping.pe/
国外：https://www.yougetsignal.com/tools/open-ports/

如果是端口被墙，修改shadowsocks的端口和防火墙设置就可以；如果是ip，可以重新建一个实例，删除原来的。

# Vultr注册链接
https://www.vultr.com/?ref=8541841
