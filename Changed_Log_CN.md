
Bee
=========
#### 工欲善其事必先利其器！——《论语·卫灵公》    
**Bee** 是一个 Java ORM框架利器, 它的开发速度快, 编码少, 还很简单！       
**Bee** 编码复杂度是O(1)，即用了Bee，**无论多少个表**,你都可以不用另外再写dao代码。  


## 详细功能介绍: 

**V1.0**  
单表Suid(select,update,insert,delete)面向对象方式的操作,方法名与数据库Suid操作对应.  
自动通过DB的表或视图生成Javabean(V1.0支持MySQL,MariaDB,其它数据库有部分类型未做映射处理,客户可通过在配置文件添加配置信息实现).  
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
**直接返回Json**格式查询结果支持.  
Procedure存储过程支持(CallableStatement.executeQuery).  

**V1.2**  
用户自定义sql支持#{para}占位参数设置，如：eg:name=#{name}; like查询 支持:#{%para%},#{%para},#{para%} 

**V1.3**  
增加:select/update链式编程

**V1.4**  
增加: selectById,deleteById  
增加: public &lt;T> List&lt;T> select(T entity,String selectFields,int start,int size)  
增加: selectJson add config:ignoreNull;date,time,timestamp Wit hMillisecond format  
增加: List<String[]> select(String sql), add config:nullToEmptyString  
完善查询结果缓存机制(一级缓存可**对用户编程透明**,也可进行细粒度配置调优控制)  
**一级缓存**即可支持: **不缓存列表,永久缓存列表,永久缓存且可更新列表**,结果集超过一定大小可不放缓存 等细粒度配置调优控制.  
增加: SysValue注解  

**V1.5**  
1.增加NameTranslate接口和默认转换实现类，支持Java与DB命名转换规则自定义。  
2.支持jdbcTypeToFieldType-{DbName}.properties,自定义DB列转Java的类型。  
3.完善Oracle类型转换；**多种DB支持轻松扩展**:可将某种DB特有的类型映射关系放在文件:  
  jdbcTypeToFieldType-{DbName}.properties，即可完成自动转换。  
4.增加entity实体名与表名的特殊映射关系支持,优化表名转实体名的情况。  
5.过滤非法实体类型。  
6.增加**文件生成工具**。  
7.完善分页功能,并支持自定义扩展接口。  
8.修复Oracle JDBC操作数据库ORA-00911 bug。  
9.增加op方法重载，默认为等号(in UpdateImpl and SelectImpl)。  
10.增加OperationType重载(in enum Op)。  

**V1.6**  
1.Suid增加**面向对象方式复杂查询**支持.  
  Suid接口增加方法:public &lt;T> List&lt;T> select(T entity,Condition condition);  
   支持范围查询;支持同时使用范围查询、模糊查询、in、>、>=、<、<=、分组、having过滤、排序、分页等复杂查询。  
2.SuidRich增加面向对象方式复杂查询支持.  
SuidRich接口增加方法:  
select(T entity, IncludeType includeType, Condition condition)  
selectJson(T entity, IncludeType includeType, Condition condition)  
3.SuidRich增加更新方法:  
updateBy(T entity,String whereFieldList)  
updateBy(T entity,String whereFieldList,IncludeType includeType)  
4.add SqlNullException in PreparedSqlLib.  
V1.6.1  
1.PreparedSql相关方法添加start,size分页参数，使自定义sql查询的分页更方便，  
    自定义的sql语句中不用带分页部分,移植性更高。  
2.PreparedSql的modify加注解:@Deprecated  
3.Condition的方法getFieldSet返回值由Set改为Set<String>。  
4.fix bug.ConditionImpl的fieldSet需要记录在between方法使用的记录。  

**V1.7**  
增加面向对象方式**多表查询**支持.  
1.**支持一对一,一对多,多对一,多对多**。  
2.支持join(inner join), left join,right join, no join。  
3.单表、多表的查询操作互不干扰。  
**V1.7.1**  
创建javabean支持添加注释.  
创建javabean的类新增getColumnNames,getFieldNames方法.  
修复自定义sql没有占位符时出现的bug.  
修复在PreparedSqlLib分页的bug.  
完善在CustomSql中sql字符串为null的异常.  
修复关于缓存的bug.  
修复SelectImpl的bug. 
修复内连接条件风格转换的bug.  
添加FileCreator接口.  
**V1.7.2**   
可以通过配置选择已实现的命名转换规则.  
完善BeeFactory类的功能.  
调整SQL输出日志格式.  
日期格式可以通过配置定义.  
[将测试/使用实例迁移到bee-exam项目](../../../bee-exam).  
添加类FileLogger,用于将日志记录到文件中.  
可以通过配置控制是否输出日志级别.  
完善测试用例/使用样例.  
支持使用模板快速生成文件.  
在Suid接口增加方法 delete(T entity, Condition condition).  
支持配置是否允许删除一个表的所有数据(在面向对象方式下有效).  
SuidRich 新增两个方法:  
  updateBy(T entity,String whereFields,Condition condition)  
  update(T entity,String updateFields,Condition condition)  
新增不使用缓存配置支持.  
Condition接口新增方法setAdd,setMultiply用于设置SQL中update操作的set设置.  

**V1.8**   
**增加分布式特性:**   
1.添加多数据源支持(读写分离一主多从, 仅分库).  
增加多数据源无需改动Java代码(对编码透明)，只需添加配置信息即可. 
添加多数据源路由接口. 
添加多数据源路由实现算法.  
添加多数据源配置.  
支持配置信息刷新.  
2.分布式环境下生成全局唯一数字递增id.	  
分布式环境下生成连续单调递增(在一个workerid内),全局唯一数字id.  
3.Bee分布式唯一id算法特性:不依赖时钟,workerid可配置,易扩展.	  
具体算法实现:SerialUniqueId,OneTimeSnowflakeId,PearFlowerId.		  
提供id生成工厂:GenIdFactory,且可配置id生成器具体实现类.	  
4.可为所有表的Long型id字段自动生成全局唯一id主键.  
**增强功能:**   
5.同库分表支持,动态表名映射支持.  
实体与任意表名映射支持. 
Suid add one method:	
public Suid setDynamicParameter(String para,String value);  
add 2 annotation:@Table,@Entity.  
6.添加for update功能,用于锁住某个表的一些记录.  
public Condition forUpdate()  
7.增加高级更新设置值支持,复杂查询、多表查询支持只查部分字段:	
在Condition添加5个新方法:  
public Condition setAdd(String field, String fieldName)  
public Condition setMultiply(String field, String fieldName)  
public Condition set(String fieldNmae, Number num)  
public Condition set(String fieldNmae, String value)  
public Condition selectField(String fieldList)  
8.支持SQL输出日志配置,占位参数可显示参数,可输出直接可执行的sql:  
bee.osql.showSQL.showType=true  
bee.osql.showSQL.showExecutableSql=true  
9.SuidRich添加一个新方法:  
public &lt;T> int update(T entity,Condition condition);  
PreparedSql添加三个新方法:  
public String selectJson(String sqlStr);  
public List<String[]> select(String sql);  
public String selectFun(String sql);  
10.Oracle DATE字段在Javabean里转成java.sql.Date存入数据库时会丢失时分秒，
转成Timestamp可以解决这个问题。  
11.GenFiles根据模板自动生成文件代码添加支持首字母大写,如: #{entityName?up1}.  
**修复原有问题:**   
12.bug修复:缓存key生成;批插入后清缓存.  
修复缺陷:解析json时多余的逗号错误.  
修复null bug,关于方法:PreparedSql's method select(String sql,Object preValues[]).  
	
	