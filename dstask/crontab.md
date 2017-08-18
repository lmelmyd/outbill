```sh
0 20 * * * /drecvdata/drecv1/cz_sh/main_action.sh
00 22 * * * /drecvdata/drecv1/cz_sh/present.sh
0 19 6-31 * * /drecvdata/drecv1/remind_adsl/run_un_cbss_sttx.sh
30 19 6-31 * * /drecvdata/drecv1/remind_adsl/run_un_tx_act.sh
1 21,22,23 5 * * /drecvdata/drecv1/remind_adsl/run_kfk_task.sh
30 0 * * * /drecvdata/drecv1/remind_adsl/run_broadand_paylog.sh
#00 10 10,20 * * /drecvdata/drecv1/remind_adsl/run_send_sms.sh
00 9 10,20 * * /drecvdata/drecv1/remind_adsl/run_send_sms_new.sh
#30 2 10-31 * * /drecvdata/drecv1/remind_adsl/csts_proc.sh
40 1 * * * /drecvdata/drecv1/kpi/kpivalue.sh
30 5 * * * /drecvdata/drecv1/chk_log/analyse_credit/m_analyse.sh
#0,15,30,45 * * * * /drecvdata/drecv1/cz_sh/4g_smart.sh

#sap_total
30 7 * * * /drecvdata/drecv1/cz_sh/run_sap_total.sh

#sp
05 18 18 * * /drecvdata/drecv1/cz_sh/sp_bakuser.sh
10 18 19 * * /drecvdata/drecv1/cz_sh/sp_getuser.sh
10 18,23,3 20,22,24 * * /drecvdata/drecv1/cz_sh/sp_detail_mob11.sh
10 18 21,23,25 * * /drecvdata/drecv1/cz_sh/sp_detail_mob12.sh

#adsl
10 18 21 * * /drecvdata/drecv1/cz_sh/run_adsl_0_3_g.sh
00 19 29,30,31 * * /drecvdata/drecv1/cz_sh/run_adsl_chk.sh
#smart -c40004000
30 17 * * * /drecvdata/drecv1/bin/smart_evehour.sh >> /drecvdata/drecv1/bin/smart_evehour.log &

#transfer
0 18 27 * * /drecvdata/drecv1/cz_sh/run_before_trunc.sh
30 19 29,30 * * /drecvdata/drecv1/cz_sh/run_before_all.sh

00 12 1 * * /drecvdata/drecv1/zm_bill/uop_act1_discnt.sh >/drecvdata/drecv1/zm_bill/uop_act1_discnt.log >&1
00 12 1 * * /drecvdata/drecv1/zm_bill/uop_act2_discnt.sh >/drecvdata/drecv1/zm_bill/uop_act2_discnt.log >&1
00 12 1 * * /drecvdata/drecv1/zm_bill/uop_act3_discnt.sh >/drecvdata/drecv1/zm_bill/uop_act3_discnt.log >&1
00 12 1 * * /drecvdata/drecv1/zm_bill/uop_act4_discnt.sh >/drecvdata/drecv1/zm_bill/uop_act4_discnt.log >&1

00 01 9 * * /drecvdata/drecv1/zm_bill/uop_act1_bill.sh >/drecvdata/drecv1/zm_bill/uop_act1_bill.log >&1
00 01 9 * * /drecvdata/drecv1/zm_bill/uop_act2_bill.sh >/drecvdata/drecv1/zm_bill/uop_act2_blll.log >&1
00 01 9 * * /drecvdata/drecv1/zm_bill/uop_act3_bill.sh >/drecvdata/drecv1/zm_bill/uop_act3_bill.log >&1
00 01 9 * * /drecvdata/drecv1/zm_bill/uop_act4_bill.sh >/drecvdata/drecv1/zm_bill/uop_act4_bill.log >&1


00 07 5 * * /drecvdata/drecv1/zm_bill/uop_act1_deposit.sh >/drecvdata/drecv1/zm_bill/uop_act1_deposit.log >&1
00 07 5 * * /drecvdata/drecv1/zm_bill/uop_act2_deposit.sh >/drecvdata/drecv1/zm_bill/uop_act2_deposit.log >&1
00 07 5 * * /drecvdata/drecv1/zm_bill/uop_act3_deposit.sh >/drecvdata/drecv1/zm_bill/uop_act3_deposit.log >&1
00 07 5 * * /drecvdata/drecv1/zm_bill/uop_act4_deposit.sh >/drecvdata/drecv1/zm_bill/uop_act4_deposit.log >&1


00 07 6 * * /drecvdata/drecv1/zm_bill/uop_act1_contract_4g.sh >/drecvdata/drecv1/zm_bill/uop_act1_contract_4g.log >&1
00 07 6 * * /drecvdata/drecv1/zm_bill/uop_act2_contract_4g.sh >/drecvdata/drecv1/zm_bill/uop_act2_contract_4g.log >&1
00 07 6 * * /drecvdata/drecv1/zm_bill/uop_act3_contract_4g.sh >/drecvdata/drecv1/zm_bill/uop_act3_contract_4g.log >&1
00 07 6 * * /drecvdata/drecv1/zm_bill/uop_act4_contract_4g.sh >/drecvdata/drecv1/zm_bill/uop_act4_contract_4g.log >&1

00 07 2 * * /drecvdata/drecv1/zm_bill/uop_act1_contract.sh >/drecvdata/drecv1/zm_bill/uop_act1_contract.log >&1
00 07 2 * * /drecvdata/drecv1/zm_bill/uop_act2_contract.sh >/drecvdata/drecv1/zm_bill/uop_act2_contract.log >&1
00 07 2 * * /drecvdata/drecv1/zm_bill/uop_act3_contract.sh >/drecvdata/drecv1/zm_bill/uop_act3_contract.log >&1
00 07 2 * * /drecvdata/drecv1/zm_bill/uop_act4_contract.sh >/drecvdata/drecv1/zm_bill/uop_act4_contract.log >&1


00 07 11 * * /drecvdata/drecv1/zm_bill/uop_act1_nodeal.sh >/drecvdata/drecv1/zm_bill/uop_act1_nodeal.log >&1
00 07 11 * * /drecvdata/drecv1/zm_bill/uop_act2_nodeal.sh >/drecvdata/drecv1/zm_bill/uop_act2_nodeal.log >&1
00 07 11 * * /drecvdata/drecv1/zm_bill/uop_act3_nodeal.sh >/drecvdata/drecv1/zm_bill/uop_act3_nodeal.log >&1
00 07 11 * * /drecvdata/drecv1/zm_bill/uop_act4_nodeal.sh >/drecvdata/drecv1/zm_bill/uop_act4_nodeal.log >&1

#480送费
#00 05 * * * /drecvdata/drecv1/zhaorz/shell/execute_single_present.sh >> /drecvdata/drecv1/zhaorz/shell/480shell.log 2>&1
#30 05 * * * /drecvdata/drecv1/zhaorz/shell/execute_count_present.sh >> /drecvdata/drecv1/zhaorz/shell/480shell.log 2>&1
30 05 * * * /drecvdata/drecv1/zhaorz/shell/new480Present/new480Present.sh >> /drecvdata/drecv1/zhaorz/shell/new480Present/shlog.log &

#账单账本数据稽核
#40 09 * * * /drecvdata/drecv1/zhaorz/shell/billDepCheck/billDepCheck.sh >> /drecvdata/drecv1/zhaorz/shell/billDepCheck/result.log 2>&1

#地市一体化核查信控核查数据更新
#5,20,35,50 8-20 * * * /drecvdata/drecv1/zhaorz/shell/creditCheck/creditTodayChkInfoUpt.sh >> /dev/null &
30 23 * * * /drecvdata/drecv1/zhaorz/shell/creditCheck/getCreditFailTrade.sh >> /dev/null &
0 3 * * * /drecvdata/drecv1/zhaorz/shell/creditCheck/creditChkPool.sh >> /dev/null &
0 1 * * * /drecvdata/drecv1/zhaorz/shell/creditCheck/secondGetBill.sh >> /dev/null &

#停机有话务用户二次停机
0 15 3-31 * * /drecvdata/drecv1/zhaorz/shell/userSecCredit/stopUserSecStop.sh >> /dev/null &

#CBSS用户调账负账单数据检查
0 8 1,10,20,25 * * /drecvdata/drecv1/zhaorz/shell/adjustBillCheck/adjustBillCheck.sh >> /dev/null &

#统一送费BSS/OCS进程稽核程序
0,10,20,30,40,50 * * * * /drecvdata/drecv1/zhaorz/src/bssTuxedo/checkBssProgram.sh >> /dev/null &

#降欠用户预估
0 19 31 1,3,5,7,8,10,12 * /drecvdata/drecv1/zhaorz/shell/lowoweYugu/lowoweYugu.sh >> /dev/null &
0 19 30 4,6,9,11 * /drecvdata/drecv1/zhaorz/shell/lowoweYugu/lowoweYugu.sh >> /dev/null &
0 19 28 2 * /drecvdata/drecv1/zhaorz/shell/lowoweYugu/lowoweYugu.sh >> /dev/null &
0 6 1 * * /drecvdata/drecv1/zhaorz/shell/lowoweYugu/lowoweYuguCbss.sh >> /dev/null &


10 01 10-31 * * sh /drecvdata/drecv1/remind_adsl/netRemindRecIndb.sh > /dev/null &
10 01 1 * * sh /drecvdata/drecv1/remind_adsl/netRemindRecIndb.sh > /dev/null &

1 0 * * 0 sh /drecvdata/drecv1/liyt/month/deposit/exec_deposit.sh > /dev/null &
0 3 * * 0 sh /drecvdata/drecv1/liyt/month/deposit/exec_chk.sh > /dev/null &
0 9 1 * * sh /drecvdata/drecv1/liyt/month/credit_i/get_all_date_exec.sh > /dev/null &
#校园营销o
#30 7,9,11,13,15,17,19 * * * sh /drecvdata/drecv1/liyt/iop_credit/state_credit.sh > /dev/null &

#备份日志
0 1 * * * sh /drecvdata/drecv1/liyt/bak_smart_log.sh  > /dev/null &
#备份参数
0 12 25 * * sh /drecvdata/drecv1/liyt/month/bakparam/execbak.sh  > /dev/null &
#0,15,30,45 7-21 * * * sh /drecvdata/drecv1/liyt/sms_deal/sh1.sh  > /dev/null &
#30 8 * * * sh /drecvdata/drecv1/shellApp/daycheck/dayCheck.sh > /dev/null 

#worelation
30 19 6 * * /drecvdata/drecv1/cz_sh/run_worelation_month_stop.sh
#drecv_monitor
0 7,9,14,20 * * * /drecvdata/drecv1/drecv_script/drecv_monitor/drecv_monitor_daemon.sh >> /drecvdata/drecv1/drecv_script/drecv_monitor/drecv_monitor_daemon_1.log 2>&1

#smsflowpackage数据处理
0 8,9,16 * * * sh /drecvdata/drecv1/liyt/month/to4g/sms_deal/sms1.sh 
0 8,9,16 * * * sh /drecvdata/drecv1/liyt/month/to4g/sms_deal/sms2.sh
0 8,9,16 * * * sh /drecvdata/drecv1/liyt/month/to4g/sms_deal/sms3.sh
0 8,9,16 * * * sh /drecvdata/drecv1/liyt/month/to4g/sms_deal/sms4.sh
#kafka discntshare   表同步
#0 1 * * * sh /drecvdata/drecv1/liyt/month/kafka/get_share.sh
0 0 * * * sh /drecvdata/drecv1/liyt/month/kafka/state_depositlimit.sh
#zp
10,20,30,40,50,0 * * * * /drecvdata/drecv1/cz_sh/run_zpbssfee.sh

#bigacct state
30 2 2 * * sh /drecvdata/drecv1/liyt/month/bigacct/exec_act1.sh
30 2 2 * * sh /drecvdata/drecv1/liyt/month/bigacct/exec_act2.sh
30 2 2 * * sh /drecvdata/drecv1/liyt/month/bigacct/exec_act3.sh 
30 2 2 * * sh /drecvdata/drecv1/liyt/month/bigacct/exec_act4.sh
#合账缴费新版接口守护进程
0,10,20,30,40,50 * * * * /drecvdata/drecv1/user/tyx/cron_monitor_hzjf.sh >>/drecvdata/drecv1/user/tyx/log/cron_monitor_hzjf.log
```