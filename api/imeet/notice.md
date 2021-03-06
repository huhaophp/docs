# 消息通知

## 消息参数说明

|  参数标识  |      说明       |
| :----: | :-------------: |
|  111111  |    系统消息环信id    |
|  222222  |    通知消息环信id    |
|  333333  |    动态消息环信id    |
| ADD:FRIEND:APPLY   |  透传消息：添加好友   |
| UPDATE:GROUP:NOTIFY |    透传消息：修改社群信息  |
| PASS:FRIEND:APPLY |    透传消息：同意好友申请  |
| DELETE:FRIEND |    透传消息：删除好友通知  扩展字段 `body` 为目标用户 `id` |
| SILENCE   |  透传消息：群内设置禁言   |
| group:quitCommunity   |  消息通知：社群退出社区   |
| plaza:submit:reject   |  消息通知：驳回广场任务提交   |


## 消息列表

**方式**

`GET`

**路径**

`/api/notify/messages`

**参数**

|  名称  |  类型  | 必须 | 说明  |
| :----: | :----: | :--: | :----: |
| type | string |  是  | remind-动态通知, message-消息通知, system-系统通知, new:dynamic-新动态提醒消息 |
| remind_type | int |  否  | 1-回复评论提醒 2-点赞收藏提醒,如 `type` 为 `remind` 必传  |
| offset | string |  是  | 偏移量 默认0 |
| limit | string |  是  | 条目数 默认20|

**响应**

`Status code 200`

**动态提醒**

```json
{
    "msg": "ok",
    "code": 0,
    "data": [
        {
            "id": 3,
            "target_id": 1,
            "body": {
                "action": "dynamic:collect",/*动态收藏*/
                "dynamic": {
                    "id": 1,
                    "content": "哈哈哈哈",
                    "video": null,
                    "images": null,
                    "location": null,
                    "type": 1
                }
            },
            "target_type": "dynamic",
            "sender_id": 3,
            "created_at": "2019-06-29 10:13:59",
            "sender": {
                "id": 3,
                "name": "eric",
                "avatar": null,
                "sex": 0,
                "number": null
            }
        },
        {
            "id": 2,
            "target_id": 1,
            "body": {
                "action": "dynamic:like",/*动态点赞*/
                "dynamic": {
                    "id": 1,
                    "content": "哈哈哈哈",
                    "video": null,
                    "images": null,
                    "location": null,
                    "type": 1
                }
            },
            "target_type": "dynamic",
            "sender_id": 3,
            "created_at": "2019-06-29 10:12:59",
            "sender": {
                "id": 3,
                "name": "eric",
                "avatar": null,
                "sex": 0,
                "number": null
            }
        },
        {
            "id": 2,
            "target_id": 1,
            "body": {
                "action": "dynamic:comment",/*动态评论*/
                "dynamic": {
                    "id": 1,
                    "content": "哈哈哈哈",
                    "video": null,
                    "images": null,
                    "location": null,
                    "type": 1
                },
                "comment": {
                    "id": 1,
                    "content": "哈哈哈哈"/*评论内容*/
                }
            },
            "target_type": "dynamic",
            "sender_id": 3,
            "created_at": "2019-06-29 10:12:59",/*时间*/
            /*评论人*/
            "sender": {
                "id": 3,
                "name": "eric",
                "avatar": null,
                "sex": 0,
                "number": null
            }
        },
        {
            "id": 2,
            "target_id": 1,
            "body": {
                "action": "dynamic:comment:reply",/*动态评论回复*/
                "dynamic": {
                    "id": 1,
                    "content": "哈哈哈哈",
                    "video": null,
                    "images": null,
                    "location": null,
                    "type": 1
                },
                /*评论内容*/
                "comment": {
                    "id": 1,
                    "content": "哈哈哈哈"/*评论内容*/
                },
                /*回复内容*/
                "reply": {
                    "id": 1,
                    "content": "哈哈哈哈"/*评论内容*/
                }
            },
            "target_type": "dynamic",
            "sender_id": 3,
            "created_at": "2019-06-29 10:12:59",/*时间*/
            /*评论人*/
            "sender": {
                "id": 3,
                "name": "eric",
                "avatar": null,
                "sex": 0,
                "number": null
            }
        },
        {
            "id": 2,
            "target_id": 1,
            "body": {
                "action": "dynamic:reply:like",/*动态回复点赞*/
                "dynamic": {
                    "id": 1,
                    "content": "哈哈哈哈",
                    "video": null,
                    "images": null,
                    "location": null,
                    "type": 1
                },
                /*评论内容*/
                "comment": {
                    "id": 1,
                    "content": "哈哈哈哈"/*评论内容*/
                },
                /*回复内容*/
                "reply": {
                    "id": 1,
                    "content": "哈哈哈哈"/*评论内容*/
                }
            },
            "target_type": "dynamic",
            "sender_id": 3,
            "created_at": "2019-06-29 10:12:59",/*时间*/
            /*评论人*/
            "sender": {
                "id": 3,
                "name": "eric",
                "avatar": null,
                "sex": 0,
                "number": null
            }
        },
        {
            "id": 2,
            "target_id": 1,
            "body": {
                "action": "dynamic:comment:like",/*动态评论点赞*/
                "dynamic": {
                    "id": 1,
                    "content": "哈哈哈哈",
                    "video": null,
                    "images": null,
                    "location": null,
                    "type": 1
                },
                /*评论内容*/
                "comment": {
                    "id": 1,
                    "content": "哈哈哈哈"/*评论内容*/
                },
                /*回复内容*/
                "reply": {
                    "id": 1,
                    "content": "哈哈哈哈"/*评论内容*/
                }
            },
            "target_type": "dynamic",
            "sender_id": 3,
            "created_at": "2019-06-29 10:12:59",/*时间*/
            /*评论人*/
            "sender": {
                "id": 3,
                "name": "eric",
                "avatar": null,
                "sex": 0,
                "number": null
            }
        }
    ]
}
```

