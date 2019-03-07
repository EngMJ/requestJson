#  出口请求结构
## 一.物流派单
### 1.提货单查询/列表

- 请求地址: /api/export/logistics/pickingorder/list
- 请求类型 POST


- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageCount|当前页数|当前页数|
|gatherSelcondition|查询关键字|查询关键字|
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
|predictPickGoodsTime|预计提货时间|预计提货时间|
|pickGoodsCompany|提货公司|提货公司|
|sumBoard|板数|板数|
|sumCartons|箱数|箱数|
|~~quantity~~|~~数量~~|~~数量~~|
| ~~unit~~ | ~~单位~~ | ~~单位--暂时不需要因为现实箱号和板号了~~ |
|status|状态|订单状态|
|remarks|备注|备注|
|pickingType|提货类型|提货类型 0-有单 1-无单|
- 响应JSON结构



```
{
"result": "success",
"cause": "查询数据成功!",
    "data": {
    "total": 17,
        "list": [
            {
            "id": "858960C2-2117-4959-9F87-5D19457B813F",
            "orderNumber": "FB180600954",
            "pickGoodsNumber": "TH180601004-01",
            "createDate": "2018-06-22 18:07:51.02",
            "predictPickGoodsTime": "2018-06-22 20时",
            "pickGoodsCompany": "深圳市冠群电子有限公司",
            "contactsName": null,
            "contactsPhone": null,
            "pickGoodsAddress": null,
            "sumCartons": "93",
            "sumBoard": "2",
            "unit": null,
            "status": "2",
            "remarks": null,
            "customId": null,
            "basb001d6oid": null,
            "pickingType": "0",
            "pickGoodsDetailList": null,
            "fileList": null
            },
            {
            "id": "B81B2B07-EF96-4E69-829F-B48DA35D74DB",
            "orderNumber": "FB180600191",
            "pickGoodsNumber": "TH180600905-01",
            "createDate": "2018-06-21 16:45:23.26",
            "predictPickGoodsTime": "2018-06-21 18时",
            "pickGoodsCompany": "深圳市冠群电子有限公司",
            "contactsName": null,
            "contactsPhone": null,
            "pickGoodsAddress": null,
            "sumCartons": "39",
            "sumBoard": "2",
            "unit": null,
            "status": "2",
            "remarks": null,
            "customId": null,
            "basb001d6oid": null,
            "pickingType": "0",
            "pickGoodsDetailList": null,
            "fileList": null
            }
        ]
    }
}
```
### 2.新增提货单
##### 2.1 获取单据ID

##### 2.2 获取单据编号---此接口在后台取号


- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|documentNumber|单据编号|单据编号|

- 响应JSON结构

```
{
    "result": 'success',
    "documentNumber": '7878s87szzzzz'
}
```


##### 2.3 提货公司列表

- 请求地址;/api/export/logistics/pickingcompany/list
- 请求类型 GET

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|提货公司列表内单项ID|提货公司列表内单项ID|
|pickGoodsCompany|提货公司|单据编号|
|contactsName|联系人姓名|联系人姓名|
|contactsPhone|联系人电话|联系人电话|
|pickGoodsAddress|提货地址|提货地址|
|boardAmount|板数|板数|
|boxAmount|箱数|箱数|

- 响应JSON结构

```
{
    "result": "success",
    "cause": "查询数据成功!",
    "data":[
        {
            "id": "0003742F-0000-0000-0000-000001FA2679",
            "pickGoodsCompany": "深圳市冠群电子有限公司",
            "contactsName": "罗文伟 13530581115",
            "contactsPhone": "罗文伟 13530581115",
            "pickGoodsAddress": "深圳市龙华新区观澜大富工业区鹏龙蟠高科技园A栋3楼"
        }
    ]
}
```

##### 2.4 提货明细列表

