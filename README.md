#  出口请求结构
## 一.物流派单
### 1.提货单查询/列表

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageCount|当前页数|当前页数|
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
### 2.新增提货单
##### 2.1 获取单据ID

##### 2.2 获取单据编号

##### 2.3 提货公司列表

##### 2.4 提货明细列表

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageCount|当前页数|当前页数|
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

##### 2.5 删除提货明细

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|idList|删除ID列表|数组字符串,传递多个被删除的ID数组|

##### 2.6 保存/提交提货明细

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
        "fileList": [
            {
                fileId: 'zd5445668',
                name: '订单确认书',
                fileType: 'doc'
            },
            {
                fileId: 'zd5445668',
                name: '需求确认书',
                fileType: 'doc'
            }
        ],
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

### 3.提货单详情

##### 3.1 获取提货单详情

- 请求参数

|响应参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pickGoodsOrderId|提货单ID|提货单ID|

- 响应参数

|响应参数|名称|说明|
| :----: | :----: | :----: |
|savePickGoodsOrderData|提货单数据|同新增提货单中保存接口数据|


- 响应JSON结构

```
{
    "result": 'success',
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
        "fileList": [
            {
                fileId: 'zd5445668',
                name: '订单确认书',
                fileType: 'doc'
            },
            {
                fileId: 'zd5445668',
                name: '需求确认书',
                fileType: 'doc'
            }
        ],
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

## 二.派货单
### 1.派货单列表


- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageCount|当前页数|当前页数|
|keyword|查询关键字|查询关键字|
|startDate|起始日期|查询对应起始日期后的订单|
|endDate|结束日期|查询对应结束日期前的订单|
|status|查询状态|查询对应状态订单|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|条目id|
|orderNumber|订单号|订单号|
|deliveryGoodsNumber|派货单号|派货单号|
|logisticsCompany|物流公司|物流公司|
|predictDeliveryTime|预计派货时间|预计派货时间|
|deliveryCompany|送达公司|送达公司|
|deliveryMode|出货方式|出货方式|
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
                "deliveryGoodsNumber": '789789',
                "logisticsCompany": '顺丰快递',
                "predictDeliveryTime": '2019-02-19',
                "deliveryCompany": '深圳市xx有限公司',
                "deliveryMode": '送货',
                "status": '待派货',
                "remarks": '无'
            },
            {
                "id": '2',
                "orderNumber": '662312545',
                "deliveryGoodsNumber": '74489789',
                "logisticsCompany": '顺丰快递',
                "predictDeliveryTime": '2019-02-19',
                "deliveryCompany": '深圳市xx有限公司',
                "deliveryMode": '自提',
                "status": '正在派货',
                "remarks": '无'
            },
        ]
    }
}
```

### 2.派货单新增

##### 2.1 获取单据ID

##### 2.2 获取单据编号

##### 2.3 物流公司列表

