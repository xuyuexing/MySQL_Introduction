# Day2

[TOC]

# 一、导入示例数据库

- 这里是[导入教程](https://www.yiibai.com/mysql/how-to-load-sample-database-into-mysql-database-server.html)。

- 可能的错误：[Navicat for Mysql 报错 1251-连接不成功](https://blog.csdn.net/wshxhghsjjsn/article/details/80459542)。

# 二、MySQL 基础 （一）- 查询语句

### 2.1 SQL与MySQL介绍

### 2.2 SQL基础查询语句

- 注释



- 查询语句（SELECT FROM）



- 筛选语句（WHERE）



- 分组语句（GROUP BY）



- 排序语句（ORDER BY）



- 函数



- 代码规范
    - [SQL编程格式的优化建议](https://zhuanlan.zhihu.com/p/27466166)
    - [SQL Style Guide](https://www.sqlstyle.guide/)

# 三、作业

### 项目一：查找重复的电子邮箱（难度：简单）

- 题目：

        创建 email表，并插入如下三行数据
        +----+---------+
        | Id | Email   |
        +----+---------+
        | 1  | a@b.com |
        | 2  | c@d.com |
        | 3  | a@b.com |
        +----+---------
        编写一个 SQL 查询，查找 Email 表中所有重复的电子邮箱。
        根据以上输入，你的查询应返回以下结果：
        +---------+
        | Email   |
        +---------+
        | a@b.com |
        +---------+
        说明：所有电子邮箱都是小写字母。

- 解题：

    创建表：

    ```sql
    CREATE TABLE email (
        ID INT NOT NULL PRIMARY KEY,
        Email VARCHAR (255)
    );
    ```

    插入数据：


    查找：



### 项目二：查找大国（难度：简单）

- 题目：

        创建如下 World 表
        +-----------------+------------+------------+------------   +---------------+
        | name            | continent  | area       | population    gdp           |
        +-----------------+------------+------------+------------   +---------------+
        | Afghanistan     | Asia       | 652230     | 25500100      20343000      |
        | Albania         | Europe     | 28748      | 2831741       12960000      |
        | Algeria         | Africa     | 2381741    | 37100000      188681000     |
        | Andorra         | Europe     | 468        | 78115         3712000       |
        | Angola          | Africa     | 1246700    | 20609294      100990000     |
        +-----------------+------------+------------+------------   +---------------+
        如果一个国家的面积超过300万平方公里，或者(人口超过2500万并且gd  过2000万)，那么这个国家就是大国家。
        编写一个SQL查询，输出表中所有大国家的名称、人口和面积。
        例如，根据上表，我们应该输出:
        +--------------+-------------+--------------+
        | name         | population  | area         |
        +--------------+-------------+--------------+
        | Afghanistan  | 25500100    | 652230       |
        | Algeria      | 37100000    | 2381741      |
        +--------------+-------------+--------------+

- 解题：