- 请求地址:/api/export/logistics/maypickingorder/list
- 请求类型 POST

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|pageSize|查询长度|一页显示多少条|
|pageCount|当前页数|当前页数|
|gatherSelcondition|关键字|订单号/品名关键字|

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
    "result": "success",
    "cause": "查询数据成功!",
    "data": {
        "total": 1,
        "list": [
                  {
                    "id": null,
                    "orderNumber": "FB190200136",
                    "productName": "手机主板",
                    "typeNumber": "S986-C",
                    "orderAmount": "185.00",
                    "pickGoodsAmount": null,
                    "mayPickGoodsAmount": "185.00",
                    "boxAmount": null,
                    "orderDate": null,
                    "unit": "个",
                    "roughWeight": "4.750",
                    "orderId": "0004E0EC-0000-0000-0000-0000356201B3",
                    "orderDetailId": "0D591FDD-2B5F-482A-B999-95CB1C69D9B3"
                  }
            ]
    }
}
```
##### 2.6 删除出口提货单

- 请求地址;/api/export/logistics/pickingorder/delete
- 请求类型 POST

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|id|提货明细主键|提货明细主键|


- 请求JSON结构
```
{
"id":"C4E7CD44-F830-41F5-A55E-3F0E08BDA366",
"type":"0"
}

```
- 响应JSON说明
```
{
"result": "success",
"cause": "删除数成功!",
"data": "已删除1条数据"
}
```


##### 2.6 删除提货明细

- 请求地址;/api/export/logistics/pickingorderdetails/delete
- 请求类型 POST

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|id|提货明细主键|提货明细主键|
|type|提货类型|0-有单,1-无单|

- 请求JSON结构
```
{
    "id":"2F175294-625F-463A-B14B-FB35599C824E,54847A3E-2E7E-4F3C-BCDD-29EFD7CDEFC1",
    "type":"0"
}

```
- 响应JSON说明
```
{
    "result": "success",
    "cause": "删除数成功!",
    "data": "已删除2条数据"
}
```


##### 2.7 保存/提交提货明细

- 请求地址;/api/export/logistics/pickingorder/save
- 请求类型 POST

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|status|保存状态|标记当前提货单保存状态/提交状态, 文本值 0=保存/ 1=提交|
|id|id|id|
|documentNumber|单据编号|单据编号--在新增的时候先去掉|
|pickGoodsCompany|提货公司|提货公司名称|
|contactsName|联系人姓名|联系人名称|
|contactsPhone|联系人电话|联系人电话|
|pickGoodsAddress|提货地址|提货地址|
|sumBoard|板数|板数-->修改前boardAmount|
|sumCartons|箱数|箱数-->修改前boxAmount|
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
    "status": "0",
    "id": "DDD90720-2C71-4961-A3FF-1A0068922F37",
    "pickGoodsCompany": "深圳市扫描王公司",
    "contactsName": "皮特",
    "contactsPhone": "13332145646",
    "pickGoodsAddress": "深圳市福田区xx中心",
    "orderNumber": "FB190200136",
    "sumBoard": "50",
    "sumCartons": "50",
    "predictPickGoodsTime": "2018-06-22 20时",
    "remarks": "备注",
    "basb001d6oid": "4D158D6A-B736-4187-B42E-34E65CA704CC",
    "pickGoodsDetailList": [
        {
        "id": "xxx123123",
        "pickGoodsAmount": "1",
        "orderId": "0004E0EC-0000-0000-0000-0000356201B3",
        "orderDetailId": "0D591FDD-2B5F-482A-B999-95CB1C69D9B3"
        }
    ],
    "fileList": [
        {
        "fileId": "zd5445668",
        "fileName": "订单确认书",
        "fileType": "doc"
        },
        {
        "fileId": "zd5445668",
        "fileName": "需求确认书",
        "fileType": "doc"
        }
    ]
}
```

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|msg|msg|信息|

- 响应JSON结构

```
{
    "result": "success",
    "cause": "保存数据成功!",
    "data": "已保存1条数据"
}
```

### 3.提货单详情

##### 3.1 获取提货单详情

- 请求地址:api/export/logistics/pickingorder/object
- 请求类型 GET

- 请求参数

|响应参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|id|提货单ID|提货单ID|
|pickingtype|提货单ID|提货单ID 0:有单,1:无单|
- 响应参数

|响应参数|名称|说明|
| :----: | :----: | :----: |
|savePickGoodsOrderData|提货单数据|同新增提货单中保存接口数据|


- 响应JSON结构

