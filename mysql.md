
<h3>知识介绍：<h3>
<h4>基础篇<h4>
<h5>SQL<h5>
<h6>
mysql数据库中关系型数据库：是建立在关系模型基础上的，由多张相互连接的二维表组成的数据库
<h6>
<h6>SQL通用语法<h6>
<ol>
<li>SQL可以单行或多行书写，以分号结尾</li>
<li>SQL可以使用空格或者缩进来增强语句的可读性</li>
<li>MySQL数据库的SQL语句不区分大小写</li>
</ol>
注释的使用：
<ul>
<li>单行注释：--注释内容或者#注释内容</li>
<li>多行注释 /* */</li>
</ul>
<h5>SQL分类<h6>
<div>
<table>
  <tr>
      <th>分类</th>
      <th>说明</th>
  </tr>
  <tr>
      <td>DDL</td>
      <td>数据定义语言，用来定义数据库对象</td>
  </tr>
  <tr>
      <td>DML</td>
      <td>数据操作语言，用来对数据进行增删改</td>
  </tr>
  <tr>
      <td>DQL</td>
      <td>数据查询语言，用来查询数据库中表的记录</td>
  </tr>
  <tr>
      <td>DCL</td>
      <td>数据控制语言，用来创建数据库用户，控制数据库访问权限</td>
  </tr>
</table>
</div>

<div>
<h6>DDL-数据库操作</h6>
查询：show databases;<br>
查询当前:select databases();<br>
创建：create database [if not exists] 数据库名 [default character set字符集] [collate排序规则];<br>
上述[]括起来的部分都是可选的,如果不指定字符集，默认latin1，也可以指定为utf-8<br>
删除数据库:drop database[if exists] 数据库名;<br>
使用数据库:use 数据库名称;
<h6>修改字符集：alter database 数据库 character set utf8;</h6>
</div>

<div>
<h5>DDL-表操作</h5>
查询当前数据库所有表：show tables;<br>
查询表结构:desc 表名称<br>
查询指定表的建表语句:show create table 表名;<br>
使用数据库:use 数据库名称;<br>
创建表:create table 表名(字段1 字段1类型,字段2 字段2类型... )[comment表注释];<br>

<ul>
<li>单行注释 # </li>
<li>多行注释 /* */</li>
</ul>
</div>


<h5>DDL-数据类型</h5>

<div>
<h6>数值类型</h6>
<table>
  <tr>
      <th>类型</th>
      <th>大小（bytes）</th>
      <th>描述</th>
  </tr>
  <tr>
      <td>tinyint</td>
      <td>1</td>
      <td>小小整数值</td>
  </tr>
  <tr>
      <td>smallint</td>
      <td>1</td>
      <td>小整数值</td>
  </tr>
  <tr>
      <td>mediumint</td>
      <td>3</td>
      <td>中整数值</td>
  </tr>
  <tr>
      <td>int</td>
      <td>4</td>
      <td>整数值</td>
  </tr>
  <tr>
      <td>bigint</td>
      <td>4</td>
      <td>大整数值</td>
  </tr>
  <tr>
      <td>float</td>
      <td>4</td>
      <td>单精度浮点数</td>
  </tr>
  <tr>
      <td>double</td>
      <td>8</td>
      <td>双精度浮点数</td>
  </tr>
  <tr>
      <td>decimal</td>
      <td>---</td>
      <td>小数值</td>
  </tr>
</table>
<h6>note:这是一个例子，举出age类型 age tinyint unsigned</h6>
</div>

<div>
<h6>字符串类型：这里主要介绍两个</h6>
<table>
  <tr>
      <th>类型</th>
      <th>大小（bytes）</th>
      <th>描述</th>
  </tr>
  <tr>
      <td>char</td>
      <td>0-255</td>
      <td>定长字符串，定义多长就是多长，剩余用空格补齐</td>
  </tr>
  <tr>
      <td>varchar</td>
      <td>0-65535</td>
      <td>变长字符串：根据所存储内容改变长度</td>
  </tr>
</table>
<h6>note:相比之下，虽然char更占用空间，但是性能较好，varchar使用时需要计算所占用空间</h6>
</div>

<div>
<h6>日期类型</h6>
<table>
  <tr>
      <th>类型</th>
      <th>大小（bytes）</th>
      <th>描述</th>
  </tr>
  <tr>
      <td>date</td>
      <td>3</td>
      <td>日期值 YYYY-MM-DD</td>
  </tr>
  <tr>
      <td>time</td>
      <td>3</td>
      <td>时间值：HH:MM:SS</td>
  </tr>
  </tr>
  <tr>
      <td>year</td>
      <td>1</td>
      <td>年份：YYYY</td>
  </tr>
  </tr>
  <tr>
      <td>datatime</td>
      <td>8</td>
      <td>时间日期混合值</td>
  </tr>
  </tr>
  <tr>
      <td>timestamp</td>
      <td>4</td>
      <td>混合日期和时间（时间戳）</td>
  </tr>
