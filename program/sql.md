
# sql 相关学习及积累内容

## 工作中 sql 语句积累

### tsm 平台 sql 语句使用

#### 基础查询语句

```sql
select * from tsm_appcaseinst a where a.seid='98683012881004249527000000000002';


select * from tsm_dcep_info a where a.seid='98683012881004249527000000000002';

select * from tsm_wallet_info a where a.seid='98683012881004249527000000000002';

select * from process_node  order by applet_type and process_id;

select * from process ;

select * from tsm_card_info;

//用于不需要关联字段的联表排列组合查询
select a.*,b.* from ams_role a join code_certype b on 1=1;

select a.*,b.*,c.* from  a join  b join c on 1=1=1 ;

//用于需要关联字段的联表查询，先 join on 再where 再 order by 再limit
select a.* from 定位信息表 a join 设备信息表 b on a.平台设备编号 = b.平台设备编号  where a.账户=? and b.IMEI=?  and （开始时间<=a.时间＜=结束时间 ）order by 定位时间 limit 0,10 ;
```

#### 常用其他语句 for mysql

```sql
//新增表格
create table if not exists process_checkplan_delete
(id varchar(64) primary key,
wallet_status varchar(64),safe_app_status varchar(64),dcep_app_status varchar(64),pro_status varchar(64),executing_node varchar(255));
//添加列
INSERT INTO interface2.c (name,dcep_app_status) VALUES ('未下载未个人化未开立','1110'),('已下载未个人化未开立','1210'),('已下载已个人化未开立','1220'),('已下载已个人化已开立','1220');
//修改表头
alter table interface2.c change  safe_app_status dcep_app_status varchar(64);
//添加主键
alter table c add primary key(dcep_app_status)；
//删除主键
 alter table 表名 drop primary key;
 //从b中查找pro_status的作为a的code，b的查找字段是a的一部分
 update process a set code=(select b.pro_status from process_checkplan_open b where a.name=concat("executing_node" ,b.id )) where a.name like 'executing_node%';
 //concat进行字符串拼接
 select concat(temp1.id ,"_"  ,temp2.id  ,"_" ,temp3.id)  from temp1,temp2,temp3;
 //使用某个数据库
 use interface
```

## PLSQL下载

### 访问10.1.14.20window

密码：威武霸气

复制原本的安装文件夹

### PLSQL的dll导入

1. 进入配置界面
![进入设置界面](/program/pictures/sql/1686572317725.png)
2. 复制文件夹并修改配置
![Alt text](/program/pictures/sql/1686572428684.png)

### PLSQL注册

> 进入界面---》help--->register

14:
Product Code：4t46t6vydkvsxekkvf3fjnpzy5wbuhphqz
serial Number：601769
password：xs374ca

13:
product code： 4vkjwhfeh3ufnqnmpr9brvcuyujrx3n3le
serial Number：226959
password: xs374ca

## sql语句书写逻辑

- 基于题目对方法的思考
- 题目：对于table表，存在id、name此两个字段，此两条字段不存在主键，请查询出id值最大的所有记录；

```sql
 x = select max(id) from table ;
 select * from table where id = x;
 ```

- 处理逻辑：先查出最大的id，通过最大的id查到所有记录即可；
- 推论：先查出限制的条件，在向外部查询；
- else：对于null 无法通过 = 查出；

## sql基础特性

1. reasonSet：输出的结果集；
2. functions：自定义的一些执行函数，可以类似于其他语言中的函数，对输出结果进行处理；
3. 关键词：与其他语言类似，不可用于重新命名方法等，如“select”、“from”等sql基础占用的词语；