**消息通知**

```json
{
    "msg": "ok",
    "code": 0,
    "data": [
        /* 自主申请加群 */
        {
            "id": 1,
            "target_id": 34,
            "body": {
                "from": null,/*来自：邀请/搜索*/
                "type": "apply:add:group",/*申请加群*/
                "remark": null,/*个人介绍*/
                "status": 0,/*0-待处理 1-同意加群 2-拒绝*/
                /*群信息*/
                "group": {
                    "id": 34,
                    "name": "Z63482创建的群聊",
                    "avatar": null
                },
            },
            "target_type": "group",
            "sender_id": 5,
            "read_id": 1,
            "created_at": "2019-06-28 18:28:44",
            /*申请人信息*/
            "sender": {
                "id": 5,
                "name": "Z63482",
                "avatar": null,
                "sex": 0,
                "number": "1295634"
            }
        },
        /* 自主申请加社区 */
        {
            "id": 18,
            "target_id": 11,
            "body": {
                "from": null,/*来源*/
                "type": "apply:add:community",/*申请加入社区*/
                "remark": null,/*申请备注*/
                "status": 1,/*0-待处理 1-同意加群 2-拒绝*/
                "allow_apply": 0,/*是否允许在申请 0-允许 1-不允许*/
                "group_ids": [22],
                /*社区信息*/
                "community": {
                    "id": 11,
                    "name": "我是社区",
                    "avatar": null
                },
                /*带入的社群信息*/
                "groups": [
                    {
                        "id": 22,
                        "name": "我是社群",
                        "avatar": null,
                        "member_count": 0/*成员数*/
                    }
                ]
            },
            "target_type": "group",
            "read_id": 7,
            "sender_id": 3,
            "created_at": "2019-07-03 11:31:35",/*时间*/
            "sender": {
                "id": 3,
                "name": "eric",
                "avatar": null,
                "sex": 0,
                "number": null,
                /*申请人等级信息*/
                "grade": {
                    "name": "青铜",
                    "level": "1",
                    "icon": "NULL",
                    "small_icon": "NULL",
                    "min": 0,
                    "max": 500,
                    "next_name": "白银"
                }
            }
        },
        /* 邀请加入社群 */
        {
            "id": 1,
            "target_id": 34,
            "body": {
                "from": null,/*来自：邀请/搜索*/
                "type": "invite:apply:add:group",/*申请加群*/
                "remark": "申请加入社区",/*个人介绍*/
                "status": 0,/*0-待处理 1-同意加群 2-拒绝*/
                /*群信息*/
                "community": {
                    "id": 34,
                    "name": "Z63482创建的群聊",
                    "avatar": null
                },
                "inviter_name": "邀请人名称",/*邀请人名称*/
                "inviter_id": 111,/*邀请人id*/
            },
            "target_type": "group",
            "sender_id": 5,
            "read_id": 1,
            "created_at": "2019-06-28 18:28:44",
            /*申请人信息*/
            "sender": {
                "id": 5,
                "name": "Z63482",
                "avatar": null,
                "sex": 0,
                "number": "1295634"
            }
        },
        /* 邀请加入社区 */
        {
            "id": 1,
            "target_id": 34,
            "body": {
                "from": null,/*来自：邀请/搜索*/
                "type": "invite:apply:add:community",/*申请加群*/
                "remark": "申请加入社区",/*个人介绍*/
                "status": 0,/*0-待处理 1-同意加群 2-拒绝*/
                /*群信息*/
                "community": {
                    "id": 34,
                    "name": "Z63482创建的群聊",
                    "avatar": null
                },
                "inviter_name": "邀请人名称",/*邀请人名称*/
                "inviter_id": 111,/*邀请人id*/
            },
            "target_type": "group",
            "sender_id": 5,
            "read_id": 1,
            "created_at": "2019-06-28 18:28:44",
            /*申请人信息*/
            "sender": {
                "id": 5,
                "name": "Z63482",
                "avatar": null,
                "sex": 0,
                "number": "1295634"
            }
        },
        /* 拒绝自重加入社群申请 */
        {
            "id": 1,
            "target_id": 34,
            "body": {
                "type": "reject:apply:add:group",/*拒绝自主申请加群*/
                "remark": "拒绝你的加入",/*拒绝备注*/
                "reason": "拒绝的理由",/*字段存在并且不为空做呈现*/
                /*群信息*/
                "group": {
                    "id": 34,
                    "name": "Z63482创建的群聊",
                    "avatar": null
                }
            },
            "target_type": "group",
            "sender_id": 5,
            "read_id": 1,
            "created_at": "2019-06-28 18:28:44",
            /*审核人信息*/
            "sender": {
                "id": 5,
                "name": "Z63482",
                "avatar": null,
                "sex": 0,
                "number": "1295634",
                "grade": {
                    "name": "青铜",
                    "level": "1",
                    "icon": "NULL",
                    "small_icon": "NULL",
                    "min": 0,
                    "max": 500,
                    "next_name": "白银"
                }
            }
        },
        /* 拒绝自主加入社区申请 */
        {
            "id": 1,
            "target_id": 34,
            "body": {
                "type": "reject:apply:add:community",/*拒绝自主申请加群*/
                "remark": "拒绝你的加入",/*拒绝备注*/
                "reason": "拒绝原因",
                /*社区信息*/
                "community": {
                    "id": 34,
                    "name": "Z63482创建的群聊",
                    "avatar": null
                }
            },
            "target_type": "group",
            "sender_id": 5,
            "read_id": 1,
            "created_at": "2019-06-28 18:28:44",
            /*审核人信息*/
            "sender": {
                "id": 5,
                "name": "Z63482",
                "avatar": null,
                "sex": 0,
                "number": "1295634",
                "grade": {
                    "name": "青铜",
                    "level": "1",
                    "icon": "NULL",
                    "small_icon": "NULL",
                    "min": 0,
                    "max": 500,
                    "next_name": "白银"
                }
            }
        },
       /* 拒绝邀请加入社群群申请 */
        {
            "id": 1,
            "target_id": 34,
            "body": {
                "type": "reject:invite:apply:add:group",/*拒绝自主申请加群*/
                "remark": "拒绝你的加入",/*拒绝备注*/
                "reason": "拒绝的理由",/*字段存在并且不为空做呈现*/
                /*群信息*/
                "group": {
                    "id": 34,
                    "name": "Z63482创建的群聊",
                    "avatar": null
                },
                "inviter_name": "邀请人名称",/*邀请人名称*/
                "inviter_id": 1,/*邀请人id*/
            },
            "target_type": "group",
            "sender_id": 5,
            "read_id": 1,
            "created_at": "2019-06-28 18:28:44",
            /*审核人信息*/
            "sender": {
                "id": 5,
                "name": "Z63482",
                "avatar": null,
                "sex": 0,
                "number": "1295634",
                "grade": {
                    "name": "青铜",
                    "level": "1",
                    "icon": "NULL",
                    "small_icon": "NULL",
                    "min": 0,
                    "max": 500,
                    "next_name": "白银"
                }
            }
        },
        /* 拒绝邀请加入社区申请 */
        {
            "id": 1,
            "target_id": 34,
            "body": {
                "type": "reject:invite:apply:add:community",/*拒绝邀请申请加群*/
                "remark": "拒绝你的加入",/*拒绝备注*/
                "reason": "拒绝原因",
                /*社区信息*/
                "community": {
                    "id": 34,
                    "name": "Z63482创建的群聊",
                    "avatar": null
                },
                "inviter_name": "邀请人名称",/*邀请人名称*/
                "inviter_id": 1,/*邀请人id*/
            },
            "target_type": "group",
            "sender_id": 5,
            "read_id": 1,
            "created_at": "2019-06-28 18:28:44",
            /*审核人信息*/
            "sender": {
                "id": 5,
                "name": "Z63482",
                "avatar": null,
                "sex": 0,
                "number": "1295634",
                "grade": {
                    "name": "青铜",
                    "level": "1",
                    "icon": "NULL",
                    "small_icon": "NULL",
                    "min": 0,
                    "max": 500,
                    "next_name": "白银"
                }
            }
        },
        /*一键挖矿特权到期提醒*/
        {
            "id": 18,
            "target_id": 0,
            "body": { 
                "type": "one:key:collection",/*一键挖矿特权*/
                "content":"您的一键挖矿特权即将到期，如需继续使用，请及时续费!",
            },
            "target_type": null,
            "read_id": 7,
            "sender_id": 0,
            "created_at": "2019-07-03 11:31:35",/*时间*/
            "sender": null
        },
        /*转账成功消息*/
        {
            "id": 41,
            "target_id": 5,
            "body": {
                "coin": "ore",/*转账代币类型: ore-矿石*/
                "type": "transfer:success",/*转账成功*/
                "title": "转账成功",/*标题*/
                "amount": "1"/*支付金额*/
            },
            "target_type": "user",
            "read_id": 20,
            "sender_id": 3,
            "created_at": "2019-07-17 14:42:21",
            /*转账目标用户信息*/
            "sender": {
                "id": 3,
                "name": "eric",
                "avatar": null,
                "sex": 0,
                "number": null,
                "grade": {
                    "name": "青铜",
                    "level": "1",
                    "icon": "NULL",
                    "small_icon": "NULL",
                    "min": 0,
                    "max": 500,
                    "next_name": "白银"
                }
            }
        }
        /*收到转账消息*/
        {
            "id": 44,
            "target_id": 5,
            "body": {
                "coin": "ore",/*收到转账代币类型: ore-矿石*/
                "type": "received:transfer",/*收到转账*/
                "title": "你收到一笔转账",/*标题*/
                "amount": "1"/*收入金额*/
            },
            "target_type": "user",
            "read_id": 23,
            "sender_id": 5,
            "created_at": "2019-07-17 14:44:00",
            /*转账人信息*/
            "sender": {
                "id": 5,
                "name": "Z63482",
                "avatar": null,
                "sex": 0,
                "number": "1295634",
                "grade": {
                    "name": "青铜",
                    "level": "1",
                    "icon": "NULL",
                    "small_icon": "NULL",
                    "min": 0,
                    "max": 500,
                    "next_name": "白银"
                }
            }
        },
        /*投诉被驳回*/
        {
            "id": 310,
            "target_id": 10,
            "body": {
                "type": "report:reject",
                "report_info": {
                    "reason": "投诉被驳回",
                    "content": "用户您好，您投诉的内容已通过审!请等待处理结果，感谢您的支持和反馈",/*内容*/
                    "target_id": 88655674802178,
                    "target_type": "group"/*投诉类型:user-用户 task-任务 dynamic-动态 group-群组*/
                }
            },
            "target_type": "report",
            "read_id": 482,
            "sender_id": 0,
            "created_at": "2019-07-26 13:54:40",
            "sender": null
        },
        /*投诉被处理*/
        {
            "id": 309,
            "target_id": 11,
            "body": {
                "type": "report:pass",
                "report_info": {
                    "reason": null,
                    "content": "用户您好，您投诉的内容已通过审!请等待处理结果，感谢您的支持和反馈",
                    "target_id": 88655674802178,
                    "target_type": "group"
                }
            },
            "target_type": "report",
            "read_id": 481,
            "sender_id": 0,
            "created_at": "2019-07-26 13:54:34",
            "sender": null
        },
         /*驳回广场任务提交*/
        {
            "id": 10,
            "target_id": 12,
            "body": {
                "type": "plaza:submit:reject",
                "report_info": {
                    "reason": null,
                    "content": "用户您好，您提交的广场任务《xxx》未通过审核，驳回原因: xxx。",
                    "target_id": 13,
                    "target_type": "task"
                }
            },
            "target_type": "task",
            "read_id": 481,
            "sender_id": 0,
            "created_at": "2019-09-04 13:54:34",
            "sender": null
        },
        /*社群升级特权即将过期通知*/
        {
            "id": 3,
            "target_id": 0,
            "body": {
                "type": "group:upgrade:expired",
                "group": {
                    "id": 1,
                    "day": 0,
                    "name": "社群啊",
                    "type": "group",
                    "level": 1
                },
                "content": "您的社群「社群啊」升级到LV1等级特权即将到期，为保障您部分群功能正常使用，请及时续费!"
            },
            "target_type": null,
            "read_id": 3,
            "sender_id": 0,
            "created_at": "2019-09-19 11:00:00",
            "sender": null
        },
    ]
}
```


