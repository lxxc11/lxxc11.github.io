# Nacos  

1.[Nacos如何实现服务自动注册](#Nacos如何实现服务自动注册)  

## Nacos如何实现服务自动注册  
1.在spring.factories里配置了一个 `NacosServiceRegistryAutoConfiguration`,在启动SpringBoot中会自动装配到IOC容器里。    
2.`NacosServiceRegistryAutoConfiguration`里实例化了`NacosAutoServiceRegistration`注册器,`NacosAutoServiceRegistration`实现了`AbstractAutoServiceRegistration<Registration>`  
3.`AbstractAutoServiceRegistration`实现了监听`WebServerInitializedEvent`事件的监听器`ApplicationListener<WebServerInitializedEvent>`,在 `onApplicationEvent`方法中主要有模拟HTTP请求，向注册中心注册服务的功能。  
4.Spring boot 在Tomcat发布成功后会发布(publishEvent) `WebServerInitializedEvent`事件，触发 `onApplicationEvent`方法的执行，完成注册。 