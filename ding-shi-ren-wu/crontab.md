

0 20 \* \* \* /drecvdata/drecv1/cz\_sh/main\_action.sh

00 22 \* \* \* /drecvdata/drecv1/cz\_sh/present.sh

\#30 19 \* \* \* /drecvdata/drecv1/remind\_adsl/run\_warn\_tx.sh

\#40 19 6-31 \* \* /drecvdata/drecv1/remind\_adsl/run\_bss\_st.sh

\#50 19 6-31 \* \* /drecvdata/drecv1/remind\_adsl/run\_kfk\_cbss\_st\_tx\_chk.sh

0 19 6-31 \* \* /drecvdata/drecv1/remind\_adsl/run\_un\_cbss\_sttx.sh

30 19 6-31 \* \* /drecvdata/drecv1/remind\_adsl/run\_un\_tx\_act.sh

1 21,22,23 5 \* \* /drecvdata/drecv1/remind\_adsl/run\_kfk\_task.sh

\#30 19 9-31 \* \* /drecvdata/drecv1/remind\_adsl/run\_cbss\_tx\_chk.sh

\#10 18 6 \* \* /drecvdata/drecv1/remind\_adsl/run\_jl\_new.sh

30 0 \* \* \* /drecvdata/drecv1/remind\_adsl/run\_broadand\_paylog.sh

\#00 10 10,20 \* \* /drecvdata/drecv1/remind\_adsl/run\_send\_sms.sh

00 9 10,20 \* \* /drecvdata/drecv1/remind\_adsl/run\_send\_sms\_new.sh

\#30 2 10-31 \* \* /drecvdata/drecv1/remind\_adsl/csts\_proc.sh

40 1 \* \* \* /drecvdata/drecv1/kpi/kpivalue.sh

30 5 \* \* \* /drecvdata/drecv1/chk\_log/analyse\_credit/m\_analyse.sh

\#0,15,30,45 \* \* \* \* /drecvdata/drecv1/cz\_sh/4g\_smart.sh



\#sap\_total

30 7 \* \* \* /drecvdata/drecv1/cz\_sh/run\_sap\_total.sh



\#sp

05 18 18 \* \* /drecvdata/drecv1/cz\_sh/sp\_bakuser.sh

10 18 19 \* \* /drecvdata/drecv1/cz\_sh/sp\_getuser.sh

10 18,23,3 20,22,24 \* \* /drecvdata/drecv1/cz\_sh/sp\_detail\_mob11.sh

10 18 21,23,25 \* \* /drecvdata/drecv1/cz\_sh/sp\_detail\_mob12.sh



\#adsl

10 18 21 \* \* /drecvdata/drecv1/cz\_sh/run\_adsl\_0\_3\_g.sh

00 19 29,30,31 \* \* /drecvdata/drecv1/cz\_sh/run\_adsl\_chk.sh

\#smart -c40004000

30 17 \* \* \* /drecvdata/drecv1/bin/smart\_evehour.sh &gt;&gt; /drecvdata/drecv1/bin/smart\_evehour.log &



\#transfer

0 18 27 \* \* /drecvdata/drecv1/cz\_sh/run\_before\_trunc.sh

30 19 29,30 \* \* /drecvdata/drecv1/cz\_sh/run\_before\_all.sh



00 12 1 \* \* /drecvdata/drecv1/zm\_bill/uop\_act1\_discnt.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act1\_discnt.log &gt;&1

00 12 1 \* \* /drecvdata/drecv1/zm\_bill/uop\_act2\_discnt.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act2\_discnt.log &gt;&1

00 12 1 \* \* /drecvdata/drecv1/zm\_bill/uop\_act3\_discnt.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act3\_discnt.log &gt;&1

00 12 1 \* \* /drecvdata/drecv1/zm\_bill/uop\_act4\_discnt.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act4\_discnt.log &gt;&1



00 01 9 \* \* /drecvdata/drecv1/zm\_bill/uop\_act1\_bill.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act1\_bill.log &gt;&1

00 01 9 \* \* /drecvdata/drecv1/zm\_bill/uop\_act2\_bill.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act2\_blll.log &gt;&1

00 01 9 \* \* /drecvdata/drecv1/zm\_bill/uop\_act3\_bill.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act3\_bill.log &gt;&1

00 01 9 \* \* /drecvdata/drecv1/zm\_bill/uop\_act4\_bill.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act4\_bill.log &gt;&1





00 07 5 \* \* /drecvdata/drecv1/zm\_bill/uop\_act1\_deposit.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act1\_deposit.log &gt;&1

