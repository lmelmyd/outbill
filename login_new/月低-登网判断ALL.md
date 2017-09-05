## 登网判断-所有业务

> sql脚本均在kfk-act库yl\_act\_it5下执行  
> shell脚本均在drecv1用户目录~/cbssup目录下执行  
> 2017.08月整合一起  
> 规则  
>   登网判断处理规则：  
>     1.产品变化  
>         a.当月与次月产品不一致，不处理  
>         b.次月产品不在监控范围内，不处理  
>     2.产品无变化，前提是用户资费历史上添加过,根据匹配情况加和减资费  
>         加资费：当前资费无效时上传加资费操作，有效不处理  
>         减资费：当前资费有效时上传减资费操作，无效不处理  
>     3.用户不在网，不处理

```
-- 其FLAG_TYPE='1' 为裸终端用户
--   FLAG_TYPE='2' 为换机送费用户
--   FLAG_TYPE='3' 为76元合约用户。
1:裸终端合约用户 
2:换机预存话费送流量用户  
3:76元及以上中高档全国套餐流量促销用户 
4:自备机套餐折扣合约体验流量(CBSS) 
5:承诺低消送语音和流量 
6:承诺低消送语音所赠送的体验流量 
7:更换流量卡槽专用流量包
8:16元套餐购机送540政策优化  
9:自备机套餐折扣合约
```

| 说明 | 名称 | 其它 |
| :---: | :--- | :---: |
| 处理脚本 | run\_loginpurchase\_n.sh | 月低和1号执行,20个通道 |
| 匹配过程 | p\_login\_purchase\_monitor\_new |  |
| 表 | JF\_login\_PURCHASE\_MONITORING |  |
| 上传表 | up\_login\_purchase\_monitor |  |
| 历史表 | uph\_login\_Purchase\_monitor |  |

#### 处理步聚

1.直接执行sh脚本

```sh
# 数据供后，直接执行shell:
cd ~/cbssup
nohup ./run_loginpurchase_n.sh.sh
```

2.核查处理结果

```sql
--查看匹配情况
select log_id,flag,msg,count(1) 
from JF_login_PURCHASE_MONITORING 
where month_id= to_char(sysdate-3,'yyyymm')
group by log_id,flag,msg;

--查看处理情况
select log_id,state,msg,count(1) 
from JF_login_PURCHASE_MONITORING 
where month_id= to_char(sysdate-3,'yyyymm')
group by log_id,state, msg;

--查看上传情况
SELECT log_id, act_type, COUNT(1)
  FROM up_login_purchase_monitor
 GROUP BY log_id, act_type;

--填写excel
SELECT flag_type, CHECK_FLAG, COUNT(1)
  FROM work_test.hw_rpt_user_int_t
 WHERE day_id = To_char(SYSDATE, 'yyyymmdd')
   AND net_type_code = '50'
 GROUP BY flag_type, CHECK_FLAG
 ORDER BY 1, 2;

--上传目标数
SELECT log_id, act_type, COUNT(1)
  FROM up_login_purchase_monitor
 GROUP BY log_id, act_type
 ORDER BY 1, 2;

--76元档数据分布
SELECT trunc(zf_start_date, 'mm'), act_type, COUNT(1)
  FROM up_login_purchase_monitor
  where log_id='3'
 GROUP BY trunc(zf_start_date, 'mm'), act_type
 order by 1,2;

--
```



