#安全性
####Verify Key
MC-Bill Verify Key是MC-Bill给商户生成的唯一的一个加密字符串。用于保证每一次交易的安全。Verify Key的使用：
>1. 集成MC-Bill在线支付和商户。
>2. 验证MC-Bill在线支付。
>3. 检查MC-Bil生成的每一笔交易。
    
####安全性检查vCode and sKey
1. vCode (merchant to MC-Bill)
> 商户生成的加密字符串，用于校验商户支付页面的交易。同时也能校验支付请求的完整性。如果商户的配置页面勾选了“Enable Verify Payment”（启用校验支付）的话，每一次交易请求都必须传vCode。
> vCode生成方式：vCode = md5( amount & merchantID & order number & verify key)
2. sKey (MC-Bill to merchant)
> MC-Bill sKey是由MC-Bill定义的一个security key，用于防止（在商户的在线商店交易返回的）交易状态被第三方伪造。商户在修改订单状态的时候必须比较MC-Bill返回的sKey和商户自己计算出来的key是否一致。
> sKey生成方式（下面的key1就是sKey）:
key0 = md5( tranID & ordered & status & domain & amount & currency ) 
key1 = md5( paydate & $domain &key0 & appcode & vKey )
    
#商户接入
####交易流程
    
>1. 商户付款页，显示的是MC-Bill 支付方式选择页面。MC-Bill Payment提供不同的支付方式。
>2. 用户输入借/贷记卡号跳转至银行页面。并等待完成支付。
>3. 银行页面完成支付之后，通知MC-Bill。同时相应的发送支付通知给用户和商户。
>4. 调用商户配置的回调URL。商户更新订单的相应的状态。
####在线交易API
    
接入地址 https://mcbill.mcpayment.co.id/pay/ MerchantID /< Parameters>
>1. 前台回调POST/GET。后台回调POST（商户登录管理后台配置的后台回调地址）
>2. 默认参数
>>1. 交易金额 浮点型数据 最小值1.01
>>2. 订单号 字母或者数字 
>>3. 账单名称（买家姓名） 字母或者数字 UTF-8编码
>>4. 买家邮箱 字母或者数字
>>5. 买家手机号 字母或者数字
>>6. 订单描述 字母或者数字
>>7. 国家编号 2位大写的字母 ISO-3166国家编号
>>8. 返回地址 商家配置的返回地址
>>9. vcode 客户端生成的用于校验的key
>>10. 币种 3位小写字母 （cny之类的）
>3. 返回值 带有*号的字段在测试的时候不会返回
>>1. 交易金额(*) 浮点型数据 
>>2. 订单号 字母或者数字 
>>3. 银行审批码(*) 字谜或者数字
>>4. 交易号 字母或者数字 用于查询使用
>>5. 商户号 字母或者数字
>>6. 状态码 2位数字 00成功11失败
>>7. 错误码(*) 字母或者数字
>>8. 错误描述(*) 字母或者数字
>>9. 币种 3位小写字母
>>10. 支付时间 日期类型 YYYY-MM-DD HH:mm:ss
>>11. channel 字符类型 
>>12. 校验码 字母或者数字 用于校验请求是否合法
    
#商户交易查询
交易查询由商户主动发起。注意：查询频率最低为每5分钟一次。MC-Bill 测试账号不支持此功能。
    
####使用单个transaction ID查询交易
使用MC-Bill生成的唯一的交易号查询。请求URLhttps://mcbill.mcpayment.co.id/query/q_by_tid。请求方式为POST/GET。
>1. 请求参数：
>>1. 交易金额 浮点型数据 最小值1.01
>>2. 交易号 整形 （MC-Bill unique Transaction ID）
>>3. 商户号
>>4. 返回数据类型 0纯文本1by post
>>5. 后台回调地址
>>6. 加密串skey
>2. 返回结果：
>>1. StatCode 2位数字 00Success 11Failure 22Pending
>>2. StatName Word？Success (captured, settled, ReqCancel, ReqChargeback, authorized)
>>3. TranID(交易号) 数值 
>>4. Amount 浮点型数据
>>5. Domain(商户号) 字母或数字
>>6. VrfKey 字母或者数字 md5(Amount &  MC-Bill Verify Key  & Domain & TranID & StatCode)
    
####使用order ID查询交易(返回单个结果)
使用MC-Bill生成的订单号查询。请求URL https://mcbill.mcpayment.co.id/query/q_by_oid。请求方式为POST/GET。
>1. 请求参数：
>>1. 交易金额 浮点型数据 最小值1.01
>>2. oID订单号号 整形 （Order ID of latest transaction.）
>>3. 商户号
>>4. 返回数据类型 0纯文本1by post
>>5. 后台回调地址
>>6. 加密串skey
>2. 返回结果：
>>1. StatCode 2位数字 00Success 11Failure 22Pending
>>2. StatName Word？Success (captured, settled, ReqCancel, ReqChargeback, authorized)
>>3. OrderID(某次特定交易的的订单号) 数值  
>>4. Amount 浮点型数据
>>5. Domain(商户号) 字母或数字
>>6. BillingName(交易时使用的名称) 字母或数字
>>7. VrfKey 字母或者数字 md5(Amount &  MC-Bill Verify Key  & Domain & TranID & StatCode)
    
####使用order ID查询交易(返回批量数据)
使用MC-Bill生成的订单号查询。请求URL https://mcbill.mcpayment.co.id/query/q_by_oid_batch。请求方式为POST/GET。
>1. 请求参数：
>>1. oID订单号号 整形 （Order ID of latest transaction.）
>>2. 商户号
>>3. 返回数据类型 0纯文本1by post
>>4. 后台回调地址
>>5. 返回格式 0纯文本使用|分割 1数组
>>6. 加密串skey
>2. 返回结果：
>>1. TranID(交易号) 数字 MC-Bill生成的唯一号
>>2. BillingDate YYYY-MM-DD 交易时间
>>3. StatCode 2位数字 00Success 11Failure 22Pending
>>4. StatName Word？Success (captured, settled, ReqCancel, ReqChargeback, authorized)
>>5. OrderID(某次特定交易的的订单号) 数值  
>>6. Amount 浮点型数据
>>7. BillingName(交易时使用的名称) 字母或数字







