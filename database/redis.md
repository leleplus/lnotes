# Redis数据库

非关系型数据库
完全开源免费高性能的key-value非关系型数据库

查看所有的配置`config get *`
设置输出的日志级别`config set loglevel [debug]`
查看当前的日志级别`config get loglevel`
查看与服务器的连接是否成功`ping`返回`PONG`

切换数据库`select index`
切换超时时间`config set timeout [s]`

在文件redis.windows.conf中设置一些配置

迭代数据数据库`scan index`

设置密码`config set requirepass`
设置客户端最大的连接数`config set maxclents`

存hash
`hset person age 18`
`hmset person name zhangsan age 18 sex w`
`hkeys person`
`hget person name`
`hmget person name age sex`
`hgetall person`

list 集合
入`lpush list s1 s2 s3`
出 `lpop list`
`lrange list 0 10`


`rpush list s1 s2 s3`

set集合
`sadd set s1 abc s2 cc`
遍历所有的值`smembers set`
`sscan set 0`

zset集合
`zadd zset 0 s1 4 s2 1 s3 3 s4 2 s5`
`zrange zset 0 9`


模糊查找key `keys **`


截取操作(闭区间)`getrange name 0 4`






