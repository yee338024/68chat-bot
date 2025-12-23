# 68聊天协议

## 简介
<img src="./docs/assets/68.png" style="width:80px;"/>  

68助手是一款基于68聊天软件的第三方自动化协议接口，支持通过websocket进行消息的发送与接收，方便开发者进行二次开发与集成，编写各类机器人🤖。


## 联系客服购买卡密

![Telegram](https://camo.githubusercontent.com/473b7dbc45a8480ab4447294490f837bcd398d028947388fecee8df9f29f1e7a/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f2534306a656e6b696e735f5f70726f2d3235613465333f6c6f676f3d74656c656772616d266c6f676f436f6c6f723d77686974652673616e6974697a653d74727565)

## 连接websocket

客户端通过`ws://127.0.0.1:5599`连接到websocket服务，连接成功后，会返回：
```json
{
	"message": "Hello"
}
```
收到服务器回复后，代表连接成功。

> websocket数据通讯格式全部采用`json`格式

## 发送消息说明
### 发送消息给好友

```json
{
    "id": "webscoket消息id",
    "type": "sendMsg", 
    "data": {
        "id": 7237423, 
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
}
```
### 发送消息到群组

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
          "content": "这里改成你的消息"
        }
      }
    ],
    "quoteInfo": null
  }
}
```

### 发送文件
```json
{
    "id": "1",
    "type": "sendFile",
    "data": {
        "file": "C:/Users/rtuge/Desktop/b.mp4",  👈文件绝对路径
        "type": "group",                         👈如果是私聊填 'friend'
        "id": 389284                             👈对应群组或者好友id
    }
}
```
当前68消息类型对照表如下：

| 消息类型值 | 文案 | 备注 |
|------------|------|------|
| 13 | 暂不支持该消息类型  ||
| 1 | 图片 ||
| 9 | 动画表情 ||
| 2 | 语音 ||
| 3 | 视频 ||
| 5 | 名片 ||
| 7 | 文件 ||
| 12 | 骰子 |dice|
| 18 | 扑克牌 |pocker|

### 检测消息是否发送成功
⚠️消息发送失败时，websocket会回调`readStatus: 0`：
```json
{
	"operator": "msgListPropertyUpdate",
	"data": {
		"id": 389284,
		"type": "group",
		"list": [
			{
				"customMsgId": "30984532587",
				"updated": {
					"readStatus": 0               
				}
			}
		],
		"readStatus": 0  
	}
}
```
✅发送成功时，回调`readStatus: 1`：
```json
{
	"operator": "msgListPropertyUpdate",
	"data": {
		"id": 389284,
		"type": "group",
		"list": [
			{
				"customMsgId": "10441859254",
				"updated": {
					"MsgID": 4667081534,
					"readStatus": 1,
					"time": "1766222907461",
					"sendTime": "1766222907461"
				}
			}
		],
		"readStatus": 1   
	}
}
```

## 收取消息
### 新的文字消息
```json
{
	"operator": "msgNew",
	"data": {
		"msgType": 0,
		"atUids": [],
		"atUsers": [],
		"links": [],
		"sendUid": 4008697,
		"groupId": 389284,
		"content": "[微笑]",
		"sendTime": 1766282269132,
		"msgId": 4688172503,
		"sendMember": {
			"user": {
				"uid": "4008697",
				"nickName": "ID采集机器人🤖",
				"icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
				"signature": "专业定制各类聊天软件自动化机器人",
				"identify": "--",
				"createTime": "1746527494000"
			},
			"groupId": "389284",
			"type": "MANAGE",
			"score": "1135394003000",
			"right": {
				"bfUpdateData": true,
				"bfJoinCheck": true,
				"bfPushNotice": true
			}
		},
		"contentMd5": "252049bb117c5bd3c77cac9051f1d198",
		"groupName": "huimei",
		"sentOverTime": 1766282269132,
		"customMsgId": "70790767392",
		"MsgID": 4688172503,
		"UserID": 4008697,
		"isSelf": true,
		"ChatType": 0,
		"chatType": 0,
		"id": 389284,
		"name": "huimei",
		"readStatus": 1,
		"time": 1766282269132,
		"type": "group",
		"user": {
			"uid": "4008697",
			"nickName": "ID采集机器人🤖",
			"icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
			"signature": "专业定制各类聊天软件自动化机器人",
			"identify": "--",
			"createTime": "1746527494000"
		}
	}
}
```

### 新的图片消息
```json
{
	"operator": "msgNew",
	"data": {
		"msgType": 1,
		"atUids": [],
		"atUsers": [],
		"links": [],
		"sendUid": 4008697,
		"groupId": 389284,
		"content": "http://r11.aiolet.xyz/chat/pic/202512/21/2e11f6748829b59e3f11f9e1f71ccc10.jpeg||http://r11.aiolet.xyz/chat/pic/202512/21/48b807c116ffe851c96d43897e9813eb.jpeg||20310||0",
		"sendTime": 1766282182859,
		"msgId": 4688146125,
		"sendMember": {
			"user": {
				"uid": "4008697",
				"nickName": "ID采集机器人🤖",
				"icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
				"signature": "专业定制各类聊天软件自动化机器人",
				"identify": "--",
				"createTime": "1746527494000"
			},
			"groupId": "389284",
			"type": "MANAGE",
			"score": "1135394003000",
			"right": {
				"bfUpdateData": true,
				"bfJoinCheck": true,
				"bfPushNotice": true
			}
		},
		"contentMd5": "cc5c7d12c19bc3abe180f319197152f9",
		"groupName": "huimei",
		"sentOverTime": 1766282182859,
		"customMsgId": "10782894930",
		"MsgID": 4688146125,
		"UserID": 4008697,
		"isSelf": true,
		"ChatType": 1,
		"chatType": 1,
		"id": 389284,
		"name": "huimei",
		"fileKey": "fg187h7vj9wwsi42",
		"readStatus": 1,
		"time": 1766282182859,
		"type": "group",
		"user": {
			"uid": "4008697",
			"nickName": "ID采集机器人🤖",
			"icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
			"signature": "专业定制各类聊天软件自动化机器人",
			"identify": "--",
			"createTime": "1746527494000"
		}
	}
}
```

### 新的文件消息
```json
{
	"operator": "msgNew",
	"data": {
		"msgType": 7,
		"atUids": [],
		"atUsers": [],
		"links": [],
		"sendUid": 4008697,
		"groupId": 389284,
		"content": "http://r11.aiolet.xyz/chat/file/202512/21/e158596ff68fd6a4669a7a7f02283a61.xml||ui.xml||11994",
		"sendTime": 1766282345669,
		"msgId": 4688196815,
		"sendMember": {
			"user": {
				"uid": "4008697",
				"nickName": "ID采集机器人🤖",
				"icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
				"signature": "专业定制各类聊天软件自动化机器人",
				"identify": "--",
				"createTime": "1746527494000"
			},
			"groupId": "389284",
			"type": "MANAGE",
			"score": "1135394003000",
			"right": {
				"bfUpdateData": true,
				"bfJoinCheck": true,
				"bfPushNotice": true
			}
		},
		"contentMd5": "903b2ddcb647933ba7ba0afa182cc381",
		"groupName": "huimei",
		"sentOverTime": 1766282345669,
		"customMsgId": "10735110335",
		"MsgID": 4688196815,
		"UserID": 4008697,
		"isSelf": true,
		"ChatType": 7,
		"chatType": 7,
		"id": 389284,
		"name": "huimei",
		"fileKey": "rpon4f3vp33bzh7h",
		"readStatus": 1,
		"fileName": "ui.xml",
		"fileSize": "11994",
		"size": "11994",
		"time": 1766282345669,
		"type": "group",
		"user": {
			"uid": "4008697",
			"nickName": "ID采集机器人🤖",
			"icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
			"signature": "专业定制各类聊天软件自动化机器人",
			"identify": "--",
			"createTime": "1746527494000"
		}
	}
}
```

## 消息回调监听

### 好友消息
```json
{
    "operator": "msgNew",
    "data": {
        "msgType": 0,
        "msgId": 2409462397,
        "sendUid": 4008697,
        "receiveUid": 7128348,
        "content": "Ffg",
        "sendTime": 1766116051970,
        "version": 6,
        "contentMd5": "ac716825f65e990167a446e9f1fd111d",
        "sendUser": {
            "uid": "4008697",
            "nickName": "协议机器人🤖",
            "icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
            "signature": "专业定制各类聊天软件自动化机器人",
            "identify": "k7m5tzmya2",
            "createTime": "1746527494000"
        },
        "customMsgId": "80499052521",
        "MsgID": 2409462397,
        "UserID": 4008697,
        "isSelf": false,
        "ChatType": 0,
        "chatType": 0,
        "id": 4008697,
        "friendId": 4008697,
        "time": 1766116051970,
        "type": "friend",
        "user": {
            "uid": "4008697",
            "nickName": "协议机器人🤖",
            "icon": "http://r11.aiolet.xyz/common/pic/202507/27/44eff667aad9eaa434a0af55d9cd4048.jpg",
            "signature": "专业定制各类聊天软件自动化机器人",
            "identify": "k7m5tzmya2",
            "createTime": "1746527494000"
        }
    }
}
```

### 群聊消息
```json
{
  "operator": "msgNew",
  "data": {
    "msgType": 0,
    "atUids": [],
    "atUsers": [],
    "sendUid": 7237423,
    "groupId": 389284,
    "content": "hhh",
    "sendTime": 1766115963742,
    "msgId": 4626337038,
    "sendMember": {
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
    "contentMd5": "a6dc56281eb1b9f670ab84ec6fceeb44",
    "groupName": "huimei、🤖群成员ID采集机器人",
    "customMsgId": "20298293316",
    "MsgID": 4626337038,
    "UserID": 7237423,
    "isSelf": false,
    "ChatType": 0,
    "chatType": 0,
    "id": 389284,
    "name": "huimei、🤖群成员ID采集机器人",
    "sendUserName": "Pwgen：",
    "time": 1766115963742,
    "type": "group",
    "user": {
      "uid": "7237423",
      "nickName": "Pwgen",
      "icon": "http://r11.aiolet.xyz/common/pic/202509/06/d55d17285d3a7290c7dc953b25465722.jpg",
      "identify": "--",
      "createTime": "1746529904000"
    }
  }
}

```
#### 群组信息更新
```json
{
  "operator": "groupUpdate",
  "data": {
    "type": "group",
    "id": 389284,
    "values": {
      "name": "新的群名"
    }
  }
}
```

#### 开启/关闭群禁言
```json
{
  "operator": "msgNew",
  "operatorType": "groupShutupAll",
  "data": {
    "id": 389284,
    "time": 1766116603039,
    "sendTime": 1766116603039,
    "type": "group",
    "targetId": 0,
    "groupId": 389284,
    "content": "管理员开启了全员禁言/管理员关闭了全员禁言", 👈
    "operator": "message",
    "chatType": 50,
    "msgType": 50,
    "notificationType": "groupShutupAll",
    "bfShutup": true / false  👈
  }
}
```

#### 开启阅后即焚
```json
{
  "operator": "msgNew",
  "operatorType": "operatorReadCancel",
  "data": {
    "id": 389284,
    "time": 1766116668353,
    "sendTime": 1766116668353,
    "type": "group",
    "targetId": 0,
    "groupId": 389284,
    "content": "「管理員設定了訊息已讀30秒後銷毀」",
    "operator": "message",
    "chatType": 50,
    "msgType": 50,
    "notificationType": "operatorReadCancel"
  }
}
```

#### 关闭阅后即焚

```json
{
    "operator": "msgNew",
    "operatorType": "operatorReadCancel",
    "data": {
        "id": 389284,
        "time": 1766116798162,
        "sendTime": 1766116798162,
        "type": "group",
        "targetId": 0,
        "groupId": 389284,
        "content": "Pwgen  關閉了閱後即焚",
        "operator": "message",
        "chatType": 50,
        "msgType": 50,
        "notificationType": "operatorReadCancel"
    }
}
```