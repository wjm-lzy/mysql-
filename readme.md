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
<h6>SQL分类<h6>
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
<h6>DDL-表操作</h6>
查询当前数据库所有表：show tables;<br>
查询表结构:desc 表名称<br>
查询指定表的建表语句:show create table 表名;<br>
使用数据库:use 数据库名称;<br>
创建表:create table 表名(字段1 字段1类型,字段2 字段2类型... )[comment表注释];<br>
<h6>DDL-数据类型</h6>
数值类型
<ul>
<li></li>
<li>多行注释 /* */</li>
</ul>
</div>
