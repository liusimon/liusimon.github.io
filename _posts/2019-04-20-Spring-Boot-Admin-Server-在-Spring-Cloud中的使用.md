在项目的pom.xml里增加对Spring Boot Admin Server的依赖(只有spring-boot-admin-starter-server是主要依赖，后面的几个依赖是因为我的项目采用NACOS-阿里巴巴开源的Spring Cloud配置和服务注册与发现服务器所需要的客户端依赖)：  
  
    <dependency>  
        <groupId>de.codecentric</groupId>  
        <artifactId>spring-boot-admin-starter-server</artifactId>  
        <version>2.1.4</version>  
    </dependency>  
    
    <dependency>  
        <groupId>org.springframework.cloud</groupId>  
        <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>  
        <exclusions>  
            <exclusion>  
                <artifactId>guava</artifactId>  
                <groupId>com.google.guava</groupId>  
            </exclusion>  
            <exclusion>  
                <artifactId>nacos-client</artifactId>  
                <groupId>com.alibaba.nacos</groupId>  
            </exclusion>  
        </exclusions>  
    </dependency>  
    <dependency>  
        <groupId>com.alibaba.nacos</groupId>  
        <artifactId>nacos-client</artifactId>  
        <exclusions>  
            <exclusion>  
                <artifactId>guava</artifactId>  
                <groupId>com.google.guava</groupId>  
            </exclusion>  
        </exclusions>  
        <!--<type>pom</type>-->  
    </dependency>  
    <dependency>  
        <groupId>org.springframework.cloud</groupId>  
        <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>  
        <exclusions>  
            <exclusion>  
                <artifactId>guava</artifactId>  
                <groupId>com.google.guava</groupId>  
            </exclusion>  
            <exclusion>  
                <artifactId>nacos-client</artifactId>  
                <groupId>com.alibaba.nacos</groupId>  
            </exclusion>  
        </exclusions>  
    </dependency>  
    <dependency>  
        <groupId>com.google.guava</groupId>  
        <artifactId>guava</artifactId>  
        <version>27.1-jre</version>  
    </dependency>  
  
接下来在Spring Boot的启动类(一般是XxxApplication)加上注解

    @EnableDiscoveryClient
    @EnableAdminServer

其中@EnableDiscoveryClient的作用是利用Spring Cloud的服务发现来将各微服务整合到Spring Boot Admin Server中集中监控，从而不再需要添加Spring Boot Admin Client到微服务的项目中。  
