| 项目   | 标题 |日期 |版本 |作者 |
| ----|:-------:| :----:|----|:---:|
| 内容   |购物车设计|2018-12-20|0.1 |杜向军|

主要介绍
===============
# 一. 数据表
## 1. cart_item 购物车子表
|字段|字段名|类型（长度）|备注|
|:---:|:---:|:---:|:---:|
|id|主键|int|自增长|
|product_id|产品id|int|-|
|car_id|购物车id|int||
|product_type|产品类型|int|使用parm表中的字段|
|num|数量 |int(7)||
|price|单价|decimal(13,8)||
|sum|总金额|decimal(15,8)||
|time|创建时间|datetime||
|remark|备注|varchar(100)||
|st|修改时间|datetime||

## 2. cart 购物车
|字段|字段名|类型（长度）|备注|
|:---:|:---:|:---:|:---:|
|id|主键|int|自增长|
|user_id|用户id|int||
|time|创建时间|datetime||
|status|状态|int|1.初始状态 2.提交  3.删除|
|st|修改时间|datetime||
|operator|操作人|int||

## 3. product_order 产品订单
|字段|字段名|类型（长度）|备注|
|:---:|:---:|:---:|:---:|
|id|主键|int|自增长|
|cart_id|购物车id|int||
|all_sum|订单金额|decimal(16,8)|
|status|订单状态|int|1.待付款  2.取消订单  3.完成订单  4.结束订单  （和parm结合）|
|operator|操作人|int||
|time|创建时间|datetime||
|st|修改时间|datetime||
# 二. 功能描述：
## 1.初始化购物车  
### 触发环境：<br>
>> 1>如果用户操作购物车（添加商品，查看购物车），但是本地没有购物车。<br>
### 操作：<br>
>> 1>如果用户没有登陆，看线下是否有购物车，如果线下有购物车就直接获取线下购物车；如果线下没有购物车就创建一个购物车。<br>
>> 2>如果用户登陆：<br>
>> ①，按照购物车

## 2.操作购物车
## 3.清空购物  
## 4.提交购物车
# 三.接口文档：
## 1.获取购物车
### url:/card/user/{userId}<br>
|字段|字段名|类型(长度)|是否必填|备注|
|:---:|:---:|:---:|:---:|:---:|
|userId|用户id|int(10)|是|这个值是拼在url上的| 
### Method: POST
### data:通过json类型传输数据 ，接口只有一个名为jsonStr的参数。
#####jsonStr数据内容<br>
|字段|字段名|类型(长度)|是否必填|备注|
|:---:|:---:|:---:|:---:|:---:|
|cardId|购物车id|int(10)|否|如果用户本地存储有这个字段就提交|
|cardDatetime|购物车时间戳|long(20)|否|如果用户本地存储这个字段就提交|
|products|本地购物车数据|String(300)|否|包含本地的购物车信息，如果没有就不传该参数|
##### products的数据<br>
|字段|字段名|类型(长度)|是否必填|备注|
|:---:|:---:|:---:|:---:|:---:|
|productId|产品id|int(10)|必填||
|num|数量|int(7)|必填||

### 返回数据（json）
#### 返回值字段<br>
|字段|字段名|类型(长度)|是否必填|备注|
|:---:|:---:|:---:|:---:|:---:|
|type|是否成功|boolean|是||
|message|返回信息|String(300)|是|当type为false返回的是错误信息，当type为true时，返回当前的购物车|
##### message结构<br>
|字段|字段名|类型(长度)|是否必填|备注|
|:---:|:---:|:---:|:---:|:---:|
|cardId|购物车id|int|<10|否|线上的购物车id|
|cardDatetime|购物车时间戳|long|<20|否|线上购物车时间戳|
|products|本地购物车数据|String(300)|否|线上购物车产品|
|allSum|购物车总金额|decimal(15,8)|否|线上购物车总金额|
##### products结构<br>
|字段|字段名|类型(长度)|是否必填|备注|
|:---:|:---:|:---:|:---:|:---:|
|productId|产品id|int(10)|必填||
|productName|产品名称|String(50)|必填||
|price|产品单价|decimal(13,8)|
|num|产品数量|int(7)|必填||
|sum|总金额|decimal(15,8)|必填||
## 2.验证操作
## 3.



