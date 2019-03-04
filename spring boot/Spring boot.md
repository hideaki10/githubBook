# ①.Spring Boot
## 简化spring应用的一个框架
## 整个spring技术的一个整合
## J2EE开发的一站式解决

# ②.微服务
## 架构风格
## 一个应用就是一组小型服务，各个服务可以通过HTTP的方式进行通信
## 传统模式 →　单体应用 优点 开发 测试简单 deploy scale也是非常简单
## 缺点 →　动一发牵动全身
## 每一个功能元素最终都是一个可独立替换和独立升级的单元
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

## 直接main方法


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

## 1.親

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


## 2.导入的依赖


```
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>

    spring-boot-starter:spring-boot场景启动器 导入web需要启动的模块
       
    
```

## 3.starter启动器

### spring有很多启动器 根据场景来导入那些启动器