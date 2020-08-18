# WeChat API 个人微信号API/微信协议/独家接口/PC hook
# 适配所有类型个人微信号及版本
# 支持傻瓜式二次开发
# WeQuick 接口规范
![alt logo](https://wequick-1257130190.cos.ap-shanghai.myqcloud.com/img/logo.png)

------
**商务合作请加微信：abcdefg_12345654321**

<img src="https://wequick-1257130190.cos.ap-shanghai.myqcloud.com/img/xiaore.jpg" width="120" align=center/>

正常使用软件不会导致封号。


**杀毒软件会对软件的正常运行构成影响，导致各种问题，请在使用前关闭杀毒软件。**

------
# 注意事项
## 指令发出的方式有两种
1. 通过 send_msg 轮询接口发出
2. 通过 receive_msg 接口 return 发出

## 接口所用编码均为utf-8编码

## 服务端发出的指令格式应该是一个json数组，示例：
```json
[{"sendId":"","api":"sendTextMessage","option":{"wxid":"","text":""}}]
```

# receive_msg
一.监听微信内部发生的各种事件,并主动向回调接口发送这些事件的详细信息. 这些事件的种类有:  
### 登录登出
1. [上报登陆二维码(reportQrCodeMessage)](#reportQrCodeMessage)  
1. [上报当前登录微信详细信息(reportLoginUser)](#2.上报当前登录微信详细信息(reportLoginUser))  
1.
1. [上报退出登录事件(reportLogout)](#3.上报退出登录事件(reportLogout))  
### 好友相关
4.上报普通好友列表(reportContacts)
5.上报企业好友列表(reportImContacts)
6.上报公众号列表(reportPublics)
7.上报单个普通好友信息(reportSingleContact)
8.上报任意普通微信反查详细信息(reportUpdateContact)
9.上报联系人新增通知(reportContactAdd)
10.上报联系人删除通知(reportContactDel)
### 群相关
11.上报普通群列表(reportChatRooms)
12.上报普通群成员昵称()
13.上报企业群列表(reportImRooms)
14.上报单个普通群成员信息(reportSingleChatRoomMembers)
15.上报单个企业群成员信息(reportSingleImRoomMembers)
16.上报通过二维码进群返回状态(reportAcceptQrCodeChatRoom)
17.上报群成员新增通知(reportChatRoomMemberAdd)
18.上报群成员删除通知(reportChatRoomMemberDel)
19.上报检测到的新群通知(reportNewChatRoom)
20.上报退群或被踢通知(reportChatRoomQuit)
### 消息相关
21.上报文本消息(reportTextMessage)
22.上报图片消息(reportPicMessage)
23.上报文件消息(reportFileMessage)
24.上报视频消息(reportVideoMessage)
25.上报语音消息(reportVoiceMessage)
26.上报GIF表情消息(reportGifMessage)
27.上报个人名片消息(reportCardMessage)
28.上报位置消息(reportLocationMessage)
29.上报链接消息(网页或群邀请)(reportLinkMessage)
30.上报小程序消息(reportMiniMessage)
31.上报转账消息(reportTransferMessage)
32.上报无痕清理僵尸粉消息(reportZombieCheckMessage)
33.上报解密图片消息(reportDecryptPicMessage)
34.上报撤回消息(reportRevokeMessage)
35.上报二维码付款消息(reportQrCodeWcPay)
36.上报收藏列表(reportFavitems)
37.上报系统消息(reportSystemMessage)
38.上报其他消息(reportOtherMessage)
39.上报其他接收应用未知消息(reportOtherAppMessage)
### 请求相关
40.上报新的加好友请求(reportFriendAddRequest)
41.上报加好友指令返回状态(reportAddFriendMessage)
42.上报通过手机号/微信号/QQ号查询任意微信号信息(reportSearchContact)
### 其他
43.上报数据库查询结果(reportSqlData)
44.上报扫描二维码结果(reportScanQrcodePic)
45.上报当前聊天对象改变(reportTalkerChange)
46.上报语音翻译结果(reportTransVoice)
47.上报URL访问状态(reportCheckUrlStatus)
48.上报上传客户端上传文件到服务端结果(resUploadFile)

# send_msg
二. 执行回调接口下发的指令: 这些指令包括:
## 登录登出
1.打开微信(openWeChat)
2.获取二维码(getLoginQrCode)
3.获取当前登录微信详细信息(getLoginUser)
4.退出微信(logout)
## 好友相关
5.获取普通好友列表(getContacts)
6.获取企业好友列表(getImContacts)
7.获取公众号列表(getPublics)
8.获取单个普通好友信息(getSingleContact)
9.任意普通微信反查详细信息(updateContact)
10.添加好友(addFriend)
11.删除好友/取消关注公众号(delFriend)
12.修改好友备注(updateRemark)
13.接收加好友请求(acceptFriend)
14.接收好友转账(acceptBankTransfer)
15.退还好友转账(refuseFriendWcpay)
16.自动同意加好友申请(autoAcceptFriend)
17.自动同意好友转帐(autoAcceptWcpay)
18.自动加名片(autoAcceptCard)
19.单向加好友(acceptOnewayFriend)
20.通过手机号/微信号/QQ号查询任意微信号信息(searchContact)
21.添加通过任意手机号/微信号/QQ号查询的联系人(addSearchContact)
## 群相关
22.获取普通群列表(getChatRooms)
23.获取普通群成员昵称()
24.获取企业群列表(getImRooms)
25.获取单个普通群成员信息(getSingleChatRoomMembers)
26.获取单个企业群成员信息(getSingleImRoomMembers)
27.网络更新群成员信息(updateChatRoom)
28.发送40人以下群邀请(sendChatroomLow)
29.发送40人以上群邀请(sendChatroomHigh)
30.同意进群邀请(acceptChatroomInvite)
31.踢群成员(delChatRoomMembers)
32.修改群名称(updateChatRoomName)
33.修改群公告(sendChatRoomNotice)
34.修改我在本群的昵称(updateChatRoomDisplayName)
35.是否显示群昵称(showDisplayName)
36.创建群聊(createChatRoom)
37.退出并删除群(quitDelChatRoom)
38.自动同意进群邀请(autoAcceptChatRoom)
39.通过二维码进群(acceptQrcodeChatRoom)
40.保存到/移出通讯录(saveRoomToContact)
## 消息相关
42.任意消息转发(transAnyMessage)
43.发送文本消息(sendTextMessage)
44.发送群内@文本消息(sendAtTextMessage)
45.发送图片(sendPicMessage)
46.发送文件(sendFileMessage)
47.发送视频(sendVideoMessage)
48.发送GIF表情(sendGifMessage)
49.发送链接消息(sendLinkMessage)
50.发送名片(sendCardMessage)
51.发送小程序(sendMiniMessage)
52.发送收藏(sendFavorite)
53.发送xml消息(sendXmlMessage)
54.发送名片xml消息(sendCardXmlMessage)
## 请求相关
55.关注公众号(addPublic)
56.获取收藏列表(getFavorites)
57.收藏指定消息(addFavoriteFrom)
58.语音翻译(transVoice)
59.无痕清粉(zombieCheck)
60.解密图片(decryptPic)
61.获取未读消息数量(unreadMsgCountChange)
62.清理微信聊天记录(clearChatHistory)
## 其他
63.识别二维码(scanQrcodePic)
64.开启/关闭消息免打扰(modRecvNotify)
65.置顶/取消置顶聊天(chatSessionTop)
66.打开浏览器(openBrowser)
67.开启/关闭防撤回功能(disableRevoke)
68.检测URL在微信中是否有效(checkUrlStatus)
69.查询微信数据库(getSqlData)
70.关闭进程(closeProcess)
71.把客户端所在PC的资料上传到指定服务器(uploadFile)
72.下载资料到客户端所在PC(downloadFile)

# receive_msg
## 参数说明
|数据格式中的参数|参数的含义|
|:--------------|:-------|
|action         |上报的名称|
|cwxid          |当前登录微信账号的微信 ID|
|data           |上报的数据|

## 数据格式
```json
{
    "action" : "",
    "cwxid" : "",
    "data" : {}
}
```

### send_msg 任务下发到DLL的响应
```json
{
    "action":"",
    "cwxid":"",
    "data":{"errorReason":"","sendId":"","sendResult":""},
}
```

### <span id="reportQrCodeMessage">1.上报登陆二维码(reportQrCodeMessage)</span>
#### 参数说明
|data 中的参数|参数说明|
|:-----------|:-------|
|message     |二维码图片的 base64 格式,将这个字符串直接填到 img 标签的 src 就可以显示了|
|sendID      |getLoginQrCode 发到客户端的 sendID|

```json
{
    "data":{
        "action":"reportQrCodeMessage",
        "cwxid":"null",
        "data":{
            "message":"",
            "sendId":""
        }
    }
}
```

### 上报登陆状态
#### 参数说明
|data 中的参数|参数说明|
|:-----------|:-------|
|code        |是否登陆 1：成功  0：不成功|

```json
{
    "data":{
        "action":"loginStatus",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "code":""
        }
    }
}
```

### 上报当前登录微信详细信息
#### 参数说明
|data 中的参数|参数说明|
|:-----------|:-------|
|wxid        |微信id|
|username    |微信号(有可能为空)|
|nick        |微信昵称|
|asName      |好友备注|
|headPic     |头像的url地址|
|sex         |性别:1男，2女,0(未知)|
|country     |祖国(可能为空)|
|province    |省份(可能为空)|
|city        |城市(可能为空)|

```json
{
    "data":{
        "action":"reportLoginUser",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "wxid":  "wxid",
            "username": "xxxxx",
            "nick":"xxxxx",
            "asName" :"xxxx",
            "headPic":"http://xxxxxxxx",
            "sex" : 0,
            "country":"xxx",
            "province":"xxxx",
            "city":"xxxxx",
            "uin":88888888
        }
    }
}
```

### 上报退出登录事件
#### 参数说明
|data 中的参数|参数说明|
|:-----------|:-------|
|code        |1:退出 0:其他|

```json
{
    "data":{
        "action":"reportLogout",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "code":""
        }
    }
}
```

### 上报当前联系人列表  reportContact
#### 参数说明
|data 中 friendList(好友) 的参数|参数说明|
|:-----------|:-------|
|wxid        |微信id|
|username    |微信号(有可能为空)|
|nick        |微信昵称|
|asName      |好友备注|
|headPic     |头像的url地址|
|sex         |性别:1男，2女,0(未知)|
|country     |祖国(可能为空)|
|province    |省份(可能为空)|
|city        |城市(可能为空)|
|isFriend    |好友状态：0非好友，1是好友，2是黑名单|


|data 中 groupList(群) 的参数|参数说明|
|:-----------|:-------|
|wxid        |微信id|
|nick        |微信昵称|
|owner       |群主的wxid|
|roomCount   |群成员数量|
|headPic     |头像的url地址|
|userLists   |当前群的成员wxid的列表|


|data 中 publicList(公众号) 的参数|参数说明|
|:-----------|:-------|
|wxid        |某些公众号也可能以wxid_ 开头|
|nick    |公众号名称|
|headPic     |群的头像的url地址|

```json
{
    "data":{
        "action":"reportContact",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "friendList":[
                {
                    "wxid":  "wxid",
                    "username": "xxxxx",
                    "nick":"xxxxx",
                    "asName" :"xxxx",
                    "headPic":"http://xxxxxxxx",
                    "sex" : 0,
                    "country":"xxx",
                    "province":"xxxx",
                    "city":"xxxxx",
                    "isFriend":""
                }
            ],
            "groupList":[
                {
                    "wxid": "xxxxxxx",
                    "nick": "xxxxxx",
                    "owner": "xxxxxxxx",
                    "roomCount":  100,
                    "headPic":"http://xxxxxxxx",
                    "userLists" :["wxid_xxx1","wxid_xxx2","..."]
                }
            ],
            "publicList":[
                {
                    "wxid":  "gh_xxxxx",
                    "nick":"xxxxx",
                    "headPic":"http://xxxxxxxxxx"
                }
            ]
        }
    }
}
```

### 上报联系人/公众号的wxid
```json
{
    "data":{
        "action" : "reportUsersWxid",
        "cwxid" : "xxxxxx",
        "data" : {
            "userLists" : ["wxid_1","wxid_2"]
        }
    }
}
```

### 上报查询到的联系人/公众号详细信息
#### 参数说明
|userLists 中的参数|参数的含义|
|:-----------|:--------|
|wxid        |微信 ID  |
|username    |微信号(有可能为空) |
|nick        |微信昵称 |
|asName      |好友备注 |
|headPic     |头像的url地址 |
|sex         |性别:1男，2女,0未知 |
|country     |祖国(可能为空) |
|province    |省份(可能为空) |
|city        |城市(可能为空) |

```json
{
    "data":{
        "action" : "reportUsersInfo",
        "cwxid" : "xxxxxx",
        "data" : {
            "userLists" : [
                {
                    "wxid":  "wxid",
                    "username": "xxxxx",
                    "nick":"xxxxx",
                    "asName" :"xxxx",
                    "headPic":"http://xxxxxxxx",
                    "sex" : "xx" ,
                    "country":"xxx",
                    "province":"xxxx",
                    "city":"xxxxx"
                }
            ]
        }
    }
}
```

### 微及时上报某个群成员列表详细信息 reportChatRoomUserLists
#### 参数说明
|data 中的参数|参数的含义|
|:-----------|:---------|
|wxid        |群的微信 ID|
|owner       |群主 ID|
|nick        |群昵称|
|headPic     |群头像|
|roomCount   |群成员数量|


|userLists 中的参数|参数的含义|
|:-----------|:---------|
|wxid        |微信 ID|
|username    |微信号(有可能为空)|
|nick        |昵称|
|headPic     |头像|
|sex         |性别:1男，2女,0未知 |
|country     |祖国(可能为空) |
|province    |省份(可能为空) |
|city        |城市(可能为空) |

```json
{
    "data":{
        "action":"reportChatRoomUserLists",
        "cwxid" : "wxid_fo1039029348sfj",
        "data" : {
            "wxid":"7510115058@chatroom",
            "owner":"xxxxx",
            "nick":"",
            "headPic":"",
            "roomCount":"",
            "userLists":[
               {
                    "wxid":"",
                    "username":"",
                    "nick":"",
                    "headPic":"",
                    "sex":"2",
                    "country":"xxx",
                    "province":"xxx",
                    "city":"xxx"
               }
           ]
        }
    }
}
```

### 上报某个群成员的群昵称

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|chatRoom   |群的微信id|
|wxid       |群成员的微信id|
|chatNick   |群成员的群昵称(如果设置了备注,则显示为备注)|

```json
{
    "data":{
        "action":"reportGetChatRoomUserNick",
        "cwxid":"wxid_qg0ssssssth22",
        "data":{
            "msg": {
                "chatRoom": "",
                "wxid" : "",
                "chatNick":"XXXX"
            }
        }
    }
}
```

### 上报文本消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|message    |消息内容，纯文本格式|

```json
{
    "data":{
        "action":"reportTextMessage",
        "cwxid":"wxid_qg0ssssth0r222",
        "data":{
            "msg": {
                "msgType": 1,
                "myMsg" : "0",
                "roomWxid":"123432432@chatroom",
                "wxidFrom"  : "wxid_sadkwqlXXX",
                "wxidTo" :"wxid_sadkwqlkq",
                "nick" : "XXXX",
                "message" : "XXXX",
            }
        }
    }
}
```

### 上报图片消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|fileIndex  |图片下载后的本地路径|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportPicMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msgType": 3,
                "myMsg" : "0",
                "roomWxid": "xxxxxxxx@chatroom",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo":  "wxid_xxxxx",
                "nick" : "XXXX",
                "fileIndex" : "XXXX",
                "xmlmsg" : ""
            }
        }
    }
}
```

### 上报文件消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|fileIndex  |文件下载后的本地路径|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportFileMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msgType": "4901",
                "myMsg" : "0",
                "roomWxid": "xxxxxxxx@chatroom",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo":  "wxid_xxxxx",
                "nick" : "XXXX",
                "fileIndex":"",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```
