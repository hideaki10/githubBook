# ①.Spring Boot
### 简化spring应用的一个框架
### 整个spring技术的一个整合
### J2EE开发的一站式解决

# ②.微服务
### 架构风格
### 一个应用就是一组小型服务，各个服务可以通过HTTP的方式进行通信
### 传统模式 →　单体应用 优点 开发 测试简单 deploy scale也是非常简单
### 缺点 →　动一发牵动全身
### 每一个功能元素最终都是一个可独立替换和独立升级的单元
![]()



# ③.环境配置


```
    <profile>
        <id>jdk-1.8</id>
        <activation>
            <activeByDefault>true</activeByDefault>
            <jdk>1.8</jdk>
        </activation>
        <properties>
            <maven.compiler.source>1.8</maven.compiler.source>
            <maven.compiler.target>1.8</maven.compiler.target>
            <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
        </properties>
    </profile>
```

```


    <groupId>com.atg.guigu</groupId>
    <artifactId>spring-boot-01-hellowrold</artifactId>
    <version>1.0-SNAPSHOT</version>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.9.RELEASE</version>
    </parent>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>


```

# ④.运行主程序

### 直接main方法


# ⑤.デプロイ
```
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

```


# ⑥.POM

### 1.親

```

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.9.RELEASE</version>
    </parent>

    	
     他的父项目

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-dependencies</artifactId>
		<version>1.5.9.RELEASE</version>
		<relativePath>../../spring-boot-dependencies</relativePath>
	</parent>

	正真管理项目的spring-boot-dependencies
	<modelVersion>4.0.0</modelVersion>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-dependencies</artifactId>
	<version>1.5.9.RELEASE</version>
	<packaging>pom</packaging>
	<name>Spring Boot Dependencies</name>
	<description>Spring Boot Dependencies</description>
	<url>http://projects.spring.io/spring-boot/</url>
	
```


### 2.导入的依赖


```
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>

    spring-boot-starter:spring-boot场景启动器 导入web需要启动的模块
       
    
```

### 3.starter启动器

#### 3.1 spring有很多启动器 根据场景来导入那些启动器

