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

![](.gitbook/assets/image%20%28109%29.png)

```sql
CREATE TABLE Department(
deptid int primary key not null identity(1,1),
deptname nvarchar(50)
);
```

```sql
package tw.hibernatedemo.util;

import org.hibernate.SessionFactory;
import org.hibernate.boot.MetadataSources;
import org.hibernate.boot.registry.StandardServiceRegistry;
import org.hibernate.boot.registry.StandardServiceRegistryBuilder;

public class HbernateUtil {
	
	private static final SessionFactory factory=createFactory();
	
	
	private static SessionFactory createFactory() {
		StandardServiceRegistry serviceRegistry = new StandardServiceRegistryBuilder().configure("hibernate.cfg.xml")
				.build();
		SessionFactory factory = new MetadataSources(serviceRegistry).buildMetadata().buildSessionFactory();

		return factory;
	}
	
	public static SessionFactory getSessionFactory() {
		return factory; //find 痊癒變數的factory
	}
	
	public static void closeSessionFactory() {
		if(factory!=null) {
			factory.close();
		}
	}
	
	
}

```

![](.gitbook/assets/image%20%28112%29.png)

![](.gitbook/assets/image%20%28111%29.png)

![](.gitbook/assets/image%20%28110%29.png)

![](.gitbook/assets/image%20%28113%29.png)

## 完整範例不含設定maven

### 第一步設定連線的JAVAUTIL

```java
package tw.hibernatedemo.util;

import org.hibernate.SessionFactory;
import org.hibernate.boot.MetadataSources;
import org.hibernate.boot.registry.StandardServiceRegistry;
import org.hibernate.boot.registry.StandardServiceRegistryBuilder;

public class HbernateUtil {
	
	private static final SessionFactory factory=createFactory();
	
	
	private static SessionFactory createFactory() {
		StandardServiceRegistry serviceRegistry = new StandardServiceRegistryBuilder().configure("hibernate.cfg.xml")
				.build();
		SessionFactory factory = new MetadataSources(serviceRegistry).buildMetadata().buildSessionFactory();

		return factory;
	}
	
	public static SessionFactory getSessionFactory() {
		return factory; //find 痊癒變數的factory
	}
	
	public static void closeSessionFactory() {
		if(factory!=null) {
			factory.close();
		}
	}
	
	
}

```

### 第二步設定bean

```java
package tw.hibernatedemo.model;

public class CompanyBean {
	private int companyId;
	private String companyName;
	
	public CompanyBean() {
		
	}

	public CompanyBean(int companyId, String companyName) {
		this.companyId = companyId;
		this.companyName = companyName;
	}

	public int getCompanyId() {
		return companyId;
	}

	public void setCompanyId(int companyId) {
		this.companyId = companyId;
	}

	public String getCompanyName() {
		return companyName;
	}

	public void setCompanyName(String companyName) {
		this.companyName = companyName;
	}

}

```

#### 設定mapping的xml

```java
<?xml version="1.0" encoding="UTF-8"?>


<hibernate-mapping>
    <class name="tw.hibernatedemo.model.CompanyBean" table="company">
        <id name="companyId" type="java.lang.Integer">
            <column name="companyID" />
            <generator class="assigned" />
        </id>
        <property name="companyName" type="java.lang.String">
            <column name="companyNAME" sql-type="nvarchar(50)" />
        </property>
    </class>
</hibernate-mapping>
```

### DAo

```java
package tw.hibernatedemo.model;

import java.util.List;

import org.hibernate.Session;
import org.hibernate.query.Query;

public class CompanyDAO {
	
	private Session session;

	public CompanyDAO(Session session) {
		
		this.session = session;
		
	}
	
	public CompanyBean insert(CompanyBean comBean) {
		CompanyBean tempBean=session.get(CompanyBean.class, comBean.getCompanyId());
		
		if(tempBean==null) {
			session.save(comBean);
			return comBean;
		}
		return null;
	}
	
	public CompanyBean getOneById(int id) {
		CompanyBean tempBean=session.get(CompanyBean.class, id);
		return tempBean;
	}
	
	public List<CompanyBean> selectAll(){
		//HQL: Hibernate Query Language
		Query<CompanyBean>	query=session.createQuery("from CompanyBean",CompanyBean.class);
		return query.list();
	}
	
	public CompanyBean updateOne(int id,String newName) {
		CompanyBean	tempBean=session.get(CompanyBean.class, id);
		if(tempBean!=null) {
			tempBean.setCompanyName(newName);
		}
		
		return tempBean;
	}
	
	public boolean deleteOne(int id) {
		CompanyBean	tempBean=session.get(CompanyBean.class, id);
		
		if(tempBean!=null) {
			session.delete(tempBean);
			return true;
		}
		return false;
	}

	
}

```

### service

```java
package tw.hibernatedemo.service;

import java.util.List;

import org.hibernate.Session;

import tw.hibernatedemo.model.CompanyBean;
import tw.hibernatedemo.model.CompanyDAO;

public class CompanyService {
	private CompanyDAO comDAO;
	
	public CompanyService(Session session) {
		comDAO=new CompanyDAO(session);
	}
	
	public CompanyBean select(int comId) {
		CompanyBean comBean = comDAO.getOneById(comId);
		return comBean;
	}
	
	public List<CompanyBean> selectAll(){
		 return comDAO.selectAll();
	}
	
	public CompanyBean insert(CompanyBean comBean) {
		CompanyBean tempBean = comDAO.insert(comBean);
		return tempBean;
	}
	
	public CompanyBean updateOne(int id, String newName) {
		return comDAO.updateOne(id, newName);
	}
	
	public boolean deleteOne(int id) {
		boolean boo = comDAO.deleteOne(id);
		return boo;
	}
	
	
}

```

### ACtion

```java
package tw.hibernatedemo.action;

import java.util.List;

import org.hibernate.Session;
import org.hibernate.SessionFactory;

import tw.hibernatedemo.model.CompanyBean;
import tw.hibernatedemo.model.CompanyDAO;
import tw.hibernatedemo.util.HbernateUtil;

public class DemoCompanyBeanDAOAction1 {

	public static void main(String[] args) {
		SessionFactory factory = HbernateUtil.getSessionFactory();
		Session session = factory.getCurrentSession();

		try {
			session.beginTransaction();
			CompanyDAO comDAO = new CompanyDAO(session);
			comDAO.insert(new CompanyBean(1009, "snowflake"));

			// print all

			// 印出全部
			System.out.println("List All");

			List<CompanyBean> listBean = comDAO.selectAll();

			for (CompanyBean one : listBean) {
				System.out.println("Company ID : " + one.getCompanyId() + " CompanyName: " + one.getCompanyName());
			}

			session.getTransaction().commit();

		} catch (Exception e) {
			session.getTransaction().rollback();
			e.printStackTrace();
		} finally {

		}

	}

}

```