### 上报群邀请的链接消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|url        |链接的地址|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportAddChatRoomMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msgType": "4902",
                "myMsg" : "0",
                "roomWxid": "xxxxxxxx@chatroom",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo":  "wxid_xxxxx",
                "nick" : "XXXX",
                "url" : "",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```



#### 上报小程序消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportMiniMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msg_type":"4903",
                "myMsg" : "0",
                "roomWxid": "xxxxxxxx@chatroom",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo": "xxxxxxxxx",
                "nick" : "",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```


### 上报网页的链接消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|title      |链接的标题|
|url        |链接的地址|
|desc       |链接的描述信息|
|pic        |链接的封面图片|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportUrlMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msgType": "4904",
                "myMsg" : "0",
                "roomWxid": "xxxxxxxx@chatroom",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo":  "wxid_xxxxx",
                "nick" : "XXXX",
                "title": "",
                "url": "",
                "desc": "",
                "pic": "",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```
### 上报转账消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|wxidFrom   |消息发送者的wxid|
|wxidTo     |消息的接收者的wxid|
|nick       |用户昵称|
|transferid |转账的ID|
|paysubtype |这笔账单的状态，1:发起转账时(包括我转账给他人，他人转账给我)；3:确认收账时(包括我确认收账，他人确认收账);4:退还转账(包括我退还转账，他人退还转账给我)|
|paymemo    |这笔账单的备注|
|feedesc    |这笔账单的金额|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportTransferMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msgType": "4905",
                "myMsg" : "0",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo":  "wxid_xxxxx",
                "nick" : "XXXX",
                "transferid": "",
                "paysubtype": "",
                "paymemo": "",
                "feedesc": "",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```

