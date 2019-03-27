#支付宝小程序与微信小程序的django后台
##支付宝小程序
##微信小程序
##django后台环境搭建
1. 环境：腾讯云服务器Ubutu Server 18.04
2. 获取root权限（省去sudo麻烦）
	+ 输入密码
	> sudo passwd root
	+ 修改ssh登录配置，修改成允许root登录，修改PermitRootLogin的值为yes
	> sudo vim /etc/ssh/sshd_config
	+ 重启ssh服务
	> sudo service ssh restart
3. Install python3.6
	+ 使用编译的方法，下载python3.6的安装压缩包
	> wget https://www.python.org/ftp/python/3.6.0/Python-3.6.0.tgz
	+ 解压下载好的包
	> tar -xvf Python-3.6.0.tgz
	+ 创建安装的文件夹
	> mkdir /usr/local/python3
	+ 进入解压后的文件夹
	> cd Python-3.6.0
	+ 编译的时候指定程序存放路径
	> ./configure --prefix=/usr/local/python3
	+ 编译
	> make
	+ 安装依赖的包
	> apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \ </br>libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \ </br>xz-utils tk-dev
	+ 安装
	> make install
	+ mv /usr/bin/python /usr/bin/python_bak
	+ 建立软连接
	> ln -s /usr/local/python3/bin/python3 /usr/bin/python
	+ python -V
	> 显示python-3.6.0即为成功
4. Install pip3
	+ apt install python3-pip
	+ rm /usr/bin/pip3</br>ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
5. Install Django
	+ pip3 install django
6. Install uwsgi
	+ pip3 install uwsgi
	+ find / --name uwsgi
	> 找到uwsgi所在位置 (uwsgi location)
	+ 创建软连接
	> ln -s (uwsgi location) /usr/bin/uwsgi
	+ uwsgi --ini uwsgi.ini
	> uwsgi --reload uwsgi.pid,uwsgi --stop uwsgi.pid
7. Install nginx
	+ apt-get install nginx -y
	+ vim /etc/nginx/sites-enabled/nginx.conf
	+ sudo systemctl restart nginx
8. 配置域名
	+ 修改nginx.conf
	+ 修改/etc/hosts
9. 配置https
	+参照发行方的技术文档