<!-- TOC -->

- [friendHandler](#friendHandler)
  - [获取路由服务器地址端口号](#获取路由服务器地址端口号)
    - [请求参数](#请求参数)
    - [返回参数](#返回参数)

<!-- /TOC -->

## friendHandler
### 添加好友
-   **desc** 添加好友
-   **request** user.friendHandler.addFriend
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "被加好友的标识"}
}
```
#### 返回参数
```javascript
{
  "code":{"type":number,"required":true,"desc":"状态码"}
}
```



---
### 好友列表
-   **desc** 好友列表
-   **request** user.friendHandler.getFriends
#### 返回参数
```javascript
[ 
  { 
    "uid":        {"type":string,"desc": "用户的uid"},
    "shortId":    {"type":number,"desc":"用户的shortId"},
    "nickname":   {"type":string,"desc":"用户的昵称"},
    "headimgurl": {"type":string,"desc":"用户头像url"},       
    "online":     {"type":boolean,"desc":"用户在线状态","value":true|false},true:在线|false:离线
    "status":     {"type":string,"desc":"用户游戏状态","value":"idle"|"ready"|"gaming"}idle:空闲|ready:准备|gaming:游戏中
  } 
]

```



---
### 好友申请列表
-   **desc** 好友申请列表
-   **request** user.friendHandler.getPendings
#### 返回参数
```javascript
[ 
  { 
    "uid":        {"type":string,"desc": "用户的uid"},
    "shortId":    {"type":number,"desc":"用户的shortId"},
    "nickname":   {"type":string,"desc":"用户的昵称"},
    "headimgurl": {"type":string,"desc":"用户头像url"},
  }
]

```



---
### 同意好友申请
-   **desc** 同意好友申请
-   **request** user.friendHandler.agree
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "申请人shortId"}
}
```
#### 返回参数
```javascript
{
  "code":{"type":number,"required":true,"desc":"状态码"}
}
```


---
### 删除好友
-   **desc** 删除好友
-   **request** user.friendHandler.removeFriend
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "被删好友的shortId"}
}
```
#### 返回参数
```javascript
{
  "code":{"type":number,"required":true,"desc":"状态码"}
}
```






---
### 邀请好友进入房间
-   **desc** 邀请好友进入房间
-   **request** user.friendHandler.inviteJoinGame
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "被邀好友的shortId"}
}
```

#### 通知好友被邀请进入游戏
-   **desc** 通知好友
-   **push** onInviteJoinGame
#### 推送参数
```typescript
{
  "nickname":{"type": string, "required": true, "desc": "邀请人昵称"},
  "roomId": { "type": string, "required": true, "desc": "邀请人房间ID"}
}
```
#### 返回参数
```javascript
{
  "code":{ "type":number, "required":true, "desc":"状态码"}
}
```

---
### 拒绝好友邀请
-   **desc** 拒绝好友邀请
-   **request** user.friendHandler.refuseInvite
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "邀请人的shortId"}
}
```
#### 通知好友拒绝邀请
-   **desc** 通知好友拒绝邀请
-   **push** onRefuseInvite
#### 推送参数
```typescript
{
  "shortId": { "type": number, "required": true, "desc": "用户shortId"},
  "nickname":{ "type": string, "required": true, "desc": "用户昵称"}
}
```
#### 返回参数
```javascript
{
  "code":{"type":number,"required":true,"desc":"状态码"}
}
```





---
### 主动进入好友所在房间 
-   **desc** 进入好友所在房间
-   **request** user.friendHandler.joinFriendGame
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "好友的shortId"}
}
```
#### 通知好友想要进入房间一起游戏
-   **desc** 通知好友想要进入房间一起游戏
-   **push** onJoinFriendGame

#### 推送参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "用户的shortId"}
  "nickname":{ "type": string, "required":true,  "desc": "用户昵称"}
}
```
#### 返回参数
```javascript
{
  "code":{"type":number, "required":true, "desc":"状态码"}
}
```


---
### 拒绝进入房间申请
-   **desc** 拒绝进入房间申请
-   **request** user.friendHandler.refuseJoinGame
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "申请进入房间的用户的shortId"}
}
```
#### 通知拒绝进入房间
-   **desc** 通知拒绝进入房间
-   **push** onRefuseJoinGame
-   
#### 推送参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "好友的shortId"}
  "nickname":{ "type": string, "required": true, "desc": "好友昵称"},
}
```
#### 返回参数
```javascript
{
  "code":{"type":number,"required":true,"desc":"状态码"}
}
```



---
### 同意进入房间申请
-   **desc** 同意进入房间申请
-   **request** user.friendHandler.agreeJoinGame
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "申请进入房间的用户的shortId"}
}
```
#### 通知同意进入房间申请
-   **desc** 通知同意进入房间申请
-   **push** onAgreeJoinGame
-   
#### 推送参数
```javascript
{
  "shortId": { "type": number,  "desc": "好友的shortId"}
  "nickname":{ "type": string,  "desc": "好友昵称"},
  "roomId":  { "type": string,  "desc": "房间Id"}
}
```
#### 返回参数
```javascript
{
  "code":{"type":number,"required":true,"desc":"状态码"}
}
```




---
### 获取好友信息 
-   **desc** 获取好友信息
-   **request** user.friendHandler.getUserDetail
#### 请求参数
```javascript
{
  "shortId": { "type": number, "required": true, "desc": "好友的shortId"}
}
```
#### 返回参数
```javascript
 { 
    "uid":        {"type":string,"desc": "用户的uid"},
    "shortId":    {"type":number,"desc":"用户的shortId"},
    "nickname":   {"type":string,"desc":"用户的昵称"},
    "headimgurl": {"type":string,"desc":"用户头像url"},       
    "online":     {"type":boolean,"desc":"用户在线状态","value":true|false},              true:在线|false:离线
    "status":     {"type":string,"desc":"用户游戏状态", "value":"idle"|"ready"|"gaming"}  idle:空闲|ready:准备|gaming:游戏中
    "ip":         {"type":string,"desc":"用户ip地址"},
    "sex":        {"type":number,"desc":"用户性别"}
  } 
```




