## Mysql数据库

### 数据库按数据模型分类

- 关系型数据库（RDBMS）：例如MySQL，SQL Server
- 非关系型数据库（NoSQL）：例如MongoDB，Redis



### 数据库的四个基本概念

- 数据：是数据库中存储的基本单位，是描述事物的符号记录（例如某个学生的学号，姓名等信息）
- 数据库：是存储数据的集合
- 数据库管理系统：用于管理数据库的软件
- 数据库系统：由 **数据库（DB）+ 数据库管理系统（DBMS）+ 硬件 + 软件 + 用户** 组成的完整系统。



### 理解MySQL数据库

- 库中存放表，表中存放数据
- 库可以有多个表，表中有唯一的标识
- 表由列组成，数据按行存储



### MySQL数据库数据

|            术语            |                      描述                      |
| :------------------------: | :--------------------------------------------: |
|  Row（行）/Record（记录）  |                 表中的一条数据                 |
| Column（列）/Field（字段） |                 表的属性/字段                  |
|        View（视图）        |    基于查询结果创建的虚拟表，不存储实际数据    |
|    Primary Key（主键）     | 唯一标识表中每一行数据的字段（唯一的、非空的） |
|    Foregin Key（外键）     |        连接两张表的字段，保证数据一致性        |
|     Unique（唯一约束）     |                  确保字段唯一                  |
|    Not Null（非空约束）    |                限制字段不能为空                |
|     Default（默认值）      |                为字段提供默认值                |
|   DDL（数据库定义语言）    | 定义数据库结构，例如create table，alter table  |
|   DML（数据库操作语言）    |      操作数据，例如insert，delete，update      |
|   DQL（数据库查询语言）    |              查询数据，例如select              |
|    DCL（权限控制语言）     |          权限管理，例如grant，revoke           |
|    TCL（事务控制语言）     |         事务管理，例如commit，rollback         |
|       Cursor（游标）       |             逐行处理查询结果的机制             |
|    Transaction（事务）     |        保证数据操作的完整性（ACID原则）        |



### 相关操作

- DDL

  - create table：创建数据表
  - alter table：修改表结构
  - drop table：删除表
  - create index：创建索引
  - drop index：删除索引

- DML

  - insert：添加/插入数据
  - delete：删除数据
  - update：修改数据

- DQL

  - select：查询数据

- DCL

  - grant：授予访问权限
  - revoke：撤销访问权限

- TCL

  - commit：提交事务

  - rollback：回滚事务
  - savepoint：设置保存点
  - lock：对数据的特定部分进行锁定



### 数据类型

- 数值

  - 整型

    |   类型   | 长度（字节） |
    | :------: | :----------: |
    | tinyint  |      1       |
    | smallint |      2       |
    | mediuint |      3       |
    |   int    |      4       |
    |  bigint  |      8       |

  - 浮点型

    |  类型   | 长度（字节） |
    | :-----: | :----------: |
    |  float  |      4       |
    | double  |      8       |
    | decimal |     变长     |

    

- 字符串

  |             类型              |         长度          |
  | :---------------------------: | :-------------------: |
  | char(n)（适用于固定长度数据） | 固定长度（n表示长度） |
  | varchar（适用于可变长度文本） |         变长          |
  |     text（适用于大文本）      |         变长          |
  | blob（适用于存储二进制数据）  |         变长          |
  |    enum（适用于有限选项）     |          1~2          |
  |     set（适用于多选字段）     |          1~8          |

  

- 日期

  |                             类型                             | 长度 |        格式         |
  | :----------------------------------------------------------: | :--: | :-----------------: |
  |                    date（适用于存储日期）                    |  3   |     YYYY-MM-DD      |
  |               datetime（适用于精确到秒的时间）               |  8   | YYYY-MM-DD HH:mm:ss |
  | timestamp（适用于存储系统日志、记录创建时间、修改时间等，受时区影响） |  4   | YYYY-MM-DD HH:mm:ss |
  |                  time（适用于存储时间间隔）                  |  3   |      HH:mm:ss       |
  |                    year（适用于存储年份）                    |  1   |        YYYY         |
  
  
  