##### 2.4 派货明细列表

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageCount|当前页数|当前页数|
|keyword|关键字|订单号/品名关键字|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|条目id|
|orderNumber|订单号|订单号|
|productName|品名|品名|
|typeNumber|型号|型号|
|orderAmount|订单数量|订单数量|
|mayDeliveryGoodsAmount|可派货数量|可派货数量|
|orderDate|订单日期|订单日期|
|unit|单位|单位|
|boxAmount|箱数|箱数|
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
                "mayDeliveryGoodsAmount": '200',
                "orderDate": '2019-02-20',
                "unit": '箱',
                "boxAmount": '200',
                "roughWeight": '500KG'
            }
        ]
    }
}
```

##### 2.5 删除派货明细

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|idList|删除ID列表|数组字符串,传递多个被删除的ID数组|

##### 2.6 保存/提交派货明细

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|saveStatus|保存状态|标记当前提货单保存状态/提交状态, 文本值 保存/提交|
|id|id|id|
|documentNumber|单据编号|单据编号|
|deliveryMode|出货方式|出货方式 1. 自提 2. 快递 3. 送货 4. 物流|
|oneselfPickGoodsCompany|自提公司|自提公司名称|
|oneselfPickGoodsName|自提人姓名|自提人姓名|
|oneselfPickGoodsPhone|自提人电话|自提人电话|
|idNumber|身份证号|身份证号|
|deliveryCompany|送达公司|送达公司名称|
|contactsName|联系人姓名|联系人名称|
|contactsPhone|联系人电话|联系人电话|
|deliveryAddress|地址|送达地址|
|freightMode|运费方式|运费方式,枚举值 1. 垫付 2. 代付 3. 第三方支付|
|freightType|运费类型|运费类型,枚举值 1. 平均收费 2. 固定收费|
|expressCardNumber|快递月结卡号|快递月结卡号|
|logisticsCompany|物流公司|物流公司|
|predictDeliveryGoodsDate|预计送货时间|预计送货时间|
|receivableAmount|收款金额|收款金额|
|Currency|币别|币别|
|remarks|备注|备注|
|expressReceipt|快递回单|快递回单, 枚举值 1/0|
|attachBill|附发票/支票|附发票/支票, 枚举值 1/0|
|insurance|保险|保险, 枚举值 1/0|
|fileList|附件列表|附件列表, 数组字符串类型, 数组内存储多个文件ID|
|fileName|文件名称|附件列表, 单个文件的文件名称|
|fileId|文件ID|附件列表, 单个文件的文件ID|
|deliveryGoodsDetailList|发货明细|发货明细列表, 数组对象类型|
|id|提货明细id|提货明细列表,单项的id|
|orderNumber|订单号|提货明细列表内,单项的订单号|
|productName|品名|提货明细列表内,单项的品名|
|typeNumber|型号|提货明细列表内,单项的型号|
|orderAmount|订单数量|提货明细列表内,单项的订单商品数量|
|deliveryGoodsAmount|派货数量|提货明细列表内,单项的派货数量|
|roughWeight|毛重|提货明细列表内,单项的毛重|


- 请求JSON结构

```
{
    "saveDeliveryGoodsOrderData": {
        "saveStatus": '保存/提交',
        "id": '5565678',
        "documentNumber": '45647888',
        "deliveryMode": '快递',
        "oneselfPickGoodsCompany": '深圳市xx公司',
        "oneselfPickGoodsName": '王尼玛',
        "oneselfPickGoodsPhone": '1335564984',
        "idNumber": '335456465456454',
        "deliveryCompany": '深圳市xx公司',
        "contactsName": '皮特',
        "contactsPhone": '1234156456',
        "deliveryAddress": '深圳市福田区xx中心',
        "freightMode": '垫付',
        "freightType": '平均收费',
        "expressCardNumber": 'cd546546545',
        "logisticsCompany": '联运通物流公司',
        "predictDeliveryGoodsDate": '2019-02-20',
        "receivableAmount": '3000',
        "Currency": 'USD',
        "expressReceipt": '1',
        "attachBill": '1',
        "insurance": '1',
        "remarks": '备注',
        "fileList": [
            {
                fileId: 'zd5445668',
                fileName: '订单确认书',
                fileType: 'doc'
            },
            {
                fileId: 'zd5445668',
                fileName: '需求确认书',
                fileType: 'doc'
            }
        ],
        "deliveryGoodsDetailList": [
            {
                "id": 'xxx123123',
                "orderNumber": '78989413',
                "productName": '电容',
                "typeNumber": 'NHK200',
                "orderAmount": '200',
                "deliveryGoodsAmount": '150',
                "roughWeight": '200'
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

### 3.派货单详情

- 请求参数

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pickGoodsOrderId|派货单ID|派货单ID|

- 响应参数

|响应参数|名称|说明|
| :----: | :----: | :----: |
|saveDeliveryGoodsOrderData|派货单数据|同新增派货单中保存接口数据|


- 响应JSON结构

```
{
    "saveDeliveryGoodsOrderData": {
        "saveStatus": '保存/提交',
        "id": '5565678',
        "documentNumber": '45647888',
        "deliveryMode": '快递',
        "oneselfPickGoodsCompany": '深圳市xx公司',
        "oneselfPickGoodsName": '王尼玛',
        "oneselfPickGoodsPhone": '1335564984',
        "idNumber": '335456465456454',
        "deliveryCompany": '深圳市xx公司',
        "contactsName": '皮特',
        "contactsPhone": '1234156456',
        "deliveryAddress": '深圳市福田区xx中心',
        "freightMode": '垫付',
        "freightType": '平均收费',
        "expressCardNumber": 'cd546546545',
        "logisticsCompany": '联运通物流公司',
        "predictDeliveryGoodsDate": '2019-02-20',
        "receivableAmount": '3000',
        "Currency": 'USD',
        "expressReceipt": '1',
        "attachBill": '1',
        "insurance": '1',
        "remarks": '备注',
        "fileList": [
            {
                fileId: 'zd5445668',
                fileName: '订单确认书',
                fileType: 'doc'
            },
            {
                fileId: 'zd5445668',
                fileName: '需求确认书',
                fileType: 'doc'
            }
        ],
        "deliveryGoodsDetailList": [
            {
                "id": 'xxx123123',
                "orderNumber": '78989413',
                "productName": '电容',
                "typeNumber": 'NHK200',
                "orderAmount": '200',
                "deliveryGoodsAmount": '150',
                "roughWeight": '200'
            }
        ]
    }
}
```

## 三.付款委托
### 1.付款委托列表


- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageCount|当前页数|当前页数|
|keyword|查询关键字|查询关键字|
|startDate|起始日期|查询对应起始日期后的订单|
|endDate|结束日期|查询对应结束日期前的订单|
|status|查询状态|查询对应状态订单|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|条目id|
|orderNumber|订单号|订单号|
|gatheringCompany|收款公司|收款公司|
|predictGatheringTime|预计收款时间|预计收款时间|
|paymentAmount|付款金额|付款金额|
|gatheringBank|收款银行|收款银行|
|createTime|创建时间|创建时间|
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
                "predictGatheringTime": '2019-02-20',
                "gatheringCompany": '深圳市xx有限公司',
                "paymentAmount": '10000',
                "gatheringBank": '花旗银行',
                "createTime": '2019-02-20',
                "status": '待付款',
                "remarks": '无'
            },
            {
                "id": '2',
                "orderNumber": '66222223',
                "predictGatheringTime": '2019-02-20',
                "gatheringCompany": '深圳市xx有限公司',
                "paymentAmount": '10000',
                "gatheringBank": '花旗银行',
                "createTime": '2019-02-20',
                "status": '已付款',
                "remarks": '无'
            },
        ]
    }
}
```

### 2.付款委托申请
##### 2.1 获取单据ID

##### 2.2 获取单据编号

##### 2.3 新增垫资付款自动带出接口

##### 2.4 保存/提交提货明细


- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|saveStatus|保存状态|标记当前提货单保存状态/提交状态, 文本值 保存/提交|
|id|id|id|
|documentNumber|单据编号|单据编号|
|orderNumber|订单号|订单号|
|sum|金额|金额|
|bank|银行|银行|
|bankAccount|账号|银行账号|
|predictGatheringTime|预计到款时间|预计到款时间|
|remarks|备注|备注|
|fileList|附件列表|附件列表, 数组字符串类型, 数组内存储多个文件ID|
|fileName|文件名称|附件列表, 单个文件的文件名称|
|fileId|文件ID|附件列表, 单个文件的文件ID|
|fileType|文件类型|附件列表, 单个文件的文件类型|


- 请求JSON结构

```
{
    "saveAdvancePaymentData": {
        "saveStatus": '保存/提交',
        "id": '5565678',
        "documentNumber": '45647888',
        "orderNumber": '45646647888',
        "sum": '60000',
        "bank": '中国建设银行',
        "bankAccount": '45645646545777888',
        "predictGatheringTime": '2019-02-20',
        "remarks": '备注',
        "fileList": [
            {
                fileId: 'zd5445668',
                fileName: '垫资申请书',
                fileType: 'doc'
            },
            {
                fileId: 'zd5445668',
                fileName: '垫资确认书',
                fileType: 'doc'
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

### 3.付款委托详情
##### 3.1 获取订单详情数据
- 请求参数

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|advancePaymentOrderId|委托垫资付款单ID|委托垫资付款单ID|

- 响应参数

|响应参数|名称|说明|
| :----: | :----: | :----: |
|saveAdvancePaymentData|委托垫资付款数据|同新增委托垫资付款保存接口数据|


- 响应JSON结构

```
{
    "saveAdvancePaymentData": {
        "saveStatus": '保存/提交',
        "id": '5565678',
        "documentNumber": '45647888',
        "orderNumber": '45646647888',
        "sum": '60000',
        "bank": '中国建设银行',
        "bankAccount": '45645646545777888',
        "predictGatheringTime": '2019-02-20',
        "remarks": '备注',
        "fileList": [
            {
                fileId: 'zd5445668',
                fileName: '垫资申请书',
                fileType: 'doc'
            },
            {
                fileId: 'zd5445668',
                fileName: '垫资确认书',
                fileType: 'doc'
            }
        ]
    }
}
```



