# 商品管理

## 列表[重写]

**方式**

`GET`

**路径**

`/admin/goods`

**参数**

|    名称     |  类型  | 默认 | 必须 |              说明              |
| :---------: | :----: | :--: | :--: | :----------------------------: |
|    name     | string |  无  |  否  |              名称              |
| category_id |  int   |  无  |  否  |            分类名称            |
|    limit    |  int   |  15  |  否  |            每页条数            |
|   status    |  int   |  无  |  否  | 上下架 可选参数: 1-上架 2-下架 |
|   delete    |  int   |  无  |  否  | 回收站 可选参数: 0-正常 2-删除 |
|   usable    | string |  无  |  否  | 传1时表示获取未绑定商户的商品 |

**响应**

`Status code 200`

```json
{
  "current_page": 1,
  "data": [
    {
      "id": 10,
      "name": "商品名1称",
      "intro": "商品卖点2",
      "detail": "1231233",
      "image": "https://www.baidu.com/",
      "cost_price": "20.00",
      "category_id": 1,
      "yz_item_id": 0,
      "merchant_id": 0,
      "type": 2,
      "spec_type": 2,
      "is_delete": 0,
      "created_at": "2019-03-04 18:22:02",
      "updated_at": "2019-03-04 18:22:11",
      "category": {
        "id": 1,
        "name": "手机数码",
        "image": "http://p59l6s1jm.bkt.clouddn.com/fcc9effd7b645167633169bba4ee7651.jpeg",
        "pid": 0,
        "level": 0,
        "path": "",
        "paths": "0,1",
        "sort": 0
      }
    },
    {
      "id": 9,
      "name": "商品名1称",
      "intro": "商品卖点2",
      "detail": "1231233",
      "image": "https://www.baidu.com/",
      "cost_price": "20.00",
      "category_id": 1,
      "yz_item_id": 0,
      "merchant_id": 0,
      "type": 2,
      "spec_type": 2,
      "is_delete": 0,
      "created_at": "2019-03-04 18:14:09",
      "updated_at": "2019-03-04 18:20:30",
      "category": {
        "id": 1,
        "name": "手机数码",
        "image": "http://p59l6s1jm.bkt.clouddn.com/fcc9effd7b645167633169bba4ee7651.jpeg",
        "pid": 0,
        "level": 0,
        "path": "",
        "paths": "0,1",
        "sort": 0
      }
    }
  ],
  "first_page_url": "http://comc-mall-amin.test/admin/goods?page=1",
  "from": 1,
  "last_page": 1,
  "last_page_url": "http://comc-mall-amin.test/admin/goods?page=1",
  "next_page_url": null,
  "path": "http://comc-mall-amin.test/admin/goods",
  "per_page": 15,
  "prev_page_url": null,
  "to": 2,
  "total": 2
}
```

## 添加[重写]

**方式**

`POST`

**路径**

`/admin/goods`

**参数**

