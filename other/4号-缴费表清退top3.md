---
title: 缴费表清退top3
create: 2017.08.07
---

# bss处理

```
各域：
exec p_top3_paylog_bss
```

## 导出结果到excel

```sql
--转账
select b.area_name, a.eparchy_code,recv_staff_id,sum_fee,cnt
from(select 'act1' db,ta.* from uop_act1.jinl_paylog_recvfee@UQRY_SEL_TO_HAACTDB11 ta
        union all select 'act2' db,ta.* from uop_act2.jinl_paylog_recvfee@UQRY_SEL_TO_HAACTDB11 ta
        union all select 'act3' db,ta.* from uop_act3.jinl_paylog_recvfee@UQRY_SEL_TO_HAACTDB22 ta
        union all select 'act4' db,ta.* from uop_act4.jinl_paylog_recvfee@UQRY_SEL_TO_HAACTDB22 ta) a,
        ucr_param.td_m_area b
 WHERE b.parent_area_code = '0076'
   AND a.eparchy_code = b.area_code
and partition_id = to_number(to_char(add_months(SYSDATE, -1), 'mm')) --4
and payment_id <> 100014
order by a.eparchy_code;

--清退
select b.area_name, a.eparchy_code,recv_staff_id,sum_fee,cnt
from(select 'act1' db,ta.* from uop_act1.jinl_paylog_recvfee@UQRY_SEL_TO_HAACTDB11 ta
        union all select 'act2' db,ta.* from uop_act2.jinl_paylog_recvfee@UQRY_SEL_TO_HAACTDB11 ta
        union all select 'act3' db,ta.* from uop_act3.jinl_paylog_recvfee@UQRY_SEL_TO_HAACTDB22 ta
        union all select 'act4' db,ta.* from uop_act4.jinl_paylog_recvfee@UQRY_SEL_TO_HAACTDB22 ta) a,
        ucr_param.td_m_area b
 WHERE b.parent_area_code = '0076'
   AND a.eparchy_code = b.area_code
and partition_id = to_number(to_char(add_months(SYSDATE, -1), 'mm')) --4
and payment_id = 100014
order by a.eparchy_code;
```

# cbss处理

可在uop\_act1下或yl\_act\_it5下执行均可

## uop\_act1下

```sql
--uop_act1域执行
BEGIN
    DELETE jinl_paylog_recvfee_cbss
     WHERE partition_id = to_number(to_char(add_months(SYSDATE, -1), 'mm'));

    FOR rec IN (SELECT *
                  FROM td_m_area
                 WHERE area_level = 20) LOOP
        --转账
        INSERT INTO jinl_paylog_recvfee_cbss
            SELECT to_number(to_char(add_months(SYSDATE, -1), 'mm')), eparchy_code,
                   recv_staff_id, fee, cnt, 100016
              FROM (SELECT eparchy_code, recv_staff_id, COUNT(*) cnt, -sum(recv_fee) fee
                       FROM work_wk.tf_b_paylog_cbss a
                      WHERE partition_id =
                            to_number(to_char(add_months(SYSDATE, -1), 'mm'))
                        AND recv_staff_id NOT IN
                            ('SYSUSER ', 'SYSUSER', 'SF_BADFEE', 'SF_TRANS', 'GJM0305')
                        AND payment_id = '100016'
                        AND channel_id = '15008'
                        AND eparchy_code = rec.area_code
                        AND recv_time > trunc(add_months(SYSDATE, -1), 'mm')
                      GROUP BY eparchy_code, recv_staff_id
                      ORDER BY COUNT(*) DESC)
             WHERE rownum < 4;

        --清退
        INSERT INTO jinl_paylog_recvfee_cbss
            SELECT to_number(to_char(add_months(SYSDATE, -1), 'mm')), eparchy_code,
                   recv_staff_id, fee, cnt, 100014
              FROM (SELECT eparchy_code, recv_staff_id, COUNT(*) cnt, -sum(recv_fee) fee
                       FROM work_wk.tf_b_paylog_cbss a
                      WHERE partition_id =
                            to_number(to_char(add_months(SYSDATE, -1), 'mm'))
                        AND recv_staff_id NOT IN
                            ('SYSUSER ', 'SYSUSER', 'SF_BADFEE', 'SF_TRANS', 'GJM0305','Z000DZQD')
                        AND payment_id = '100014'
                        AND nvl(remark, '0') NOT IN ('普通预存款转合约预存款业务的预存清退')
                        AND eparchy_code = rec.area_code
                        AND recv_time > trunc(add_months(SYSDATE, -1), 'mm')
                      GROUP BY eparchy_code, recv_staff_id
                      ORDER BY COUNT(*) DESC)
             WHERE rownum < 4;
        COMMIT;
    END LOOP;
END;
/
```

## yl\_act\_it5下

