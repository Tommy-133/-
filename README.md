在忘记root密码的时候，可以这样

以windows为例：   

1. 关闭正在运行的MySQL服务。  
 
2. 打开DOS窗口，转到mysql\bin目录。  

3. 输入mysqld --skip-grant-tables 回车。--skip-grant-tables 的意思是启动MySQL服务的时候跳过权限表认证。  

4. 再开一个DOS窗口（因为刚才那个DOS窗口已经不能动了），转到mysql\bin目录。  

5. 输入mysql回车，如果成功，将出现MySQL提示符 >。  

6. 连接权限数据库： use mysql; 。  

6. 改密码：update user set password=password("123") where user="root";（别忘了最后加分号） 。 
 
7. 刷新权限（必须步骤）：flush privileges;　。  
 
8. 退出 quit。  

9. 注销系统，再进入，使用用户名root和刚才设置的新密码123登录。

## 直接解压mysql-advanced-5.7.27-win32.zip

1.解压后，初始化MySQL的：

```
mysqld-初始化
```

   执行完成后，会输出root用户的初始初始密码

2.安装成为的Windows服务：

```
mysqld安装
```

3.启动MySQL：

```
启动mysqld
```

4. Mysql安装成功后，默认的root用户密码为空，需要创建root用户的密码：

```
mysqladmin -u root密码“ new_password”；
```

5.连接到mysql的服务器：

```
mysql -u root -p
输入密码：*******     
```

6.解压的MySQL-GUI的工具-noinstall-5.0-R17-Win32中，用MySQLQueryBrowser工具创建数据库，创建表

## 运行安装程序的MySQL的安装程序，商业8.0.17.0.msi：

    https://blog.csdn.net/bobo553443/article/details/81383194
    注意安装的时候要输入用户名，密码
    安装完成后可以用工作台来创建数据库，创建表

## 遇到的问题

1.命令行可访问的MySQL，但GUI工具连接不上的MySQL

```
mysql> ALTER USER'root'@'localhost'与mysql_native_password标识为'123456';
```

2.修改密码：

```
mysql> ALTER USER'root'@'localhost'由'123456'密码永不过期；
```

3.忘记密码无法登陆：

停止MySQL服务，删除数据文件夹，重新运行mysqld --initialize
