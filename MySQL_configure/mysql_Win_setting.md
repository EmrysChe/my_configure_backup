# MySQL的Windows下的安装配置

## MySQL官网

[https://www.mysql.com](https://www.mysql.com)

## 一. 将从官网下载的包解压到指定的路径，自己可以指定路径.

例如:

> F:\DevelopSoftFolder\mysql-5.7.19-winx64

## 二. 配置环境变量

我的电脑->属性->高级->环境变量

选择PATH,在其后面添加MySQL的bin文件夹的路径.

比如当bin文件夹的路径为:

>F:\DevelopSoftFolder\mysql-5.7.19-winx64\bin

则在PATH后追加文件路径

比如:

```
PATH=.......;F:\DevelopSoftFolder\mysql-5.7.19-winx64\bin
```

## 三. my-default.ini文件

5.7.18版本以后,解压后,就不带my-default.ini文件,需要手动创建好my.ini文件,然后放置到指定的目录下.

我的my-default.ini文件配置为:

```
[client]
# 设置3306端口
port=3306
default-character-set=utf8
[mysqld]
# 设置3306端口
port=3306
# 服务器端使用的字符集为utf8
character_set_server=utf8
# 允许最大连接数
max_connections=200
# MySQL安装目录
basedir=F:\DevelopSoftFolder\mysql-5.7.19-winx64
# MySQL数据存放目录
datadir=F:\DevelopSoftFolder\mysql-5.7.19-winx64\data
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB 
[WinMySQLAdmin]
F:\DevelopSoftFolder\mysql-5.7.19-winx64\bin\mysqld.exe
```

建立好my-default.ini后放置在bin文件夹下.

## 四. 安装
1. 使用管理员身份打开cmd或者powershell.
2. 切换目录至MySQL包所在的bin目录(其实不用切换到这个目录下面，因为前面已经把MySQL加入到环境变量中了,以防万一而已).然后输入:

```
mysqld.exe -install
```

执行命令后,提示:

>Service successfully installed.

表示安装成功.

3. 初始化MySQL数据,并创建一个具有空密码的root用户:

```
mysqld --initialize-insecure --user=mysql
```

4. 启动MySQL服务

```
net start mysql
```

5. 设置MySQL的root用户密码:

```
mysqladmin -u root -p password
```

原本的密码是空的,如果为了安全,可以修改密码,如果不在意,可以不改.

6. 登录MySQL:

```
mysql -u root -p
```

7. 关闭MySQL服务:

```
net stop mysql
```

如果没强迫症,其实可以一直开着,用起来方便点,当然,可能有大佬们会说,这么做其实有点危险.

8. 删库跑路:

```
mysqld --remove
```

## 五. 其他:

某些在安装过程中,某些安(liu)全(mang)软件可能会报毒或者跳出默认是阻止操作的窗口,如果是从官网下的,不用担心,这玩意儿肯定没危险,如果你看着不爽,请先关掉这些软件,或者,等它跳出来的时候选择允许操作(运气不好可能会点错，然后GG).

百度上可能会找到什么破解版之类的,或者老版本什么鬼的,建议去官网下,这玩意儿有社区版,免费的,没必要冒危险去下,官网的在线安装版操作会比较简单,但因为某些不可描述的原因,速度会超级慢,当然,科学上网的话就不用怕了,对于有点计算机知识的(不懒不傻的)一般人,下压缩包会靠谱点(如果这都嫌慢,可以去国内的一些镜像站下，推荐[清华大学tuna协会](tuna.moe)镜像地址：[https://mirrors.tuna.tsinghua.edu.cn/mysql](https://mirrors.tuna.tsinghua.edu.cn/mysql),不过我好像没找到Windows的压缩包,其实,如果你不会耍点小聪明,或者你很有钱,你家网速贼快,那么,如果直接用浏览器下,不过官网或者国内镜像站,你都会感到很慢).