**系统通知**

```json
{
    "msg": "ok",
    "code": 0,
    "data": [
        {
            "id": 5,
            "target_id": 0,
            "body": {
                "title": "哈哈啊哈",/*通知标题*/
                "content": "asdasdasdsadsadasda"/*通知类型*/
            },
            "read_id": 5,
            "target_type": "system",
            "sender_id": 0,
            "created_at": "2019-06-29 10:13:59"
        }
    ]
}
```

**新动态提醒消息**
```json
{
    "msg": "ok",
    "code": 0,
    "data": {
        "status": 0            //  0-不需要提醒用户 1-需要提醒用户
    }
}
```

## 重置新动态提醒消息

**方式**

`PUT`

**路径**

`/api/notify/messages`

**参数**


**响应**

`Status code 200`

```json
{
    "msg": "ok",
    "code": 0,
    "data": null
}
```

## 系统消息置顶

**方式**

`POST`

**路径**

`/api/notify/messages/top`

**参数**

|  名称  |  类型  | 必须 | 说明  |
| :----: | :----: | :--: | :----: |
| system_id | int |  是  | 系统消息通知id |


**响应**

`Status code 200`

```json
{
    "msg": "ok",
    "code": 0,
    "data": null
}
```

## 系统消息取消置顶

**方式**

`POST`

**路径**

`/api/notify/messages/down`

**参数**

|  名称  |  类型  | 必须 | 说明  |
| :----: | :----: | :--: | :----: |
| system_id | int |  是  | 系统消息通知id |


**响应**

`Status code 200`

```json
{
    "msg": "ok",
    "code": 0,
    "data": null
}
```

## 删除消息

**方式**

`DELETE`

**路径**

`/api/notify/messages/{readId}`

**响应**

`Status code 200`

```json
{
    "msg": "Success",
    "code": 0,
    "data": null
}
```

## 清空消息

**方式**

`DELETE`

**参数**

|  名称  |  类型  | 必须 | 说明  |
| :----: | :----: | :--: | :----: |
| type | string |  是  | `remind`-动态通知 `message`-消息通知 `system`-系统通知 |

**路径**

`/api/notify/messages/clear`

**响应**

`Status code 200`

```json
{
    "msg": "Success",
    "code": 0,
    "data": null
}
```