</table>
<h6>note:相比之下，虽然char更占用空间，但是性能较好，varchar使用时需要计算所占用空间</h6>
</div>

<div>
<h5>DDL-表操作-修改</h5>
<h6>添加字段：alter table 表名 add 字段名 类型(长度) [comment注释] [约束];</h6>
<h6>修改字段：alter table 表名 change 旧字段名 新字段名 类型(长度) [comment注释] [约束];</h6>
<h6>删除字段：alter table 表名 drop 字段名;</h6>
<h6>修改表名：alter table 表名 rename to 新表名;</h6>
<h6>删除表：alter table 表名;</h6>
<h6>插入数据：insert into 表名 values()或者insert into 表名 (属性)values()</h6>
<h6>select 属性,属性 as 别名 from 表名 where 条件</h6>
<h6>如果在上面的语句后面添加 \G就会按照每行多要素分布显示</h6>
<h6>修改数据：update 表名 set 属性=数值;</h6>
<h6>删除表中数据：delete from 表名 where 条件,也可以使用truncate table 表名，但是这样数据无法回滚</h6>
</div>
<h5>简单案例</h5>
<h6>按math成绩从小大的排序, 求math成绩在5-8名的<br>
select * from student order by math limit 4, 4;<br>
		 limit后面的两个数字的意思:
		 	第一个4: 表示要跳过前面几个
		 	第二个4: 表示连续取几个.
</h6>
<h6>--查出各个班的总分和最高分<br>
select class_id, sum(chinese+english+math), max(chinese+english+math) from student group by class_id;<br>
group表示分组通过class_id
</h6>
<h6>--求各个班级英语的平均分<br>
			select class_id, avg(english) from student group by class_id;
</h6>
<h6>--查询出班级总分大于1300分的班级ID<br>
			select class_id, sum(chinese+english+math) sumscore from student group by class_id having sumscore>1300;
</h6>

<h4>mysql 中的时间日期函数</h4>
<h6>mysql中的函数分为三类，时间，日期，时间戳（含义时分秒的sysdate）</h6>
<h6>查看当前时间戳，select sysdate() from dual;<br>now()函数和sysdate函数表示意义一致</h6>
<h6>获取年year(now()),获取月month(now()),获取日day(now())</h6>
<h6>获取日期，时间，时间戳：select CURRENT_DATE(),CURRENT_TIME(),CURRENT_TIMESTAMP() from daul;</h6>
<h4>常用数学函数</h4>
<h6>若发生错误，所有数学函数会返回 NULL </h6>
<h6>ABS(X) 返回X 的绝对值。 </h6>
<h6>bin(X) 返回X 的二进制。 </h6>
<h6>ceiling(X) 向上取整。 </h6>
<h6>floor(X) 向下取整。 </h6>
<h6>mod(X，Y) 取余。 </h6>
<h6>rand() 随机值。 </h6>

<h4>多表查询</h4>
<h6>导入数据：source 文件（要求文件为sql文件）</h6>
<h6>交叉连接---相当于笛卡尔积：select e.*, d.* from emp e cross join dept d;</h6>
<h6>自连接，查询两个表的所有信息select e.*, d.* from emp e inner join dept d on e.deptno=d.deptno;</h6>
<h6>左外连接：select e.*, d.* from emp e right outer join dept d on e.deptno=d.deptno;</h6>
<h6>右外连接：select e.*, d.* from dept d left outer join emp e on e.deptno=d.deptno;
</h6>
<h6>外链接取值与关系表达式=号左右位置无关。取值跟from后表的书写顺序有关。 
</h6>
<h4>字符串</h4>
<h6>charset(str)返回编码集</h6>
<h6>concat(st11,str2...)连接多个字符串</h6>
<h6>返回sub在str中的位置，没有则返回0 instr(str,sub)</h6>
<h6>大小写转换：大写：ucase(),小写lcase();</h6>
<h6>left(str,num),从左边开始取num个字符</h6>
<h6>length()返回长度</h6>
<h6>replace(str,str1,str2)将str中的str1转换为str2</h6>
<h6>strcmp()比较两个字符串</h6>
<h6>substring(str,num1,num2)从str的 num1位置取出num2个字符，num1为负数代表从右侧取出</h6>
<h4>表的约束</h4>
<h6>*定义主键约束　primary key:	不允许为空，不允许重复<br>
	*定义主键自动增长　auto_increment<br>
	*定义唯一约束　unique<br>
	*定义非空约束　not null<br>
	*定义外键约束　constraint ordersid_FK foreign key(ordersid) references orders(id)<br>
	*删除主键：alter table tablename drop primary key ;<br>
</h6>
<h6>准备两个表:<br>
create table class (<br>
id INT(11) primary key auto_increment,<br>
name varchar(20) unique<br>
);
<br>
create table student (<br>
id INT(11) primary key auto_increment, <br>
name varchar(20) unique,<br>
passwd varchar(15) not null,<br>
classid INT(11),<br>
constraint stu_classid_FK foreign key(classid) references class(id)<br>
);<br>
note:主键自动增长，没有数据自动给你填入数据
</h6>