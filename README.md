
Bee
=========
**Easy for Stronger.**   
**Bee** is an ORM framework.   
**Bee** is an easy and high efficiency ORM framework.    
**Coding Complexity is O(1),it means that Bee will do the Dao for you**.  
**You don't need to write the Dao by yourself anymore**.  
**Good Feature:**  AI, Timesaving/Tasteful, Easy, Automatic (**AiTeaSoft Style**)   
**Bee** see:  
https://github.com/automvc/bee  
**Honey** see:  
https://github.com/automvc/honey  

## [中文介绍](../../../bee/blob/master/README_CN.md)  
[点击链接可查看中文介绍](../../../bee/blob/master/README_CN.md)  

## Requirement  
jdk1.7+

## Feature & Function: 

**V1.0**  
Single entity(table) Suid (select,update,insert,delete) object-oriented operation.  
Automatically generate the Javabean via DB table or view(MySQL,MariaDB).  
Convention-over-configuration:Javabean no annotation,no xml.  
Automatically mapping the table column and the Javabean field.  
Javabean support the raw type:int,double,and so on.  
PreparedStatement support.  
Procedure support.  
Native SQL support.  
Batch operate support.  
Transaction support.  
Automatic filter the null and empty field for default.  
MAX,MIN,SUM,AVG,COUNT support.  
Order by,Paging.  
Select some field.  
Dynamic & random combination of query conditions,no need to prepare the interface in advance; new query requirements, no need to change the query interface.  
All Suid(select,update,insert,delete) operation use the same Bee interface,no longer need any new dao interface.  
Users/Developer only need to pay attention to the Bee interface.  

......

**V1.8**   
**Add Distributed Feature:**   
1.Add multi-DataSource support(Write/Read, only Split Database).  
add multi-DataSource no need change the Java code.  
add the route interface of multi-Datasource.  
add multi-DataSource route.  
add multi-DataSource config.  
support refresh multi-DataSource config information.  
2.Generate global unique id number in distributed environment.  
3.Generate Serial Unique id number in one workid of distributed environment.  
Independent clock,workerid can config and easily expand.  
Implement algorithms:SerialUniqueId,OneTimeSnowflakeId,PearFlowerId.  
Support GenId Factory,and can config the id generator.  
4.Gen Serial Unique Id for all Table's Long Id field as primary key.  
**Enhance Function:**   
5.The same database sub table support, dynamic table name mapping support.  
Entity and any table name mapping support.  
Suid add one method:	
public Suid setDynamicParameter(String para,String value);  
add 2 annotation:@Table,@Entity.  
6.Use 'for update' lock some select record(s).   
public Condition forUpdate()  
7.Added support for advanced update set,   
Complex query and multi table query support only project some fields.   
Add 5 methods in Condition  
8.Support show type of data in sql and show ExecutableSql:  
bee.osql.showSQL.showType=false  
bee.osql.showSQL.showExecutableSql=false  
9.Add one method in SuidRich  
Add three methods in PreparedSql  
10.Oracle DATE column mapping to Timestamp,fix the problem:miss the hour,minute,second in Oracle DATE column.  
11.GenFiles support upper case first letter,eg: #{entityName?up1}.  
**Fix bug:**   
12.fixed cache bug:genkey;clear cache for batch insert.  
fixed bug:parse the json has extra comma.	
fixed null bug about:PreparedSql's method select(String sql,Object preValues[]).  	

## [Function Detail](../../../bee/blob/master/Changed_Log.md)  
[click for:  Function Detail](../../../bee/blob/master/Changed_Log.md)  

## Compare	

[ORM-Compare](../../../orm-compare)  

Test Evn : Local windows.  
DB: MySQL (Version 5.6.24).  
Test point: Batch Insert;Select paging; Transaction(update and select).  

<table cellspacing="0" cellpadding="0">
  <col width="62" />
  <col width="69" />
  <col width="64" />
  <col width="69" span="2" />
  <col width="96" />
  <tr height="19">
    <td colspan="6" height="19" width="429"><div align="center">Batch Insert(unit: ms)</div></td>
  </tr>
  <tr height="19">
    <td height="19">　</td>
    <td>5k</td>
    <td>1w</td>
    <td>2w</td>
    <td>5w</td>
    <td>10w</td>
  </tr>
  <tr height="19">
    <td height="19">Bee</td>
    <td align="right">529.00 </td>
    <td align="right">458.33 </td>
    <td align="right">550.00 </td>
    <td align="right">1315.67 </td>
    <td align="right">4056.67 </td>
  </tr>
  <tr height="19">
    <td height="19">MyBatis</td>
    <td align="right">1193</td>
    <td align="right">713</td>
    <td align="right">1292.67 </td>
    <td align="right">1824.33 </td>
    <td>Exception</td>
  </tr>