- BLOB

  | BLOB数据类型 |                      大小                       |
  | :----------: | :---------------------------------------------: |
  |   TINYBLOB   |            存储最大 255 字节的数据。            |
  |     BLOB     |          存储最大 65,535 字节的数据。           |
  |  MEDIUMBLOB  |        存储最大 16,777,215 字节的数据。         |
  |   LONGBLOB   | 存储最大 4,294,967,295 字节（大约 4GB）的数据。 |

  
  
- ENUM vs SET

  | **特性** | **ENUM**                            | **SET**                        |
  | -------- | ----------------------------------- | ------------------------------ |
  | 存储方式 | 单选（一个值）                      | 多选（多个值）                 |
  | 例子     | `ENUM('A', 'B', 'C')`               | `SET('A', 'B', 'C')`           |
  | 存储值   | 只能存 `A`、`B` 或 `C` 中的**一个** | 可以存 `A,B` 或 `B,C` 等多个值 |
  | 适用场景 | 性别、状态等单选字段                | 兴趣爱好、标签等多选字段       |



### 数据库的常用操作

|                             格式                             |         描述         |
| :----------------------------------------------------------: | :------------------: |
|                      mysql -u 用户名 -p                      |      登录数据库      |
|                        show databases                        | 查询已有的数据库列表 |
| create database 数据库名 库选项（create database students charset utf8）（注意utf8） |      创建数据库      |
| alter database 数据库名 库选项（alter database stu charset gbk） |      修改数据库      |
| drop database if exists 数据库名 （drop database if exists stu） |      删除数据库      |
|                    use database 数据库名                     |      指定数据库      |

PS：修改数据库名只能手动迁移数据，还有注意分号的使用



### 数据库表的常用操作

|                             格式                             |    描述    |
| :----------------------------------------------------------: | :--------: |
| create table 表名（字段1 数据类型 约束条件，……）<br />（create table student(stu_id primary key auto_increment,stu_name varchar(10),score int(11))） |   创建表   |
|                          desc 表名                           | 查看表结构 |
|                    show columns from 表名                    | 查看表结构 |
| alter table 表名 add column 字段名称 数据类型（长度） 约束条件 |  添加字段  |
| alter table 表名 change 原始名称 新名称 数据类型（长度） 约束条件 |  修改字段  |
|                alter table 表名 drop 字段名称                |  删除字段  |
|          insert into 表名(字段1，……) value(值1，……)          |  插入数据  |
|               delete from 表名 （where 条件）                |  删除数据  |
|       updata 表名 SET 字段1 = 值1 （where 字段2=值2）        |  修改数据  |
|              select * from 表名 （where 条件）               |  查询数据  |
|                       drop table 表名                        |   删除表   |
|                         show tables                          | 查看所有表 |

ps：注意分号的使用，exit；退出数据库



### MySQL的进阶操作



### Python操作MySQL

```python
# 安装mypython：pip install pymysql

# 导入模块
import pymysql

# 连接数据库
# 官方建议使用passwors，不建议使用passwd，里面可以指定数据库，还有一个属性autocommit=True（默认False），自动提交事务
conn = pymysql.connect(host='localhost', port=3306, user='root',password='123456',autocommit=True)

# 通过游标操作数据库（游标是数据库连接和数据库之间的中介）
cur = conn.cursor()
cur.execute('create database if not exists stu')
cur.execute('use stu')
create_students = 'create table if not exists students (stu_id int(11) primary key auto_increment,stu_name varchar(255),score float)'
cur.execute(create_students)
cur.execute('insert into students (stu_name,score) values ("scr",100)')
"""
    fetchall()：获取所有结果，返回一个包含所有结果的列表，每一行是一个元组。
    fetchone()：获取查询结果的第一行，返回一个元组。如果没有更多结果，则返回 None。
    fetchmany(n)：获取指定数量的结果，返回一个包含前 n 行的列表，每一行是一个元组。
"""
cur.execute('select * from students')
results = cur.fetchall()
for i in results:
    print(i)
```



### 游标（Cursor）的作用

游标（Cursor）在 Python 操作数据库时，起到了执行 SQL 语句、遍历查询结果、管理事务的作用。主要用于查询、插入、更新、删除数据，特别是在需要逐行处理数据时非常有用。
