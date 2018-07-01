
Bee
=========
Bee is ORM framework.
Honey implements the interface in the Bee.
Bee see:
https://github.com/automvc/bee
Honey see:
https://github.com/automvc/honey

<h1> Function: </h1>
<B>Bee</B> is <B>Sea</B>(Simple, Easy, Automatic) style ORM framework.
V1.0
Single entity Suid (select,update,insert,delete) object-oriented operation.
Automatic generate the Javabean via DB table (mysql).
PreparedStatement support.
Procedure support.
Native SQL support.
Automatic filter the null and empty field for default.
Order by,MAX,MIN,SUM,AVG,COUNT support.


Quick Start:
=========

public static void main(String[] args) {
		Suid suid=BeeFactory.getHoneyFactory().getSuid();
		
		Orders orders1=new Orders();
		orders1.setId(100001L);
		orders1.setName("Bee--ORM Framework");
		
		List<Orders> list1 =suid.select(orders1);  //select
		for (int i = 0; i < list1.size(); i++) {
			System.out.println(list1.get(i).toString());
		}
		
		orders1.setName("Bee(V1.0)--ORM Framework");
		int updateNum=suid.update(orders1);   //update
		System.out.println("update record:"+updateNum);
		
		Orders orders2=new Orders();
		orders2.setUserid("client01");
		orders2.setName("ORM book");
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





