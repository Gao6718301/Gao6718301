/* Windows服务 */
--启动MySql
    net start mysql
--创建Windows服务
    sc create mysql binPath= mysqld_bin_path

/*连接与断开服务器*/
musql -h 地址 -P 端口 -u 用户名 -p 密码

SHOW PROCESSLIST -- 显示哪些线程正在运行
SHOW VARIABLES -- 显示系统变量信息

------/* 数据库操作 */ -------
-- 查看当前数据库
    SELECT DATABASE();
-- 显示当前时间、用户名、数据库版本
    SELECT now(), user(), version();
-- 创建库
    CREATE DATABASE [ IF NOT EXISTS] 数据库名 数据库选项
    数据库选项：
        CHARACTER SET charset_name
        COLLATE collation_name
-- 
