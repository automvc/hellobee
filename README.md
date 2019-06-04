
Bee
=========
**Bee** 是一个 ORM框架,它的开发速度快，编码少,还很简单。    
**Bee** 是一个具有省时/优雅、简易、自动( **Tea:** Timesaving/Tasteful, Easy, Automatic) 风格的ORM框架。  
你还在为不断重复写ORM操作数据库的代码而烦恼吗?每写一个service业务层，就要写一个dao层(即使我们知道dao就是简单的查改增删suid操作)。  
请试试**Bee** 吧，让它帮你从烦琐的编码工作中解脱出来。  
Bee是一种更接近SQL语言思维的ORM框架，  
一种开发速度和开发成本都不比php差的Java ORM框架，  
而且它的编码复杂度是O(1)，即用了Bee，你可以不用另外再写dao代码。  

## Bee主要功能特点介绍：  
* 1.接口简单，使用方便。Suid接口只有4个方法,对应SQL语言的select,update,insert,delete操作。  
* 2.使用了Bee,你可以不用再另外编写dao代码，直接调用Bee的api即可完成对DB的操作。  
* 3.Javabean没有注解,也不需要xml映射文件,只是纯的Javabean即可,甚至get,set方法不用也可以。  
* 4.自动过滤null和空字符串，不用再写一堆的判断非空的代码。  
* 5.支持只查询一部分字段。  
* 6.动态/任意组合查询条件,不需要提前准备dao接口,有新的查询需求也不用修改或添加接口。  
* 7.支持存储过程，支持原生SQL，支持事务，支持批处理操作。  
* 8.SQL中排序,分页支持。  
* 9.支持直接返回Json格式查询结果;链式编程。  


**Bee** 网址:  
https://github.com/automvc/bee  
**Bee在gitee** 的网址:  
https://gitee.com/automvc/bee


## 环境要求  
jdk1.7+

## 功能介绍: 

**V1.0**  

单表Suid(select,update,insert,delete)面向对象方式的操作,方法名与数据库Suid操作对应.  
自动通过DB的表或视图生成Javabean(目前支持MySQL,MariaDB,其它数据库有部分类型未做映射处理,客户可通过在配置文件添加配置信息实现).  
约定优于配置:Javabean没有注解,没有xml,只是纯的Javabean即可(为什么要给Javabean那么重的负担呢??!!!).  
自动映射表的列与的字段.  
Javabean支持原生类型:int,double等.  
使用PreparedStatement防止SQL注入攻击.  
Procedure存储过程支持.  
原生SQL支持.  
批处理操作支持.  
Transaction事务支持.  
自动过滤null和空字符串(作为默认实现).  
SQL中函数:MAX,MIN,SUM,AVG,COUNT支持.  
SQL中排序,分页支持.  
支持只查询一部分字段.  
动态/任意组合查询条件,不需要提前准备dao接口,有新的查询需求也不用修改或添加接口.  
所有的suid操作都是用同一个bee接口,不用再定义任何新的dao接口,更不用实现dao接口.  
用户/开发者仅需要关注bee接口如何调用即可.  

**V1.1**  
直接返回Json格式查询结果支持.  
Procedure存储过程支持(CallableStatement.executeQuery).  

**V1.2**  
用户自定义sql支持#{para}占位参数设置，如：eg:name=#{name}; like查询 支持:#{%para%},#{%para},#{para%} 

**V1.3**  
增加:select/update链式编程

**V1.4**  
增加: selectById,deleteById  
增加: public <T> List<T> select(T entity,String selectFields,int from,int size)  

快速开始:
=========	
## 1. 引入Bee  
#### 1.1 maven工程,添加如下依赖  

```xml
		<dependency>
			<groupId>org.teasoft</groupId>
			<artifactId>bee</artifactId>
			<version>1.4.2</version>
		</dependency>

		<dependency>
			<groupId>org.teasoft</groupId>
			<artifactId>honey</artifactId>
			<version>1.4.23</version>
		</dependency>
```

#### 1.2  也可以直接下载jar文件  	
		
## 2. 创建数据库和表  

创建一个数据库,默认名称为bee.  
用bee.sql脚本创建一个表和插入初始化数据.  

## 3. 更新数据库的配置信息(在bee.properties)  

bee.db.driverName = com.mysql.jdbc.Driver  
bee.db.url =jdbc:mysql://localhost:3306/bee?characterEncoding=UTF-8  
bee.db.username = root  
bee.db.password =  

## 4. 运行下面的 java代码    

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
public class SuidExam {
	
	public static void main(String[] args) {
		Suid suid=BeeFactory.getHoneyFactory().getSuid();
		
		Orders orders1=new Orders();
		orders1.setId(100001L);
		orders1.setName("Bee--ORM Framework");
		
		//默认不处理null和空字符串.不用再写一堆的判断;其它有值的字段全部自动作为过滤条件
		List<Orders> list1 =suid.select(orders1);  //select
		for (int i = 0; i < list1.size(); i++) {
			System.out.println(list1.get(i).toString());
		}
		
		orders1.setName("Bee--ORM Framework");
		//默认只更新需要更新的字段. 过滤条件默认只用id字段,其它需求可用SuidRich中的方法.
		int updateNum=suid.update(orders1);   //update
		System.out.println("update record:"+updateNum);
		
		Orders orders2=new Orders();
		orders2.setUserid("bee");
		orders2.setName("Bee-ORM framework");
		orders2.setTotal(new BigDecimal(91.99));
		orders2.setRemark("");  //empty String test
		
		//默认不处理null和空字符串.不用再写一堆的判断;其它有值的字段全部自动插入数据库中. 
		//方便结合DB插值,如id自动增长,由DB插入;createtime由DB默认插入
		int insertNum=suid.insert(orders2); //insert
		System.out.println("insert record:"+insertNum);
		
		//默认不处理null和空字符串.不用再写一堆的判断;其它有值的字段全部自动作为过滤条件
//		int deleteNum=suid.delete(orders2);   //delete
//		System.out.println("delete record:"+deleteNum);
		
		List<Orders> list2 =suid.select(orders1); //select  confirm the data
		for (int i = 0; i < list2.size(); i++) {
			System.out.println(list2.get(i).toString());
		}
	}

}

```

综合应用:
=========	
**更快的开发Java Web的新组合：**  
[Bee+Spring+SpringMVC](../../../../aiteasoft/bee-spring-springmvc)  

**更快的开发Spring Cloud微服务的新组合：**  
[Bee + Spring Boot](../../../bee-springboot)  


#### 作者的电子邮箱email:    honeysoft@126.com  
#### 如有任何相关建议,欢迎给作者发邮件,不胜感激!  
#### 同时,也欢迎你加入到Bee框架的开发之中,相信有你的加入,Bee会更加美好! 
