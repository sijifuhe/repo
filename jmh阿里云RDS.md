# 阿里云-RDS

## 一、简介

RDS（Relational Database Service）是阿里云提供的一种稳定可靠、可弹性伸缩的在线数据库服务。它支持多种数据库引擎，包括 MySQL、SQL Server、PostgreSQL 和 MariaDB，并提供了容灾、备份、恢复、监控、迁移等全套解决方案，帮助用户解决数据库运维的烦恼。

RDS 默认部署主备架构，具备高可用性和安全性，支持自动备份、跨可用区容灾等功能。通过 RDS，用户可以快速创建和管理数据库实例，而无需关注底层硬件和软件的维护

## 二、部署

**部署环境**

| 本地虚拟机，部署mysql | 192.168.100.100 |
| --------------------- | --------------- |
| 阿里云                |                 |

![     ](https://raw.githubusercontent.com/sijifuhe/repo/main/jmh20250922085504240.png)

![image-20250920160430338](https://raw.githubusercontent.com/sijifuhe/repo/main/jmh20250922085525996.png)

![image-20250920160629848](https://raw.githubusercontent.com/sijifuhe/repo/main/jmh20250922085541120.png)

![image-20250920160959717](https://raw.githubusercontent.com/sijifuhe/repo/main/jmh20250922085549140.png)

**授权**

在 **RDS控制台** → **白名单** 中，添加你本地虚拟机或ECS的IP，否则无法远程访问 。

RDS Mysql开通公网

![image-20250920162203314](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920162203314.png)

![image-20250920162239682](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920162239682.png)

![image-20250920162257083](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920162257083.png)

**可以不开外网**

**查看实例公网IP**60.205.248.97

![image-20250920162614732](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920162614732.png)

**将获取的公网IP加入白名单**

![image-20250920162708078](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920162708078.png)

![image-20250920162832723](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920162832723.png)

![image-20250920162922177](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920162922177.png)

**复制外网IPrm-2zedev05s5en3vb26eo.mysql.rds.aliyuncs.com**

```bash
#在ECS实例访问测试
[root@iZ2zeij7fwnkiohbj5ijykZ ~]# yum -y install mysql
[root@iZ2zeij7fwnkiohbj5ijykZ ~]# mysql -h rm-2zedev05s5en3vb26eo.mysql.rds.aliyuncs.com -u jmh_rds -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 642
Server version: 8.0.36 Source distribution

Copyright (c) 2000, 2025, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> quit
Bye
```

**本地安装MySQL并插入数据**

```bash
root@jmh-mysql tmp]# wget https://dev.mysql.com/get/mysql80-community-release-el8-7.noarch.rpm
root@jmh-mysql tmp]# rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2023
root@jmh-mysql tmp]# rpm -Uvh mysql80-community-release-el8-7.noarch.rpm
root@jmh-mysql tmp]# dnf module disable mysql -y
root@jmh-mysql tmp]# dnf install mysql-community-server -y
[root@jmh-mysql tmp]# sudo grep 'temporary password' /var/log/mysqld.log
2025-09-20T08:47:25.844425Z 6 [Note] [MY-010454] [Server] A temporary password is generated for root@localhost: 1gttaLhsA%O_

root@jmh-mysql tmp]# mysql -uroot -p1gttaLhsA%O_
root@jmh-mysql tmp]# mysql_secure_installation  #交互式修改密码
[root@jmh-mysql tmp]# mysql -uroot -pJMHjmh123.
mysql: [Warning] Using a password on the command line interface 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 22
Server version: 8.0.43 MySQL Community Server - GPL

Copyright (c) 2000, 2025, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or it
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current in

mysql> CREATE DATABASE hansir;
Query OK, 1 row affected (0.00 sec)

mysql> use hansir
Database changed
mysql> CREATE TABLE IF NOT EXISTS user (id          BIGINT AUTO_INCREMENT PRIMARY KEY,username    VARCHAR(50)  NOT NULL UNIQUE,age         TINYINT      CHECK (age BETWEEN 0 AND 150)) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='用户表';
Query OK, 0 rows affected (0.03 sec)

mysql> INSERT INTO user (username, age) VALUES ('wx', 30),('jmh', 28);
Query OK, 2 rows affected (0.02 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM user;
+----+----------+------+
| id | username | age  |
+----+----------+------+
|  1 | wx       |   30 |
|  2 | jmh      |   28 |
+----+----------+------+
2 rows in set (0.00 sec)


```

**数据备份**

```bash
[root@jmh-mysql tmp]# mysqldump -u root -p hansir > /opt/hansir.sql
Enter password: 
[root@jmh-mysql opt]# ls
hansir.sql
[root@jmh-mysql opt]# sz hansir.sql 
[root@jmh-mysql opt]# 

```

![image-20250920170046899](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170046899.png)

**导入到RDS**

![image-20250920170152218](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170152218.png)

![image-20250920170229484](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170229484.png)

![image-20250920170421144](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170421144.png)

![image-20250920170522492](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170522492.png)

![image-20250920170606371](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170606371.png)

![image-20250920170628391](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170628391.png)

![image-20250920170720991](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170720991.png)

![image-20250920170736564](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170736564.png)

![image-20250920170802171](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170802171.png)

![image-20250920170824174](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170824174.png)

![image-20250920170844934](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170844934.png)

**验证**

![image-20250920170957772](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920170957772.png)

**设置备份**

![image-20250920171244926](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920171244926.png)

![image-20250920171317045](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920171317045.png)

![image-20250920171421502](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920171421502.png)

![image-20250920171430636](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920171430636.png)

![image-20250920171456393](D:/%E6%A1%8C%E9%9D%A2/RDS/image-20250920171456393.png)

设置全量备份策略（基础备份）

1. **登录阿里云 RDS 控制台**
   进入「云数据库 RDS」→ 选择目标实例 → 左侧菜单「备份恢复」→「备份设置」。
2. **配置全量备份参数**
   在「自动备份设置」中，可设置以下关键参数：
   - **备份周期**：选择每周哪几天执行全量备份（如周一、周四）。
   - **备份时间**：设置全量备份的执行时间段（如凌晨 2:00-4:00，避开业务高峰期）。
   - **备份保留时长**：全量备份文件的保存天数（默认 7 天，最大可设置 35 天，如需更长时间可配置跨区域备份）。
3. **开启自动备份**
   确保「自动备份」开关处于开启状态，设置完成后点击「确定」，系统会按周期自动执行全量备份。

三、增量备份的自动配置（无需手动设置）

阿里云 RDS 的增量备份是**自动开启**的，无需额外配置，原理如下：



- 基于数据库的事务日志（如 MySQL 的 binlog、SQL Server 的事务日志），实时记录数据变化。
- 每次全量备份后，系统会自动从全量备份的终点开始记录增量日志。
- 增量备份文件会与全量备份关联，用于「按时间点恢复」（精确到秒）。

**什么是DMS**

DMS 即 Data Management Service，是阿里云一款支撑数据全生命周期的一站式数据管理平台。以下是对它的简单介绍：



- **支持多种数据库类型**：涵盖关系型数据库，如 MySQL、SQL Server、PostgreSQL 等；NoSQL 数据库，如 Redis、MongoDB 等；OLAP 数据库，如 AnalyticDB for MySQL、AnalyticDB for PostgreSQL 等。
- **全域数据资产管理**：可进行数据库实例信息的查看、录入、编辑等操作，还能对实例、库、表等进行授权、回收权限等管理，同时支持数据分类管理，方便不同人员更好地管理和使用数据，也可通过全局搜索快速查找数据。
- **可靠的数据安全治理**：内置多种设计及审核规范，支持实例、库、表、数据列、数据行级权限管理，提供域账号及权限的全自动化管理，还支持企业上市合规审计、常规内审等功能，全面覆盖多种法律法规，实现敏感数据的自动分类分级。
- **保障数据库稳定性**：通过无锁变更、变更前备份及变更异常自动回滚等策略保障变更过程中数据库稳定可控，还能进行数据质量监测与校验，结合安全规则对上传的 SQL 语句进行审核并提供优化建议，整合数据库自治服务 DAS 的部分功能，掌握数据库实例的性能状况。
- **高效研发数据库**：支持多引擎统一开发，可自定义研发流程，研发人员全自助即可完成合规的数据库开发，非生产环境可做到免审批，仅生产环境需要审核，还提供库级别的数据复制能力，支持批量生成测试数据，以及 SQL 复用等功能。
- **数据开发与分析功能丰富**：提供 SQL 窗口，可便捷执行各类 SQL 语句，支持可视化操作。任务编排可进行周期或事件调度执行，提高数据开发效率。逻辑数仓能将异构数据源进行逻辑聚合。Data Copilot 是基于阿里云大模型构建的数据智能助手，可帮助用户更高效、规范地使用和管理数据。此外，还提供典型的数据集、仪表盘和大屏模型，方便直观呈现业务数据。
- **实时数据传输**：基于 DTS 的实时数据传输，提供数据迁移、数据同步、数据订阅功能，支持分布式集成架构，突破单机瓶颈，通过性能监控、一键诊断等策略，实现极低运维门槛，还可按需配置调度，调度周期低至 5 分钟。