00 07 5 \* \* /drecvdata/drecv1/zm\_bill/uop\_act2\_deposit.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act2\_deposit.log &gt;&1

00 07 5 \* \* /drecvdata/drecv1/zm\_bill/uop\_act3\_deposit.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act3\_deposit.log &gt;&1

00 07 5 \* \* /drecvdata/drecv1/zm\_bill/uop\_act4\_deposit.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act4\_deposit.log &gt;&1





00 07 6 \* \* /drecvdata/drecv1/zm\_bill/uop\_act1\_contract\_4g.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act1\_contract\_4g.log &gt;&1

00 07 6 \* \* /drecvdata/drecv1/zm\_bill/uop\_act2\_contract\_4g.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act2\_contract\_4g.log &gt;&1

00 07 6 \* \* /drecvdata/drecv1/zm\_bill/uop\_act3\_contract\_4g.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act3\_contract\_4g.log &gt;&1

00 07 6 \* \* /drecvdata/drecv1/zm\_bill/uop\_act4\_contract\_4g.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act4\_contract\_4g.log &gt;&1



00 07 2 \* \* /drecvdata/drecv1/zm\_bill/uop\_act1\_contract.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act1\_contract.log &gt;&1

00 07 2 \* \* /drecvdata/drecv1/zm\_bill/uop\_act2\_contract.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act2\_contract.log &gt;&1

00 07 2 \* \* /drecvdata/drecv1/zm\_bill/uop\_act3\_contract.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act3\_contract.log &gt;&1

00 07 2 \* \* /drecvdata/drecv1/zm\_bill/uop\_act4\_contract.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act4\_contract.log &gt;&1





00 07 11 \* \* /drecvdata/drecv1/zm\_bill/uop\_act1\_nodeal.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act1\_nodeal.log &gt;&1

00 07 11 \* \* /drecvdata/drecv1/zm\_bill/uop\_act2\_nodeal.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act2\_nodeal.log &gt;&1

00 07 11 \* \* /drecvdata/drecv1/zm\_bill/uop\_act3\_nodeal.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act3\_nodeal.log &gt;&1

00 07 11 \* \* /drecvdata/drecv1/zm\_bill/uop\_act4\_nodeal.sh &gt;/drecvdata/drecv1/zm\_bill/uop\_act4\_nodeal.log &gt;&1



\#480送费

\#00 05 \* \* \* /drecvdata/drecv1/zhaorz/shell/execute\_single\_present.sh &gt;&gt; /drecvdata/drecv1/zhaorz/shell/480shell.log 2&gt;&1

\#30 05 \* \* \* /drecvdata/drecv1/zhaorz/shell/execute\_count\_present.sh &gt;&gt; /drecvdata/drecv1/zhaorz/shell/480shell.log 2&gt;&1

30 05 \* \* \* /drecvdata/drecv1/zhaorz/shell/new480Present/new480Present.sh &gt;&gt; /drecvdata/drecv1/zhaorz/shell/new480Present/shlog.log &



\#账单账本数据稽核

\#40 09 \* \* \* /drecvdata/drecv1/zhaorz/shell/billDepCheck/billDepCheck.sh &gt;&gt; /drecvdata/drecv1/zhaorz/shell/billDepCheck/result.log 2&gt;&1



\#地市一体化核查信控核查数据更新

\#5,20,35,50 8-20 \* \* \* /drecvdata/drecv1/zhaorz/shell/creditCheck/creditTodayChkInfoUpt.sh &gt;&gt; /dev/null &

30 23 \* \* \* /drecvdata/drecv1/zhaorz/shell/creditCheck/getCreditFailTrade.sh &gt;&gt; /dev/null &

0 3 \* \* \* /drecvdata/drecv1/zhaorz/shell/creditCheck/creditChkPool.sh &gt;&gt; /dev/null &

0 1 \* \* \* /drecvdata/drecv1/zhaorz/shell/creditCheck/secondGetBill.sh &gt;&gt; /dev/null &



\#停机有话务用户二次停机

0 15 3-31 \* \* /drecvdata/drecv1/zhaorz/shell/userSecCredit/stopUserSecStop.sh &gt;&gt; /dev/null &



\#CBSS用户调账负账单数据检查

0 8 1,10,20,25 \* \* /drecvdata/drecv1/zhaorz/shell/adjustBillCheck/adjustBillCheck.sh &gt;&gt; /dev/null &



\#统一送费BSS/OCS进程稽核程序

