# 群组更新操作

| 枚举 | 值 | 含义 |
| --- | --- | --- |
| ADD | 0 | 创建群组 |
| DEL | 1 | 删除群组 |
| TOP | 2 | 群组置顶 |
| STAR | 3 | 群组星标 / 收藏 |
| DISTURB | 4 | 群组免打扰 |
| ADDRESS | 5 | 群组地址 / 定位相关设置 |
| JOIN_CHECK | 6 | 入群验证 |
| UPDATE_GROUP_NAME | 7 | 修改群名称 |
| UPDATE_NICK_NAME | 8 | 修改群内昵称 |
| UPDATE_GROUP_PIC | 9 | 修改群头像 |
| JOIN_FRIEND | 10 | 添加好友入群 |
| SHUTUP | 11 | 群禁言 |
| NOTICE | 12 | 设置群公告 |
| CLEAR_NOTICE | 13 | 清除群公告 |
| ADD_ADMIN | 14 | 添加群管理员 |
| EDIT_ADMIN | 15 | 编辑 / 取消群管理员 |
| GROUP_READ_CANCEL_OP | 16 | 取消群已读状态 |
| GROUP_READ_CANCEL_TIME_OP | 17 | 按时间取消群已读状态 |
| UPDATE_REMARK | 18 | 修改群备注 |
| UNRECOGNIZED | -1 | 未识别的操作类型 |


## 更新群简介
先发送api请求到websocket，`"bfAll":true`代表向所有群成员发送通知
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
这里要注意，更新通知后，是不会发送通知的，要手动再执行一次发送消息：
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
