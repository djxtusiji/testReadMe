wayi_backend代码
=============================
使用框架
-----------------------------
#[地址][https://www.wayi.cn]<br>
#项目中使用的框架
* 项目开发使用的是spring-boot
* 持久层框架，使用的是 Spring Data
* NoSql框架使用的是 Redis
* 页面使用vue
* 权限使用spring-security

代码结构
-----------------------------
#项目代码结构<br>
* wayi-hash 和云算力，矿机相关的数据库，以及业务操作。
* wayi-otc	和otc相关的数据库，以及业务操作
* wayi-pool	有关矿池的数据库，以及业务操作
* wayi-task 包含所有的定时器
* wayi-user 有关用户的相关操作
* wayi-utils parm相关数据库，以及业务操作;工具类。
* wayi-web	所有的controller，权限操作类。<br>
* wayi-web下的static文件中是存放vue编译好的前端文件的目录

#项目前后端关系<br>
>>	项目前端和后端分离，前端都是以vue编写，后端用java编码。controller都用@ResetController注解，前台访问后台controller之后，返回用Message封装的json数据。

#前后台权限控制<br>
>>	前后端项目的权限操作在 AuthUtils.java 中，将权限信息封装在token中传递给页面，再由页面以头部“Authorization”传回。

#项目代码编写习惯<br>
>>有关业务都是在service中实现的。

配置文件相关
-----------------------------
#配置文件全部放在resources<br>
* application-dev.properties 部署使用的配置文件
* application-local.properties 本地启动的配置文件
* application-service.properties 给前端部署使用的配置文件
* application-test.properties 测试网站部署使用的配置文件
* application.properties 
* logback-spring.xml 
* server.key https相关

部署时需要注意的事项
-----------------------------
* AuthUtils.java 第186-188行代码中  和 WebConfig.java 第8-9行注释都是和跨域相关的，因为当页面和我们分开开发的时候前端页面访问后端需要跨域，在部署的时候需要将跨域打开。
* 因为有权限控制，需要过滤的url需要放在 AuthUtils.java 的 configure 方法中。
* 在webApplication.java中配置了有关Https的.java配置。

导入工程
-----------------------------
#下载
* 先将项目fork 到自己账户中
* 通过git clone 将项目clone到本地

#idea
* 使用idea打开项目。
* 果不能识别maven项目,找到项目的总pom.xml文件，右键-" add as maven project"。
* 在file->Project Structure->Modules中将wayi-web下src/main/resources设置为Resources。<br>
#eclipse
* 使用eclipse的maven方式打开项目
* 找到wayi-web下的src/main/resources, 设置为Source Folder


本地启动
-----------------------------
* 调整项目开发环境为 jdk1.8
* 把wayi-web下application.properties 配置为local
* 执行 wayi-web下webApplication.java 的 main 方法启动项目


