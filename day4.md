### 项目七: 各部门工资最高的员工（难度：中等）

创建Employee 表，包含所有员工信息，每个员工有其对应的 Id, salary 和 department Id。

+----+-------+--------+--------------+
| Id | Name | Salary | DepartmentId |
+----+-------+--------+--------------+
| 1 | Joe | 70000 | 1 |
| 2 | Henry | 80000 | 2 |
| 3 | Sam | 60000 | 2 |
| 4 | Max | 90000 | 1 |
+----+-------+--------+--------------+

创建Department 表，包含公司所有部门的信息。
+----+----------+
| Id | Name |
+----+----------+
| 1 | IT |
| 2 | Sales |
+----+----------+
编写一个 SQL 查询，找出每个部门工资最高的员工。例如，根据上述给定的表格，Max 在 IT 部门有最高工资，Henry 在 Sales 部门有最高工资。
+------------+----------+--------+
| Department | Employee | Salary |
+------------+----------+--------+
| IT | Max | 90000 |
| Sales | Henry | 80000 |
+------------+----------+--------+

- 解题：

-- 建表

```sql
CREATE TABLE IF NOT EXISTS Employee (
	Id SMALLINT PRIMARY KEY AUTO_INCREMENT,
	Name VARCHAR(20) NOT NULL,
	Salary INT NOT NULL,
	DepartmentId TINYINT NOT NULL
)
;

CREATE TABLE IF NOT EXISTS Department (
	Id SMALLINT PRIMARY KEY AUTO_INCREMENT,
	Name VARCHAR(20) NOT NULL
)
;
```

-- 插入数据

```sql
INSERT Employee(Name,Salary,DepartmentId)
Values('Joe',70000,1),
			('Henry',80000,2),
			('Sam',60000,2),
			('Max',90000,1)
;

INSERT Department(Name)
Values('IT'),
			('Sales')
;
```

-- chaxun

```sql
SELECT d.Name as Department, e.Name as Employee, e.Salary
FROM Employee e, Department d
WHERE e.DepartmentId = d.Id 
and e.Salary = (
	SELECT MAX(Employee.Salary)
	FROM Employee
	WHERE Employee.DepartmentId = d.Id
	)
;	
```

------

### 项目八: 换座位（难度：中等）

小美是一所中学的信息科技老师，她有一张 seat 座位表，平时用来储存学生名字和与他们相对应的座位 id。
其中纵列的 id 是连续递增的
小美想改变相邻俩学生的座位。
你能不能帮她写一个 SQL query 来输出小美想要的结果呢？
 请创建如下所示seat表：
示例：
+---------+---------+
| id | student |
+---------+---------+
| 1 | Abbot |
| 2 | Doris |
| 3 | Emerson |
| 4 | Green |
| 5 | Jeames |
+---------+---------+
假如数据输入的是上表，则输出结果如下：
+---------+---------+
| id | student |
+---------+---------+
| 1 | Doris |
| 2 | Abbot |
| 3 | Green |
| 4 | Emerson |
| 5 | Jeames |
+---------+---------+
注意：
如果学生人数是奇数，则不需要改变最后一个同学的座位。

- 解题：

-- 建表

```sql
CREATE TABLE IF NOT EXISTS seat (
  id int(10) NOT NULL AUTO_INCREMENT,
  student varchar(20) NOT NULL,
  PRIMARY KEY (id)
)
;
```

-- 插入数据

```sql
INSERT INTO seat student
VALUES
	( 'Abbot' ),
	( 'Doris' ),
	( 'Emerson' ),
	( 'Green' ),
	( 'Jeames' )
;
```

-- 查询

```sql
SELECT
	(
CASE
	
	WHEN MOD ( id, 2 ) = 1 
	AND id != maxid THEN
		id + 1 
		WHEN MOD ( id, 2 ) = 1 
		AND id = maxid THEN
			id ELSE id - 1 
		END 
		) AS id,
		student 
	FROM
		seat,
		( SELECT max( id ) AS maxid FROM seat ) AS TEMP 
ORDER BY id
;
```

------

### 项目九: 分数排名（难度：中等）
编写一个 SQL 查询来实现分数排名。如果两个分数相同，则两个分数排名（Rank）相同。请注意，平分后的下一个名次应该是下一个连续的整数值。换句话说，名次之间不应该有“间隔”。
创建以下score表：
+----+-------+
| Id | Score |
+----+-------+
| 1 | 3.50 |
| 2 | 3.65 |
| 3 | 4.00 |
| 4 | 3.85 |
| 5 | 4.00 |
| 6 | 3.65 |
+----+-------+
例如，根据上述给定的 Scores 表，你的查询应该返回（按分数从高到低排列）：
+-------+------+
| Score | Rank |
+-------+------+
| 4.00 | 1 |
| 4.00 | 1 |
| 3.85 | 2 |
| 3.65 | 3 |
| 3.65 | 3 |
| 3.50 | 4 |
+-------+------+

- 解题：


-- 建表

```sql
CREATE TABLE IF NOT EXISTS score (
	Id TINYINT PRIMARY KEY AUTO_INCREMENT,
	Score FLOAT(5,2) NOT NULL
)
;
```

-- 插入shuju

