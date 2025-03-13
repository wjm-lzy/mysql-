1.在mysql官网下载文档后安装
2.在终端使用net start mysql80启动mysql，使用net stop mysql80停止mysql，note 需要使用管理员身份进行运行终端
3.在终端中可以使用
4.客户端连接mysql: mysql [-h 127.0.0.1] [-P 3306] -u root -p

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
查询：show database;<br>
查询当前:select databases();<br>
创建：create database [if not exists] 数据库名 [default charset字符集] [collate排序规则];<br>
上述[]括起来的部分都是可选的<br>
删除数据库:drop database[if exists] 数据库名;<br>
使用数据库:use 数据库名称;
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
</div>