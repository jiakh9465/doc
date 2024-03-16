参考文档
https://www.docs4dev.com/docs/zh/mysql/5.7/reference/fulltext-stopwords.html
mysql有自己的停用词，导致一些拼音无法检索
创建自己的停用词表
```
CREATE TABLE t_custom_stopwords (value VARCHAR(255)) ENGINE=InnoDB;
```
使用自己的停用词表
```
SET GLOBAL innodb_ft_server_stopword_table = 'db/t_custom_stopwords';
```
修改分词大小
```
[mysqld]
innodb_ft_min_token_size=2
```
重启mysql服务
重新创建索引，就可以了
