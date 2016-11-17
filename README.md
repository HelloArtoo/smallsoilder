#手机充值请求
*供应商：Flexi Trendy, Simpati, Kartu As, XL, Mentari, IM3, Esia, 3, Smartfren, Axis*
-1.电话号码 13位的数字或者字母（左对齐，不足用空格填充）</br>
-2.充值金额 12位数字（非浮点型数据）
#手机充值返回
-1.电话号码 13位的数字或者字母（左对齐，不足用空格填充）</br>
-2.充值金额 12位数字（非浮点型数据）<br/>
-3.附加字段 24位数字
######Flexi Trendy
-3.1Region code 2位数字<br/>
-3.2Datel code 4位数字<br/>
-3.3Number of bill 1位数字<br/>
-3.4Reference number 6位数字<br/>
-3.5Filler 11位数字
######XL, 3
-3.1Region code 2位数字或字母<br/>
-3.2Serial number 14位数字或字母<br/>
-3.3Filler 18位数字或字母<br/>
######Simpati, Kartu AS, Mentari, IM3, Esia, Smartfren, Axis
-3.1Bill reference 16位数字或字母<br/>
-3.2Filler 8位数字或字母<br/>

#账单查询请求
######Telkom(PSTN, Speedy, Flexy Classy)<br/>
电话号码 13位数字（左对齐，不足用空格填充）<br/>
######BII Credit Card信用卡<br/>
信用卡卡号 16位的数字（左对齐，不足用空格填充）<br/>
######后付通信费 (Telkomsel, Indosat, Xl, Smartfren, Esia, Axis)<br/>
电话号码 13位数字（左对齐，不足用空格填充）<br/>
######PAM(房产)<br/>
供应商代码（Palyja=10, Aetra=1）2位数字<br/>
客户ID 15位数字（左对齐，不足用空格填充）<br/>
######PLN(电费-后付)<br/>
客户编号 12位数字或字母<br/>
######PLN Non-Taglis(电费-)<br/>
唯一码 20位数字或字母<br/>
语言编码 1位(默认为0)<br/>
######PLN(电费-预付)<br/>
支付标记 1位数字或字母(0电表号 1客户编号)<br/>
电表号 11位数字或字母<br/>
客户编号 13位数字或字母<br/>
#账单查询返回
