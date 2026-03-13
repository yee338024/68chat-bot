# HTTP请求

## 获取个人资料

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "UserInfo",
  "url": "https://webbiz.angg1.com/user/userInfo"
}
```

### 响应示例

```json
{
  "commonResult": {
	"errCode": 200
  },
  "userInfo": {
	"uid": "4008697",
	"nickName": "ID采集机器人🤖",
	"icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
	"signature": "专业定制各类聊天软件自动化机器人",
	"identify": "k7m5tzmya2",
	"createTime": "1746527494000"
  },
  "bfPassword": true,
  "privacy": 4256,
  "signature": "专业定制各类聊天软件自动化机器人"
}
```

## 获取联系人列表

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "ContactsList",
  "url": "https://webbiz.angg1.com/contacts/contactsList",
  "data": {}
}
```

### 响应示例

```json
{
  "commonResult": {
	"errCode": 200
  },
  "contactsList": [
	{
	  "userInfo": {
		"uid": "5858052",
		"nickName": "12🌽34🌽收cu商",
		"friendRelation": {
		  "bfFriend": true
		},
		"userOnOrOffline": {
		  "uid": "5858052",
		  "createTime": "1765734028244",
		  "bfShow": true
		},
		"identify": "b6jo6y4p8h"
	  },
	  "letter": "#",
	  "msgCancelTime": 30,
	  "bfReadReceipt": true
	}
  ],
  "count": 36,
  "pageNum": 1,
  "lastUpdateTime": "1766113547565"
}
```

## 报错测试

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "GroupReqList",
  "url": "https://webbiz.angg1.com/group/groupReqList",
  "data": {
	"pageNum": 0,
	"pageSize": 100
  }
}
```

### 响应示例（错误）

```json
{
  "errorCode": 300,
  "errorDesc": "很抱歉，服务繁忙，请联系客服 #A0030"
}
```

## 获取群组列表

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/getGroups`

### 请求参数

无

### 响应示例

```json
[
  {
	"id": 389284,
	"hostId": 7237423,
	"name": "huimei",
	"pic": "http://r22.aiolet.xyz/config/default_group_icon.png",
	"groupAliasName": "k7d2dng8q8",
	"memberCount": 4,
	"groupMsgCancelTime": 30,
	"qrExpire": null,
	"bfShutup": false,
	"bfGroupReadCancel": false,
	"bfJoinCheck": false,
	"bfJoinFriend": true,
	"bfAddress": true,
	"groupNotice": ""
  }
]
```

## 获取群组成员

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "GroupMemberList",
  "protoType": "group",
  "url": "https://webbiz.kngg3.com/group/groupMemberListV2",
  "data": {
	"groupId": 389284,
	"pageSize": 1000,
	"pageNum": 1
  }
}
```

### 响应示例

```json
{
  "commonResult": {
	"errCode": 200
  },
  "members": [
	{
	  "user": {
		"uid": "7237423",
		"nickName": "Pwgen",
		"icon": "http://r11.aiolet.xyz/common/pic/202509/06/d55d17285d3a7290c7dc953b25465722.jpg",
		"friendRelation": {
		  "bfFriend": true
		},
		"identify": "--"
	  },
	  "groupId": "389284",
	  "score": "807415200000",
	  "right": {}
	}
  ],
  "count": "4",
  "lastUpdateTime": "1766114002864"
}
```

## 发送消息

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/sendMsg`

### 请求参数

```json
{
  "id": 4017572,
  "type": "friend",
  "list": [
  {
	"type": "text",
	"values": {
	"chatType": 0,
	"content": "这里改成你的消息"
	}
  }
  ],
  "quoteInfo": null
}
```

### 响应示例

```json
{
  "data": "success"
}
```

## 发送文件

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/sendFile`

### 请求参数

```json
{
  "file": "C:/Users/rtuge/Desktop/test.txt",
  "type": "group",
  "id": 389284
}
```

### 响应示例

```json
{
  "data": "success"
}
```

## 获取联系人资料

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "ContactsDetail",
  "url": "https://webbiz.angg1.com/contacts/contactsDetail",
  "data": {
	"targetUid": 7237423
  }
}
```

### 响应示例

```json
{
  "commonResult": {
	"errCode": 200
  },
  "contactsDetailBase": {
	"userInfo": {
	  "uid": "7237423",
	  "nickName": "Pwgen",
	  "icon": "http://r11.aiolet.xyz/common/pic/202509/06/d55d17285d3a7290c7dc953b25465722.jpg",
	  "friendRelation": {
		"bfFriend": true
	  },
	  "userOnOrOffline": {
		"uid": "7237423",
		"createTime": "1766242839299",
		"bfShow": true
	  },
	  "identify": "02lx0l99q6",
	  "createTime": "1746529904000"
	},
	"letter": "P",
	"msgCancelTime": 30,
	"commonGroupNum": 1,
	"bfReadReceipt": true,
	"bfIdSearch": true
  }
}
```

