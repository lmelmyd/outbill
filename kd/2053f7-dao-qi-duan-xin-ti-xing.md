# 宽带到期短信提醒
10号和20号执行

# 定时间任务，每月10号和20号执行
    00 9 10,20 * * /drecvdata/drecv1/remind_adsl/run_send_sms_new.sh

# 检查执行状态
    drecv1主机
    ls ~/remind_adsl/*.ctl
    #无 *sms* 的为结束

# 库内查看
    --bss
    SELECT remark, COUNT(1)
      FROM Tf_f_Broad_Warn_New_sms
     WHERE update_day = to_char(SYSDATE - 1, 'yyyymmdd')
     GROUP BY remark;
    --cbss查看
    
   