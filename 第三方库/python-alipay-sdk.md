# python-alipay-sdk



## 基础介绍



用户支付流程：
```
[用户点击支付] →
[跳转到支付宝付款页面] →
[用户完成付款] →
[支付宝回调 notify_url 到你服务器] → ✅ 验签 & 更新订单状态
```


准备工作：
1. 访问 支付宝开放平台
2. 创建应用（开发者中心 → 创建应用）
3. 设置接口权限：开通所需支付能力（如电脑网站支付、当面付等）
4. 设置公钥 / 私钥
5. 拿到以下信息：
    - app_id：	你的应用ID
    - 支付宝网关：	https://openapi.alipay.com/gateway.do
    - 商户私钥：	你的 RSA2 私钥
    - 支付宝公钥：	官方提供的公钥，用于验签
    - 回调地址：	用户支付成功后支付宝通知你服务器（必须使用公网IP）

创建支付订单：
    1. 加载密钥（商户私钥、支付宝公钥）
    2. 实例化支付宝 SDK（appid、app_notify_url、app_private_key_string、alipay_public_key_string、sign_type）
    3. 构造订单字符串
        - out_trade_no：订单编号
        - total_amount：总金额
        - subject：
        - return_url：支付成功跳转
        - notify_url：支付成功回调
    4. 跳转到支付页面

处理支付回调（服务器接收支付结果）
    1. request:
        - sign: 签名
        - trade_status：订单状态
        - out_trade_no：订单号
    2. 响应success、failure



Alipay常见接口：
- 网页支付：	api_alipay_trade_page_pay
- H5 支付：	api_alipay_trade_wap_pay
- 查询订单：	api_alipay_trade_query
- 退款：	api_alipay_trade_refund
- 转账到用户支付宝账户：api_alipay_fund_trans_toaccount_transfer


## 核心内容
```yaml
alipy:
    Alipay:
        api_alipay_trade_page_pay(): # 创建 页面支付 URL参数
        api_alipay_trade_query(): # 主动查询订单状态
            ---
            trade_status:
        verify(): # 验签
```



### 创建订单
### 同步通知
### 异步通知




## 支付宝沙箱


1. 进入开发者平台沙箱页面
    - 打开：https://open.alipay.com/platform/appDaily.htm
2. 创建沙箱应用（或启用现有沙箱）
    - 点击「沙箱环境工具」→ 下载开发助手 → 获取沙箱账号 & 沙箱钱包（手机扫码登录）
3. 配置沙箱参数
    - 网关地址：https://openapi.alipaydev.com/gateway.do
    - app_id：沙箱专属的 app_id
    - 支付宝公钥：沙箱支付宝提供的（和正式环境不同）
    - 商户私钥：你自己生成的，用于签名
    - 商户公钥：你上传到沙箱平台的，支付宝验签用
4. 测试买家、卖家账号