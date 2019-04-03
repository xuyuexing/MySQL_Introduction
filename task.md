# Day 1

## 第一次任务发布

任务一任务内容&打卡链接：https://shimo.im/docs/cTEYCyunBqM81E4T/ 《MySQL任务1打卡》

请在上面链接中查看任务内容，完成后在表格对应处填写博客链接。
截止时间：3月31日（明天）22:00，未按时打卡将会被清退。

## 任务一内容

### MySQL 软件安装及数据库基础

#### 学习

1. 软件安装及服务器设置。
   教程 http://www.runoob.com/mysql/mysql-install.html

2. (选做，但是强烈建议) 使用图形界面软件 Navicat for SQL
   群里提供破解版Navicat for SQL，看群公告或聊天记录搜索888查找。
   简易步骤:
      解压缩文件，复制key
      打开文件夹中的navicat.e
      用户名随意，输入key，然后连接数据库
      输入密码，连接名改成自己喜欢的
      剩下的自己探索，怎么在navicat中创建数据库、表等等

3. 数据库基础知识
   数据库定义
   关系型数据库
   二维表
   行
   列
   主键
   外键

4. MySQL数据库管理系统
   数据库
   数据表
   视图
   存储过程

------

# Day 2

## 第二次任务发布

任务二任务内容&打卡链接：https://shimo.im/docs/fJGE6lUscyQWdMz4/ 《MySQL任务2打卡》

请大家在4月2日22:00前在石墨文档中的打卡表格处打卡。
任务二是最最基础的查询语句，可以说学完本次课程，SQL语句就掌握了30%了。
语言规范非常重要，请大家认真仔细阅读。请记住，你写SQL需要考虑别人review时的心情。写的过于杂乱会分分钟造成暴力事件。
学习内容中函数部分，是让大家了解下MySQL可以怎样处理一些数据。了解些常用的，等实际中遇到了再回头查找详细就行。
祝大家学习开心。:-)

## 任务二内容

### MySQL 基础 （一）- 查询语句

#### 学习

1. 导入示例数据库，教程 https://www.yiibai.com/mysql/how-to-load-sample-database-into-mysql-database-server.html

2. SQL是什么？MySQL是什么？

3. 查询语句 SELECT FROM 
    语句解释
    去重语句
    前N个语句
    CASE...END判断语句

4. 筛选语句 WHERE 
    语句解释
    运算符/通配符/操作符

5. 分组语句 GROUP BY
    聚集函数
    语句解释
    HAVING子句

6. 排序语句 ORDER BY 
    语句解释
    正序、逆序

7. 函数
    时间函数
    数值函数
    字符串函数

8. SQL注释

