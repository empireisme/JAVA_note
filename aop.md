# AOPandMVChelloworld

AOP解決了以下的事情

![](.gitbook/assets/image%20%28130%29.png)

上圖可以發現為了log的關係，所以有很多重複的程式碼

所以他有兩個問題

![](.gitbook/assets/image%20%28129%29.png)

![](.gitbook/assets/image%20%28131%29.png)

## [What is flow of Spring MVC applicati](https://stackoverflow.com/questions/25616155/what-is-flow-of-spring-mvc-application)

{% embed url="https://www.javaguides.net/2018/10/spring-mvc-5-hello-world-example.html" %}

{% embed url="https://www.journaldev.com/14476/spring-mvc-example\#spring-mvc-example-hello-world-eclipse-project" %}



![](.gitbook/assets/image%20%28133%29.png)

![](.gitbook/assets/image%20%28132%29.png)

![](.gitbook/assets/image%20%28134%29.png)

## pom.xml

![](.gitbook/assets/image%20%28137%29.png)

```markup
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>web.spring</groupId>
	<artifactId>mvcExercise</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>war</packaging>
	<properties>
		<maven.compiler.source>11</maven.compiler.source>
		<maven.compiler.target>11</maven.compiler.target>
		<hibernate.version>5.4.30.Final</hibernate.version>
		<spring.version>5.3.6</spring.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>javax.servlet-api</artifactId>
			<version>3.1.0</version>
			<scope>provided</scope>
		</dependency>

		<dependency>
			<groupId>javax.servlet.jsp</groupId>
			<artifactId>javax.servlet.jsp-api</artifactId>
			<version>2.3.1</version>
			<scope>provided</scope>
		</dependency>
		
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>jstl</artifactId>
			<version>1.2</version>
		</dependency>
		
		<dependency>
			<groupId>com.mchange</groupId>
			<artifactId>c3p0</artifactId>
			<version>0.9.5.2</version>
		</dependency>
		
		<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-core</artifactId>
			<version>${hibernate.version}</version>
		</dependency>
		
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${spring.version}</version>
		</dependency>
		
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-orm</artifactId>
			<version>${spring.version}</version>
		</dependency>
		
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-oxm</artifactId>
			<version>${spring.version}</version>
		</dependency>
		
		<dependency>
			<groupId>com.fasterxml.jackson.core</groupId>
			<artifactId>jackson-databind</artifactId>
			<version>2.9.4</version>
		</dependency>

		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>8.0.13</version>
		</dependency>

		<dependency>
			<groupId>com.microsoft.sqlserver</groupId>
			<artifactId>mssql-jdbc</artifactId>
			<version>8.4.1.jre11</version>
		</dependency>

		<dependency>
			<groupId>commons-fileupload</groupId>
			<artifactId>commons-fileupload</artifactId>
			<version>1.2.2</version>
		</dependency>

		<dependency>
			<groupId>org.apache.commons</groupId>
			<artifactId>commons-io</artifactId>
			<version>1.3.2</version>
		</dependency>

	</dependencies>
	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-war-plugin</artifactId>
				<version>3.2.0</version>
				<configuration>
					<failOnMissingWebXml>false</failOnMissingWebXml>
				</configuration>
			</plugin>
		</plugins>
	</build>

</project>
```

![](.gitbook/assets/image%20%28135%29.png)

![](.gitbook/assets/image%20%28136%29.png)

![](.gitbook/assets/image%20%28139%29.png)

![](.gitbook/assets/image%20%28138%29.png)

![](.gitbook/assets/image%20%28140%29.png)

