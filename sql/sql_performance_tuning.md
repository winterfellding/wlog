### 慢查之日设置

    show variables like 'slow_query_log'; --查询慢查日志是否打开
    set global slow_query_log_file=‘/var/lib/mysql/mysql-slow.log’;
    set global log_queries_not_using_indexes=on;
    set global long_query_time=0.1;       --设置超过0.1s的sql记录下来
    
    long_query_time因为是session variable，有的时候不能覆盖，可以使用
    set @@GLOBAL.long_query_time = 0.1;
    show global variables like 'long_query_time';
    show variables like 'long_query_time';
    
### 打开日志后，记录一段时间后可使用工具查看

    比如mysqldumpslow，或者三方工具pt-query-digest
    mysqldumpslow是mysql安装自带的，pt-query-digest是percona tool里带的
    pt-query-digest /var/lib/mysql/mysql-slow.log
    之后就能看到频率高查询慢的sql，
    处理where xxx = 'aaa'和order by语句时，我们可以使用创建对应列的索引处理
    explain sql_query 可以查到sql查询信息
    
    explain
    table: 哪张表
    type: 重要列，显示连接使用了何种类型。最好到最差排序为: const, eq_reg, ref, range, index和ALL
    possible_keys: 现实可能应用在这张表中的索引，如果为空，没有可能的索引
    key: 实际使用的索引。如果为NULL，则没有使用索引
    key_len: 使用索引的长度。在不损失精确性的情况下，长度越短越好
    ref: 显示索引的哪一列被使用了，如果可能的话，是一个常数
    rows: mysql认为必须检查的用来返回请求数据的行数
    
    建立联合索引时，要把离散程度高的放到前面
    
### percona-toolkit中索引的一些工具

    pt-duplicated-key-checker 重复索引检测工具
    pt-index-usage -uroot -p mysql-slow.log 索引使用情况
    
### mysql数据库的一些重要优化参数
    
    -- 可以使用http://tools.percona.com/wizard配置

    innodb_buffer_pool_size  总内存的75%
    innodb_buffer_pool_instances 
    innodb_log_buffer_size
    innodb_flush_log_at_trx_commit IO性能高的2，安全性是1 *
    innodb_read_io_threads
    innodb_write_io_threads
    innodb_file_per_table * 
    innodb_stats_on_metadata
    