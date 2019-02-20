##  出口请求结构
#### 物流派单
##### 1.提货单查询/列表

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageIndex|当前页数|当前页数|
|keyword|查询关键字|查询关键字|
|startDate|起始日期|查询对应起始日期后的订单|
|endDate|结束日期|查询对应结束日期前的订单|
|status|查询状态|查询对应状态订单|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|条目id|
|orderNumber|订单号|订单号|
|pickGoodsNumber|提货单号|提货单号|
|createDate|提货单创建时间|提货单创建时间|
|pickGoodsCompany|提货公司|提货公司|
|amount|数量|数量|
|unit|单位|单位|
|status|状态|订单状态|
|remarks|备注|备注|

- 响应JSON结构

```
{
    "result": 'success',
    "data": {
        "total": '100',
        "content": [
            {
                "id": '1',
                "orderNumber": '6623123',
                "pickGoodsNumber": '789789',
                "createdDate": '2019-02-19',
                "pickGoodsCompany": '深圳市xx有限公司',
                "amount": '100',
                "unit": '箱',
                "status": '待受理',
                "remarks": '无'
            },
            {
                "id": '2',
                "orderNumber": '6623155',
                "pickGoodsNumber": '785589',
                "createdDate": '2019-02-20',
                "pickGoodsCompany": '深圳市xx有限公司',
                "amount": '100',
                "unit": '板',
                "status": '已受理',
                "remarks": '无'
            },
        ]
    }
}
```
##### 2.新增提货单
> 2.1 获取单据ID

> 2.2 获取单据编号

> 2.3 提货公司列表

> 2.4 提货明细列表

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageIndex|当前页数|当前页数|
|keyword|关键字|订单号/品名关键字|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|条目id|
|orderNumber|订单号|订单号|
|productName|品名|品名|
|typeNumber|型号|型号|
|orderAmount|订单数量|订单数量|
|mayPickGoodsAmount|可提货数量|可提货数量|
|orderDate|订单日期|订单日期|
|unit|单位|单位|
|roughWeight|毛重|毛重|

- 响应JSON结构

```
{
    "result": 'success',
    "data": {
        "total": '100',
        "content": [
            {
                "id": '1',
                "orderNumber": '6623123',
                "productName": '电容',
                "typeNumber": 'NK500',
                "orderAmount": '600',
                "mayPickGoodsAmount": '200',
                "orderDate": '2019-02-20',
                "unit": '箱',
                "roughWeight": '500KG'
            }
        ]
    }
}
```

> 2.5 删除提货明细

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|idList|删除ID列表|数组字符串,传递多个被删除的ID数组|

> 2.6 保存/提交提货明细

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|saveStatus|保存状态|标记当前提货单保存状态/提交状态, 文本值 保存/提交|
|id|id|id|
|documentNumber|单据编号|单据编号|
|pickGoodsCompany|提货公司|提货公司名称|
|contacts|联系人|联系人名称|
|pickGoodsAddress|提货地址|提货地址|
|boardAmount|板数|板数|
|boxAmount|箱数|箱数|
|predictPickGoodsDate|预计提货时间|预计提货时间|
|remarks|备注|备注|
|fileList|附件列表|附件列表, 数组字符串类型, 数组内存储多个文件ID|
|pickGoodsDetailList|提货明细|提货明细列表, 数组对象类型|
|id|提货明细id|提货明细列表,单项的id|
|orderNumber|订单号|提货明细列表内,单项的订单号|
|productName|品名|提货明细列表内,单项的品名|
|typeNumber|型号|提货明细列表内,单项的型号|
|orderAmount|订单数量|提货明细列表内,单项的订单商品数量|
|pickGoodsAmount|提货数量|提货明细列表内,单项的提货数量|


- 请求JSON结构

```
{
    "savePickGoodsOrderData": {
        "saveStatus": '保存/提交',
        "id": '5565678',
        "documentNumber": '45647888',
        "pickGoodsCompany": '深圳市xx公司',
        "contacts": '皮特',
        "pickGoodsAddress": '深圳市福田区xx中心',
        "boardAmount": '50',
        "boxAmount": '50',
        "predictPickGoodsDate": '2019-02-20',
        "remarks": '备注',
        "fileList": ['addixi11231', 'bbszz23334'],
        "pickGoodsDetailList": [
            {
                "id": 'xxx123123',
                "orderNumber": '78989413',
                "productName": '电容',
                "typeNumber": 'NHK200',
                "orderAmount": '200',
                "pickGoodsAmount": '150'
            }
        ]
    }
}
```

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|msg|msg|信息|

- 响应JSON结构

```
{
    "result": 'success',
    "msg": '保存/提交成功!'
}
```

##### 3.提货单详情
```
{
    "data": [
        {
            "id": 'id'
        }
    ]
}
```

#### 付款委托


