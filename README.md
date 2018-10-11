# Spring Boot Demo

[![MIT](https://img.shields.io/github/license/xkcoding/spring-boot-demo.svg)](https://github.com/xkcoding/spring-boot-demo/blob/master/LICENSE) [![GitHub stars](https://img.shields.io/github/stars/xkcoding/spring-boot-demo.svg?style=flat&label=Star)](https://github.com/xkcoding/spring-boot-demo/stargazers) [![GitHub forks](https://img.shields.io/github/forks/xkcoding/spring-boot-demo.svg?style=flat&label=Fork)](https://github.com/xkcoding/spring-boot-demo/fork) [![GitHub watchers](https://img.shields.io/github/watchers/xkcoding/spring-boot-demo.svg?style=flat&label=Watch)](https://github.com/xkcoding/spring-boot-demo/watchers)

spring boot demo 是一个用来学习 spring boot 的项目，已经集成 actuator (监控)、admin (可视化监控)、logback (日志)、aopLog (通过 AOP 记录 web 请求日志)、统一异常处理( json 级别和页面级别)、freemarker (模板引擎)、thymeleaf (模板引擎)、Beetl (模板引擎)、JdbcTemplate、JPA (ORM 框架)、mybatis (ORM 框架)、redis-cache (缓存)、task (定时任务)、swagger (API 接口管理测试)、ureport2 (中国式报表)、打包成 war 文件、集成 ElasticSearch (采用原生操作 ES 的方式)、集成 Dubbo (采用非官方的 starter)，后续会集成activemq,email,shiro,websocket,quartz,netty等模块。

### 分支：

- master 分支：基于 SpringBoot 版本 2.0.5.RELEASE，每个 module 的 parent 依赖根目录下的pom.xml，主要用于管理每个module的依赖版本，方便大家学习
- v-1.5.x 分支：基于 SpringBoot 版本 1.5.8.RELEASE，每个 module 均依赖 spring-boot-demo-parent，有挺多同学们反映这种方式对新手不是很友好，运行起来有些难度，因此 ***此分支(v-1.5.x)会暂停开发维护*** ，所有内容会慢慢以 master 分支的形式同步过去，此分支暂未完成的，也会直接在master分支上加，在此分支学习的同学们，仍然可以在此分支学习，但是建议后期切换到master分支，会更加容易。🙂

### 开发环境

- **JDK1.8 +**
- **Maven 3.5 +**
- **IntelliJ IDEA ULTIMATE 2018.2 +**
- **mysql 5.7 +** (*尽量5.7版本以上，因为5.7版本加了一些新特性，不向下兼容。本demo里会尽量避免这种不兼容的地方，但还是建议尽量保证5.7版本以上*)

### 运行方式

1. `git clone https://github.com/xkcoding/spring-boot-demo.git`
2. 使用 IDEA 打开 clone 下来的项目
3. 在 IDEA 中打开项目
4. 在 IDEA 中 Maven Projects 的面板导入根目录下 的 `pom.xml`
5. Maven Projects 找不到的童鞋，可以勾上 View -> Tool Buttons ，然后Maven Projects的面板就会出现在IDEA的右侧
6. 找到各个 module 的 Application 类就可以运行各个 module 了

### 开发计划

[**进度计划**](https://github.com/xkcoding/spring-boot-demo/projects/1?fullscreen=true) 或直接查看 [TODO](./TODO.md)

### 根目录下的 pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.xkcoding</groupId>
	<artifactId>spring-boot-demo</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<modules>
		<module>spring-boot-demo-helloworld</module>
		<module>spring-boot-demo-properties</module>
		<module>spring-boot-demo-actuator</module>
		<module>spring-boot-demo-admin-client</module>
		<module>spring-boot-demo-admin-server</module>
		<module>spring-boot-demo-logback</module>
		<module>spring-boot-demo-log-aop</module>
		<module>spring-boot-demo-exception-handler</module>
		<module>spring-boot-demo-template-freemarker</module>
		<module>spring-boot-demo-template-thymeleaf</module>
		<module>spring-boot-demo-template-beetl</module>
	</modules>
	<packaging>pom</packaging>

	<name>spring-boot-demo</name>
	<url>http://xkcoding.com</url>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<java.version>1.8</java.version>
		<maven.compiler.source>1.8</maven.compiler.source>
		<maven.compiler.target>1.8</maven.compiler.target>
		<spring.boot.version>2.0.5.RELEASE</spring.boot.version>
		<hutool.version>4.1.17</hutool.version>
		<user.agent.version>1.20</user.agent.version>
	</properties>

	<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-dependencies</artifactId>
				<version>${spring.boot.version}</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
			<!-- hutool工具类 -->
			<dependency>
				<groupId>cn.hutool</groupId>
				<artifactId>hutool-all</artifactId>
				<version>${hutool.version}</version>
			</dependency>
			<!-- 解析 UserAgent 信息 -->
			<dependency>
				<groupId>eu.bitwalker</groupId>
				<artifactId>UserAgentUtils</artifactId>
				<version>${user.agent.version}</version>
			</dependency>
		</dependencies>
	</dependencyManagement>

	<build>
		<pluginManagement>
			<plugins>
				<plugin>
					<artifactId>maven-clean-plugin</artifactId>
					<version>3.0.0</version>
				</plugin>
				<plugin>
					<artifactId>maven-resources-plugin</artifactId>
					<version>3.0.2</version>
				</plugin>
				<plugin>
					<artifactId>maven-compiler-plugin</artifactId>
					<version>3.7.0</version>
				</plugin>
				<plugin>
					<artifactId>maven-surefire-plugin</artifactId>
					<version>2.20.1</version>
				</plugin>
				<plugin>
					<artifactId>maven-jar-plugin</artifactId>
					<version>3.0.2</version>
				</plugin>
				<plugin>
					<artifactId>maven-install-plugin</artifactId>
					<version>2.5.2</version>
				</plugin>
				<plugin>
					<artifactId>maven-deploy-plugin</artifactId>
					<version>2.8.2</version>
				</plugin>
				<plugin>
					<groupId>org.springframework.boot</groupId>
					<artifactId>spring-boot-maven-plugin</artifactId>
					<version>${spring.boot.version}</version>
					<executions>
						<execution>
							<goals>
								<goal>repackage</goal>
							</goals>
						</execution>
					</executions>
				</plugin>
			</plugins>
		</pluginManagement>
	</build>
</project>
```

### 各 Module 介绍

| Module 名称                                                  | Module 介绍                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [spring-boot-demo-helloworld](./spring-boot-demo-helloworld) | spring-boot 的一个 helloworld                                |
| [spring-boot-demo-properties](./spring-boot-demo-properties) | spring-boot 读取配置文件中的内容                             |
| [spring-boot-demo-actuator](./spring-boot-demo-actuator)     | spring-boot 集成 spring-boot-starter-actuator 用于监控 spring-boot 的启动和运行状态 |
| [spring-boot-demo-admin-client](./spring-boot-demo-admin-client) | spring-boot 集成 spring-boot-admin 来可视化的监控 spring-boot 程序的运行状态，可以与 actuator 互相搭配使用，客户端示例 |
| [spring-boot-demo-admin-server](./spring-boot-demo-admin-server) | spring-boot 集成 spring-boot-admin 来可视化的监控 spring-boot 程序的运行状态，可以与 actuator 互相搭配使用，服务端示例 |
| [spring-boot-demo-logback](./spring-boot-demo-logback)       | spring-boot 集成 logback 日志                                |
| [spring-boot-demo-log-aop](./spring-boot-demo-log-aop)       | spring-boot 使用 AOP 切面的方式记录 web 请求日志             |
| [spring-boot-demo-exception-handler](./spring-boot-demo-exception-handler) | spring-boot 统一异常处理，包括2种，第一种返回统一的 json 格式，第二种统一跳转到异常页面 |
| [spring-boot-demo-template-freemarker](./spring-boot-demo-template-freemarker) | spring-boot 集成 freemarker 模板引擎                         |
| [spring-boot-demo-template-thymeleaf](./spring-boot-demo-template-thymeleaf) | spring-boot 集成 thymeleaf 模板引擎                          |
| [spring-boot-demo-template-beetl](./spring-boot-demo-template-beetl) | spring-boot 集成 Beetl 模板引擎                              |
| [spring-boot-demo-orm-jpa](./spring-boot-demo-orm-jpa)       | spring-boot 集成 spring-boot-starter-data-jpa 操作数据库     |
| [spring-boot-demo-orm-mybatis](./spring-boot-demo-orm-mybatis) | spring-boot 集成 [mybatis-spring-boot-starter](https://github.com/mybatis/spring-boot-starter)、[mybatis-spring-boot-starter](https://github.com/alibaba/druid/tree/master/druid-spring-boot-starter) |
| [spring-boot-demo-cache-redis](./spring-boot-demo-cache-redis) | spring-boot 使用 Redis 做缓存                                |
| [spring-boot-demo-task-schedule](./spring-boot-demo-task-schedule) | spring-boot 使用 @Scheduled 实现定时任务                     |
| [spring-boot-demo-swagger](./spring-boot-demo-swagger)       | spring-boot 集成 [spring-boot-starter-swagger](https://github.com/SpringForAll/spring-boot-starter-swagger) (由大佬[翟永超](http://blog.didispace.com/)开源)用于统一管理、测试 API 接口 |
| [spring-boot-demo-ureport2](./spring-boot-demo-ureport2)     | spring-boot 集成 [ureport2](https://github.com/youseries/ureport) 实现自定义报表（ureport2可以轻松实现复杂的中国式报表，功能十分强大） |
| [spring-boot-demo-war](./spring-boot-demo-war)               | spring-boot 打成 war 包的配置                                |
| [spring-boot-demo-elasticsearch](./spring-boot-demo-elasticsearch) | spring-boot 集成 ElasticSearch（采用原生操作 ES 的方式）     |
| [spring-boot-demo-dubbo-parent](./spring-boot-demo-dubbo-parent) | spring-boot 集成 Dubbo                                       |

# 官方提供的 starter 介绍

| Name                                   | Description                              |
| :------------------------------------- | :--------------------------------------- |
| spring-boot-starter                    | The core Spring Boot starter, including auto-configuration support, logging and YAML. |
| spring-boot-starter-actuator           | Production ready features to help you monitor and manage your application. |
| spring-boot-starter-amqp               | are neat                                 |
| spring-boot-starter-aop                | Support for aspect-oriented programming including spring-aop and AspectJ. |
| spring-boot-starter-artemis            | Support for “Java Message Service API” via Apache Artemis. |
| spring-boot-starter-batch              | Support for “Spring Batch” including HSQLDB database. |
| spring-boot-starter-cache              | Support for Spring’s Cache abstraction.  |
| spring-boot-starter-cloud-connectors   | Support for “Spring Cloud Connectors” which simplifies connecting to services in cloud platforms like Cloud Foundry and Heroku. |
| spring-boot-starter-data-elasticsearch | Support for the Elasticsearch search and analytics engine including spring-data-elasticsearch. |
| spring-boot-starter-data-gemfire       | Support for the GemFire distributed data store including spring-data-gemfire. |
| spring-boot-starter-data-jpa           | Support for the “Java Persistence API” including spring-data-jpa, spring-orm and Hibernate. |
| spring-boot-starter-data-mongodb       | Support for the MongoDB NoSQL Database, including spring-data-mongodb. |
| spring-boot-starter-data-rest          | Support for exposing Spring Data repositories over REST via spring-data-rest-webmvc. |
| spring-boot-starter-data-solr          | Support for the Apache Solr search platform, including spring-data-solr. |
| spring-boot-starter-freemarker         | Support for the FreeMarker templating engine. |
| spring-boot-starter-groovy-templates   | Support for the Groovy templating engine. |
| spring-boot-starter-hateoas            | Support for HATEOAS-based RESTful services via spring-hateoas. |
| spring-boot-starter-hornetq            | Support for “Java Message Service API” via HornetQ. |
| spring-boot-starter-integration        | Support for common spring-integration modules. |
| spring-boot-starter-jdbc               | Support for JDBC databases.              |
| spring-boot-starter-jersey             | Support for the Jersey RESTful Web Services framework. |
| spring-boot-starter-jta-atomikos       | Support for JTA distributed transactions via Atomikos. |
| spring-boot-starter-jta-bitronix       | Support for JTA distributed transactions via Bitronix. |
| spring-boot-starter-mail               | Support for javax.mail.                  |
| spring-boot-starter-mobile             | Support for spring-mobile.               |
| spring-boot-starter-mustache           | Support for the Mustache templating engine. |
| spring-boot-starter-redis              | Support for the REDIS key-value data store, including spring-redis. |
| spring-boot-starter-security           | Support for spring-security.             |
| spring-boot-starter-social-facebook    | Support for spring-social-facebook.      |
| spring-boot-starter-social-linkedin    | Support for spring-social-linkedin.      |
| spring-boot-starter-social-twitter     | Support for spring-social-twitter.       |
| spring-boot-starter-test               | Support for common test dependencies, including JUnit, Hamcrest and Mockito along with the spring-test module. |
| spring-boot-starter-thymeleaf          | Support for the Thymeleaf templating engine, including integration with Spring. |
| spring-boot-starter-velocity           | Support for the Velocity templating engine. |
| spring-boot-starter-web                | Support for full-stack web development, including Tomcat and spring-webmvc. |
| spring-boot-starter-websocket          | Support for WebSocket development.       |
| spring-boot-starter-ws                 | Support for Spring Web Services.         |

# License

[MIT](http://opensource.org/licenses/MIT)

Copyright (c) 2018 Yangkai.Shen