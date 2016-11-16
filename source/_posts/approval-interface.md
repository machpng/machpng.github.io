title: 预审批系统接口文档

date: 2016-11-16 23:58:47

categories: document

tags: [document]

---

1. [用户登录接口](#login)
2. [用户信息接口](#info)
3. [用户修改密码接口](#update-pwd)
4. [用户登出操作](#logout)
5. [App首页](#index)
6. [订单列表](#order-list)
7. [消息列表](#message-list)

<a name='login'></a>
#### 接口说明 **1、** 用户登录接口

- **请求的URL**
> [/api/login](#)

- **请求方式**
> POST

- **请求参数**
 
| 请求参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| version | STRING | APP版本号 | N |
| dtype | INT | 终端类型 1:pc 2:android 3:ios 4:其他 | N |
| device | STRING | 设备扁号 | N |
| secret | STRING | 访问秘钥 | N |
| username | STRING | 登录用户名 | N |
| password | STRING | 登录密码 | N |

- **接收实例**

```php
version:"1.0.0"
dtype:2
device:862325031385220
secret:f5b0ccae001ddb0ebf99085d45d95c96
username:18701932869	
password:111111
```

- **返回参数**

| 返回参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| errcode | INT | 错误码 0:为成功 其他错误:10000+ |  N |
| errmsg | STRING | 返回的错误信息 | N |
| data | Array | 返回的接口数据 | Y |

- **返回示例**

```php
{
    "code": 0,
    "msg": "请求成功",
    "data": {
        "token": "6c0b06eef457a6ff5ee0c0d25bfa386b" // 验证的token
    }
}
```



<a name='info'></a>
#### 接口说明 **2、** 用户信息接口

- **请求的URL**
> [/api/user/info](#)

- **请求方式**
> POST

- **请求参数**
  
| 请求参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| version | STRING | APP版本号 | N |
| dtype | INT | 终端类型 1:pc 2:android 3:ios 4:其他 | N |
| device | STRING | 设备扁号 | N |
| secret | STRING | 访问秘钥 | N |
| token | STRING | 用户登陆token | N |

- **接收实例**

```php
version:"1.0.0"
dtype:2
device:862325031385220
secret:f5b0ccae001ddb0ebf99085d45d95c96
token:f2f38b36e8c901918b4e2ee65b3fae06
```

- **返回参数**

| 返回参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| errcode | INT | 错误码 0:为成功 其他错误:10000+ |  N |
| errmsg | STRING | 返回的错误信息 | N |
| data | Array | 返回的接口数据 | Y |

- **返回示例**

```php
{
  "code": 0,
  "msg": "success",
  "data": {
    "username": "18701932869",  		 //用户名
    "realname": "张德帅", 				 // 姓名 
    "email": "abcd1234@gmail.ocm", 	 // 邮箱
    "mobile": "18701932869" 			// 手机号
  }
}
```


<a name='update-pwd'></a>
#### 接口说明 **3、** 用户修改密码接口

- **请求的URL**
> [/api/user/update-pwd](#)

- **请求方式**
> POST

- **请求参数**
  
| 请求参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| version | STRING | APP版本号 | N |
| dtype | INT | 终端类型 1:pc 2:android 3:ios 4:其他 | N |
| device | STRING | 设备扁号 | N |
| secret | STRING | 访问秘钥 | N |
| token | STRING | 用户登陆token | N |
| old_pwd | STRING | 旧密码 | N |
| password | STRING | 新密码 | N |

- **接收实例**

```php
version:"1.0.0"
dtype:2
device:862325031385220
secret:f5b0ccae001ddb0ebf99085d45d95c96
token:f2f38b36e8c901918b4e2ee65b3fae06
old_pwd:111111
password:123456
```

- **返回参数**

| 返回参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| errcode | INT | 错误码 0:为成功 其他错误:10000+ |  N |
| errmsg | STRING | 返回的错误信息 | N |
| data | Array | 返回的接口数据 | Y |

- **返回示例**

```php
{
  "code": 0,
  "msg": "密码修改成功",
  "data": []
}
```


<a name='logout'></a>
#### 接口说明 **4、** 用户登出操作

- **请求的URL**
> [/api/user/do-logout](#)

- **请求方式**
> POST

- **请求参数**
  
| 请求参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| version | STRING | APP版本号 | N |
| dtype | INT | 终端类型 1:pc 2:android 3:ios 4:其他 | N |
| device | STRING | 设备扁号 | N |
| secret | STRING | 访问秘钥 | N |
| token | STRING | 用户登陆token | N |


- **接收实例**

```php
version:"1.0.0"
dtype:2
device:862325031385220
secret:f5b0ccae001ddb0ebf99085d45d95c96
token:f2f38b36e8c901918b4e2ee65b3fae06
```

- **返回参数**

| 返回参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| errcode | INT | 错误码 0:为成功 其他错误:10000+ |  N |
| errmsg | STRING | 返回的错误信息 | N |
| data | Array | 返回的接口数据 | Y |

- **返回示例**

```php
{
  "code": 0,
  "msg": "用户登出成功",
  "data": []
}
```

<a name='index'></a>
#### 接口说明 **5、** app首页

- **请求的URL**
> [/api/user/index](#)

- **请求方式**
> POST

- **请求参数**
  
| 请求参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| version | STRING | APP版本号 | N |
| dtype | INT | 终端类型 1:pc 2:android 3:ios 4:其他 | N |
| device | STRING | 设备扁号 | N |
| secret | STRING | 访问秘钥 | N |
| token | STRING | 用户登陆token | N |


- **接收实例**

```php
version:"1.0.0"
dtype:2
device:862325031385220
secret:f5b0ccae001ddb0ebf99085d45d95c96
token:f2f38b36e8c901918b4e2ee65b3fae06
```

- **返回参数**

| 返回参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| errcode | INT | 错误码 0:为成功 其他错误:10000+ |  N |
| errmsg | STRING | 返回的错误信息 | N |
| data | Array | 返回的接口数据 | Y |


- **返回示例**

```php
{
  "code": 0,
  "msg": "成功",
  "data": {
    "all": 20,  // 全部
    "audit": 5, // 待审核
    "fail": 4, // 失败
    "pass": 6, // 通过
  }
}
```


<a name='order-list'></a>
#### 接口说明 **6、** 订单列表

- **请求的URL**
> [/api/order/list](#)

- **请求方式**
> POST

- **请求参数**
  
| 请求参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| version | STRING | APP版本号 | N |
| dtype | INT | 终端类型 1:pc 2:android 3:ios 4:其他 | N |
| device | STRING | 设备扁号 | N |
| secret | STRING | 访问秘钥 | N |
| token | STRING | 用户登陆token | N |
| status | INT | 订单状态 -1：未通过 0：草稿 1：待审核 2：审核通过 | N |
| page | INT | 页数 | N |


- **接收实例**

```php
version:"1.0.0"
dtype:2
device:862325031385220
secret:f5b0ccae001ddb0ebf99085d45d95c96
token:f2f38b36e8c901918b4e2ee65b3fae06
status:1
page:2
```

- **返回参数**

| 返回参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| errcode | INT | 错误码 0:为成功 其他错误:10000+ |  N |
| errmsg | STRING | 返回的错误信息 | N |
| data | Array | 返回的接口数据 | Y |

- **返回示例**

```php
{
	"code": 0,
	"msg": "成功",
	"data": [
		{
		  "name": "长得帅",
		  "code": "36126789999",
		  "status": 1,
		  "updated_at": "2016-11-16 08:54:53"
		}
	]
}
```

<a name='message-list'></a>
#### 接口说明 **7、** 消息列表

- **请求的URL**
> [/api/order/message-list](#)

- **请求方式**
> POST

- **请求参数**
  
| 请求参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| version | STRING | APP版本号 | N |
| dtype | INT | 终端类型 1:pc 2:android 3:ios 4:其他 | N |
| device | STRING | 设备扁号 | N |
| secret | STRING | 访问秘钥 | N |
| token | STRING | 用户登陆token | N |
| page | INT | 页数 | N |


- **接收实例**

```php
version:"1.0.0"
dtype:2
device:862325031385220
secret:f5b0ccae001ddb0ebf99085d45d95c96
token:f2f38b36e8c901918b4e2ee65b3fae06
page:2
```

- **返回参数**

| 返回参数 | 参数类型 | 参数说明 | 是否为空 Y/N |
| :-------- | :--------| :------ | :-------- |
| errcode | INT | 错误码 0:为成功 其他错误:10000+ |  N |
| errmsg | STRING | 返回的错误信息 | N |
| data | Array | 返回的接口数据 | Y |

- **返回示例**

```php
{
	"code": 0,
	"msg": "成功",
	"data": [
		{
		  "name": "长得帅",
		  "code": "36126789999",
		  "status": 1,
		  "updated_at": "2016-11-16 08:54:53"
		}
	]
}
```



