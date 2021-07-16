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
        SHOW ENGINE 引擎名 {LOGS|STATUS} -- 显示存储引擎的日志
        
        
