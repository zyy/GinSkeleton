### 这是什么?  
>   1.这是一个基于go语言gin框架的web项目骨架，其目的主要在于将web项目主线逻辑梳理清晰，最基础的东西封装完善，开发者更多关注属于自己的的业务即可。  
>   2.本项目骨架封装了以`tb_users`表为核心的全部功能（主要包括用户相关的接口参数验证器、注册、登录获取token、刷新token、CURD以及token鉴权等），开发者拉取本项目骨架，在此基础上就可以快速开发自己的项目。  
####    开箱即用
>   1.安装的go语言版本最好>=1.14,只为更好的支持 `go module` 包管理.  
>   2.配置go包的代理，参见`https://goproxy.cn`,有详细设置教程.  
>   3.使用 `goland(>=2019.3版本)` 打开本项目，找到`database/db_demo.sql`导入数据库，自行配置账号、密码、端口等。  
>   4.双击`main.go`，进入代码界面，鼠标右键`run`运行本项目，首次会自动下载依赖， 片刻后即可启动.  
>   5.`windwos`开发环境编译`linux`环境项目：goland终端底栏打开`terminal`,依次执行 `set GOARCH=amd64` `set GOOS=linux` `set CGO_ENABLED=0` `go build`即可。  
>![avatar](http://139.196.101.31:2080/GinSkeleton.jpg)  

####    压力测试  
>   2核4g云服务器，并发（Qps）可以达到1w+，所有请求100%成功！  
![avatar](http://139.196.101.31:2080/concurrent.png)  


####    框架使用文档  
[进入项目骨架介绍文档](./Document.md)  

####    本项目测试用例路由  
[进入Api接口测试用例文档](./ApiDoc.md)   
>GET    /                         
>GET   /Admin/ws         
>POST   /Admin/users/register     
>POST   /Admin/users/login        
>POST   /Admin/users/refreshtoken        
>GET    /Admin/users/index        
>POST   /Admin/users/create       
>POST   /Admin/users/edit         
>POST   /Admin/users/delete       
>POST   /Admin/upload/file     

#### 版本
V 1.0.12   2020-05-06(5月份开发计划预告)   
>   1.增加CURL客户端，封装完善好用的http请求模块系列功能。  
>   2.增加消息队列，RabbitMq。  
>   3.关键、核心代码编写更多的单元测试。   

V 1.0.11   2020-04-30   
>   1.`SqlServer`、`Mysql`驱动初始化代码相似度比较高，因此进行了优化合并。   
>   2.`SqlServer`、`Mysql`操作基类进一步完善，规范日志记录。  
>   3. 增加项目骨架使用文档。    

V 1.0.10   2020-04-29   
>   1.`websocket`功能开发完成,特色如下：  
>   1.1 屏蔽底层繁琐的基础设置，使用超级简单，对于开发者只需要关注`OnOpen`、`OnMessage`、`OnError`、`OnClose` 事件即可。     
>   1.2 严格按照`websocket`协议实现，服务器、浏览器自动隐式维护心跳，开发者只需要关注业务的核心数据交互，无需额外维护任何形式的心跳数据包。  
>   1.3 `websocket`服务模块默认不开启，若有需要请在配置文件`Config/Config.yaml ` 中开启。  
>   2 `SqlServer`数据库驱动以及相关Api封装完成，像其他数据库一样具有完善的连接池，无感知调用。  

V 1.0.09   2020-04-25  
>   1.增加用户`token`刷新接口，精简刷新逻辑代码。  
>   2.完善用户密码加密存储方式，同步更新`DataBase/db_demo.sql`文件。       
 
V 1.0.08   2020-04-24 
>   1.增加SnowFlake算法，用于全局生成唯一ID，便于业务使用。  
>   2.封装MD5函数，方便快速调用。      
>   3.文件上传公共模块完善，存储文件自动使用SnowFlake、MD5算法生成全局唯一名称存储。      

V 1.0.07   2020-04-23 
>   1.自定义错误常量包名调整：Errors——>MyErrors，避免和系统错误包名称混淆。  
>   2.文件上传公共模块示例代码完善。    
>   3.路由增加静态资源处理以及相关说明。      
>   4.验证器示例代码进一步简洁清晰化、同时增加了最常用的注释说明（参见：App\Http\Validator\Users\Register.go）。      

V 1.0.06   2020-04-22 
>   1.完善文件上传公共模块，增加文件上传最大值限制，允许的文件`mimetype`类型设置。  
>   2.文件上传验证器同步增加验证条件相关的代码、全部错误代码、提示消息、yaml配置项等。     
>   3.验证器初始化加载顺序由原来的验证器调用时加载调整为程序启动时加载。     
>   4.增加跨域，默认开启，该功能与 `nginx` 跨域二选一。       

V 1.0.05   2020-04-20 
>   1.增加`json`统一返回逻辑。  
>   2.用户模块核心逻辑全部完成（注册、登录、`token`授权、`token`认证、`CURD`等操作）。   
>   3.全局常量增加`CURD`常用的列表。  
>   4.增加`Service`层逻辑，并提供相关的示例代码。     
>   5.继续精简代码，使本项目骨架逻辑主线更加清晰，快速上手。       
>   6.更新本项目所必须的数据库`db_demo.sql`文件。       
>   7.精简代码，基本的业务操作只保留`tb_users`表的完整操作示例代码。         
>   8.增加文件上传公共模块，供任何有需要上传文件的业务模块调用。            
>   9.日志存储路径调整为全局变量统一定义。        

V 1.0.04   2020-04-19 
>   1.路由——>中间件——>表单验证器——>控制器 上下文数据一致性开发完成。    
>   2.验证器结构调整，将业务部分和系统核心部分分离，开发者只需更多关注业务即可。  
>   3.增加项目骨架所需的demo数据库。      

V 1.0.03   2020-04-17   
>   1.增加`linux`环境`chan signal`监听信号值，使程序在退出时，更加优雅，资源的释放更加完善。    

V 1.0.02   2020-04-16 
>   1.容器、事件注册器调整命名规范，增加模糊处理函数。        

V 1.0.01   2020-04-15 
>   1.增加容器，将一些比较繁琐的功能模块率先注册在容器，方便后续调用。  
>   2.表单参数验证器首先注册在容器，避免在路由模块不停地引入表单验证器造成该文件过于庞大。   
>   3.函数类事件精简代码，删除原有的一个键对应多个事件的逻辑，目前设置为键值一一对应关系。   
>   4.Mysql、Redis数据库连接的释放统一注册在函数事件管理器，由程序退出时统一释放。   
>   5.容器存储变量修改为sync.map，避免了并发情况下发生bug。     

V 1.0.00   2020-04-14 
>   1.基于gin框架的web项目骨架.  
>   2.开发单体应用基本的功能模块全部已经封装完毕.  
