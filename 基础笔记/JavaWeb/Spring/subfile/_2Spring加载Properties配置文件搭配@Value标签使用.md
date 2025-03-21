## Spring加载Properties配置文件搭配@Value标签使用

#### 第一步：创建配置文件

![](../images/3.png)

**注意：这里不是必须要使用`.properties`结尾的文件才能加载（例如：xxx.conf文件也可以加载），只需要在格式上符合properties文件即可。（中间用等号或者冒号隔开）**

#### 第二步：配置加载配置文件

![](../images/4.png)

​	<font color="red">**注：如果在一个项目中，需要加载多个配置文件，那么多个配置文件路径之间用逗号隔开，不能写多个property-placeholder,哪怕是模块化配置spring（多个spring配置文件）这些配置文件中，也只能包含一个这个标签**</font>

```xml
<context:property-placeholder location="classpath:config/db.properties,classpath:config/resource.properties,classpath:config/website.properties,classpath:config/client.conf" />
```

#### 第三步：使用@Value注解加载值

![](../images/5.png)

或者在配置文件注入依赖时使用：

```xml
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource"
		destroy-method="close">
		<property name="url" value="${jdbc.url}" />
		<property name="username" value="${jdbc.username}" />
		<property name="password" value="${jdbc.password}" />
		<property name="driverClassName" value="${jdbc.driver}" />
</bean>
```

