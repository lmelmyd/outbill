```sh
00 20 * * * /drecvdata/drecv2/cz_sh/main_action.sh
#30 20 30,31 * * /drecvdata/drecv2/cz_sh/run_4g_discnt_proc.sh
0 10 * * * /drecvdata/drecv2/cz_sh/run_balance_chk.sh
30 19 30,31 * * /drecvdata/drecv2/cz_sh/chk_cond_feepolicy.sh
#0,15,30,45 * * * * /drecvdata/drecv2/cz_sh/4g_smart.sh
# 活动异常数据检查
0 8 * * * /drecvdata/drecv2/cz_sh/run_actioncode_chk.sh
# 自动提醒任务
10 8-20 * * * /drecvdata/drecv2/cz_sh/run_todolist.sh
#1 7 * * * sh /drecvdata/drecv1/shellApp/daycheck/dayCheck.sh > /dev/null  
0 1 * * * sh /drecvdata/drecv2/liyt/bak_smart_log.sh 

#sp
05 18 18 * * /drecvdata/drecv2/cz_sh/sp_bakuser.sh
10 18 19 * * /drecvdata/drecv2/cz_sh/sp_getuser.sh
10 18,23,3 20,22,24 * * /drecvdata/drecv2/cz_sh/sp_detail_mob11.sh
10 18 21,23,25 * * /drecvdata/drecv2/cz_sh/sp_detail_mob12.sh
#smart -c40004000
30 17 * * * /drecvdata/drecv2/bin/smart_evehour.sh >> /drecvdata/drecv2/bin/smart_evehour.log &

#adsl
10 18 21 * * /drecvdata/drecv2/cz_sh/run_adsl_0_3_g.sh
00 19 29,30,31 * * /drecvdata/drecv2/cz_sh/run_adsl_chk.sh
# 个人自动任务执行
10 0,2,19,20,21,22 1,5,6,7,8,30,31 * * /drecvdata/drecv2/cz_sh/run_jinl_task_proc.sh

#transfer
0 18 27 * * /drecvdata/drecv2/cz_sh/run_before_trunc.sh
30 19 29,30 * * /drecvdata/drecv2/cz_sh/run_before_all.sh
#5,15,25,35,45,55 18,19,20,21,22,23,0,1,2,3,4,5,6,7 * * * /drecvdata/drecv2/cz_sh/jin_batch_pre0.sh
#5,15,25,35,45,55 * 29,30,31 * * /drecvdata/drecv2/cz_sh/jin_batch_pre0.sh
# 提前转兑0缴费
0,5,10,15,20,25,30,35,40,45,50,55 * 28,29,30,31 * * /drecvdata/drecv2/cz_sh/jin_batch_pre0.sh
# 4g活动返销处理
30 8,17 28,29,30,31 * * /drecvdata/drecv2/cz_sh/run_4g_cancel_action.sh
#owepredeal 专票数据提取
0,10,20,30,40,50 * * * * /drecvdata/drecv2/cz_sh/run_owepredeal.sh

#worelation
30 19 6 * * /drecvdata/drecv2/cz_sh/run_worelation_month_stop.sh

#480
#00 05 * * * /drecvdata/drecv2/zhaorz/shell/execute_single_present.sh >> /drecvdata/drecv2/zhaorz/shell/480shell.log 2>&1
#30 05 * * * /drecvdata/drecv2/zhaorz/shell/execute_count_present.sh >> /drecvdata/drecv2/zhaorz/shell/480shell.log 2>&1

#apncheck
02 09 * * 1 /drecvdata/drecv2/zhaorz/shell/apnConfigCheck/apnConfigCheck.sh >> /drecvdata/drecv2/zhaorz/shell/apnConfigCheck/apnConfigCheck.log 2>&1

#yth
00 03 * * * /drecvdata/drecv2/zhaorz/shell/ythSysInfo/ythRecvInfo.sh >> /dev/null &
0,10,20,30,40,50 9-17 * * * /drecvdata/drecv2/zhaorz/shell/ythSysInfo/ythChkErrInfo.sh >> /dev/null &
00 8 * * * /drecvdata/drecv2/zhaorz/shell/ythSysInfo/ythCrmInfo.sh >> /dev/null &
25 8 * * * /drecvdata/drecv2/zhaorz/shell/ythSysInfo/ythWxSend.sh >> /dev/null &
30 9,10,13 * * * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh ythSysInfo.ini >> /dev/null &

#wosell
00 21 29 4,6,9,11 * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh woSellPresent.ini >> /dev/null &
00 21 30 1,3,5,7,8,10,12 * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh woSellPresent.ini >> /dev/null &
00 21 27 2 * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh woSellPresent.ini >> /dev/null &
45 07 30 4,6,9,11 * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh woSellPresentUpt.ini >> /dev/null &
45 07 31 1,3,5,7,8,10,12 * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh woSellPresentUpt.ini >> /dev/null &
45 07 28 2 * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh woSellPresentUpt.ini >> /dev/null &

#srbz
00 02 5 * * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh srbzDetailInfo.ini >> /dev/null &
00 06 5 * * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh srbzCollectInfo.ini >> /dev/null &
40 08 6 * * /drecvdata/drecv2/zhaorz/auto/autoDeploy.sh srbzOcsInfoUpt.ini >> /dev/null &

#question
0,10,20,30,40,50 * * * * /drecvdata/drecv2/zhaorz/auto/protectTemp.sh giveFlowJar.ini >> /dev/null &


#降欠新规则增加用户统计
30 20 4 * * /drecvdata/drecv2/zhaorz/shell/desoweNewUserCnt/desoweNewUserCnt.sh >> /dev/null &

#cbss用户转账提醒
#0,10,20,30,40,50 11,5 * * * /drecvdata/drecv2/zhaorz/shell/cbssTransWarn/cbssTransWarn.sh >> /dev/null &

#drecv_monitor
0 7,9,14,20 * * * /drecvdata/drecv2/drecv_script/drecv_monitor/drecv_monitor_daemon.sh >> /drecvdata/drecv2/drecv_script/drecv_monitor/drecv_monitor_daemon_2.log 2>&1
#zp
10,20,30,40,50,0 * * * * /drecvdata/drecv2/cz_sh/run_zpbssfee.sh
#11,21,31,41,51,1 * * * * /drecvdata/drecv2/cz_sh/run_special_ticket.sh

#合账缴费新版接口守护进程
0,10,20,30,40,50 * * * * /drecvdata/drecv2/user/tyx/cron_monitor_hzjf.sh >>/drecvdata/drecv2/user/tyx/log/cron_monitor_hzjf.log
```



