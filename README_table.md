
ORM Compare
=========
Which feature do you want?	

Test Evn : Local windows 
DB: MySQL (Version 5.6.24)	
Test point: Batch Insert;Select paging; Transaction(update and select).		

<table cellspacing="0" cellpadding="0">
  <col width="62" />
  <col width="69" />
  <col width="64" />
  <col width="69" span="2" />
  <col width="96" />
  <tr height="19">
    <td colspan="6" height="19" width="429">Batch Insert(unit: ms)</td>
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
    <td align="right">880</td>
    <td align="right">720</td>
    <td align="right">620</td>
    <td align="right">1420</td>
    <td align="right">4700</td>
  </tr>
  <tr height="19">
    <td height="19">Bee</td>
    <td align="right">359</td>
    <td align="right">358</td>
    <td align="right">484</td>
    <td align="right">1248</td>
    <td align="right">4000</td>
  </tr>
  <tr height="19">
    <td height="19">Bee</td>
    <td align="right">348</td>
    <td align="right">297</td>
    <td align="right">546</td>
    <td align="right">1279</td>
    <td align="right">3470</td>
  </tr>
  <tr height="19">
    <td height="19">(AVG)</td>
    <td align="right">529.00 </td>
    <td align="right">458.33 </td>
    <td align="right">550.00 </td>
    <td align="right">1315.67 </td>
    <td align="right">4056.67 </td>
  </tr>
  <tr height="10">
    <td height="10">　</td>
    <td>　</td>
    <td>　</td>
    <td>　</td>
    <td>　</td>
    <td>　</td>
  </tr>
  <tr height="19">
    <td height="19">MyBatis</td>
    <td align="right">1513</td>
    <td align="right">1092</td>
    <td align="right">1466</td>
    <td align="right">1700</td>
    <td>Not Support</td>
  </tr>
  <tr height="19">
    <td height="19">MyBatis</td>
    <td align="right">1045</td>
    <td align="right">577</td>
    <td align="right">812</td>
    <td align="right">1923</td>
    <td>Not Support</td>
  </tr>
  <tr height="19">
    <td height="19">MyBatis</td>
    <td align="right">1021</td>
    <td align="right">470</td>
    <td align="right">1600</td>
    <td align="right">1850</td>
    <td>Not Support</td>
  </tr>
  <tr height="19">
    <td height="19">(AVG)</td>
    <td align="right">1193</td>
    <td align="right">713</td>
    <td align="right">1292.67 </td>
    <td align="right">1824.33 </td>
    <td>Exception</td>
  </tr>
</table>



**Bee** is an ORM framework.   
**Bee** is an easy and high efficiency ORM framework. **Easy for Stronger.** 	 
**Coding Complexity is O(1),it means that Bee will do the Dao for you**.  

**Bee** see:  
https://github.com/automvc/bee  