9. SQL代码规范
    [SQL编程格式的优化建议](https://zhuanlan.zhihu.com/p/27466166)
    [SQL Style Guide](https://www.sqlstyle.guide/)

#### 作业

- 项目一：查找重复的电子邮箱（难度：简单）
      
      创建 email表，并插入如下三行数据
      +----+---------+
      | Id | Email   |
      +----+---------+
      | 1  | a@b.com |
      | 2  | c@d.com |
      | 3  | a@b.com |
      +----+---------+

      编写一个 SQL 查询，查找 Email 表中所有重复的电子邮箱。
      根据以上输入，你的查询应返回以下结果：
      +---------+
      | Email   |
      +---------+
      | a@b.com |
      +---------+
      说明：所有电子邮箱都是小写字母。

- 项目二：查找大国（难度：简单）

      创建如下 World 表
      +-----------------+------------+------------+--------------+---------------+
      | name            | continent  | area       | population   | gdp           |
      +-----------------+------------+------------+--------------+---------------+
      | Afghanistan     | Asia       | 652230     | 25500100     | 20343000      |
      | Albania         | Europe     | 28748      | 2831741      | 12960000      |
      | Algeria         | Africa     | 2381741    | 37100000     | 188681000     |
      | Andorra         | Europe     | 468        | 78115        | 3712000       |
      | Angola          | Africa     | 1246700    | 20609294     | 100990000     |
      +-----------------+------------+------------+--------------+---------------+
      如果一个国家的面积超过300万平方公里，或者(人口超过2500万并且gdp超过2000万)，那么这个国家就是大国家。
      编写一个SQL查询，输出表中所有大国家的名称、人口和面积。
      例如，根据上表，我们应该输出:
      +--------------+-------------+--------------+
      | name         | population  | area         |
      +--------------+-------------+--------------+
      | Afghanistan  | 25500100    | 652230       |
      | Algeria      | 37100000    | 2381741      |
      +--------------+-------------+--------------+

#### 彩蛋

考虑到本次集训有很多新手，本次作业赠送建表代码，意不意外，开不开心。
直接将附件code内容复制到cmd或者navicat运行就行。

项目一

-- 创建表

      CREATE TABLE email (
      ID INT NOT NULL PRIMARY KEY,
      Email VARCHAR(255)
      );

-- 插入数据

      INSERT INTO email VALUES('1','a@b.com');
      INSERT INTO email VALUES('2','c@d.com');
      INSERT INTO email VALUES('3','a@b.com');

项目二

-- 创建表

      CREATE TABLE World (
      name VARCHAR(50) NOT NULL,
      continent VARCHAR(50) NOT NULL,
      area INT NOT NULL,
      population INT NOT NULL,
      gdp INT NOT NULL
      );

-- 插入数据

      INSERT INTO World
      VALUES('Afghanistan','Asia',652230,25500100,20343000);
      INSERT INTO World 
      VALUES('Albania','Europe',28748,2831741,12960000);
      INSERT INTO World 
      VALUES('Algeria','Africa',2381741,37100000,188681000);
      INSERT INTO World
      VALUES('Andorra','Europe',468,78115,3712000);
      INSERT INTO World
      VALUES('Angola','Africa',1246700,20609294,100990000);
      
------

# Day 3

## 第三次任务发布

任务3打卡链接：https://shimo.im/docs/Gz4khXKEc1YQevKJ/ 《MySQL任务3打卡-1群》

上次任务作业参考答案：https://shimo.im/docs/JzxO54I1by8yPx4p/ 

请于4月4日22:00前完成，在打卡表格处打卡。逾期尚未打卡的会被清退。
本次作业以及之后的都需要小伙伴自己创建表和插入数据啦。就当表操作的练习。请注意语句规范，可参考上次作业的参考答案。
表联结是SQL语句核心部分。因为在正式业务中必然会涉及到多表之间的数据调用。所以大家务必完全理解吃透这部分的内容。
祝大家学习开心。:-)

## 任务三内容

### MySQL 基础 （二）- 表操作

#### 学习

1. MySQL表数据类型
 
2. 用SQL语句创建表
    语句解释
    设定列类型 、大小、约束
    设定主键

3. 用SQL语句向表中添加数据
    语句解释
    多种添加方式（指定列名；不指定列名）

4. 用SQL语句删除表
    语句解释
    DELETE
    DROP
    TRUNCATE
    不同方式的区别

5. 用SQL语句修改表
    修改列名
    修改表中数据
    删除行
    删除列
    新建列
    新建行

#### 作业

- 项目三：超过5名学生的课（难度：简单）

      创建如下所示的courses 表 ，有: student (学生) 和 class (课程)。
      例如,表:
      +---------+------------+
      | student | class      |
      +---------+------------+
      | A       | Math       |
      | B       | English    |
      | C       | Math       |
      | D       | Biology    |
      | E       | Math       |
      | F       | Computer   |
      | G       | Math       |
      | H       | Math       |
      | I       | Math       |
      | A      | Math       |
      +---------+------------+

      编写一个 SQL 查询，列出所有超过或等于5名学生的课。
      应该输出:
      +---------+
      | class   |
      +---------+
      | Math    |
      +---------+
      Note:
      学生在每个课中不应被重复计算。

- 项目四：交换工资（难度：简单）

      创建一个 salary表，如下所示，有m=男性 和 f=女性的值 。
      例如:
      | id | name | sex | salary |
      |----|------|-----|--------|
      | 1  | A    | m   | 2500   |
      | 2  | B    | f   | 1500   |
      | 3  | C    | m   | 5500   |
      | 4  | D    | f   | 500    |

      交换所有的 f 和 m 值(例如，将所有 f 值更改为 m，反之亦然)。要求使用一个更新查询，并且没有中间临时表。
      运行你所编写的查询语句之后，将会得到以下表:
      | id | name | sex | salary |
      |----|------|-----|--------|
      | 1  | A    | f  | 2500   |
      | 2  | B    | m   | 1500   |
      | 3  | C    | f   | 5500   |
      | 4  | D    | m   | 500    |

### MySQL 基础 （三）- 表联结

#### 学习

1. MySQL别名

2. INNER JOIN

3. LEFT JOIN

4. CROSS JOIN

5. 自连接

6. UNION

7. 以上几种方式的区别和联系