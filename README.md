/* Windows服务 */
--启动MySql
    net start mysql
--创建Windows服务
    sc create mysql binPath= mysqld_bin_path

/*连接与断开服务器*/
musql -h 地址 -P 端口 -u 用户名 -p 密码

SHOW PROCESSLIST -- 显示哪些线程正在运行
SHOW VARIABLES -- 显示系统变量信息
