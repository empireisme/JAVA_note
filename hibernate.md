# Hibernate

## 5/3

{% file src=".gitbook/assets/apache-maven-3.6.3-bin.zip" %}

```markup
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
		"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
		"http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
         
        <property name="hibernate.connection.driver_class">com.microsoft.sqlserver.jdbc.SQLServerDriver</property>
        <property name="hibernate.connection.password">1234</property>
        <property name="hibernate.connection.url">jdbc:sqlserver://localhost:1433;databaseName=hibernateDB</property>
        <property name="hibernate.connection.username">sa</property>
         
        <property name="hibernate.dialect">org.hibernate.dialect.SQLServerDialect</property>
        
     
        <property name="current_session_context_class">thread</property>
        
		<!-- 是否在 console 顯示經由 hibernate 產生的 SQL 指令-->
        <property name="show_sql">true</property>
		
		<!-- 上述 SQL 指令是否排版-->
        <property name="format_sql">true</property>
		
		<!-- hibernate 內建 連線池 -->
		<property name="connection.pool_size">2</property>
        
        <!-- setting auto generate table: update/validate  -->
<!--         <property name="hbm2ddl.auto">update</property> -->
        
        <!--  source mapping in xml file -->
        <mapping resource="tw/hibernatedemo/model/CompanyBean.hbm.xml"/>
        
        <!--  class mapping -->
        <!-- <mapping class="tw.hibernatedemo.model.Department"/> -->
    
        
    </session-factory>
</hibernate-configuration>

```

```markup
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>Hibernate</groupId>
	<artifactId>Hibernate</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<dependencies>
		<dependency>
			<groupId>com.microsoft.sqlserver</groupId>
			<artifactId>mssql-jdbc</artifactId>
			<version>9.2.1.jre11</version>
		</dependency>

		<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-core</artifactId>
			<version>5.4.29.Final</version>
		</dependency>



	</dependencies>


	<build>
		<sourceDirectory>src</sourceDirectory>
		<plugins>
			<plugin>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.8.1</version>
				<configuration>
					<release>11</release>
				</configuration>
			</plugin>
		</plugins>
	</build>
</project>
```

