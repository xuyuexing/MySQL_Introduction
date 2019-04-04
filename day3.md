# Day3

[TOC]

# 一、MySQL 基础 （二）- 表操作

### 2.1 SQL与MySQL介绍

### 2.2 SQL基础查询语句

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

# 二、MySQL 基础 （三）- 表联结

1. MySQL别名

2. INNER JOIN

3. LEFT JOIN

4. CROSS JOIN

5. 自连接

6. UNION

7. 以上几种方式的区别和联系

# 三、作业

### 项目三：超过5名学生的课（难度：简单）

- 题目：

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

- 解题：

    指定数据库（沿用项目一中的test）：

    ```sql
    USE test;
    ```

    创建表：

    ```sql
    CREATE TABLE courses (
    student VARCHAR (50) NOT NULL,
    class VARCHAR (50) NOT NULL
    );
    ```

    插入数据：

    ```sql
    INSERT INTO courses VALUES('A','Math');
    INSERT INTO courses VALUES('B','English');  
    INSERT INTO courses VALUES('C','Math');
    INSERT INTO courses VALUES('D','Biology');
    INSERT INTO courses VALUES('E','Math');
    INSERT INTO courses VALUES('F','Computer');
    INSERT INTO courses VALUES('G','Math');
    INSERT INTO courses VALUES('H','Math');
    INSERT INTO courses VALUES('I','Math');
    INSERT INTO courses VALUES('A','Math');
    ```

    查找>=5行的课程：

    ```sql
    SELECT t.class
    FROM
    (
    SELECT DISTINCT student, class
    FROM courses
    ) AS t     -- 确保同一个课程，没有重复的学生
    GROUP BY class
    HAVING count(class) >= 5
    ;
    ```

### 项目四：交换工资（难度：简单）

- 题目：

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

- 解题：

    指定数据库（沿用项目一中的test）：

    ```sql
    USE test;
    ```

    创建表：

    ```sql
    CREATE TABLE salary (
    id INT NOT NULL PRIMARY KEY,
    name VARCHAR (50) NOT NULL,
    sex VARCHAR (50) NOT NULL,
    salary INT NOT NULL
    );
    ```

    插入数据：

    ```sql
    INSERT INTO salary VALUES(1,'A','m',2500);
    INSERT INTO salary VALUES(2,'B','f',1500);
    INSERT INTO salary VALUES(3,'C','m',5500);
    INSERT INTO salary VALUES(4,'D','f',500);
    ```

    交换所有的f和m的值：

    ```sql
    UPDATE salary SET sex= (CASE WHEN sex = 'm' THEN 'f' ELSE 'm' END);
    SELECT * FROM salary;
    ```