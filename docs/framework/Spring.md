# Spring  
1.[@Component和@Bean的区别是什么](#@Component和@Bean的区别是什么)  

## @Component和@Bean的区别是什么  
1.作用对象不同。@Component注解作用于类、接口、枚举，而@Bean注解作用于方法、注解。

2.@Component注解通常是通过类路径扫描来自动侦测以及自动装配到Spring容器中（我们可以使用@ComponentScan注解定义要扫描的路径）。  
@Bean注解通常是在标有该注解的方法中定义产生这个bean，告诉Spring这是某个类的实例，当我需要用它的时候还给我。

3.@Bean注解比@Component注解的自定义性更强，而且很多地方只能通过@Bean注解来注册bean。比如当引用第三方库的类需要装配到Spring容器的时候，就只能通过@Bean注解来实现。