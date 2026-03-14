# 收发送消息说明
当前68消息类型对照表如下：

| 消息类型值 | 文案 | 常量名 | 备注 |
|------------|------|--------|------|
| 0 | 文本 | MESSAGE_TYPE_TEXT | 普通文本消息 |
| 1 | 图片 | MESSAGE_TYPE_IMAGE | 单张图片 |
| 2 | 语音 | MESSAGE_TYPE_VOICE | 语音消息 |
| 3 | 视频 | MESSAGE_TYPE_VIDEO | 视频消息 |
| 4 | 位置 | MESSAGE_TYPE_LOCATION | 位置消息 |
| 5 | 名片 | MESSAGE_TYPE_NAMECARD | 好友/群名片 |
| 6 | 系统消息 | MESSAGE_TYPE_SYSTEM | 系统消息 |
| 7 | 文件 | MESSAGE_TYPE_FILE | 文件消息 |
| 8 | 通知 | MESSAGE_TYPE_NOTICE | 系统通知 |
| 9 | 动画表情 | MESSAGE_TYPE_DYNAMIC_IMAGE | GIF/动态表情 |
| 10 | 红包 | MESSAGE_TYPE_REDPACKET | 普通红包 |
| 11 | HTML | MESSAGE_TYPE_HTML | HTML 消息 |
| 12 | 骰子 | MESSAGE_TYPE_SETIMAGE | 游戏骰子 |
| 13 | 暂不支持该消息类型 | MESSAGE_TYPE_CHAT_TRANSFER | 转账消息（未支持显示） |
| 14 | 转账结果 | MESSAGE_TYPE_CHAT_TRANSFER_RESULT | 转账结果通知 |
| 15 | 红包结果 | MESSAGE_TYPE_REDPACKET_RESULT | 红包领取结果 |
| 16 | HTML2 | MESSAGE_TYPE_HTML2 | HTML 消息（备用） |
| 17 | 图片列表 | MESSAGE_TYPE_IMAGE_LIST | 多图消息 |
| 18 | 扑克牌 | MESSAGE_TYPE_ANIMATED_GAME | 扑克牌动画 |
| 19 | 红包变化 | MESSAGE_TYPE_REDPACKET_CHANGE | 红包金额变化 |
| 20 | 红包事件 | MESSAGE_TYPE_REDPACKET_EVENT | 红包相关事件 |
| 100 | 流媒体 | MESSAGE_TYPE_STREAM | 流媒体消息 |
| 101-104 | 系统提示 | MESSAGE_TYPE_SYSTEM_TIP / MESSAGE_TYPE_GROUP_TIP | 群提示或系统提示消息 |
| 201 | 撤回成功 | MESSAGE_TYPE_RECALL_SUCCESS | 消息撤回成功提示 |
| 202 | 错误提示 | MESSAGE_TYPE_ERROR_TIP | 系统错误提示 |
| 203 | 撤回消息 | MESSAGE_TYPE_RECALL | 消息撤回 |
| -1 | 未知消息 | MESSAGE_TYPE_UNKNOW | 未知类型消息 |
| -2 | 未解密消息 | MESSAGE_TYPE_UNDECRYPT | 加密或未解密消息 |

## 发送消息

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

### 发送文件
```json
{
    "id": "1",
    "type": "sendFile",
    "custom_msg_id": "104418592527",            👈自定义消息id，随机数11位，不能重复   
    "data": {
        "file": "C:/Users/rtuge/Desktop/b.mp4",  👈文件绝对路径
        "type": "group",                         👈如果是私聊填 'friend'
        "id": 389284                             👈对应群组或者好友id
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

### 消息双向删除
```json
{
	"operator": "recall_msg",
	"data": {
		"recallOneToOneMessages": [
			{
				"msgId": "2565552547",
				"msgTargetId": "4008697",
				"clearTime": "1773390253258"
			}
		]
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

### 🎲骰子消息

#### content内容解释
骰子消息由`点数`和`随机数`构成

| content | 点数 |
| -----|----|
|1\|\|4967201057 |1|
|2\|\|4967192662 |2|
|3\|\|4967183513 |3|
|4\|\|4967234223 |3|
|5\|\|4967208709 |3|
|6\|\|4967265240 |3|
```
{
	"operator": "msgNew",
	"data": {
		"msgType": 12,
		"atUids": [],
		"atUsers": [],
		"links": [],
		"sendUid": 4008697,
		"groupId": 389284,
		"content": "1||4966349477",
		"sendTime": 1767006189933,
		"msgId": 4966349477,
		"sendMember": {
			"user": {
				"uid": "4008697",
				"nickName": "unknown",
				"icon": "http://r22.aiolet.xyz/common/pic/202512/29/35c3fd5007037906fdb972b6cd3d5ce1.jpg",
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
		"contentMd5": "7df4984661841fc912d7d62d59f71124",
		"groupName": "huimei",
		"sentOverTime": 1767006189933,
		"customMsgId": "60986865605",
		"MsgID": 4966349477,
		"UserID": 4008697,
		"isSelf": true,
		"ChatType": 12,
		"chatType": 12,
		"id": 389284,
		"name": "huimei",
		"readStatus": 1,
		"time": 1767006189933,
		"type": "group",
		"user": {
			"uid": "4008697",
			"nickName": "unknown",
			"icon": "http://r22.aiolet.xyz/common/pic/202512/29/35c3fd5007037906fdb972b6cd3d5ce1.jpg",
			"identify": "--",
			"createTime": "1746527494000"
		}
	}
}
```