```sql
INSERT INTO score Score
VALUES('4.00'),
			('3.85'),
			('3.65'),
			('3.65'),
			('3.65'),
			('3.50')
;
```

-- 查询

```sql
SELECT Score,
			(SELECT COUNT(DISTINCT Score)
				FROM score AS s2 
				WHERE s2.Score>=s1.Score
			) 
FROM score AS s1
ORDER BY Score DESC
; 
```

------

### 项目十：行程和用户（难度：困难）
Trips 表中存所有出租车的行程信息。每段行程有唯一键 Id，Client_Id 和 Driver_Id 是 Users 表中 Users_Id 的外键。Status 是枚举类型，枚举成员为 (‘completed’, ‘cancelled_by_driver’, ‘cancelled_by_client’)。
+----+-----------+-----------+---------+--------------------+----------+
| Id | Client_Id | Driver_Id | City_Id | Status |Request_at|
+----+-----------+-----------+---------+--------------------+----------+
| 1 | 1 | 10 | 1 | completed |2013-10-01|
| 2 | 2 | 11 | 1 | cancelled_by_driver|2013-10-01|
| 3 | 3 | 12 | 6 | completed |2013-10-01|
| 4 | 4 | 13 | 6 | cancelled_by_client|2013-10-01|
| 5 | 1 | 10 | 1 | completed |2013-10-02|
| 6 | 2 | 11 | 6 | completed |2013-10-02|
| 7 | 3 | 12 | 6 | completed |2013-10-02|
| 8 | 2 | 12 | 12 | completed |2013-10-03|
| 9 | 3 | 10 | 12 | completed |2013-10-03|
| 10 | 4 | 13 | 12 | cancelled_by_driver|2013-10-03|
+----+-----------+-----------+---------+--------------------+----------+
Users 表存所有用户。每个用户有唯一键 Users_Id。Banned 表示这个用户是否被禁止，Role 则是一个表示（‘client’, ‘driver’, ‘partner’）的枚举类型。
+----------+--------+--------+
| Users_Id | Banned | Role |
+----------+--------+--------+
| 1 | No | client |
| 2 | Yes | client |
| 3 | No | client |
| 4 | No | client |
| 10 | No | driver |
| 11 | No | driver |
| 12 | No | driver |
| 13 | No | driver |
+----------+--------+--------+
写一段 SQL 语句查出 2013年10月1日 至 2013年10月3日 期间非禁止用户的取消率。基于上表，你的 SQL 语句应返回如下结果，取消率（Cancellation Rate）保留两位小数。
+------------+-------------------+
| Day | Cancellation Rate |
+------------+-------------------+
| 2013-10-01 | 0.33 |
| 2013-10-02 | 0.00 |
| 2013-10-03 | 0.50 |
+------------+-------------------+

- 解题：

尚需考虑

------

### 项目十一：各部门前3高工资的员工（难度：中等）
将项目7中的employee表清空，重新插入以下数据（其实是多插入5,6两行）：
+----+-------+--------+--------------+
| Id | Name | Salary | DepartmentId |
+----+-------+--------+--------------+
| 1 | Joe | 70000 | 1 |
| 2 | Henry | 80000 | 2 |
| 3 | Sam | 60000 | 2 |
| 4 | Max | 90000 | 1 |
| 5 | Janet | 69000 | 1 |
| 6 | Randy | 85000 | 1 |
+----+-------+--------+--------------+
编写一个 SQL 查询，找出每个部门工资前三高的员工。例如，根据上述给定的表格，查询结果应返回：
+------------+----------+--------+
| Department | Employee | Salary |
+------------+----------+--------+
| IT | Max | 90000 |
| IT | Randy | 85000 |
| IT | Joe | 70000 |
| Sales | Henry | 80000 |
| Sales | Sam | 60000 |
+------------+----------+--------+

- 解题：

--插入数据

```sql
INSERT INTO Employee(Id,Name,Salary,DepartmentId)
VALUES(5,"Janet",69000,1);
INSERT INTO Employee(Id,Name,Salary,DepartmentId)
VALUES(6,"Randy",85000,1);
```

--查询

```sql
SELECT Department.Name AS Department, e1.Name AS Employee, e1.Salary AS Salary
FROM Employee e1
JOIN Department ON e1.DepartmentId = Department.Id
WHERE 3 >   (
            SELECT COUNT(DISTINCT e2.Salary) 
            FROM Employee e2
            WHERE e2.Salary > e1.Salary AND e1.DepartmentId = e2.DepartmentId
            )
ORDER BY Department.Name, e1.Salary DESC;
```

------

### 项目十二 分数排名 - （难度：中等）
依然是昨天的分数表，实现排名功能，但是排名是非连续的，如下：
+-------+------+
| Score | Rank |
+-------+------+
| 4.00 | 1 |
| 4.00 | 1 |
| 3.85 | 3 |
| 3.65 | 4 |
| 3.65 | 4 |
| 3.50 | 6 |
+-------+------

- 解题：

```sql
-- 查询（直接把DISTINCT去掉即可）
SELECT Score,
			(SELECT COUNT(Score)
				FROM score AS s2 
				WHERE s2.Score>=s1.Score
			) 
FROM score AS s1
ORDER BY Score DESC
; 
```

------