### 上报个人名片

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportCardMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msgType": 42,
                "myMsg" : "0",
                "roomWxid" : "",
                "wxidFrom"  : "",
                "wxidTo" :"wxid_sadkwqlkq",
                "nick" : "",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```

### 上报表情消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|url        |表情的url地址|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportGifMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msg_type":47,
                "myMsg" : "0",
                "roomWxid": "xxxxxxxx@chatroom",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo": "xxxxxxxxx",
                "nick" : "",
                "url" : "",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```

### 上报语音消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|voiceIndex |语音文件下载后的本地路径|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportVoiceMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msgType": 34,
                "myMsg" : "0",
                "roomWxid": "xxxxxxxx@chatroom",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo":  "wxid_xxxxx",
                "nick" : "XXXX",
                "voiceIndex" : "XXXX",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```

### 上报视频消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|nick       |群内发送消息用户昵称|
|coverIndex |视频文件封面图片的本地路径|
|videoIndex  |视频文件下载后的本地路径|
|xmlmsg     |微信原始的 xml 信息|

```json
{
    "data":{
        "action":"reportVideoMessage",
        "cwxid":"wxid_qg0saisth0r222",
        "data":{
            "msg": {
                "msgType": 43,
                "myMsg" : "0",
                "roomWxid": "xxxxxxxx@chatroom",
                "wxidFrom": "wxid_xxxxxx",
                "wxidTo":  "wxid_xxxxx",
                "nick" : "XXXX",
                "coverIndex":"",
                "videoIndex":"",
                "xmlmsg": "xxxxxxx"
            }
        }
    }
}
```

### 上报群相关系统消息
#### 参数说明
|msg 中的参数| 参数的含义|
|:-----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|message    |具体的通知内容,纯文本格式|

```json
{
    "data":{
        "action":"reportChatroomMessage",
        "cwxid":"",
        "data":{
            "msg": {
                "msgType": 10000,
                "myMsg" : "",
                "roomWxid"  : "",
                "wxidFrom" : "",
                "wxidTo" : "",
                "message": "xxxxxx",
            }
        }
    }
}
```
> 群相关系统消息示例:
    1.有红包出没时:"发出红包，请在手机上查看"
    2.修改群名称后:xxxxx修改群名为xxxxxxx
    3.群主已恢复默认进群方式。
    4.群主已启用“群聊邀请确认”，群成员需群主确认才能邀请朋友进群。
    5.你已成为新群主
    6.xxxxxx已成为新群主
    7.你邀请xxxx加入了群聊
    8.xxxx邀请xxxx加入了群聊
    9.xxxxx通过扫描你分享的二维码加入群聊"
    10.xxxxx通过扫描xxxxxx分享的二维码加入群聊"


### 上报其他微信系统消息

#### 参数说明
|msg 中的参数| 参数的含义|
|:----------|:---------|
|myMsg      |是否是本人发出的消息，1为是，0为不是|
|roomWxid   |聊天消息发生在哪个群(如果是私聊则为空)|
|wxidFrom   |消息发送者的wxid 如果是自己发的消息这里的wxid就是自己的微信号|
|wxidTo     |消息的接收者的wxid 如果发往群的消息,这个值就是群的wxid  如果是别人私聊给自己的消息,这里就是自己的微信号|
|message    |具体的通知内容,纯文本格式|

```json
{
    "data":{
        "action":"reportSystemMessage",
        "cwxid":"wxid_qgsssh0r222",
        "data":{
            "msg": {
                "msgType": 10000,
                "myMsg" :"",
                "roomWxid":"",
                "wxidFrom"  : "",
                "wxidTo" :"wxid_sadkwqlkq",
                "message": "xxxxxxx"
            }
        }
    }
}
```


> 系统通知示例:
    1.发消息-被对方拉黑之后,message 为"消息已发出，但被对方拒收了"
    2.有红包出没时:"发出红包，请在手机上查看"


### 上报新的加好友请求
#### 个别参数说明，未给出的则参考其他接口的说明
|msg 中的参数|参数的含义|
|:----------|:--------|
|v1         |通过好友请求时需要用到的 v1|
|v2         |通过好友请求时需要用到的 v2|
|noticeWord |打招呼的消息  |
|xmlmsg     |微信中的原始消息,xml格式|

```json
{
    "data":{
        "action":"reportFriendAddRequest",
        "cwxid":"wxid_qg0saisth0r222",
        "data" : {
                    "wxid":"",
                    "username":"",
                    "nick":"",
                    "headPic":"",
                    "sex":"2",
                    "country":"xxx",
                    "province":"xxx",
                    "city":"xxx",
                    "v1":"xxxxxx",
                    "v2":"xxxxxxx",
                    "noticeWord":"xxxxxxx",
                    "xmlmsg":"xxxxxxxxxxx",
        }
    }
}
```

### 上报新群
#### 个别参数说明，未给出的则参考其他接口的说明
|msg 中的参数|参数的含义|
|:----------|:--------|
|nick       |群昵称，可能为空|
|chatroom   |群的wxid|

```json
{
    "data":{
        "action":"reportChatRoomChange",
        "cwxid":"",
        "data" : {
                    "nick":"",
                    "chatroom":  "",
        }
    }
}
```

### 上报上传客户端上传文件到服务端
#### 个别参数说明，未给出的则参考其他接口的说明
|msg 中的参数|参数的含义|
|:----------|:--------|
|sendResult |服务端接收文件的返回值|

```json
{
    "data":{
        "action":"resUploadFile",
        "cwxid":"",
        "data" : {
                    "errorReason": "",
                    "sendId": "8859663",
                    "sendResult": ""
        }
    }
}
```

# send_msg
## 数据格式
```json
{
    "api" : "",
    "sendId":"",
    "option" : {}
}
```

### 打开微信
```json
{
    "api" : "openWeChat",
    "sendId":"",
    "option" : {}
}
```

### 获取登陆二维码
```json
{
    "api" : "getLoginQrCode",
    "sendId":"",
    "option" : {}
}
```

###  获取登陆状态
```json
{
    "api" : "getLoginStatus",
    "sendId":"",
    "option" : {}
}
```

### 微信退出登录
```json
{
    "api" : "logout",
    "sendId":"",
    "option" : {}
}
```

### 发送文本消息  sendTextMessage

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid         |要发送的对象的微信id|
|text         |消息文本|

```json
{
    "api" : "sendTextMessage",
    "sendId":"",
    "option" : {
        "wxid":"",
        "text":"",
    }
}
```

### 发送图片消息  sendPicMessage

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid         |要发送的对象的微信id|
|imgPath      |图片地址（客户端所在主机的本地图片地址或网络地址）|

```json
{
    "api" : "sendPicMessage",
    "sendId":"",
    "option" : {
        "wxid":"",
        "imgPath":""
    }
}
```

### 发送文件
注意：文件大小建议不要超过50M，否则会发送失败;

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid         |要发送的对象的微信id|
|filePath     |文件地址（客户端所在主机的本地文件地址或网络地址）|

```json
{
    "api" : "sendFileMessage",
    "sendId":"",
    "option" : {
        "wxid":"",
        "filePath":""
    }
}
```

### 发送网页的链接消息(sendXmlMessage)

```json
{
    "api" : "sendXmlMessage",
    "sendId":"",
    "option" : {
        "wxid":"",
        "title":"标题",
        "url":"url链接",
        "desc":"描述",
        "pic":"图片url链接"
    }
}
```

### 发送个人名片

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid         |要发送的对象的微信id|
|wxidCard     |要发送的名片的微信id|

```json
{
    "api" : "sendCardMessage",
    "sendId":"",
    "option" : {
        "wxid":"",
        "wxidCard":""
    }
}
```

### 发送群邀请

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid         |要发送的对象的微信id|
|chatroom     |群的id|

```json
{
    "api" : "sendChatroom",
    "sendId":"",
    "option" : {
        "wxid":"",
        "chatroom":""
    }
}
```

### 获取当前联系人列表

#### 参数说明
flag:
若在reportContact中完整上报[好友+群+公众号]三者的数据会导致数据量太大/冗余,故新增该flag来设置只上报其中一部分关心的数据值，默认为1
含义:
0|不上报任何信息
1|上报好友的信息(friendList)
2|上报群的信息(groupList)
3|上报好友和群的信息(1+2=3)
4|上报公众号的信息(publicList)
5|上报好友和公众号的信息(1+4=5)
6|上报群和公众号的信息(2+4=6)
7|上报所有的信息(1+2+4=7)

```json
{
    "api" : "getContact",
    "sendId":"",
    "option" : {
        "flag":""
    }
}
```


### 获取联系人/公众号的wxid
```json
{
    "api" : "getUsersWxid",
    "sendId":"",
    "option" : {}
}
```


##  好友操作:

### 通过wxid获取联系人/公众号详细信息(一次最少一个，最多五十个)

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxidLists    |需要获取详细信息的微信id|

```json
{
    "api" : "getUsersInfo",
    "sendId":"",
    "option" : {
        "wxidLists":["wxid_qgxxxxxx222", "xyzxxxx53"]
    }
}
```

### 删除好友

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid    |需要删除的好友的微信id|

```json
{
    "api" : "delUser",
    "sendId":"",
    "option" : {
        "wxid":""
    }
}
```

### 同意新好友,通过好友验证
```json
{
    "api" : "acceptFriend",
    "sendId":"",
    "option" : {
        "v1":"",
        "v2":""
    }
}
```

### 修改好友备注

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid    |需要修改备注的好友的微信id|
|asName    |备注信息|

```json
{
    "api" : "updateAsName",
    "sendId":"",
    "option" : {
        "wxid":"",
        "asName":""
    }
}
```

##  群操作:

### 获取某个群的群成员列表详细信息

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid    |需要获取的群的id|

```json
{
    "api" : "getChatRoomUsers",
    "sendId":"",
    "option" : {
        "wxid":""
    }
}
```

### 获取某个群成员的群昵称

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|chatroom     |群的微信id|
|wxid         |群成员的微信id|

```json
{
    "api" : "getChatRoomUserNick",
    "sendId":"",
    "option" : {
        "chatroom":"",
        "wxid":""
    }
}
```

### 踢群成员，当前微信必须有踢人权限(为群主或者群管理员)

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxid         |需要获取的群的id|
|chatroom     |群的微信id|

```json
{
    "api" : "delChatRoomUser",
    "sendId":"",
    "option" : {
        "chatroom":"",
        "wxid":""
    }
}
```

### 修改群名称

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|chatroom    |群的微信id|
|name        |要修改的名称|

```json
{
    "api" : "updateChatRoomName",
    "sendId":"",
    "option" : {
        "chatroom":"",
        "name":""
    }
}
```

###  修改我在本群的昵称

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|chatroom    |群的微信id|
|nick        |要修改的昵称|

```json
{
    "api" : "updateRoomAsName",
    "sendId":"",
    "option" : {
        "chatroom":"",
        "nick":""
    }
}
```

###  加群成员为好友（两条此指令之间的间隔时间不能低于5s）

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|chatroom    |群的微信id|
|wxid        |要加为好友的个人微信id|
|noticeWord  |打招呼的消息|

```json
{
    "api" : "addRoomFriend",
    "sendId":"",
    "option" : {
        "chatroom":"23XXXXX71@chatroom",
        "wxid":"xyz11111",
        "noticeWord":"你好！我是XXX"
    }
}
```

### 创建群聊
注:每个微信号每天能创建的群是有上限的,无限制的创建群会带来封号风险

#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|wxidLists    |要添加群聊的人员的微信id(由于群聊必须至少3个人, 因此必须包含至少2个好友的wxid)|

```json
{
    "api":"createChatRoom",
    "sendId":"",
    "option":{
        "wxidLists":""
    }
}
```

### 退出群聊
#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|chatroom    |群的微信id|

```json
{
    "api":"exitChatRoom",
    "sendId":"",
    "option":{
        "chatroom":""
    }
}
```

### 接受群邀请
#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|url          |入群链接的地址 (该值从上报的入群链接消息的url字段中获取)|

```json
{
    "api":"acceptChatroomInvite",
    "sendId":"",
    "option":{
        "url":"https://support...."
    }
}
```

### 接受转账
#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|transferid   |收哪一笔转账(reportTransferMessage 中的 transferid)|
|wxid         |转账发起者wxid|

```json
{
    "api":"acceptBankTransfer",
    "sendId":"",
    "option":{
        "transferid":"",
        "wxid":""
    }
}
```

### 上传文件到服务器
#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|fileUrl      |文件地址（如：C:/work/demo.md）|
|upUrl        |文件上传的地址（如：http://xxx/upload）|
注：接受上传文件的服务端必须返回一个数字型状态码，这个状态码会返回到sendResult

```json
{
    "api":"uploadFile",
    "sendId":"",
    "option":{
        "fileUrl":"",
        "upUrl":""
    }
}
```

### 关闭进程
#### 参数说明
|option中的参数|参数的含义|
|:------------|:--------|
|pid          |进程id(send_msg 接口中收到的 pid)|

```json
{
    "api":"closeProcess",
    "sendId":"",
    "option":{
        "pid":""
    }
}
```

<a name="cooperation"></a>
## 商务合作
![alt 联系方式](https://github.com/juguang2018/wequick/blob/master/img/xiaore.jpg)

![alt 联系方式](https://wequick-1257130190.cos.ap-shanghai.myqcloud.com/img/service.png)