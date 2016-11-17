#手机充值请求
#####供应商：Flexi Trendy, Simpati, Kartu As, XL, Mentari, IM3, Esia, 3, Smartfren, Axis
1. 电话号码 13位的数字或者字母（左对齐，不足用空格填充）
2. 充值金额 12位数字（非浮点型数据）
    
#手机充值返回
1. 电话号码 13位的数字或者字母（左对齐，不足用空格填充）
2. 充值金额 12位数字（非浮点型数据）
3. 附加字段 24位数字
    
> **Flexi Trendy**
>- Region code 2位数字
>- Datel code 4位数字
>- Number of bill 1位数字
>- Reference number 6位数字
>- Filler 11位数字
    
> **XL, 3**
>- Region code 2位数字或字母
>- Serial number 14位数字或字母
>- Filler 18位数字或字母
    
> **Simpati, Kartu AS, Mentari, IM3, Esia, Smartfren, Axis**
>- Bill reference 16位数字或字母
>- Filler 8位数字或字母

#账单查询请求
**Telkom(PSTN, Speedy, Flexy Classy)**
>1. 电话号码 13位数字（左对齐，不足用空格填充）
    
**BII Credit Card信用卡**
>1. 信用卡卡号 16位的数字（左对齐，不足用空格填充）
    
**后付通信费 (Telkomsel, Indosat, Xl, Smartfren, Esia, Axis)**
>1. 电话号码 13位数字（左对齐，不足用空格填充）
    
**PAM(房产)**
>1. 供应商代码（Palyja=10, Aetra=1）2位数字
>2. 客户ID 15位数字（左对齐，不足用空格填充）
