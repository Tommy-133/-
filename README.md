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

git设置

1.git config --global user.name "你的名字或昵称"

　git config --global user.email "你的邮箱"

2.git init

  git remote add origin <你的项目地址> //注:项目地址形式为:https://gitee.com/xxx/xxx.git或者 git@gitee.com:xxx/xxx.git

3.如果你想克隆，只需要执行命令
  
  git clone <项目地址>


/*
SQLyog 浼佷笟鐗?- MySQL GUI v8.14
MySQL - 5.1.49-community : Database - sushe
*********************************************************************
*/


/*!40101 SET NAMES utf8 */;

/*!40101 SET SQL_MODE=''*/;

/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;
CREATE DATABASE /*!32312 IF NOT EXISTS*/`sushe` /*!40100 DEFAULT CHARACTER SET utf8 */;

USE `sushe`;

/*Table structure for table `admin` */

DROP TABLE IF EXISTS `admin`;

CREATE TABLE `admin` (
  `Admin_ID` int(11) NOT NULL AUTO_INCREMENT,
  `Admin_Username` varchar(20) DEFAULT NULL,
  `Admin_Password` varchar(20) DEFAULT NULL,
  `Admin_Name` varchar(20) DEFAULT NULL,
  `Admin_Sex` varchar(10) DEFAULT NULL,
  `Admin_Tel` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`Admin_ID`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

/*Data for the table `admin` */

insert  into `admin`(`Admin_ID`,`Admin_Username`,`Admin_Password`,`Admin_Name`,`Admin_Sex`,`Admin_Tel`) values (1,'java1234','123','admin','',NULL);

/*Table structure for table `building` */

DROP TABLE IF EXISTS `building`;

CREATE TABLE `building` (
  `Building_ID` int(11) NOT NULL AUTO_INCREMENT,
  `Building_Name` varchar(50) DEFAULT NULL,
  `Building_Introduction` varchar(1000) DEFAULT NULL,
  PRIMARY KEY (`Building_ID`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;

/*Data for the table `building` */

insert  into `building`(`Building_ID`,`Building_Name`,`Building_Introduction`) values (1,'妤煎畤1','杩欎釜妤煎畤1'),(2,'妤煎畤2','杩欎釜妤煎畤2');

/*Table structure for table `domitory` */

DROP TABLE IF EXISTS `domitory`;

CREATE TABLE `domitory` (
  `Domitory_ID` int(11) NOT NULL AUTO_INCREMENT,
  `Domitory_BuildingID` int(11) DEFAULT NULL,
  `Domitory_Name` varchar(20) DEFAULT NULL,
  `Domitory_Type` varchar(20) DEFAULT NULL,
  `Domitory_Number` varchar(20) DEFAULT NULL,
  `Domitory_Tel` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`Domitory_ID`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;

/*Data for the table `domitory` */

insert  into `domitory`(`Domitory_ID`,`Domitory_BuildingID`,`Domitory_Name`,`Domitory_Type`,`Domitory_Number`,`Domitory_Tel`) values (1,1,'11','11','11','11'),(2,2,'002','鍝堝搱','12','312');

/*Table structure for table `log` */

DROP TABLE IF EXISTS `log`;

CREATE TABLE `log` (
  `Log_ID` int(11) NOT NULL AUTO_INCREMENT,
  `Log_StudentID` int(11) DEFAULT NULL,
  `Log_TeacherID` int(11) DEFAULT NULL,
  `Log_Date` varchar(50) DEFAULT NULL,
  `Log_Remark` varchar(1000) DEFAULT NULL,
  PRIMARY KEY (`Log_ID`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

/*Data for the table `log` */

insert  into `log`(`Log_ID`,`Log_StudentID`,`Log_TeacherID`,`Log_Date`,`Log_Remark`) values (1,2,1,'2013-04-10','we');

/*Table structure for table `out1` */

DROP TABLE IF EXISTS `out1`;

SELECT * FROM mysql_user m;

/*Data for the table `out1` */

insert  into `out1`(`Out_ID`,`Out_StudentID`,`Out_Date`,`Out_Remark`) values (1,'2','2013-4-28','13'),(2,'1','2013-4-28','鎼滅储');

/*Table structure for table `student` */

DROP TABLE IF EXISTS `student`;

CREATE TABLE `student` (
  `Student_ID` int(11) NOT NULL AUTO_INCREMENT,
  `Student_DomitoryID` int(11) DEFAULT NULL,
  `Student_Username` varchar(20) DEFAULT NULL,
  `Student_Password` varchar(20) DEFAULT NULL,
  `Student_Name` varchar(20) DEFAULT NULL,
  `Student_Sex` varchar(20) DEFAULT NULL,
  `Student_Class` varchar(20) DEFAULT NULL,
  `Student_State` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`Student_ID`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;

/*Data for the table `student` */

insert  into `student`(`Student_ID`,`Student_DomitoryID`,`Student_Username`,`Student_Password`,`Student_Name`,`Student_Sex`,`Student_Class`,`Student_State`) values (1,2,'001','123','瀛︾敓涓€','鐢?,'08璁℃湰','杩佸嚭'),(2,1,'002','123','鍙?,'濂?,'鑼冨痉钀?,'鍏ヤ綇');

/*Table structure for table `tb` */

DROP TABLE IF EXISTS `tb`;

CREATE TABLE `tb` (
  `TB_ID` int(11) NOT NULL AUTO_INCREMENT,
  `TB_TeacherID` int(11) DEFAULT NULL,
  `TB_BuildingID` int(11) DEFAULT NULL,
  PRIMARY KEY (`TB_ID`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

/*Data for the table `tb` */

insert  into `tb`(`TB_ID`,`TB_TeacherID`,`TB_BuildingID`) values (1,1,1);

/*Table structure for table `teacher` */

DROP TABLE IF EXISTS `teacher`;

CREATE TABLE `teacher` (
  `Teacher_ID` int(11) NOT NULL AUTO_INCREMENT,
  `Teacher_Username` varchar(20) DEFAULT NULL,
  `Teacher_Password` varchar(20) DEFAULT NULL,
  `Teacher_Name` varchar(20) DEFAULT NULL,
  `Teacher_Sex` varchar(10) DEFAULT NULL,
  `Teacher_Tel` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`Teacher_ID`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

/*Data for the table `teacher` */

insert  into `teacher`(`Teacher_ID`,`Teacher_Username`,`Teacher_Password`,`Teacher_Name`,`Teacher_Sex`,`Teacher_Tel`) values (1,'Teacher1','123','妤煎畤绠＄悊鍛?','濂?,'123');

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;
