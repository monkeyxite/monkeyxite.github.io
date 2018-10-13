<html><body><p>如果 MySQL 正在运行，首先杀之： killall -TERM mysqld。
启动 MySQL ：mysqld_safe --skip-grant-tables &amp;
就可以不需要密码就进入 MySQL 了。
然后就是
&gt;use mysql
&gt;update user set password=password("new_pass") where user="root";
&gt;flush privileges;
重新杀 MySQL ，用正常方法启动 MySQL</p></body></html>