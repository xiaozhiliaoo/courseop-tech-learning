# Spring Core

container:configuration model + dependency injection

Lightweight and minimally invasive development with POJOs
Loose coupling through DI and interface orientation
Declarative programming through aspects and common conventions
Eliminating boilerplate code with aspects and templates

Spring一个包里面的support都是接口的便利实现。

## 核心对象
BeanWrapper,PropertiesEditor

BeanFactory,XmlBeanFactory,ListableBeanFactory

BeanDefinition

ApplicationContext,WebApplicationContext,

xxxTemplate(JDBC,JMS)

Resource,AbstractResource,ResourceLoader

BeanDefinitionRegistry,BeanDefinition,

异常处理：受检成运行，捕获能处理

Spring源码先看Interface，在看Interface继承关系，在看AbstractInterface

AbstractInterface里面的protected方法和属性需要注意。没有protected属性，说明不是为了继承而设计的。

spring aop的实现？

spring ioc的实现？

spring 事务的实现？

## AOP

Aspect：跨多个类的模块化横切点
Join point：程序执行的地点。
Advice：程序执行的地方发生的操作。
Pointcut：满足程序执行地点的条件。
Introduction：代表类型声明其他方法或字段
Target object: 被多个Aspect Advice的对象
AOP proxy:
Weaving:

join points matched by pointcuts is the key to AOP

auto-proxying

aop is proxy-based frameworks

动态代理失效： AspectJ does not have this self-invocation issue because it is not a proxy-based AOP framework.

Pointcut以及实现.




## Data Access

JDBC,DAO(二级抽象),ORM(JPA,Hibernate),Spring-Data-JDBC,spring-boot-starter-data-jdbc
一级(低级别抽象)：一个控制JDBC工作流程和错误处理的框架。 org.springframework.jdbc.core 核心JdbcTemplate
二级(高级别抽象)：RDBMS操作建模Java对象操作 - org.springframework.jdbc.object 核心RdbmsOperation
ORM:org.springframework.orm

mybatis,spring-mybatis,spring-mybatis-starter

AOP:Advisor=Advice+PointCut

## AOP

JavaBean+ProxyFactory=Proxy JavaBean

JavaBean+ProxyFactory+TransactionInterceptor=Proxy Transaction JavaBean

JavaBean+TransactionProxyFactoryBean=Proxy Transaction JavaBean

## 其他感悟

Spring从来不用别人接口，都是自己定义接口。

Spring源码先读接口和实现类，此垂直为类之职责。在读关联，此水平为类之交互。




