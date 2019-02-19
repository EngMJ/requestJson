##  出口请求结构
#### 物流派单
> 1.提货单查询/列表

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
> 2.新增提货单
```
{
    "data": [
        {
            "id": 'id'
        }
    ]
}
```
> 3.提货单详情
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


