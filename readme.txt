
   1.系统基础环境配置：

        关闭selinux；

            vi /etc/sysconfig/selinux

            设置：SELINUX=disabled

            保存，退出，需重启生效。

        防火墙关闭；

            service iptables stop

            chkconfig iptables off

        检查启动列表，关闭无用的程序；

            chkconfig sendmail off

            chkconfig ip6tables off

        安装中文支持：

            yum groupinstall chinese-support -y

    2.安装数据库：

        yum install mysql mysql-server -y

        设置开机启动，并启动：

            chkconfig mysqld on

            service mysqld start

        设置mysql安全启动脚本：

            mysql_secure_installation

            回车：

            Set root password? [Y/n] 选择：n 回车（安装不修改root密码）

            Remove anonymous users? [Y/n] 选择：n 回车（删除匿名用户）

            Disallow root login remotely? [Y/n] 选择：n回车（禁止root远程登录）

            Remove test database and access to it? [Y/n] 

            选择：y 回车（删除test测试数据库）

            Reload privilege tables now? [Y/n]

            选择：y 回车（现在重新加载数据库）

         设置数据库支持utf8：

            参考：http://506554897.blog.51cto.com/2823970/1902098

    4.安装java环境：

        rpm -ivh jdk-1_5_0_08-linux-i586.rpm 

        配置环境变量：

          vi /etc/profile

          添加一下内容

            export JAVA_HOME=/usr/java/jdk1.5.0_08

            export CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib

            export PATH=$PATH:$JAVA_HOME/bin 

        应用环境变量：

        source /etc/profile        
        tar -zxvf apache-tomcat-5.5.15.tar.gz -C /usr/ 
		rpm -ivh perl-DBI-1.40-5.i386.rpm
        rpm -ivh emp-2.1.2-0.noarch.rpm
        rpm -ivh mbx3000-2.1.2-0.i586.rpm
        rpm -ivh ivr-2.1.2-0.i586.rpm
		rpm -ivh vos3000-2.1.2-0.i586.rpm

 9.创建license：
运行vos注册机bin文件
查RPM Time；VOS Time；JDK Time值并记录
输入MAC时一定要大写 中间要用短横杆代替
例：A1-B2-C3-D4-F5-G6
运行vos注册机
输入到期年月日,mac和ip，还有RPM Time；VOS Time；JDK Time和公司名称等就可以注册成功了。
例：
[root@vos vos2009_V2.1.2.0]# ./vos20092120
Year :2030
Month :8
Day :10
MAC Address:00-0C-29-66-49-49
JDK Time:1362120490
RPM Time:1362119866
VOS Time:1362120705
IP Address:192.168.18.18
Company :voiptongxin
VOS FUNC(1/0):1
IVR SERVICELIMIT:10000
MBX CALLLIMIT:10000
License Data:


        在/usr/kunshi/下面创建license文件夹；

      在文件夹下创建一个license.dat文件

        将注册好生成的license data：下边的所有数据拷贝到license.dat文件里。

       license data生成方式在下载的包里有。

        重启系统生效：shutdown -r now 


    10.客户端安装VOS3000 V2.1.2.0：

        VOS3000-client-v2.1.2.0.exe 双击即可安装

        客户端连接：默认用户名/密码：admin/admin


    11.启动服务命令：

        /etc/init.d/vos3000dall restart

        /etc/init.d/mbx3000d restart 

         /etc/init.d/ivrd restart 