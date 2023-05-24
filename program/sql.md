# sql 相关学习及积累内容

## 工作中 sql 语句积累

### tsm 平台 sql 语句使用

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
```