```
{
"result": "success",
"cause": "查询数据成功!",
"data": {
"id": "858960C2-2117-4959-9F87-5D19457B813F",
"orderNumber": null,
"pickGoodsNumber": null,
"createDate": null,
"predictPickGoodsTime": "2018-06-22 20时",
"pickGoodsCompany": "深圳市冠群电子有限公司",
"contactsName": "罗文伟 13530581115",
"contactsPhone": "罗文伟 13530581115",
"pickGoodsAddress": "深圳市龙华新区观澜大富工业区鹏龙蟠高科技园A栋3楼",
"sumCartons": "93",
"sumBoard": "2",
"unit": null,
"status": null,
"remarks": null,
"customId": null,
"basb001d6oid": null,
"pickingType": null,
 "pickGoodsDetailList": [
        {
        "id": "95F46A19-98E6-4DDE-A0A9-00DD1EA4E571",
        "orderNumber": "FB180600954",
        "productName": "WCDMA/GSM手机",
        "typeNumber": "S7（2G+16G）",
        "orderAmount": "780.00",
        "pickGoodsAmount": "780.00",
        "mayPickGoodsAmount": null,
        "boxAmount": null,
        "orderDate": null,
        "unit": null,
        "roughWeight": null,
        "orderId": null,
        "orderDetailId": null
        }
  ],
  "fileList": [
        {
        "id": "000E2339-0000-0000-0000-000026F05ED8",
        "fileName": "富森出口货物确认单20180622-FB180600954.xls",
        "fileId": "SHPC/10c7b7ed-6312-44c3-8ad9-135cb73d7b75.xls",
        "orderId": "858960C2-2117-4959-9F87-5D19457B813F",
        "createDate": "2018-06-22 18:08:51.0",
        "lastUpDate": "2018-06-22 18:09:10.0",
        "fileType": "xls",
        "fTypeName": null
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
|gatherSelcondition|查询关键字|查询关键字|
|startDate|起始日期|查询对应起始日期后的订单|
|endDate|结束日期|查询对应结束日期前的订单|
|status|查询状态|查询对应状态订单-->暂时没有添加这个搜索|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|条目id|
|fusenOrder|订单号|订单号|
|sendNo|派货单号|派货单号|
|logisticsCompany|物流公司|物流公司|
|fcDate|预计派货时间|预计派货时间|
|sendCompany|送达公司|送达公司|
|shipmentType|出货方式|出货方式|
|status|状态|订单状态|
|remarks|备注|备注|

- 响应JSON结构

```
{
    "result": "success",
    "cause": "查询数据成功!",
    "data": {
        "total": 64,
        "list": [
            {
                "id": "3E22BEE7-4C18-4103-9042-EE1608FE8307",
                "createDate": null,
                "fusenOrder": "FB180600954",
                "sendNo": "PH180610769",
                "sendGoodOrder": null,
                "logisticsCompany": null,
                "fcTime": null,
                "shipmentType": "送货",
                "signOrder": null,
                "bill": null,
                "insure": null,
                "custId": null,
                "fcDate": null,
                "basb001FkWl": null,
                "shipFeeType": null,
                "carFreight": null,
                "rcvAmt": null,
                "currency": null,
                "status": "已派货",
                "remark": "散交；入仓号：18060267AES；跟骐驷FB180601007/1008一起交；请安排6-23交仓，交仓后请提供签收单，提前联系；",
                "customId": null,
                "shipmentTypeFk": null,
                "sendCompany": "深圳市冠群电子有限公司",
                "linkMan": null,
                "linkPhone": null,
                "iDCard": null,
                "provinceName": null,
                "cityName": null,
                "countyName": null,
                "address": null,
                "express_type": null,
                "logisticsway": null,
                "goods": null,
                "file": null,
                "total": null
            },
            {
                "id": "0D26A7D7-6813-4078-B05A-F79B4A9BE1D6",
                "createDate": null,
                "fusenOrder": "FB180600191",
                "sendNo": "PH180610324",
                "sendGoodOrder": null,
                "logisticsCompany": null,
                "fcTime": null,
                "shipmentType": "送货",
                "signOrder": null,
                "bill": null,
                "insure": null,
                "custId": null,
                "fcDate": null,
                "basb001FkWl": null,
                "shipFeeType": null,
                "carFreight": null,
                "rcvAmt": null,
                "currency": null,
                "status": "已派货",
                "remark": "散交；入仓号：1806140018；跟骐驷FB180600972一起交；请安排6-22交仓，交仓后请提供签收单，提前联系；",
                "customId": null,
                "shipmentTypeFk": null,
                "sendCompany": "深圳市冠群电子有限公司",
                "linkMan": null,
                "linkPhone": null,
                "iDCard": null,
                "provinceName": null,
                "cityName": null,
                "countyName": null,
                "address": null,
                "express_type": null,
                "logisticsway": null,
                "goods": null,
                "file": null,
                "total": null
            }
        ]
    }
}
```

### 2.派货单新增

##### 2.1 获取单据ID

##### 2.2 获取单据编号-->暂时不需要取

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|documentNumber|单据编号|单据编号|

- 响应JSON结构

```
{
    "result": 'success',
    "documentNumber": '7878s87szzzzz'
}
```

##### 2.3 物流公司列表

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|logisticsCompanyList|物流公司列表|物流公司列表|

- 响应JSON结构

```
{
    "result": 'success',
    "logisticsCompanyList": [
        '顺丰物流',
        '京东物流'
    ]
}
```

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
- 请求地址:/api/export/logistics/sendgoods/object
- 请求类型:GET

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionid|sessionId|sessionId|
|id|派货单ID|派货单ID|

- 响应参数

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|派货单主键ID|
|createDate|创建时间|派货单创建时间|
|sendNo|派货单|派货单|
|shipmentType|出货方式|出货方式|
|basb001FkWl|物流公司外键|物流公司外键|
|shipFeeType|运费方式|运费方式|
|remark|备注|备注|
|sendCompany|送达公司|送达公司|
|linkMan|联系人|联系人|
|linkPhone|联系电话|联系电话|
|iDCard|身份证|身份证|
|provinceName|省|省|
|cityName|市|市|
|countyName|区|区|
|address|详细地址|详细地址|
|shipperType|发货方|发货方|
|passNameType|清关|清关|
|fcDate|预计送达日期|预计送达日期|
|status|状态|状态|
|custId|快递月结卡号|快递月结卡号|
|id|id|派货单明细主键ID|
|partName|品名|品名|
|fusenOrder|富森订单号|富森订单号|
|model|型号|型号|
|quantity|订单数量|订单数量|
|ksendQty|可发货数量|可发货数量|
|sendQty|派货数量|派货数量|
|grossWeight|可发货数量|可发货数量|
|id|id|文件主键ID|
|fileName|文件名称|文件名称|
|fileId|fileId|MongoDB 返回来的文件Id|


- 响应JSON结构

```
{
    "result": "success",
    "cause": "查询数据成功!",
    "data": {
        "id": "CF99BF73-3283-40B8-AA43-A16EBB876CC5",
        "createDate": null,
        "fusenOrder": null,
        "sendNo": "PH180900005",
        "sendGoodOrder": null,
        "logisticsCompany": null,
        "fcTime": null,
        "shipmentType": "送货",
        "signOrder": "0",
        "bill": "0",
        "insure": "0",
        "custId": null,
        "fcDate": null,
        "basb001FkWl": "412ACD32-EA1E-4B69-91A3-5E729A2DF959",
        "shipFeeType": "2",
        "carFreight": "2",
        "rcvAmt": null,
        "currency": null,
        "status": null,
        "remark": "；",
        "customId": null,
        "shipmentTypeFk": null,
        "sendCompany": "禾苗通信科技（香港）有限公司",
        "linkMan": "0",
        "linkPhone": "31195380",
        "iDCard": null,
        "provinceName": "香港",
        "cityName": null,
        "countyName": null,
        "address": "香港九龙长沙湾道72号昌明大厦8楼B室",
        "express_type": null,
        "logisticsway": "送货",
        "shipperType": "2",
        "passNameType": "1",
        "goods": [
                    {
                    "id": "FA511681-AC6F-401F-8888-79DC51EB2A7E",
                    "partName": "4G手机整套散件",
                    "fusenOrder": "FB180601152",
                    "model": "Q402+（屏4.0寸）",
                    "quantity": "10000.00",
                    "sendQty": "10000.00",
                    "ksendQty": "0.00",
                    "grossWeight": "2882.000",
                    "carton": null,
                    "unit": null,
                    "price": null,
                    "declDate": null,
                    "orderId": null,
                    "goodsId": null,
                    "sendOrderId": null
                    }
        ],
        "file": [
                    {
                    "id": "4EED76AA-BB5D-42E7-94CF-E735FC75AA7B",
                    "fileName": "test文件.txt",
                    "fileId": "testfinlID412341234",
                    "orderId": "CF99BF73-3283-40B8-AA43-A16EBB876CC5",
                    "createDate": "2019-03-06 15:16:49.84",
                    "lastUpDate": "2019-03-06 15:16:49.84",
                    "fileType": "txt",
                    "fTypeName": null
                    }
        ],
        "total": null
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

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|documentNumber|单据编号|单据编号|

- 响应JSON结构

```
{
    "result": 'success',
    "documentNumber": '7878s87szzzzz'
}
```

##### 2.3 新增垫资付款自动带出接口

- 请求参数说明

|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|

- 响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|bank|银行|银行|
|bankAccount|账号|银行账号|

- 响应JSON结构

```
{
    "result": 'success',
    "carryData": {
        "bank": '中国建设银行',
        "bankAccount": '465465456'
    }
}
```

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
|producer|制单人|制单人姓名|
|produceTime|制单时间|制单时间|


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
        "producer": '小张',
        "produceTime": '2019-02-20',
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

##  二.订单操作
### 1.订单详情查询

- 请求地址:
/api/export/order/orderinfo/object


|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|id|订单主键|查询对应的订单明细|

- (订单主表)响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|orderId|订单主键|订单主键|
|customId|客户Id|客户表主键|
|fusenOrder|订单号|订单号|
|orderId|订单号ID|订单号主键|
|customOrder|客户单号|客户单号|
|exportBuyer|海外客户|海外客户|
|supplier|国内供应商|国内供应商|
|basa019Id|目的国外键|目的国外键|
|orderCurrency|订单币别|订单币别|
|basa020Id|币别外键|币别外键|
|recWay|收货方式|收货方式|
|settlements|结算方式|结算方式|
|status|订单状态|订单状态|
|declDate|报关时间|报关时间|
|amount|订单金额（原币）|订单金额（原币）|
|declAmount|报关金额|报关金额|
|cstamte|已报关金额|已报关金额|
|logisticsStatus|物流状态|物流状态|
|quality|总数量|总数量|
|originalPacNum|总箱数|总箱数|
|remark|备注|备注|
|comfirmbookUrl|订单确认书|订单确认书|
|orderrate|订单汇率|订单汇率 获取当天汇率|
|customscrate|海关汇率|海关汇率 获取当月海关汇率|
|busitype|业务类型|业务类型|
|orderstatusnew|订单状态20|订单状态20|
|orderstatus|订单状态30|订单状态30|
|cwarehousename|报关仓库名称|报关仓库名称|

- (订单明细)响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|订单明细主键|
|productName|品名|品名|
|model|型号|型号|
|parts|配件|配件|
|unit|单位|单位|
|unitPrice|单价|单价|
|quality|数量|数量|
|recQty|已收数量|已收数量|
|declareQty|报关数量|报关数量|
|preSendQty|发货数量|发货数量|
|declAmount|报关金额|报关金额|
|brand|品牌|品牌|
|origin|产地|产地|
|pacNum|箱数|箱数|
|oriNetWeight|净重|净重|
|oriGrossWeight|毛重|毛重|
|ordb001Id|Paking明细外键|Paking明细外键|

- (附件明细)响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|文件主键ID|文件主键ID|
|fileName|文件名称|文件名称|
|fileId|文件ID|MongoDB 返回来的文件Id|
|orderId|订单Id|订单Id|
|createDate|创建时间|创建时间|
|fileType|文件类型 (后缀)|文件类型 (后缀)|

- (备品清单)响应参数说明

|响应参数|名称|说明|
| :----: | :----: | :----: |
|id|id|备品清单ID|
|productName|品名|品名|
|qty|数量|数量|
|unit|单位|单位|
|grossweight|毛重|毛重|
|netweight|净重|净重|
|boxnum|箱数|箱数|


- 响应JSON结构
```
{
"result": "success",
"data": {
"orderId": "0004E0EC-0000-0000-0000-0000356201B2",
"createDate": null,
"customId": null,
"fusenOrder": null,
"exportBuyer": "NEW-BUND TECHNOLOGY CO., LIMITED",
"supplier": null,
"basa019Id": "5429CA6D-CAAD-4E59-9890-279C5C60CDB8",
"orderCurrency": null,
"basa020Id": "8700A79F-371D-4347-A7B3-10826518AB9F",
"recWay": "2",
"customOrder": null,
"settlements": null,
"status": null,
"declDate": null,
"amount": null,
"declAmount": null,
"cstamte": null,
"logisticsStatus": null,
"quality": null,
"originalPacNum": null,
"remark": null,
"goodsinfo": [
{
"id": "E94E4F5C-3431-4B77-9F98-3772749294FD",
"productName": "手机主板",
"model": "S986-C",
"parts": "内存型号：KM3H6001CM-B515",
"unit": "个",
"unitPrice": 97,
"quality": 185,
"recQty": null,
"declareQty": null,
"preSendQty": null,
"declAmount": "17945.00000000",
"brand": "无牌/安科利通讯设备(深圳)有限公司",
"origin": "中国",
"pacNum": "2",
"oriNetWeight": "1.670",
"oriGrossWeight": "4.750",
"ordb001Id": "00034650-0000-0000-0000-000035624573"
}
],
"file": [
{
"id": "B83E8405-697B-4BC0-A5EE-AB8EFE9C2EA8",
"fileName": "格平.pdf",
"fileId": "5c25a1e2ea1c9c6cabd31bd8",
"orderId": "0004E0EC-0000-0000-0000-0000356201B2",
"createDate": "2019-02-25T07:47:32.740+0000",
"lastUpDate": "2019-02-25T07:47:32.740+0000",
"fileType": "pdf",
"fTypeName": ""
}
],
"spare": [
{
"partname": "马达",
"qty": "292.00",
"unit": "个",
"grossweight": "2.660",
"netweight": "2.210",
"boxnum": "3.00"
}
]
}
}
```

### 1.保存订单

- 请求地址:
/api/export/order/orderinfo/save


|请求参数|名称|说明|
| :----: | :----: | :----: |
|sessionId|sessionId|sessionId|
|orderId|订单主键|订单主键|
|fusenOrder|订单号|订单号|
|customOrder|客户单号|客户单号|
|exportBuyer|海外客户|海外客户|
|supplier|国内供应商|国内供应商|
|basa019Id|目的国外键|目的国外键|
|orderCurrency|订单币别|订单币别|
|basa020Id|币别外键|币别外键|
|settlements|结算方式|结算方式|
|status|订单状态|订单状态|
|amount|订单金额（原币）|订单金额（原币）|
|remark|备注|备注|
|productName|品名|品名|
|model|型号|型号|
|parts|配件|配件|
|unit|单位|单位|
|unitPrice|单价|单价|
|quality|数量|数量|
|~~declAmount~~|~~报关金额~~|~~报关金额~~|
|brand|品牌|品牌|
|origin|产地|产地|
|pacNum|箱数|箱数|
|oriNetWeight|净重|净重|
|oriGrossWeight|毛重|毛重|
|fileName|文件名称|文件名称|
|fileId|文件ID|MongoDB 返回来的文件Id|
|fileType|文件类型 (后缀)|文件类型 (后缀)|

- 响应JSON结构

```
{
    "orderId": "0004E0EC-0000-0000-0000-0000356201B4",
    "fusenOrder": "FB190200136",
    "exportBuyer": "NEW-BUND TECHNOLOGY CO., LIMITED",
    "supplier": "KAILINUO(HK） TECHNOLOGY  CO., LIMITED",
    "basa019Id": "5429CA6D-CAAD-4E59-9890-279C5C60CDB8",
    "orderCurrency": "USD",
    "basa020Id": "8700A79F-371D-4347-A7B3-10826518AB9F",
    "recWay": "2",
    "customOrder": "E2413LV(SKD)-01",
    "settlements": "LC",
    "settletype":"1",
    "status": "0",
    "amount": "10000.00",
    "remark": "出口订单测试一",
"goodsinfo":
    [
        {
        "productName": "手机主板",
        "model": "S986-C",
        "parts": "内存型号：KM3H6001CM-B515",
        "unit": "个",
        "unitPrice": 97,
        "quality": 185,
        "declAmount": "17945.00000000",
        "brand": "无牌/安科利通讯设备(深圳)有限公司",
        "origin": "中国",
        "pacNum": "2",
        "oriNetWeight": "1.670",
        "oriGrossWeight": "4.750"
        }
    ],
"file":
    [
        {
        "fileName": "格平.pdf",
        "fileId": "5c25a1e2ea1c9c6cabd31bd8",
        "fileType": "pdf"
        }
    ],
"spare":
    [
        {
        "partname": "马达",
        "qty": "292.00",
        "unit": "个",
        "grossweight": "2.660",
        "netweight": "2.210",
        "boxnum": "3.00"
        }
    ]
}

```
