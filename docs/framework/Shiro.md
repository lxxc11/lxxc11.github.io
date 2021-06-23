# Shiro  

1.[简述Shiro的3个核心组件](#简述Shiro的3个核心组件)  
2.[简述Shiro的登入运行流程](#简述Shiro的登入运行流程)  

## 1.简述Shiro的3个核心组件  
### 1.Subject  
正与系统进行交互的人, 或某一个第三方服务.
所有 Subject 实例都被绑定到一个SecurityManager 上。

### 2.SecurityManager  
Shiro 架构的心脏, 用来协调内部各安全组件, 管理内部组件实例, 并通过它来提供安全管理的各种服务.
当 Shiro 与一个 Subject 进行交互时, 实质上是幕后的 SecurityManager 处理所有繁重的 Subject 安全操作。

### 3.Realm  
本质上是一个特定安全的 DAO. 当配置 Shiro 时, 必须指定至少一个 Realm 用来进行`身份验证和授权`.
Shiro 提供了多种可用的 Realms 来获取安全相关的数据. 例如关系数据库(JDBC), INI 及属性文件等.
可以定义自己 Realm 实现来代表自定义的数据源。  

## 2.简述Shiro的登入运行流程  
1.首先调用Subject.login(token)进行登录，他会委托给SecurityManager  
```java
		UsernamePasswordToken token = new UsernamePasswordToken(userName, password);
		Subject subject = SecurityUtils.getSubject();
		subject.login(token);
```  
2.SecurityManager负责真正的身份验证逻辑；它会委托给Authenticator进行身份验证；  

3.Authenticator会把相应的token传入Realm，从Realm获取身份验证信息，如果没有就返回认证失败，有的话就继续执行操作。 