```json
{
  "name": "花花公子 高领毛衣 2018秋季新款", // 商品名称 必填
  "intro": "花花公子 高领毛衣 2018秋季新款", // 商品简述或卖点 必填
  "detail": "花花公子 高领毛衣 2018秋季新款", // 商品详情 必填
  "category_id": 1, // 分类id 必须
  "type": 2, // 1-虚拟商品 2-实体商品
  "spec_type": 1, // 1-单规格 2-多规格
  "cost_price": 111.1, // 成本价
  "image": 0, // 商品主图地址, 获取第一张商品图片地址
  "images": [1, 2, 3, 4], // 图片id
  "merchant_id": 0, // 商家ID
  "specs_properties": [
    {
      // 如spec_type为2必传，须按照此格式传递
      "name": "颜色", // 规格
      "properties": ["红色", "蓝色"] // 规格属性
    },
    {
      "name": "尺寸",
      "properties": ["S", "M"]
    }
  ],
  "skus": [
    {
      "sale_price": 100, // 销售价,单位人民币元
      "image": "http://p59l6s1jm.bkt.clouddn.com/16ddf9eef740c6585a219908dbb2b791.jpeg", // 图片地址
      "specs_properties": [
        // 单个sku的规格属性 如spec_type为2必传，按照此格式传递
        {
          "s_name": "颜色", // 规格名称
          "p_name": "红色" // 规格属性
        },
        {
          "s_name": "尺寸",
          "p_name": "S"
        }
      ]
    },
    {
      "sale_price": 100, // 销售价,单位人民币元
      "image": "http://p59l6s1jm.bkt.clouddn.com/16ddf9eef740c6585a219908dbb2b791.jpeg", // 图片地址
      "specs_properties": [
        {
          "s_name": "颜色",
          "p_name": "红色"
        },
        {
          "s_name": "尺寸",
          "p_name": "M"
        }
      ]
    },
    {
      "sale_price": 100, // 销售价,单位人民币元
      "image": "http://p59l6s1jm.bkt.clouddn.com/16ddf9eef740c6585a219908dbb2b791.jpeg", // 图片地址
      "specs_properties": [
        {
          "s_name": "颜色",
          "p_name": "蓝色"
        },
        {
          "s_name": "尺寸",
          "p_name": "S"
        }
      ]
    },
    {
      "sale_price": 100, // 销售价,单位人民币元
      "image": "http://p59l6s1jm.bkt.clouddn.com/16ddf9eef740c6585a219908dbb2b791.jpeg", // 图片地址
      "specs_properties": [
        {
          "s_name": "颜色",
          "p_name": "蓝色"
        },
        {
          "s_name": "尺寸",
          "p_name": "M"
        }
      ]
    }
  ]
}
```

**响应**

`Status code 200`

```json
{
  "message": "添加商品成功"
}
```

## 详情[重写]

**方式**

`GET`

**路径**

`/admin/goods/:good`

```json
{
  "id": 10,
  "name": "商品名1称",
  "intro": "商品卖点2",
  "detail": "1231233",
  "image": "https://www.baidu.com/",
  "cost_price": "20.00",
  "category_id": 1,
  "yz_item_id": 0,
  "merchant_id": 0,
  "type": 2,
  "spec_type": 2,
  "is_delete": 0,
  "created_at": "2019-03-04 18:22:02",
  "updated_at": "2019-03-04 18:22:11",
  "specs_properties": [],
  "images": [
    {
      "id": 1,
      "filename": "fcc9effd7b645167633169bba4ee7651.jpeg",
      "file_url": "http://p59l6s1jm.bkt.clouddn.com/fcc9effd7b645167633169bba4ee7651.jpeg"
    },
    {
      "id": 2,
      "filename": "24449e53dcdf4a7e848e893ae6554749.jpeg",
      "file_url": "http://p59l6s1jm.bkt.clouddn.com/24449e53dcdf4a7e848e893ae6554749.jpeg"
    },
    {
      "id": 3,
      "filename": "7a1b0aef4f91ee7f1ecd9a569d766df6.jpeg",
      "file_url": "http://p59l6s1jm.bkt.clouddn.com/7a1b0aef4f91ee7f1ecd9a569d766df6.jpeg"
    },
    {
      "id": 4,
      "filename": "7a1b0aef4f91ee7f1ecd9a569d766df6.jpeg",
      "file_url": "http://p59l6s1jm.bkt.clouddn.com/7a1b0aef4f91ee7f1ecd9a569d766df6.jpeg"
    }
  ],
  "skus": [],
  "category": {
    "id": 1,
    "name": "手机数码",
    "image": "http://p59l6s1jm.bkt.clouddn.com/fcc9effd7b645167633169bba4ee7651.jpeg",
    "pid": 0,
    "level": 0,
    "path": "",
    "paths": "0,1",
    "sort": 0
  }
}
```

## 编辑[重写]

**方式**

`PUT`

**路径**

`/admin/goods/:goods`

**响应**

`Status code 200`

```json
{
  "message": "编辑商品成功"
}
```

## 删除[重写]

**方式**

`DELETE`

**路径**

`/admin/goods/:goods`

**响应**

`Status code 204`

## 获取货币价格

**方式**

`DELETE`

**路径**

`/admin/currency/price`

**响应**

`Status code 200`

```json
{
  "ore": 0.3004001,
  "comc": 0.3007002
}
```

## 同步有赞商品到兑换区

