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

//用于需要关联字段的联表查询
select a.* from 设备最新定位信息表 a join 设备信息表 b on a.平台设备编号 = b.平台设备编号 where (where 账户=? and IMEI=? and （开始时间<=时间＜=结束时间 ）and 前分页信息条) order by 定位时间
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
