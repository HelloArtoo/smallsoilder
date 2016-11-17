#手机充值请求
#####供应商：Flexi Trendy, Simpati, Kartu As, XL, Mentari, IM3, Esia, 3, Smartfren, Axis
1. 电话号码 13位的数字或者字母（左对齐，不足用空格填充）
2. 充值金额 12位数字（非浮点型数据）
<br/>
#手机充值返回
1. 电话号码 13位的数字或者字母（左对齐，不足用空格填充）
2. 充值金额 12位数字（非浮点型数据）
3. 附加字段 24位数字
>######Flexi Trendy
>- Region code 2位数字
>- Datel code 4位数字
>- Number of bill 1位数字
>- Reference number 6位数字
>- Filler 11位数字
>######XL, 3
>- Region code 2位数字或字母
>- Serial number 14位数字或字母
>- Filler 18位数字或字母
>######Simpati, Kartu AS, Mentari, IM3, Esia, Smartfren, Axis
>- Bill reference 16位数字或字母
>- Filler 8位数字或字母

#账单查询请求
####Telkom(PSTN, Speedy, Flexy Classy)<br/>
电话号码 13位数字（左对齐，不足用空格填充）<br/>
####BII Credit Card信用卡<br/>
信用卡卡号 16位的数字（左对齐，不足用空格填充）<br/>
####后付通信费 (Telkomsel, Indosat, Xl, Smartfren, Esia, Axis)<br/>
电话号码 13位数字（左对齐，不足用空格填充）<br/>
####PAM(房产)<br/>
供应商代码（Palyja=10, Aetra=1）2位数字<br/>
客户ID 15位数字（左对齐，不足用空格填充）<br/>
####PLN(电费-后付)<br/>
客户编号 12位数字或字母<br/>
####PLN Non-Taglis(电费-)<br/>
唯一码 20位数字或字母<br/>
语言编码 1位(默认为0)<br/>
####PLN(电费-预付)<br/>
支付标记 1位数字或字母(0电表号 1客户编号)<br/>
电表号 11位数字或字母<br/>
客户编号 13位数字或字母<br/>
####机票<br/>
支付ID(payment ID) 13位数字或字母<br/>
####火车票(PT. KAI)<br/>
火车票(Ticket number) 13位数字或字母<br/>
####房产税等税收(PBB)<br/>
Indicator(0004) 4位数字或字母<br/>
NOP(Ticket number) 18位数字或字母<br/>
Tahun SPT 4位数字或字母<br/>
####高速路费(Sriwijaya Air & BSD City)<br/>
唯一码 20位数字或字母<br/>
语言(0印尼 1英语) 1位数字<br/>
####虚拟账号<br/>
虚拟账号 20位数字或字母<br/>
####WOM Finance<br/>
虚拟账号= 78900 + customer number <br/>
#账单查询返回
