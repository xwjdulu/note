MySQL 事务的四大特性
原子性:逻辑操作过程具有原子性，不会出现有的逻辑操作成功，有的逻辑操作失败这种情况
要么全部成功，要么全部失败
一致性:张三给李四转账 100 元，那么张三的余额应减少 100 元，李四的余额应增加 100 元，张三的余额减少和李四的余额增加这是两个逻辑操作具有一致性
隔离性:个事务内部的操作及使用的数据，对并发的其他事务是隔离的，并发执行的各个事务之间不会互相干扰
持久性:个事务被提交后，在数据库中的改变就是永久的，即使系统崩溃重新启动数据库数据也不会发生改变

关于事务隔离性：
脏读: 在一个事务里面，由于其他事务修改了数据并且没有提交，而导致前后两次读取的数据不一致的情况，这种事务并发问题称之为 “脏读”
不可重复读: 一个事务读取到其他事务已提交的数据导致前后两次读取数据不一样的情况
例如第一个事务对一个表中的数据进行了修改，这种修改涉及到表中的全部数据行。同时，第二个事务也修改这个表中的数据，这种修改是向表中插入一行新数据。那么，以后就会发生操作第一个事务的用户发现表中还有没有修改的数据行，就好象发生了幻觉一样。

隔离级别	    脏读	  不可重复读	幻读
READ UNCOMITTED	√	      √	          √
READ COMMITTED	×	      √	          √
REPEATABLE READ	×	      ×	          √
SERIALIZABLE	×	      ×	          ×

MySQL 包括的事务隔离级别如下：
读未提交:可以读到未提交的内容。
读提交:只能读到已经提交了的内容。
可重复读:专门针对不可重复读这种情况而制定的隔离级别,如果有事务正在读取数据，就不允许有其它事务进行修改操作
串行化（SERIALIZABLE）如果一个事务先根据某些条件查询出一些记录，之后另一个事务又向表中插入了符合这些条件的记录，原先的事务再次按照该条件查询时，能把另一个事务插入的记录也读出来。那么这种隔离级别就称之为串行化。就是在每个读取的数据行上加上共享锁实现(加锁实现事务排序)，这样就避免了脏读、不可重复读和幻读等问题。但是该事务隔离级别执行效率低下，且性能开销也最大，所以一般情况下不推荐使用。



