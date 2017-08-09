## 登网判断-cbss串号监控

> sql脚本均在kfk-act库yl\_act\_it5下执行  
> shell脚本均在drecv1用户目录~/cbssup目录下执行

## cbss串号监控

> cbss串号监控，匹配前14位

|  | 说明 | 名称 |
| :---: | :--- | :--- |
| 处理脚本 | run\_cbpurchase.sh | _**月低手动执行**_ |
| 匹配过程 | p\_cbss\_purchase\_monitoring |  |
| 表 | up\_Tf\_f\_User\_Purchase\_monitor |  |
| 上传表 | cb\_Tf\_fh\_User\_Purchase\_monitor |  |

#### 处理步聚

1.核查处理结果

```sql
--查看处理情况
select act_type,count(1) 
from Tf_f_User_Purchase_monitor 
where cycle_id = to_char(sysdate,'yyyymm') 
group by act_type;

--执行
DECLARE
    v_curr_cycle_id NUMBER;
    v_pre_cycle_id  NUMBER;
    v_pre_act_type  NUMBER;
    v_pre_cnt       NUMBER;
    v_month6        date;
BEGIN
    if to_char(sysdate,'dd') = '01' then
        v_curr_cycle_id := To_char(add_months(SYSDATE, -1), 'yyyymm');
        v_pre_cycle_id  := To_char(add_months(SYSDATE, -2), 'yyyymm');
        v_month6 := trunc(add_months(sysdate,-6),'mm');
    else
        v_curr_cycle_id := To_char(add_months(SYSDATE, -0), 'yyyymm');
        v_pre_cycle_id  := To_char(add_months(SYSDATE, -1), 'yyyymm');
        v_month6 := trunc(add_months(sysdate,-5),'mm');
    end if;

    dbms_output.put_line('v_curr_cycle_id' || v_curr_cycle_id);
    dbms_output.put_line('v_pre_cycle_id' || v_pre_cycle_id);
    delete up_Tf_f_User_Purchase_monitor 
    where cycle_id = v_curr_cycle_id;

    FOR r IN (SELECT ROWID, a.*
                FROM Tf_f_User_Purchase_monitor a
               WHERE cycle_id = v_curr_cycle_id
                AND start_date > v_month6) LOOP
        BEGIN

            SELECT 1, act_type
              INTO v_pre_cnt, v_pre_act_type
              FROM cb_Tf_fh_User_Purchase_monitor
             WHERE cycle_id = (SELECT MAX(cycle_id)
                                 FROM cb_Tf_fh_User_Purchase_monitor
                                WHERE user_id = r.user_id)
               AND user_id = r.user_id;
        EXCEPTION
            WHEN OTHERS THEN
                v_pre_cnt := 0;
        END;
        --转匹配标示
        select decode(r.act_Type,1,0,0,1) into r.act_Type from dual;
        --往月没有写入，本月为不匹配，写入
        --往月有写入，匹配状态和当月不同，写入
        --其它情况不处理
        IF (v_pre_cnt = 0 AND r.act_type = 1) OR
           (v_pre_cnt > 0 AND r.act_type <> v_pre_act_type) THEN
            INSERT INTO up_Tf_f_User_Purchase_monitor
                SELECT cycle_id, user_id, partition_id, bindsale_attr, extra_dev_fee,
                       mpfee, feeitem_code, foregift, foregift_code, foregift_backmode,
                       agreement_months, end_mode, device_type, mobile_cost, device_name,
                       device_brand, imei, list_bank, list_fee, list_code, credit_org,
                       credit_type, credit_card_num, agreement, product_id, package_id,
                       staff_id, depart_id, start_date, end_date, remark, item_id,
                       prov_code, update_time, serial_number, eparchy_code, open_date,
                       in_date, decode(act_type, 1, 0, 0, 1) act_type, expenses_id,
                       db_user
                  FROM Tf_f_User_Purchase_monitor
                 WHERE ROWID = r.rowid;
        END IF;

    END LOOP;
    COMMIT;
END;
/
```

```sql
--查看上传情况
Select act_type,Count(1) 
From up_Tf_f_User_Purchase_monitor 
group by act_type;
```