```sql
--yl_act_it5
BEGIN
    DELETE jinl_paylog_recvfee_cbss
     WHERE partition_id = to_number(to_char(add_months(SYSDATE, -1), 'mm'));

    FOR rec IN (SELECT *
                  FROM ucr_param.td_m_area
                 WHERE area_level = 20 and province_code = '76') LOOP
        --转账
        INSERT INTO jinl_paylog_recvfee_cbss
            SELECT to_number(to_char(add_months(SYSDATE, -1), 'mm')), eparchy_code,
                   recv_staff_id, fee, cnt, 100016
              FROM (SELECT eparchy_code, recv_staff_id, COUNT(*) cnt, -sum(recv_fee) fee
                       FROM ucr_act5.tf_b_paylog a
                      WHERE partition_id =
                            to_number(to_char(add_months(SYSDATE, -1), 'mm'))
                        AND recv_staff_id NOT IN
                            ('SYSUSER ', 'SYSUSER', 'SF_BADFEE', 'SF_TRANS', 'GJM0305')
                        AND payment_id = '100016'
                        AND channel_id = '15008'
                        AND eparchy_code = rec.area_code
                        AND recv_time > trunc(add_months(SYSDATE, -1), 'mm')
                      GROUP BY eparchy_code, recv_staff_id
                      ORDER BY COUNT(*) DESC)
             WHERE rownum < 4;

        --清退
        INSERT INTO jinl_paylog_recvfee_cbss
            SELECT to_number(to_char(add_months(SYSDATE, -1), 'mm')), eparchy_code,
                   recv_staff_id, fee, cnt, 100014
              FROM (SELECT eparchy_code, recv_staff_id, COUNT(*) cnt, -sum(recv_fee) fee
                       FROM ucr_act5.tf_b_paylog a
                      WHERE partition_id =
                            to_number(to_char(add_months(SYSDATE, -1), 'mm'))
                        AND recv_staff_id NOT IN
                            ('SYSUSER ', 'SYSUSER', 'SF_BADFEE', 'SF_TRANS', 'GJM0305',
                             'Z000DZQD')
                        AND payment_id = '100014'
                        AND nvl(remark, '0') NOT IN ('普通预存款转合约预存款业务的预存清退')
                        AND eparchy_code = rec.area_code
                        AND recv_time > trunc(add_months(SYSDATE, -1), 'mm')
                      GROUP BY eparchy_code, recv_staff_id
                      ORDER BY COUNT(*) DESC)
             WHERE rownum < 4;
        COMMIT;
    END LOOP;
END;
/
```

## 导出结果到excel

### uop\_act1下

```sql
--转账
select b.area_name, a.eparchy_code,recv_staff_id,sum_fee,cnt
from(select 'act1' db,ta.* from uop_act1.jinl_paylog_recvfee_cbss@UQRY_SEL_TO_HAACTDB11 ta) a,
        ucr_param.td_m_area b
 WHERE b.parent_area_code = '0076'
   AND a.eparchy_code = b.area_code
and partition_id = to_number(to_char(add_months(SYSDATE, -1), 'mm')) --4
and payment_id <> 100014
order by a.eparchy_code,cnt desc;

--清退
select b.area_name, a.eparchy_code,recv_staff_id,sum_fee,cnt
from(select 'act1' db,ta.* from uop_act1.jinl_paylog_recvfee_cbss@UQRY_SEL_TO_HAACTDB11 ta) a,
        ucr_param.td_m_area b
 WHERE b.parent_area_code = '0076'
   AND a.eparchy_code = b.area_code
and partition_id = to_number(to_char(add_months(SYSDATE, -1), 'mm')) --4
and payment_id = 100014
order by a.eparchy_code,cnt desc;
```

### yl\_act\_it5下

```sql
--转账
SELECT b.area_name, a.eparchy_code, recv_staff_id, sum_fee, cnt
  FROM (SELECT 'act1' db, ta.*
           FROM jinl_paylog_recvfee_cbss ta) a,
       ucr_param.td_m_area b
 WHERE b.parent_area_code = '76'
   AND a.eparchy_code = b.area_code
   AND partition_id = to_number(to_char(add_months(SYSDATE, -1), 'mm')) --4
   AND payment_id <> 100014
 ORDER BY a.eparchy_code, cnt DESC;

--清退
SELECT b.area_name, a.eparchy_code, recv_staff_id, sum_fee, cnt
  FROM (SELECT 'act1' db, ta.*
           FROM jinl_paylog_recvfee_cbss ta) a,
       ucr_param.td_m_area b
 WHERE b.parent_area_code = '76'
   AND a.eparchy_code = b.area_code
   AND partition_id = to_number(to_char(add_months(SYSDATE, -1), 'mm')) --4
   AND payment_id = 100014
 ORDER BY a.eparchy_code, cnt DESC;
```

# 发送邮件

```
白银明, 李艳玲, 宁伟锋, 李亚涛, 邢帅奇
```