</table>
<p>&nbsp;</p>
<table cellspacing="0" cellpadding="0">
  <col width="62" />
  <col width="69" />
  <col width="64" />
  <col width="69" span="2" />
  <col width="96" />
  <tr height="19">
    <td colspan="6" height="19" width="429"><div align="center">Select(unit: ms)</div></td>
  </tr>
  <tr height="19">
    <td height="19">　</td>
    <td align="right">20</td>
    <td align="right">50</td>
    <td align="right">100</td>
    <td align="right">200</td>
    <td align="right">500</td>
  </tr>
  <tr height="19">
    <td height="19">Bee</td>
    <td align="right">17.33 </td>
    <td align="right">58.67 </td>
    <td align="right">52.33 </td>
    <td align="right">38.33 </td>
    <td align="right">57.33 </td>
  </tr>
  <tr height="19">
    <td height="19">MyBatis</td>
    <td align="right">314.33 </td>
    <td align="right">446.00 </td>
    <td align="right">1546.00 </td>
    <td align="right">2294.33 </td>
    <td align="right">6216.67 </td>
  </tr>
</table>
<p>&nbsp;</p>
<table cellspacing="0" cellpadding="0">
  <col width="62" />
  <col width="69" />
  <col width="64" />
  <col width="69" span="2" />
  <col width="96" />
  <tr height="19">
    <td colspan="6" height="19" width="429"><div align="center">Transaction(update and select) (unit: ms)</div></td>
  </tr>
  <tr height="19">
    <td height="19">　</td>
    <td align="right">20</td>
    <td align="right">50</td>
    <td align="right">100</td>
    <td align="right">200</td>
    <td align="right">500</td>
  </tr>
  <tr height="19">
    <td height="19">Bee</td>
    <td align="right">1089.00 </td>
    <td align="right">70.00 </td>
    <td align="right">84.00 </td>
    <td align="right">161.33 </td>
    <td align="right">31509.33 </td>
  </tr>
  <tr height="19">
    <td height="19">MyBatis</td>
    <td align="right">1144</td>
    <td align="right">35</td>
    <td>79.67 </td>
    <td align="right">146.00 </td>
    <td align="right">32155.33 </td>
  </tr>
</table>

Quick Start:
=========	
## 1. Add Bee   
#### 1.1 if it is a maven project,add the following dependency  

```xml
		<dependency>
			<groupId>org.teasoft</groupId>
			<artifactId>bee</artifactId>
			<version>1.8</version>
		</dependency>

		<dependency>
			<groupId>org.teasoft</groupId>
			<artifactId>honey</artifactId>
			<version>1.8</version>
		</dependency>
```

#### 1.2  Of course, can download the jar file directly  

## 2. Create the database and the table  

eg:  
Create one database,default name is bee.  
Create the tables and init the data by run the [init-data(user-orders)-mysql.sql](../../../bee-exam/blob/master/src/main/resources/init-data(user-orders)-mysql.sql) file(it is mysql sql script).  

## 3. Update the database configuration in bee.properties if need  
If no the bee.properties file, you can create it by yourself.

bee.databaseName=mysql  
bee.db.driverName = com.mysql.jdbc.Driver  
bee.db.url =jdbc:mysql://localhost:3306/bee?characterEncoding=UTF-8  
bee.db.username = root  
bee.db.password =  

## 4. Run the following java code  

```java
		
import java.math.BigDecimal;
import java.util.List;

import org.teasoft.bee.osql.Suid;
import org.teasoft.honey.osql.core.BeeFactory;
import org.teasoft.honey.osql.example.entity.Orders;

/**
 * @author Kingstar
 * @since  1.0
 */
public class OsqlExamEN {
	
	public static void main(String[] args) {
		Suid suid=BeeFactory.getHoneyFactory().getSuid();
		
		Orders orders1=new Orders();
		orders1.setId(100001L);
		orders1.setName("Bee(ORM Framework)");
		
		List<Orders> list1 =suid.select(orders1);  //select
		for (int i = 0; i < list1.size(); i++) {
			System.out.println(list1.get(i).toString());
		}
		
		orders1.setName("Bee--ORM Framework");
		int updateNum=suid.update(orders1);   //update
		System.out.println("update record:"+updateNum);
		
		Orders orders2=new Orders();
		orders2.setUserid("client01");
		orders2.setName("Bee(ORM Framework)");
		orders2.setTotal(new BigDecimal(91));
		orders2.setRemark("");  //empty String test
		
		int insertNum=suid.insert(orders2); //insert
		System.out.println("insert record:"+insertNum);
		
		int deleteNum=suid.delete(orders2);   //delete
		System.out.println("delete record:"+deleteNum);
		
		List<Orders> list2 =suid.select(orders1); //select  confirm the data
		for (int i = 0; i < list2.size(); i++) {
			System.out.println(list2.get(i).toString());
		}
	}
// notice: this is just a simple sample. Bee suport transaction,paging,complicate select,slect json,and so on.
}
```

Rapid application development:
=========	
**Let Java more quicker programming than php and Rails.**  

**Faster development of new combinations of Java Web：**  
[Bee+Spring+SpringMVC](../../../../aiteasoft/bee-spring-springmvc)  

**Faster development of new combinations of Spring Cloud microservices：**  
[Bee + Spring Boot](../../../bee-springboot)  

...  
  
Contact & Welcome:
=========	
#### Author's email:    honeysoft@126.com  
#### If you have any problem on bee, please let me know kindly! Thank you, so much!  
#### ORM QQ Group: 992650213     WeChat:AiTeaSoft  
#### At the same time, welcome you to join Bee team create a better future. 