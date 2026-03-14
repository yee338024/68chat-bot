# WebSocket请求示例

## 获取个人资料
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
    "type": "UserInfo",
    "url": "https://webbiz.angg1.com/user/userInfo"
  }
}
```

⬇️响应示例
```json
{
	"id": "1",
	"type": "request",
	"data": {
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
}
```

## 获取联系人列表
⬆️发送请求
```json
{
  "id": "2",
  "type": "request",
  "data": {
    "type": "ContactsList",
    "url": "https://webbiz.angg1.com/contacts/contactsList",
    "data": {}
  }
}
```

⬇️响应示例
```json
{
  "id": "2",
  "type": "request",
  "data": {
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
}
```

## 报错测试
⬆️发送请求
```json
{
  "id": "error-test",
  "type": "request",
  "data": {
    "type": "GroupReqList",
    "url": "https://webbiz.angg1.com/group/groupReqList",
    "data": {
      "pageNum": 0,
      "pageSize": 100
    }
  }
}
```

⬇️响应示例（错误）
```json
{
  "id": "error-test",
  "type": "request",
  "error": {
    "errorCode": 300,
    "errorDesc": "很抱歉，服务繁忙，请联系客服 #A0030"
  }
}
```

## 获取群组列表（发送请求示例）
⬆️发送请求
```json
{
  "id": "webscoket消息id",
  "type": "getGroups"
}
```

⬇️响应示例
```json
{
  "id": "1",
  "type": "getGroups",
  "data": [
    {
      "id": 389284,
      "hostId": 7237423,
      "name": "huimei",
      "pic": "http://r22.aiolet.xyz/config/default_group_icon.png",
      "groupAliasName": "k7d2dng8q8",
      "memberCount": 4,
      "groupMsgCancelTime": 30,
      "memberType": 1,
      "qrExpire": 4070908800000,
      "qrUrl": "https://68chat.com?qrCode=CW3W6NMT&imQrCodeType=1&IdCode=DFA39FEAF43382DCDE35927E641A1D83&fromUid=4008697",
      "bfShutup": false,
      "bfGroupReadCancel": false,
      "bfJoinCheck": true,
      "bfJoinFriend": true,
      "bfAddress": true,
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
      "bfPushNotice": true,
      "bfResetQrcode": false,
      "bfUpdateData": true,
      "type": "group"
    }
  ]
}
```

## 发送好友信息（示例）
⬆️发送请求
```json
{
  "id": "webscoket消息id",
  "type": "sendMsg",
  "data": {
    "id": 7237423,
    "type": "friend",
    "custom_msg_id": "104418592528",            👈自定义消息id，随机数11位，不能重复
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
}
```

## 发送群组信息（示例）
⬆️发送请求
```json
{
  "id": "webscoket消息id",
  "type": "sendMsg",
  "data": {
    "id": 389284,
    "type": "group",
    "custom_msg_id": "104418592527",            👈自定义消息id，随机数11位，不能重复
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
}
```

## 获取群组列表（请求示例2）
⬆️发送请求
```json
{
  "id": "getGroups-1",
  "type": "getGroups"
}
```

## 获取群组成员
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
    "type": "GroupMemberList",
    "protoType": "group",
    "url": "https://webbiz.kngg3.com/group/groupMemberListV2",
    "data": {
      "groupId": 389284,
      "pageSize": 1000,
      "pageNum": 1
    }
  }
}
```

⬇️响应示例
```json
{
  "id": "1",
  "type": "request",
  "data": {
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
}
```

## 获取联系人资料
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
    "type": "ContactsDetail",
    "url": "https://webbiz.angg1.com/contacts/contactsDetail",
    "data": {
      "targetUid": 7237423
    }
  }
}
```

⬇️响应示例
```json
{
  "id": "1",
  "type": "request",
  "data": {
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
}
```

## 获取好友请求列表
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
    "type": "ContactsApplyList",
    "url": "https://webbiz.angg1.com/contacts/contactsApplyList"
  }
}
```

⬇️响应示例
```json
{
  "id": "1",
  "type": "request",
  "data": {
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
}
```

## 获取群成员在线状态
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
    "protoType": "group",
    "type": "GroupMemberOnLineStatusList",
    "url": "https://webbiz.angg1.com/group/groupMemberOnLineStatusList",
    "data": {
      "groupId": 389284,
      "uids": [7237423, 4008697, 4017572, 7128348]
    }
  }
}
```

⬇️响应示例
```json
{
  "id": "1",
  "type": "request",
  "data": {
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
}
```

## 获取群组信息
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
    "type": "GroupDetail",
    "url": "https://webbiz.angg1.com/group/groupDetail",
    "data": {
      "groupId": 389284
    }
  }
}
```

⬇️响应示例
```json
{
  "id": "1",
  "type": "request",
  "data": {
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
}
```

## 发送文件（示例）
⬆️发送请求
```json
{
  "id": "1",
  "type": "sendFile",
  "data": {
    "file": "C:/Users/rtuge/Desktop/b.mp4",
    "type": "group",
    "id": 389284
  }
}
```

## 获取 apiUrl
⬆️发送请求
```json
{
  "id": "request-1",
  "type": "getApiUrl"
}
```

⬇️响应示例
```json
{
  "id": "request-1",
  "type": "getApiUrl",
  "data": "https://webbiz.qika.xyz"
}
```

## 发送多行文本（示例）
⬆️发送请求
```json
{
  "id": "webscoket消息id",
  "type": "sendMsg",
  "data": {
    "id": 389284,
    "type": "group",
    "list": [
      {
        "type": "text",
        "values": {
          "chatType": 0,
          "content": "发送多行文本\\n123\\n1234"
        }
      }
    ],
    "quoteInfo": null
  }
}
```

## 更新群简介
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
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
}
```

⬇️响应示例
```json
{
  "id": "1",
  "type": "request",
  "data": {
    "commonResult": {
      "errCode": 200
    },
    "noticeId": "1048785"
  }
}
```

## 发送群简介变更通知（示例）
⬆️发送请求
```json
{
  "id": "webscoket消息id",
  "type": "sendMsg",
  "data": {
    "id": 389284,
    "type": "group",
    "list": [
      {
        "type": "text",
        "values": {
          "chatType": 8,
          "content": "新的群通知",
          "bfAll": true
        }
      }
    ]
  }
}
```

## 群禁言（示例）
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
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
}
```

## 发送群禁言消息（示例）
⬆️发送请求
```json
{
  "id": "webscoket消息id",
  "type": "sendMsg",
  "data": {
    "id": 389284,
    "type": "group",
    "list": [
      {
        "type": "text",
        "values": {
          "chatType": 50,
          "content": "管理员开了全员禁言",
          "bfShutup": true
        }
      }
    ]
  }
}
```

## 群成员禁言（示例）
⬆️发送请求
```json
{
  "id": "1",
  "type": "request",
  "data": {
    "type": "GroupMemberShutup",
    "url": "https://webbiz.kngg3.com/group/groupMemberShutup",
    "data": {
      "targetUid": 7128348,
      "shutupTime": 3600,
      "groupId": 441298
    }
  }
}
```

## 重启68（示例）
⬆️发送请求
```json
{
  "id": "1",
  "type": "restart68"
}
```

