# swagger-spring-boot-starter

参考：  
https://github.com/SpringForAll/spring-boot-starter-swagger

### 如何生成jar，打包javadoc文档和source源码，并将github作为maven仓库
指定项目源码的jdk版本  
org.apache.maven.plugins:maven-compiler-plugin:3.5.1  

生成javadoc文档包的插件  
org.apache.maven.plugins:maven-javadoc-plugin:2.10.4  

生成sources源码包的插件  
org.apache.maven.plugins:maven-source-plugin:3.0.1  

将项目根目录下的repository配置为仓库地址  
```xml
<repository>
    <id>release</id>
    <url>file:${basedir}/repository</url>
</repository>
```

[参考pom.xml](pom.xml)  
- 执行命令 `mvn deploy`

### 如何使用
- 在`pom.xml`中添加仓库地址和引入依赖： 
```xml
<repository>
    <id>release</id>
    <url>https://raw.githubusercontent.com/chengit163/swagger-spring-boot-starter/master/repository</url>
</repository>

<dependency>
    <groupId>com.cit</groupId>
    <artifactId>swagger-spring-boot-starter</artifactId>
    <version>1.0.0</version>
</dependency>
```

- 在应用主类中增加`@EnableSwagger2Doc`注解： 
```java
@EnableSwagger2Doc
@SpringBootApplication
public class Bootstrap {

    public static void main(String[] args) {
        SpringApplication.run(Bootstrap.class, args);
    }
    
}
```

- 在Spring Boot的配置文件`application.yml`： 
```yml
swagger:
  enabled: true
  base-package: com.cit
  title: API
  description: Demo project for Spring Boot
  version: 1.0.0
  contact:
    name: chengit163
    url: https://github.com/chengit163
    email: cheng_it@163.com
```