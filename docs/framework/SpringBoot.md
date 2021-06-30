# SpringBoot  

1.[SpringBoot核心注解是什么,由哪几个注解组成,有什么作用](#springboot核心注解是什么)  
2.[SpringBoot启动过程主要做了哪些事情](#SpringBoot启动过程主要做了哪些事情)
## SpringBoot核心注解是什么,由哪几个注解组成,有什么作用 <span id='springboot核心注解是什么'></span>   
启动类上面的注解是`@SpringBootApplication`，它也是 Spring Boot 的核心注解，主要组合包含了以下 3 个注解：

1.`@SpringBootConfiguration`：组合了 @Configuration 注解，实现配置文件的功能。

2.`@EnableAutoConfiguration`：打开自动配置的功能，通过`@Import`加载META-INF/spring-factories 里自动装配的类 ,也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：`@SpringBootApplication(exclude = { DataSourceAutoConfiguration.class })`。

3.`@ComponentScan`：Spring组件扫描。  
  

## SpringBoot启动过程主要做了哪些事情   
1.创建了一个`SpringApplication`实例,给初始化器`ApplicationContextInitializer`、监听器`ApplicationListener`赋值，起到准备工作。  
2.执行run方法. 主要包括：  
2.1 加载 `SpringApplicationRunListeners`监听器，开启监听  
2.2 加载SpringBoot配置环境(ConfigurableEnvironment),将其加入`SpringApplicationRunListeners`监听器对象中
2.3 创建应用上下文 `ConfigurableApplicationContext`,将监听器、配置环境等赋值到 应用上下文 中去  
2.4 将含有 `@Import`,`@ComponentScan` 注解过的类实例化到容器中  
2.5 执行afterRefresh收尾工作


