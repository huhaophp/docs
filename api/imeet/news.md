# 快讯

## 快讯列表

**方式**

`GET`

**路径**

`/api/news`

**参数**

|  名称  |  类型  | 必须 |                                   说明                                    |
| :----: | :----: | :--: | :-----------------------------------------------------------------------: |
| limit | int |  是  |             条目数 默认20                      |
| after | int |  是  |             最后一条数据id                   |

**响应**

`Status code 200`

```json
{
    "msg": "ok",
    "code": 0,
    "data": [
        {
            "id": 30,
            "title": "标题",/*标题*/
            "content": "内容",/*内容*/
            "original_link": null,/*快讯链接地址*/
            "bad_vote": 1,/*利空数量*/
            "bull_vote": 0,/*利好数量*/
            "created_at": "2019-10-08 15:20:30",/*时间*/
            "voted_type": 2 /*投票类型: 0-未投票 1-利好 2-利空*/
        },
    ]
}
```

## 快讯投票

**方式**

`POST`

**路径**

`/api/news/:id/vote`

`id 为 快讯列表 id`

**参数**

|  名称  |  类型  | 必须 |  说明  |
| :----: | :----: | :--: | :-----------------: |
| type | int |  是  | 1-利好 2-利空 |

**响应**

`Status code 200`

```json
{
    "msg": "操作成功",
    "code": 0,
    "data": null
}
```