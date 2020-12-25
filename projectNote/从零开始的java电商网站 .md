# 从零开始的企业级别java电商网站

> Spring + springMvc+Mybatis

 整个项目的架构是由基础到复杂,希望你可以通过这个过程学习到真实的项目开发经验.

## 第一章 项目导学

### **课程安排**

1. 环境搭建 :分别从windows和centos搭建开发环境
2. 数据库及接口:学习数据库的表关系设计
3. 项目初始化:学习Maybatis三剑客的使用以及便利于开发插件与Ide工具
4. 用户模块
5. 分类模块:
6. 商品模块:前台\后天部分,ftp的对接,文件上传
7. 购物车模块:封装复用性强的购物车模块
8. 收货地址模块
9. 支付模块:集成支付宝的模块
10. 订单模块:前/后  
11. 云服务器发布

### 架构演变介绍 

> 根据老师讲解的粗浅理解

一个项目部署的架构,主要是三部分内容:`应用程序` `数据数据库` `文件系统`,项目用户量较少时可以全部部署到一台服务器上.

随着用户量的增加,可以考虑将应用程序与服务器间的分离,应用程序部署到高cpu运行的服务器上,`文件系统` 与`数据数据库`部署到存储空间较大的服务器上

随着应用程序的使用,发现一部分接口数据变化较小,不需要每次都重新请求.为了提高性能我们可以考虑将一部分数据做缓存,缓存分为本地缓存与远程缓存(单机缓存\集群缓存).

 单个服务器的性能是有上限的,随着配置增高价格会指数型增长,我们可以考虑搭多个服务器缓解压力.集群服务器-负载均衡调度

服务器集群式分布后,用户的身份验证可能只在一台服务器上存在,如何解决呢.演变趋势:` 身份验证多台服务器同步` `身份验证存于cookie` `身份验证作为一个单独的模块\服务器`

在集群式服务器下数据库的数据存储压力过大,考虑分为读取服务器\存储服务器.或者按照模块功能分类.可能存在不同地区的服务器访问功能问题,cdn解决

**项目的架构是随着`技术` `功能要求` 不断变化的,建议根据自己的需求选择使用最适宜的项目架构**



## 第二章环境搭建

**项目环境需要的安装包**:http://learning.happymmall.com/

jdk

tomcat

### Maven

**常用命令**

- 清除命令 mvn clean
- 编译命令 mvn compile
- 打包命令  mvn package
- 跳过单元测试 mvn clean package-Dmaven.test.skip=true

### vsftpd 

> 完全免费,开放源代码的ftp服务器

### Nginx

**常用命令**

- 测试配置文件

  nginx-t

- 启动命令

  nginx

- 停止命令

  nginx -s stop  或者 nginx -s quit
  
-  重启命令
	nginx -s reload
	
- 查看进程命令

  ps -ef | hrep nginx

- 平滑重启

  kill -HUP  [Nginx主进程号(即查看进程命令查到的PID)]

 ### Mysql

**常用命令**

* 登录

```sql
mysql -u root -p 
```



* 查看当前mysql的用户

```sql
select user.host.password from mysql.user
```
* 修改root密码

```sql
set password for root@127.0.0.1 = password("yourpassword")
```

* 退出

```
exit			
```

* 使操作生效

```
flush privileges
```

* 赋予本地用户所有权限

```sql
 grant all privileges on mmall.* to sunsf @localhost identified by 'sunsf';
```

* 给账户开通外网所有权限

```sql
grant all privileges on mmall.* to 'sunsf' @'%' identified by 'sunsf';
```

mmall.可以指数据库下的哪张表 \ @'%'可以指定哪个外网端口号可以访问

### Git

**git基础设置**

> global是全局变量配置

* 配置用户名(提交时引用)

```git
git config --global user.name "账户名称"
```

* 配置邮箱(提交时引用)

```
config --global user.email "邮箱账号"
```

* git 忽略Windows/unix换行符转换

```
git config --global core.autocrlf false
```

**编码配置**

* 避免git gui中中文乱码

  ```
  git config --global gui.endcoding utg-8
  ```

* 避免git status 显示的中文文件名乱码

  ```
  git config --global core.quotepath off
  ```

### 数据表结构关系

* 表之间的关系
* 唯一索引与组合索引
* 后悔药-时间戳



## 三:项目初始化

> 包含Maven\jdk\mybatis\mybatis三剑客安装配置,都是简单内容就不记录了



## 四:用户模块开发

> Wiki地址: https://gitee.com/imooccode/happymmallwiki/
>
> 笔记网址:https://www.cnblogs.com/chen-chen-chen/p/12295138.html
>
> https://www.imooc.com/article/284560