## 获取好友请求列表

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "ContactsApplyList",
  "url": "https://webbiz.angg1.com/contacts/contactsApplyList"
}
```

### 响应示例

```json
{
  "commonResult": {
	"errCode": 200
  },
  "recordList": [
	{
	  "userInfo": {
		"uid": "5138518",
		"nickName": "八方来财4",
		"icon": "http://r11.aiolet.xyz/common/pic/202509/07/a77c66e78a2c23d817e5ab00ca326baf.jpg",
		"identify": "am6gqf58go",
		"createTime": "1757214075000"
	  },
	  "msg": "验证：我是八方来财4",
	  "modifyTime": "1759928661000",
	  "type": "IDENTIFY",
	  "bfIdSearch": true
	}
  ]
}
```

## 获取群成员在线状态

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "protoType": "group",
  "type": "GroupMemberOnLineStatusList",
  "url": "https://webbiz.angg1.com/group/groupMemberOnLineStatusList",
  "data": {
	"groupId": 389284,
	"uids": [7237423, 4008697, 4017572, 7128348]
  }
}
```

### 响应示例

```json
{
  "commonResult": {
	"errCode": 200
  },
  "userOnLineStatusList": [
	{
	  "uid": "7237423",
	  "createTime": "1766242839299",
	  "bfShow": true
	},
	{
	  "uid": "4008697",
	  "online": true,
	  "createTime": "1766280644006",
	  "bfShow": true
	},
	{
	  "uid": "4017572",
	  "createTime": "1761010560062",
	  "bfShow": true
	},
	{
	  "uid": "7128348",
	  "createTime": "1766141350379",
	  "bfShow": true
	}
  ]
}
```

## 获取群组信息

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "GroupDetail",
  "url": "https://webbiz.angg1.com/group/groupDetail",
  "data": {
	"groupId": 389284
  }
}
```

### 响应示例

```json
{
  "commonResult": {
	"errCode": 200
  },
  "group": {
	"groupId": "389284",
	"hostId": "7237423",
	"name": "huimei",
	"pic": "http://r22.aiolet.xyz/config/default_group_icon.png",
	"createTime": "1753495200000",
	"memberCount": "4",
	"bfJoinFriend": true,
	"groupMsgCancelTime": 30,
	"groupAliasName": "k7d2dng8q8"
  },
  "bfAddress": true,
  "right": {
	"bfUpdateData": true,
	"bfJoinCheck": true,
	"bfPushNotice": true
  },
  "groupNotice": {
	"editUser": {
	  "user": {
		"uid": "7237423",
		"nickName": "Pwgen",
		"icon": "http://r11.aiolet.xyz/common/pic/202509/06/d55d17285d3a7290c7dc953b25465722.jpg",
		"identify": "--",
		"createTime": "1746529904000"
	  },
	  "groupId": "389284",
	  "score": "807415200000"
	},
	"notice": "asdd",
	"releaseTime": "1766201544598",
	"noticeId": "1043631"
  },
  "memberType": "MANAGE",
  "qrUrl": "https://68chat.com?qrCode=CW3W6NMT&imQrCodeType=1&IdCode=DFA39FEAF43382DCDE35927E641A1D83&fromUid=4008697",
  "qrExpire": "4070908800000"
}
```

## 更新群简介

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "GroupUpdate",
  "url": "https://webbiz.kngg3.com/group/groupUpdate",
  "data": {
	"op": 12,
	"groupParam": {
	  "notice": "新的群通知",
	  "bfAll": true,
	  "groupId": 389284
	}
  }
}
```

### 响应示例

```json
{
  "commonResult": {
	"errCode": 200
  },
  "noticeId": "1048785"
}
```

## 群禁言

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "GroupUpdate",
  "url": "https://webbiz.kngg3.com/group/groupUpdate",
  "data": {
	"op": 11,
	"groupParam": {
	  "shutup": true,
	  "groupId": 389284
	}
  }
}
```

## 群成员禁言

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/request`

### 请求参数

```json
{
  "type": "GroupMemberShutup",
  "url": "https://webbiz.kngg3.com/group/groupMemberShutup",
  "data": {
	"targetUid": 7128348,
	"shutupTime": 3600,
	"groupId": 441298
  }
}
```

### 响应示例

暂无响应示例

## 获取 apiUrl

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/getApiUrl`

### 请求参数

无

### 响应示例

```json
{
  "data": "https://webbiz.kngg3.com"
}
```

## 重启68

### 接口信息

- 方法：`POST`
- 地址：`http://127.0.0.1:5598/restart68`

### 请求参数

无

### 响应示例

```json
{
  "data": "restarting"
}
```

