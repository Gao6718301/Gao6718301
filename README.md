/* Windows服务 */
--启动MySql
    net start mysql
--创建Windows服务
    sc create mysql binPath= mysqld_bin_path

/*连接与断开服务器*/
musql -h 地址 -P 端口 -u 用户名 -p 密码

SHOW PROCESSLIST -- 显示哪些线程正在运行
SHOW VARIABLES -- 显示系统变量信息

/* 数据库操作 */ -------------------
-- 查看当前数据库
    SELECT DATABASE();
-- 显示当前时间、用户名、数据库版本
    SELECT now(), user(), version();
-- 创建库
    CREATE DATABASE 【 IF NOT EXISTS】 数据库名 数据库选项
    数据库选项：
        CHARACTER SET charset_name
        COLLATE collation_name
-- 查看已有库
    SHOW DATABASES【 LIKE 'PATTERN'】
-- 查看当前库信息
    SHOW CREATE DATABASE 数据库名
-- 修改库的选项信息
    ALTER DATABASE 库名 选项信息
-- 删除库
    DROP DATABASE【IF EXISTS】 数据库名
        同时删除该数据库相关的目录及其目录内容
        
/* 表的操作 */ -------------------
-- 创建表
    CREATE 【TEMPORARY】 TABLE【 IF NOT EXISTS】
        每个字段必须有数据类型
        最后一个字段后不能有逗号
        TEMPORARY 临时表，会话结束时表自动消失
        对于字段的定义：
            字段名 数据类型【NOT NULL | NULL】 【DEFAULT default_value】 【AUTO_INCREMENT】 【UNIQUE 【KEY】 | 【PRINARY】 KEY 】【COMMENT 'string'】
-- 表选项
    -- 字符集
        CHARSET = charset_name
        如果表没有设定，则使用数据库字符集
    -- 存储引擎
        ENGINE = engine_name
        表在管理数据时采用的不同的数据结构，结构不同会导致处理方式，提供的特性操作等不同
        常见的引擎：InnoDB MyISAM Memory/Heap BDB Merge Example CSV MaxDB Archive
        不同的引擎在保存表的结构和数据时采用不同的方式
        MyISAM表文件含义：.frm表定义, .MYD表数据, .MYI表索引
        InnoDB表文件含义：.frn表定义, 表空间数据和日志文件
        SHOW ENGINES --显示存储引擎的状态信息
        SHOW ENGINE 引擎名 {LOGS|STATUS} -- 显示存储引擎的日志或状态信息
    -- 自增起始数
        AUTO_INCREMENT = 行数
    -- 数据文件目录
        DATA DIRECTORY = '目录'
    -- 表注释
        COMMENT = 'string'
    -- 分区选项
        PARTITION BY ...
-- 查看所有表
    SHOW TABLES【 LIKE 'pattren'】
    SHOW TABLES FROM 表名
-- 查看表机构
    SHOW CREATE TABLE 表名 （信息更详细）
    DESC 表名 / DESCRIBE 表名 / EXPLAIN 表名 / SHOW COLUMNS FROM 表名 【LIKE 'PATTERN'】
    SHOW TABLE STATUS 【FRON db_name】【LIKE 'pattern'】
-- 修改表
    -- 修改表本身的选项
        ALTER TABLE 表名 表的选项
        eg：ALTER TABLE 表名 ENGINE=MYISAM;
    -- 对表进行重命名
        RENAME TABLE 原表名 TO 新表名
        RENAME TABLE 原表名 TO 库名。表名 （可将表移动到另一个数据库）
        -- RENAME可以交换两个表名
    -- 修改表的字段机构（13。1.2. ALTER TABLE语法）
        ALTER TABLE 表名 操作名
        -- 操作名
            ADD【 COLUMN】字段定义        -- 增加字段
                AFTER 字段名             -- 表示增加在该字段名后面
                FIRST                   -- 表示增加在第一个
            ADD PRIMARY KEY(字段名)     -- 创建主键
            ADD UNIQUE 【索引名】(字段名)-- 创建唯一索引
            ADD INDEX 【索引名】(字段名) -- 创建普通索引
            DROP【 COLUMN】字段名        -- 删除字段
            
            
        
        
        