`admin/yzgoods/:goods/sync`

**请求方式**

`PUT`

**请求参数**

|   名称   |  类型  | 默认 | 必须 | 说明                                    |
| :------: | :----: | :--: | :--: | --------------------------------------- |
| currency | string |  无  |  是  | 兑换区: comc-comc 兑换区 ore-矿石兑换区 |

**返回体**

```json
{
  "type": 2,
  "cost_price": 0,
  "merchant_id": null,
  "category_id": null,
  "spec_type": 2,
  "yz_item_id": 454046399,
  "name": "【网红爆款光魔方灭蚊灯】智能光控  强力物理灭蚊  无辐射婴儿孕妇可用 1年质保、无效全额退款",
  "detail": "详情",
  "skus": [
    {
      "image": "",
      "sale_price": 129,
      "price": 0,
      "stock_num": 1424,
      "sales_num": 576,
      "properties": ["光魔方紫色", "标配款（USB接头）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方紫色"
        },
        {
          "s_name": "配置",
          "p_name": "标配款（USB接头）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 139,
      "price": 0,
      "stock_num": 1144,
      "sales_num": 856,
      "properties": ["光魔方紫色", "升级款（USB接头+适配器）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方紫色"
        },
        {
          "s_name": "配置",
          "p_name": "升级款（USB接头+适配器）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 129,
      "price": 0,
      "stock_num": 1265,
      "sales_num": 729,
      "properties": ["光魔方白色", "标配款（USB接头）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方白色"
        },
        {
          "s_name": "配置",
          "p_name": "标配款（USB接头）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 139,
      "price": 0,
      "stock_num": 836,
      "sales_num": 1160,
      "properties": ["光魔方白色", "升级款（USB接头+适配器）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方白色"
        },
        {
          "s_name": "配置",
          "p_name": "升级款（USB接头+适配器）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 129,
      "price": 0,
      "stock_num": 940,
      "sales_num": 1059,
      "properties": ["光魔方蓝色", "标配款（USB接头）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方蓝色"
        },
        {
          "s_name": "配置",
          "p_name": "标配款（USB接头）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 139,
      "price": 0,
      "stock_num": 507,
      "sales_num": 1602,
      "properties": ["光魔方蓝色", "升级款（USB接头+适配器）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方蓝色"
        },
        {
          "s_name": "配置",
          "p_name": "升级款（USB接头+适配器）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 129,
      "price": 0,
      "stock_num": 1760,
      "sales_num": 240,
      "properties": ["光魔方黄色", "标配款（USB接头）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方黄色"
        },
        {
          "s_name": "配置",
          "p_name": "标配款（USB接头）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 139,
      "price": 0,
      "stock_num": 1670,
      "sales_num": 328,
      "properties": ["光魔方黄色", "升级款（USB接头+适配器）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方黄色"
        },
        {
          "s_name": "配置",
          "p_name": "升级款（USB接头+适配器）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 129,
      "price": 0,
      "stock_num": 1549,
      "sales_num": 452,
      "properties": ["光魔方粉色", "标配款（USB接头）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方粉色"
        },
        {
          "s_name": "配置",
          "p_name": "标配款（USB接头）"
        }
      ]
    },
    {
      "image": "",
      "sale_price": 139,
      "price": 0,
      "stock_num": 1232,
      "sales_num": 767,
      "properties": ["光魔方粉色", "升级款（USB接头+适配器）"],
      "specs_properties": [
        {
          "s_name": "款式",
          "p_name": "光魔方粉色"
        },
        {
          "s_name": "配置",
          "p_name": "升级款（USB接头+适配器）"
        }
      ]
    }
  ],
  "intro": "【网红爆款光魔方灭蚊灯】智能光控  强力物理灭蚊  无辐射婴儿孕妇可用 1年质保、无效全额退款",
  "specs_properties": [
    {
      "name": "款式",
      "properties": [
        "光魔方紫色",
        "光魔方白色",
        "光魔方蓝色",
        "光魔方黄色",
        "光魔方粉色"
      ]
    },
    {
      "name": "配置",
      "properties": ["标配款（USB接头）", "升级款（USB接头+适配器）"]
    }
  ],
  "images": [
    {
      "id": 410,
      "filename": "https://img.yzcdn.cn/upload_files/2018/02/24/FgP7SBAWVtHQa2F3j8VgAvZO1zCn.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2018/02/24/FgP7SBAWVtHQa2F3j8VgAvZO1zCn.jpg"
    },
    {
      "id": 411,
      "filename": "https://img.yzcdn.cn/upload_files/2018/02/24/FkLjrJgw024ef00qK17kf2f9nNmM.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2018/02/24/FkLjrJgw024ef00qK17kf2f9nNmM.jpg"
    },
    {
      "id": 412,
      "filename": "https://img.yzcdn.cn/upload_files/2018/02/24/Fgb6G9tu3CYHVS7ROOuongOQtNSS.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2018/02/24/Fgb6G9tu3CYHVS7ROOuongOQtNSS.jpg"
    },
    {
      "id": 413,
      "filename": "https://img.yzcdn.cn/upload_files/2018/02/24/Fp5TbCFa3RaHR31K1Lmjq2rRyNtE.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2018/02/24/Fp5TbCFa3RaHR31K1Lmjq2rRyNtE.jpg"
    },
    {
      "id": 414,
      "filename": "https://img.yzcdn.cn/upload_files/2017/04/12/Fn7eE13uk1DHQ4yBw3aWzfUXp8Yi.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2017/04/12/Fn7eE13uk1DHQ4yBw3aWzfUXp8Yi.jpg"
    },
    {
      "id": 415,
      "filename": "https://img.yzcdn.cn/upload_files/2017/04/01/Fj71XOFa3oJCQRyzpQ6LbHa-2Q4A.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2017/04/01/Fj71XOFa3oJCQRyzpQ6LbHa-2Q4A.jpg"
    },
    {
      "id": 416,
      "filename": "https://img.yzcdn.cn/upload_files/2017/04/01/FjL-I60p23sZso3JMR0lE5-9MpSb.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2017/04/01/FjL-I60p23sZso3JMR0lE5-9MpSb.jpg"
    },
    {
      "id": 417,
      "filename": "https://img.yzcdn.cn/upload_files/2017/04/01/FrJDLslbpse1J9tiZhdnQMKtKUbA.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2017/04/01/FrJDLslbpse1J9tiZhdnQMKtKUbA.jpg"
    },
    {
      "id": 418,
      "filename": "https://img.yzcdn.cn/upload_files/2017/04/01/FkE9KOqGjZWMAWxkvF5ZOMtmX0fC.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2017/04/01/FkE9KOqGjZWMAWxkvF5ZOMtmX0fC.jpg"
    },
    {
      "id": 419,
      "filename": "https://img.yzcdn.cn/upload_files/2017/04/01/Fk4ijOwKfNQbxxW7Y_3S_ughZeyc.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2017/04/01/Fk4ijOwKfNQbxxW7Y_3S_ughZeyc.jpg"
    },
    {
      "id": 420,
      "filename": "https://img.yzcdn.cn/upload_files/2018/02/24/FltSlVOUwDLBAUpaEpC2mpRMM5aK.jpg",
      "file_url": "https://img.yzcdn.cn/upload_files/2018/02/24/FltSlVOUwDLBAUpaEpC2mpRMM5aK.jpg"
    }
  ]
}
```

## 修改商品上下架

`/admin/goods/status`

**请求方法**

`PUT`

**请求参数**

|   名称   | 类型  | 必须 | 默认 |                     说明                      |
| :------: | :---: | :--: | :--: | :-------------------------------------------: |
|  status  |  int  |  是  |  无  |                1: 上架 2: 下架                |
| goods_id | array |  是  |  无  | 需要操作的商品集合 例如：批量-[1, 2] 单个-[1] |

**返回体**

```json
{
  "message": "修改成功"
}
```

## 修改商品成本价

`/admin/goods/{goods}/cost-price`

**请求方法**

`PATCH`

**请求参数**

| 名称  |  类型   | 必须 | 默认 |  说明  |
| :---: | :-----: | :--: | :--: | :----: |
| price | numeric |  是  |  无  | 成本价 |

**返回体**

```json
{
  "message": "修改成功"
}
```
