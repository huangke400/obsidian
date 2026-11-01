

1. 派生规则和报表查看：
派生规则：FMDERIVE				
容差强弱控制：S_KI4_38000345		

TCODE:FMRP_RW_BUDGET----预算报告
FMAVCR01----显示控制对象的年度数据
FMRP_RW_BUDCON		预算消耗		
可以通过关联的单据查看AC预算凭证
2. 预算：				
FMBDP--基金管理预算更改行项目表格（基金、承诺项目凭证录入行级别数据维度）				
FMBDT--财务预算管理总表（进行汇总，不到凭证录入级别）				
FMBH抬头  行FMBL（预算录入凭证-FMBB）				

3. 和FI凭证相关的过账的基金凭证：				
FMIFIHD基金管理中的 FI 标题表				
FMIFIIT   在资金管理中的FI行项目表				
V_FMIFI （来自 FI 的 FM 实际行项目）				
视图： 是FMIFIHD和FMIFIIT关联的视图				
4. 承诺表（预算占用）：				
FMIOI 资金管理承诺凭证明细表（含财务手工承诺项（包含表KBLK\KBLP数据）包括后勤端的承诺如采购订单和采购申请等）	
报销报账预算冻结接口			FI30547		
报销报账预算释放接口			FI30548					
预算占用函数：ZFM_GFI_BUDGET_CHK_AND_FREZ				
采购订单和申请承诺占用预算时间（按交货日期，注意跨年的订单按交货日期）				
合同&计划协议 不占用承诺预算				




|                              |
| ---------------------------- |
| 4、报表查询：                      |
| TCODE:FMRP_RW_BUDGET----预算报告 |
| FMAVCR01----显示控制对象的年度数据      |
| 5、预算相关表如下：                   |
| FMBDT--财务预算管理总表              |
| FMIT--基金管理的总计表               |
| FMCI--承诺项目                   |
| FMCIT--承诺项目文本                |
| FMFCTR--基金中心主记录              |
| FMFCTRT--基金中心文本              |
| FMFINT--FIFM:资金文本（基金）        |
| FMBDP--基金管理预算更改行项目表格         |
| FMIFIIT--在资金管理中的FI行项目表       |
| KBLK--凭证表头：人工凭证项（FMZ1）       |
| KBLP--凭证项目：人工凭证项             |

FMBH抬头  行FMBL（预算录入凭证-FMBB）

FMRP_RW_BUDGET

FMEDOW

.FMDERIVE 科目分配对像衍生规则配置

ZFM_GFI_BUDGET_CHK_AND_FREZ


sap 预算凭证

1、FMBBC/FMEDD-------------预算工作台-创建/显示凭证：下达预算，同时产生凭证，基金凭证

FMBB--------------预算工作台。

下达预算同时也可以批量创建凭证：BAPI_0050_CREATE.例：

CALL FUNCTION ‘BAPI_0050_CREATE’

EXPORTING

HEADER_DATA = LS_FM_HD

TESTRUN = PV_TEST(是否需要测试运行)

IMPORTING

FMAREA = LS_HD_INFO-FM_AREA

DOCUMENTYEAR = LS_HD_INFO-DOC_YEAR

DOCUMENTNUMBER = LS_HD_INFO-DOCUMENT

TABLES

ITEM_DATA = GST_FM_LI

SENDER_ITEM_DATA = LST_FM_LI_S

PERIOD_DATA = GST_FM_PERIOD

SENDER_PERIOD_DATA = LST_FM_PERIOD_S

RETURN = LST_LOG.

备注：此FUNCTION也可作预算增加与减少，SENDER行为发送方。

2、FMZ1/FMZ2/FMZ3----创建/更改/显示基金承诺（产生基金凭证），创建基金凭证的同时，会占用掉预算

创建基金承诺（称预算占用凭证），也可以使用相应的FUNCTION：

‘FMFR_CREATE_FROM_DATA’。例：

DATA: TYPE ANY TABLE,

GT_SMESGX TYPE TABLE OF SMESGX WITH HEADER LINE.

CALL FUNCTION ‘FMFR_CREATE_FROM_DATA’

EXPORTING

I_FLG_CHECKONLY = ‘’

I_FLG_COMMIT = ‘X’

TABLES

T_POSDATA = T_POSDATA

CHANGING

C_F_HEADDATA = C_F_HEADDATA

EXCEPTIONS

ERROR_MESSAGE = 1

WARNING_MESSAGE = 2.

ASSIGN (’(SAPLSMSG)XMESG[]’) TO .

REFRESH: GT_SMESGX.

IF IS ASSIGNED.

LOOP AT INTO GT_SMESGX.

APPEND GT_SMESGX.

ENDLOOP.

UNASSIGN: .

ENDIF.

3、释放预算，即从占用转为消耗掉预算也有相应的

FUNCTION:‘FMFR_CHANGE_COMPLETION_FLAG’

4、报表查询：TCODE:FMRP_RW_BUDGET----预算报告

FMAVCR01----显示控制对象的年度数据

预算表：FMBDP

预算占用表：KBLK,KBLP

预算消耗表：FMIFIIT

5、预算相关表如下：

FMBDT–财务预算管理总表

FMIT–基金管理的总计表

FMCIT–承诺项目

FMFCTR–基金中心主记录

FMFCTRT–基金中心文本

FMFINT–FIFM:资金文本（基金）

FMBDP–基金管理预算更改行项目表格

FMIFIIT–在资金管理中的FI行项目表

KBLK–凭证表头：人工凭证项（FMZ1）

KBLP–凭证项目：人工凭证项

————————————————

原文链接：https://blog.csdn.net/CHOWWY/article/details/121995657


![[Pasted image 20261024112344.png]]
![[Pasted image 20261024112356.png]]