0,10,20,30,40,50 \* \* \* \* /drecvdata/drecv1/zhaorz/src/bssTuxedo/checkBssProgram.sh &gt;&gt; /dev/null &



\#降欠用户预估

0 19 31 1,3,5,7,8,10,12 \* /drecvdata/drecv1/zhaorz/shell/lowoweYugu/lowoweYugu.sh &gt;&gt; /dev/null &

0 19 30 4,6,9,11 \* /drecvdata/drecv1/zhaorz/shell/lowoweYugu/lowoweYugu.sh &gt;&gt; /dev/null &

0 19 28 2 \* /drecvdata/drecv1/zhaorz/shell/lowoweYugu/lowoweYugu.sh &gt;&gt; /dev/null &

0 6 1 \* \* /drecvdata/drecv1/zhaorz/shell/lowoweYugu/lowoweYuguCbss.sh &gt;&gt; /dev/null &





10 01 10-31 \* \* sh /drecvdata/drecv1/remind\_adsl/netRemindRecIndb.sh &gt; /dev/null &

10 01 1 \* \* sh /drecvdata/drecv1/remind\_adsl/netRemindRecIndb.sh &gt; /dev/null &



1 0 \* \* 0 sh /drecvdata/drecv1/liyt/month/deposit/exec\_deposit.sh &gt; /dev/null &

0 3 \* \* 0 sh /drecvdata/drecv1/liyt/month/deposit/exec\_chk.sh &gt; /dev/null &

0 9 1 \* \* sh /drecvdata/drecv1/liyt/month/credit\_i/get\_all\_date\_exec.sh &gt; /dev/null &

\#校园营销o

\#30 7,9,11,13,15,17,19 \* \* \* sh /drecvdata/drecv1/liyt/iop\_credit/state\_credit.sh &gt; /dev/null &



\#备份日志

0 1 \* \* \* sh /drecvdata/drecv1/liyt/bak\_smart\_log.sh  &gt; /dev/null &

\#备份参数

0 12 25 \* \* sh /drecvdata/drecv1/liyt/month/bakparam/execbak.sh  &gt; /dev/null &

\#0,15,30,45 7-21 \* \* \* sh /drecvdata/drecv1/liyt/sms\_deal/sh1.sh  &gt; /dev/null &

\#30 8 \* \* \* sh /drecvdata/drecv1/shellApp/daycheck/dayCheck.sh &gt; /dev/null 



\#worelation

30 19 6 \* \* /drecvdata/drecv1/cz\_sh/run\_worelation\_month\_stop.sh

\#drecv\_monitor

0 7,9,14,20 \* \* \* /drecvdata/drecv1/drecv\_script/drecv\_monitor/drecv\_monitor\_daemon.sh &gt;&gt; /drecvdata/drecv1/drecv\_script/drecv\_monitor/drecv\_monitor\_daemon\_1.log 2&gt;&1



\#smsflowpackage数据处理

0 8,9,16 \* \* \* sh /drecvdata/drecv1/liyt/month/to4g/sms\_deal/sms1.sh 

0 8,9,16 \* \* \* sh /drecvdata/drecv1/liyt/month/to4g/sms\_deal/sms2.sh

0 8,9,16 \* \* \* sh /drecvdata/drecv1/liyt/month/to4g/sms\_deal/sms3.sh

0 8,9,16 \* \* \* sh /drecvdata/drecv1/liyt/month/to4g/sms\_deal/sms4.sh

\#kafka discntshare   表同步

\#0 1 \* \* \* sh /drecvdata/drecv1/liyt/month/kafka/get\_share.sh

0 0 \* \* \* sh /drecvdata/drecv1/liyt/month/kafka/state\_depositlimit.sh

\#zp

10,20,30,40,50,0 \* \* \* \* /drecvdata/drecv1/cz\_sh/run\_zpbssfee.sh



\#bigacct state

30 2 2 \* \* sh /drecvdata/drecv1/liyt/month/bigacct/exec\_act1.sh

30 2 2 \* \* sh /drecvdata/drecv1/liyt/month/bigacct/exec\_act2.sh

30 2 2 \* \* sh /drecvdata/drecv1/liyt/month/bigacct/exec\_act3.sh 

30 2 2 \* \* sh /drecvdata/drecv1/liyt/month/bigacct/exec\_act4.sh

\#合账缴费新版接口守护进程

0,10,20,30,40,50 \* \* \* \* /drecvdata/drecv1/user/tyx/cron\_monitor\_hzjf.sh &gt;&gt;/drecvdata/drecv1/user/tyx/log/cron\_monitor\_hzjf.log