#### 3.2 @SpringBootApplication 
```
@SpringBootApplication
public class HelloWorldMainApplication {

    public  static  void  main(String[] args){
        SpringApplication.run(HelloWorldMainApplication.class,args);
    }
}

@SpringBootApplication SpringBoot标注在某个类说明这个类是SpringBoot的主配置类，SpringBoot就应该运行这个类的 main方法来启动SpringBoot应用


@Target({ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Inherited
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan(
    excludeFilters = {@Filter(
    type = FilterType.CUSTOM,
    classes = {TypeExcludeFilter.class}
), @Filter(
    type = FilterType.CUSTOM,
    classes = {AutoConfigurationExcludeFilter.class}
)}
)
public @interface SpringBootApplication {

@SpringBootConfiguration SpringBoot的配置类 标注在某个类上，表示这是一个Spring Boot的配置类

 

@Configuration:配置类上来标注这个注解 配置类 ---- 配置文件;配置类也是容器中一个组件 @Component
@EnableAutoConfiguration:开启自动配置功能 以前我们需要配置的东西，SpringBoot帮我们自动配置 @EnableAutoConfiguration告诉 SpringBoot 开启自动配置功能 这样自动配置才能生效


@AutoConfigurationPackage
@Import({EnableAutoConfigurationImportSelector.class})
public @interface EnableAutoConfiguration {

@AutoConfigurationPackage: 自动配置包 
  @Import({Registrar.class}) spring的底层注解import 给容器中导入一个组件；导入的组件由
将主配置类的(@SpringBootApplication标注的类)的所在的包及下面

@Import({EnableAutoConfigurationImportSelector.class})给容器中导入组件
EnableAutoConfigurationImportSelector 导入哪些组件
将所有需要导入的组件以全类名的方式返回这些组件就会被添加到容器中
会给容器中导入非常多的自动配置类 

this = {EnableAutoConfigurationImportSelector@2997} 
annotationMetadata = {StandardAnnotationMetadata@3000} 
autoConfigurationMetadata = {AutoConfigurationMetadataLoader$PropertiesAutoConfigurationMetadata@3374} 
attributes = {AnnotationAttributes@3381}  size = 2
configurations = {ArrayList@3398}  size = 96
 0 = "org.springframework.boot.autoconfigure.admin.SpringApplicationAdminJmxAutoConfiguration"
 1 = "org.springframework.boot.autoconfigure.aop.AopAutoConfiguration"
 2 = "org.springframework.boot.autoconfigure.amqp.RabbitAutoConfiguration"
 3 = "org.springframework.boot.autoconfigure.batch.BatchAutoConfiguration"
 4 = "org.springframework.boot.autoconfigure.cache.CacheAutoConfiguration"
 5 = "org.springframework.boot.autoconfigure.cassandra.CassandraAutoConfiguration"
 6 = "org.springframework.boot.autoconfigure.cloud.CloudAutoConfiguration"
 7 = "org.springframework.boot.autoconfigure.context.ConfigurationPropertiesAutoConfiguration"
 8 = "org.springframework.boot.autoconfigure.context.MessageSourceAutoConfiguration"
 9 = "org.springframework.boot.autoconfigure.context.PropertyPlaceholderAutoConfiguration"
 10 = "org.springframework.boot.autoconfigure.couchbase.CouchbaseAutoConfiguration"
 11 = "org.springframework.boot.autoconfigure.dao.PersistenceExceptionTranslationAutoConfiguration"
 12 = "org.springframework.boot.autoconfigure.data.cassandra.CassandraDataAutoConfiguration"
 13 = "org.springframework.boot.autoconfigure.data.cassandra.CassandraRepositoriesAutoConfiguration"
 14 = "org.springframework.boot.autoconfigure.data.couchbase.CouchbaseDataAutoConfiguration"
 15 = "org.springframework.boot.autoconfigure.data.couchbase.CouchbaseRepositoriesAutoConfiguration"
 16 = "org.springframework.boot.autoconfigure.data.elasticsearch.ElasticsearchAutoConfiguration"
 17 = "org.springframework.boot.autoconfigure.data.elasticsearch.ElasticsearchDataAutoConfiguration"
 18 = "org.springframework.boot.autoconfigure.data.elasticsearch.ElasticsearchRepositoriesAutoConfiguration"
 19 = "org.springframework.boot.autoconfigure.data.jpa.JpaRepositoriesAutoConfiguration"
 20 = "org.springframework.boot.autoconfigure.data.ldap.LdapDataAutoConfiguration"
 21 = "org.springframework.boot.autoconfigure.data.ldap.LdapRepositoriesAutoConfiguration"
 22 = "org.springframework.boot.autoconfigure.data.mongo.MongoDataAutoConfiguration"
 23 = "org.springframework.boot.autoconfigure.data.mongo.MongoRepositoriesAutoConfiguration"
 24 = "org.springframework.boot.autoconfigure.data.neo4j.Neo4jDataAutoConfiguration"
 25 = "org.springframework.boot.autoconfigure.data.neo4j.Neo4jRepositoriesAutoConfiguration"
 26 = "org.springframework.boot.autoconfigure.data.solr.SolrRepositoriesAutoConfiguration"
 27 = "org.springframework.boot.autoconfigure.data.redis.RedisAutoConfiguration"
 28 = "org.springframework.boot.autoconfigure.data.redis.RedisRepositoriesAutoConfiguration"
 29 = "org.springframework.boot.autoconfigure.data.rest.RepositoryRestMvcAutoConfiguration"
 30 = "org.springframework.boot.autoconfigure.data.web.SpringDataWebAutoConfiguration"
 31 = "org.springframework.boot.autoconfigure.elasticsearch.jest.JestAutoConfiguration"
 32 = "org.springframework.boot.autoconfigure.freemarker.FreeMarkerAutoConfiguration"
 33 = "org.springframework.boot.autoconfigure.gson.GsonAutoConfiguration"
 34 = "org.springframework.boot.autoconfigure.h2.H2ConsoleAutoConfiguration"
 35 = "org.springframework.boot.autoconfigure.hateoas.HypermediaAutoConfiguration"
 36 = "org.springframework.boot.autoconfigure.hazelcast.HazelcastAutoConfiguration"
 37 = "org.springframework.boot.autoconfigure.hazelcast.HazelcastJpaDependencyAutoConfiguration"
 38 = "org.springframework.boot.autoconfigure.info.ProjectInfoAutoConfiguration"
 39 = "org.springframework.boot.autoconfigure.integration.IntegrationAutoConfiguration"
 40 = "org.springframework.boot.autoconfigure.jackson.JacksonAutoConfiguration"
 41 = "org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration"
 42 = "org.springframework.boot.autoconfigure.jdbc.JdbcTemplateAutoConfiguration"
 43 = "org.springframework.boot.autoconfigure.jdbc.JndiDataSourceAutoConfiguration"
 44 = "org.springframework.boot.autoconfigure.jdbc.XADataSourceAutoConfiguration"
 45 = "org.springframework.boot.autoconfigure.jdbc.DataSourceTransactionManagerAutoConfiguration"
 46 = "org.springframework.boot.autoconfigure.jms.JmsAutoConfiguration"
 47 = "org.springframework.boot.autoconfigure.jmx.JmxAutoConfiguration"
 48 = "org.springframework.boot.autoconfigure.jms.JndiConnectionFactoryAutoConfiguration"
 49 = "org.springframework.boot.autoconfigure.jms.activemq.ActiveMQAutoConfiguration"
 50 = "org.springframework.boot.autoconfigure.jms.artemis.ArtemisAutoConfiguration"
 51 = "org.springframework.boot.autoconfigure.flyway.FlywayAutoConfiguration"
 52 = "org.springframework.boot.autoconfigure.groovy.template.GroovyTemplateAutoConfiguration"
 53 = "org.springframework.boot.autoconfigure.jersey.JerseyAutoConfiguration"
 54 = "org.springframework.boot.autoconfigure.jooq.JooqAutoConfiguration"
 55 = "org.springframework.boot.autoconfigure.kafka.KafkaAutoConfiguration"
 56 = "org.springframework.boot.autoconfigure.ldap.embedded.EmbeddedLdapAutoConfiguration"
 57 = "org.springframework.boot.autoconfigure.ldap.LdapAutoConfiguration"
 58 = "org.springframework.boot.autoconfigure.liquibase.LiquibaseAutoConfiguration"
 59 = "org.springframework.boot.autoconfigure.mail.MailSenderAutoConfiguration"
 60 = "org.springframework.boot.autoconfigure.mail.MailSenderValidatorAutoConfiguration"
 61 = "org.springframework.boot.autoconfigure.mobile.DeviceResolverAutoConfiguration"
 62 = "org.springframework.boot.autoconfigure.mobile.DeviceDelegatingViewResolverAutoConfiguration"
 63 = "org.springframework.boot.autoconfigure.mobile.SitePreferenceAutoConfiguration"
 64 = "org.springframework.boot.autoconfigure.mongo.embedded.EmbeddedMongoAutoConfiguration"
 65 = "org.springframework.boot.autoconfigure.mongo.MongoAutoConfiguration"
 66 = "org.springframework.boot.autoconfigure.mustache.MustacheAutoConfiguration"
 67 = "org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaAutoConfiguration"
 68 = "org.springframework.boot.autoconfigure.reactor.ReactorAutoConfiguration"
 69 = "org.springframework.boot.autoconfigure.security.SecurityAutoConfiguration"
 70 = "org.springframework.boot.autoconfigure.security.SecurityFilterAutoConfiguration"
 71 = "org.springframework.boot.autoconfigure.security.FallbackWebSecurityAutoConfiguration"
 72 = "org.springframework.boot.autoconfigure.security.oauth2.OAuth2AutoConfiguration"
 73 = "org.springframework.boot.autoconfigure.sendgrid.SendGridAutoConfiguration"
 74 = "org.springframework.boot.autoconfigure.session.SessionAutoConfiguration"
 75 = "org.springframework.boot.autoconfigure.social.SocialWebAutoConfiguration"
 76 = "org.springframework.boot.autoconfigure.social.FacebookAutoConfiguration"
 77 = "org.springframework.boot.autoconfigure.social.LinkedInAutoConfiguration"
 78 = "org.springframework.boot.autoconfigure.social.TwitterAutoConfiguration"
 79 = "org.springframework.boot.autoconfigure.solr.SolrAutoConfiguration"
 80 = "org.springframework.boot.autoconfigure.thymeleaf.ThymeleafAutoConfiguration"
 81 = "org.springframework.boot.autoconfigure.transaction.TransactionAutoConfiguration"
 82 = "org.springframework.boot.autoconfigure.transaction.jta.JtaAutoConfiguration"
 83 = "org.springframework.boot.autoconfigure.validation.ValidationAutoConfiguration"
 84 = "org.springframework.boot.autoconfigure.web.DispatcherServletAutoConfiguration"
 85 = "org.springframework.boot.autoconfigure.web.EmbeddedServletContainerAutoConfiguration"
 86 = "org.springframework.boot.autoconfigure.web.ErrorMvcAutoConfiguration"
 87 = "org.springframework.boot.autoconfigure.web.HttpEncodingAutoConfiguration"
 88 = "org.springframework.boot.autoconfigure.web.HttpMessageConvertersAutoConfiguration"
 89 = "org.springframework.boot.autoconfigure.web.MultipartAutoConfiguration"
 90 = "org.springframework.boot.autoconfigure.web.ServerPropertiesAutoConfiguration"
 91 = "org.springframework.boot.autoconfigure.web.WebClientAutoConfiguration"
 92 = "org.springframework.boot.autoconfigure.web.WebMvcAutoConfiguration"
 93 = "org.springframework.boot.autoconfigure.websocket.WebSocketAutoConfiguration"
 94 = "org.springframework.boot.autoconfigure.websocket.WebSocketMessagingAutoConfiguration"
 95 = "org.springframework.boot.autoconfigure.webservices.WebServicesAutoConfiguration"


有了自动配置类就不需要手动配置了

spring boot 在启动的时候从类路径下的META-INF/spring.factories中获取EnableAutoConfigure指定的值
将这些值作为自动配置类导入到容器中，自动配置类就生效

J2EE的整体整合解决方案和自动配置都在org.springframework.boot.autoconfigure


```


# ⑦.使用springboot创建向导快速创建springboot

#### 7.1　选择要使用的模块
#### 7.2　主程序已经写好了
#### 7.3　resources文件中的目录结构
##### 7.3.1　static:保存所有的静态资源; js css images;
##### 7.3.2  tmpleates: 保存所有的模板页面 
##### 7.3.3  application.properties: 保存所有的模板页面的配置 


# ⑧.配置文件
#### 8.1 配置文件名是固定 8.1.1 application.properties 8.1.2 application.yml
#### 8.2 yml 文件 以数据为中心 

```
yml 设定方法


server:
  port:8081
```



