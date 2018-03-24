<!-- TOC -->

- [Schema](#schema)
    - [GamePlayer](#gameplayer)
    - [RoomInfo](#roominfo)
    - [ddz3GameInfo](#ddz3gameinfo)
- [通用推送](#通用推送)
    - [通知玩家更新房卡](#通知玩家更新房卡)
        - [推送参数](#推送参数)
- [房间推送](#房间推送)
    - [通知系统文字&表情](#通知系统文字表情)
        - [推送参数](#推送参数-1)
    - [通知玩家聊天](#通知玩家聊天)
        - [推送参数](#推送参数-2)
    - [通知房间销毁](#通知房间销毁)
        - [推送参数](#推送参数-3)
    - [通知玩家准备](#通知玩家准备)
        - [推送参数](#推送参数-4)
    - [通知玩家重新登录](#通知玩家重新登录)
        - [推送参数](#推送参数-5)
    - [通知玩家离线](#通知玩家离线)
        - [推送参数](#推送参数-6)
    - [通知断线重连恢复玩家数据](#通知断线重连恢复玩家数据)
        - [推送参数](#推送参数-7)
    - [当本玩家加入房间](#当本玩家加入房间)
        - [推送参数](#推送参数-8)
    - [通知有玩家加入房间](#通知有玩家加入房间)
        - [推送参数](#推送参数-9)
    - [通知有玩家离开房间](#通知有玩家离开房间)
        - [推送参数](#推送参数-10)
    - [通知玩家坐下](#通知玩家坐下)
        - [推送参数](#推送参数-11)
    - [通知玩家坐下](#通知玩家坐下-1)
        - [推送参数](#推送参数-12)
    - [通知玩家站起](#通知玩家站起)
        - [推送参数](#推送参数-13)
    - [通知玩家请求解散游戏](#通知玩家请求解散游戏)
        - [推送参数](#推送参数-14)
    - [通知玩家刷新解散状态列表](#通知玩家刷新解散状态列表)
        - [推送参数](#推送参数-15)
    - [通知玩家解散结果](#通知玩家解散结果)
        - [推送参数](#推送参数-16)
    - [通知游戏销毁](#通知游戏销毁)
        - [推送参数](#推送参数-17)
    - [通知玩家刷新准备状态](#通知玩家刷新准备状态)
        - [推送参数](#推送参数-18)
    - [有玩家断线重连登录](#有玩家断线重连登录)
        - [推送参数](#推送参数-19)
    - [游戏内玩家离线](#游戏内玩家离线)
        - [推送参数](#推送参数-20)
    - [断线重连恢复玩家数据](#断线重连恢复玩家数据)
        - [推送参数](#推送参数-21)
    - [通知玩家大结算](#通知玩家大结算)
        - [推送参数](#推送参数-22)
- [斗地主推送](#斗地主推送)
    - [明牌|开始](#明牌开始)
        - [推送参数](#推送参数-23)
    - [发牌中点击明牌](#发牌中点击明牌)
        - [推送参数](#推送参数-24)
    - [发牌](#发牌)
        - [推送参数](#推送参数-25)
    - [推送倍数](#推送倍数)
        - [推送参数](#推送参数-26)
    - [叫地主](#叫地主)
        - [推送参数](#推送参数-27)
    - [确定地主](#确定地主)
        - [推送参数](#推送参数-28)
    - [叫地主|踢拉|出牌 广播](#叫地主踢拉出牌-广播)
        - [推送参数](#推送参数-29)
    - [踢拉](#踢拉)
        - [推送参数](#推送参数-30)
    - [打牌](#打牌)
        - [推送参数](#推送参数-31)
    - [流局](#流局)
        - [推送参数](#推送参数-32)
    - [结算](#结算)
        - [推送参数](#推送参数-33)
    - [记牌器](#记牌器)
        - [推送参数](#推送参数-34)

<!-- /TOC -->
## Schema

### GamePlayer
```typescript
{
  "id": { "type": string, "required": true, "desc": "玩家Id" },
  "shortId": { "type": number, "required": true, "desc": "玩家ShortId" },
  "nickname": { "type": string, "required": true, "desc": "玩家昵称" },
  "isGuest": { "type": boolean, "required": true, "desc": "是否游客账号" },
  "sex": { "type": number, "required": true, "desc": "1: 男 2: 女" },
  "headimgurl": { "type": string, "required": true, "desc": "头像URL地址" },
  "signature": { "type": string, "required": true, "desc": "玩家个性签名" }
}
```
---
### RoomInfo
```typescript
{
  "roomId": { "type": string, "required": true, "desc": "房间号" },
  "roomName": { "type": string, "default": "", "desc": "房间名称" },
  "currentRound": { "type": number, "required": true, "desc": "当前局数" },
  "state": { "type": string, "required": true, "desc": "游戏当前状态" },
  "playerCount": { "type": number, "required": true, "desc": "最大房间人数" },
  "stateRemain": { "type": number, "default": 0, "desc": "状态剩余秒数" },
  "gamePlayers": { "type": Array<GamePlayer>, "required": true, "desc": "玩家列表" },
  
}
```
---
### ddz3GameInfo
```typescript
{
  "type":"ddz3/sd3/ddz2/ddz4/lz3/tdlz3/pz3"
  "baseScore": { "type": array<number>,"allow":[32,64,128,0], "required": false, "defalut":[0] "desc": "封顶 0无封顶" },
  "cardLandlord": { "type": array<number>,"allow":[1,2], "required": true, "default":[1], "desc": "1 轮流先叫 | 2胜利先叫" },
  "grabLandlord": { "type": array<string>,"allow":["rob", "fractions", "redouble"], "required": true,"default":["redouble"],  "desc": "叫地主 rob叫地主 | fractions三分 |  redouble抢地主" },
  "play": { "type": array<number>, "allow":[1,2,3], "required": true, "default":[1], "desc": "踢拉 1可踢拉 | 2 可踢不可拉 | 3不可踢拉" },
  "sendCards": { "type": array<number>,"allow":[1,2,3], "required":true , "default": [1],  "desc": "发牌 1逐张发| 2两次发完 |3三次发完" },
  "showCard": { "type": array<number>, "allow":[1,2,3],  "required": true, "default":[1], "desc": "明牌 1明牌 | 2不明牌 | 3闷抓 " },
  "JiPaiQi":{ "type": array<number>, "allow":[1,2,3],  "required": true, "default":[1], "desc": "1可使用 2不可使用 " },
  "remaining":{"type":array<number>,"allow":[1,2],"required":true,default:[1],"desc":"剩下几张 1显示 2不显示"},
  "graspBottom": { "type": array<number>, "allow":[1,2], "required": true, "default":[1], "desc": "抓底 1 特殊牌型不可翻 | 2 特殊底牌可翻" },
  "article3": { "type": array<string>,"allow":['1','2','3'], "required": true,"default":[1] "desc": "3张  1可带单 | 2可带队 | 3不带最后出" },
  "plane": { "type": array<string>, "allow":['1','2','3','4'], "required": true, "desc","default":[]: "飞机  1 不可带1对 | 2不可带2队 | 3可带两对 | 4不带最后出" },
  "four": { "type": array<string>,"allow":['1','2'], "required": true,"default":['1','2','3'] "desc": "四张 1 可带单 | 2可带2队 | 3可带1对 " },
}
```
---
## 通用推送

### 通知玩家更新房卡

-   **desc** 通知玩家更新房卡
-   **push** onUpdateCoin

#### 推送参数

```typescript
{ 
  "coin": { "type": object, "required": true, "desc": "玩家货币", keys: {
    "card": { "type": number, "required": true, "desc": "房卡数" }
  }},
  "msg": { "type": string, "required": true, "desc": "更新房卡原因" }
}
```
---
## 房间推送

### 通知系统文字&表情

-   **desc** 通知系统文字&表情
-   **push** onChat

#### 推送参数

```typescript
{ 
  "uid": { "type": string, "required": true, "desc": "玩家Id" },
  "type": { "type": number, "required": true, "desc": "0: 文字 1: 表情" },
  "index": { "type": number, "required": true, "desc": "所选索引" }
}
```
---
### 通知玩家聊天

-   **desc** 通知玩家聊天
-   **push** onChatText

#### 推送参数

```typescript
{ 
  "uid": { "type": string, "required": true, "desc": "玩家Id" },
  "text": { "type": string, "required": true, "desc": "玩家输入文字" }
}
```
---
### 通知房间销毁

-   **desc** 通知房间销毁
-   **push** onGameDestroy

#### 推送参数
---
### 通知玩家准备

-   **desc** 通知玩家准备
-   **push** onGameReady

#### 推送参数

```typescript
{ 
  "uids": { "type": Array<string>, "required": true, "desc": "已准备玩家Id列表", keys: [{
    "type": string, "required": true, "desc": "玩家Id" 
  }]},
  "uid": { "type": string, "required": true, "desc": "玩家Id" }
}
```
---
### 通知玩家重新登录

-   **desc** 通知玩家重新登录
-   **push** onGamePlayerLogin

#### 推送参数

```typescript
{ 
  "uid": { "type": string, "required": true, "desc": "玩家Id" }
}
```
---
### 通知玩家离线

-   **desc** 通知玩家离线
-   **push** onGamePlayerLogout

#### 推送参数

```typescript
{ 
  "uid": { "type": string, "required": true, "desc": "玩家Id" }
}
```
---
### 通知断线重连恢复玩家数据

-   **desc** 通知断线重连恢复玩家数据
-   **push** onRestoreGameInfo

#### 推送参数
[参见 RoomInfo](#roominfo)
---
### 当本玩家加入房间

-   **desc** 当本玩家加入房间
-   **push** onPlayerJoinGame_

#### 推送参数
[参见 RoomInfo](#roominfo)
---
### 通知有玩家加入房间

-   **desc** 通知有玩家加入房间
-   **push** onPlayerJoinGame

#### 推送参数
[参见 GamePlayer](#GamePlayer)
---
### 通知有玩家离开房间

-   **desc** 通知有玩家离开房间
-   **push** onPlayerLeaveGame

#### 推送参数

```typescript
{
  "uid": { "type": string, "required": true, "desc": "玩家Id" },
  "reason": { "type": string, "default": "", "desc": "开发房间原因" }
}
```
---
### 通知玩家坐下

-   **desc** 通知玩家坐下
-   **push** onPlayerSitDown

#### 推送参数

```typescript
{
  "gamePlayer": { "type": GamePlayer, "required": true, "desc": "玩家信息" }
}
```
---
### 通知玩家坐下

-   **desc** 通知玩家坐下
-   **push** onPlayerSitDown

#### 推送参数

```typescript
{
  "gamePlayer": { "type": GamePlayer, "required": true, "desc": "玩家信息" }
}
```
---
### 通知玩家站起

-   **desc** 通知玩家站起
-   **push** onPlayerStandUp

#### 推送参数

```typescript
{
  "uid": { "type": string, "required": true, "desc": "玩家Id" }
}
```
---
### 通知玩家请求解散游戏

-   **desc** 通知玩家请求解散游戏
-   **push** onRequestGameDissolve

#### 推送参数

```typescript
{
  "uid": { "type": string, "required": true, "desc": "玩家Id" },
  "seconds": { "type": number, "required": true, "desc": "解散倒计时秒数" },
  "states": { "type": any, "required": true, "desc": "玩家解散状态" }
}
```
---
### 通知玩家刷新解散状态列表

-   **desc** 通知玩家刷新解散状态列表
-   **push** onRefreshGameDissolve

#### 推送参数

```typescript
{
  "uid": { "type": string, "required": true, "desc": "玩家Id" },
  "states": { "type": any, "required": true, "desc": "玩家解散状态" }
}
```
---
### 通知玩家解散结果

-   **desc** 通知玩家解散结果
-   **push** onGameDissolveResult

#### 推送参数

```typescript
{
  "result": { "tyoe": boolean, "required": true, "desc": "true: 解散成功 | false: 解散失败" }
}
```
---
### 通知游戏销毁

-   **desc** 通知游戏销毁
-   **push** onGameDestroy

#### 推送参数

---
### 通知玩家刷新准备状态

-   **desc** 通知玩家刷新准备状态
-   **push** onGameReady

#### 推送参数

```typescript
{
  "uids": { "tyoe": Array<string>, "required": true, "desc": "已准备玩家Id列表" },
  "uid": { "type": string, "required": true, "desc": "玩家Id" }
}
```
---
### 有玩家断线重连登录

-   **desc** 有玩家断线重连登录
-   **push** onGamePlayerLogin

#### 推送参数

```typescript
{
  "uid": { "type": string, "required": true, "desc": "玩家Id" }
}
```
---
### 游戏内玩家离线

-   **desc** 游戏内玩家离线
-   **push** onGamePlayerLogout

#### 推送参数

```typescript
{
  "uid": { "type": string, "required": true, "desc": "玩家Id" }
}
```
---
### 断线重连恢复玩家数据

-   **desc** 断线重连恢复玩家数据
-   **push** onRestoreGameInfo

#### 推送参数
[参见 RoomInfo](#roominfo)
---
### 通知玩家大结算

-   **desc** 通知玩家大结算
-   **push** onGameFinish

#### 推送参数

```typescript
{
  "results": { "type": Array<any>, "required": true, "desc": "玩家Id", keys: [{
    "uid": { "type": string, "required": true, "desc": "玩家Id" },
    "isGuest": { "type": boolean, "required": true, "desc": "是否是游客账号" },
    "score": { "type": number, "required": true, "desc": "总的输赢积分" },
    "winCount": { "type": number, "required": true, "desc": "玩家赢局数" },
    "loseCount": { "type": number, "required": true, "desc": "玩家输局数" },
    "drawCount": { "type": number, "required": true, "desc": "玩家平局数" }
  }]}
}
```
---
## 斗地主推送

### 明牌|开始

-   **desc** 通知 明牌|开始  当发牌中推送明牌时 不包含 gameStart multiple 字段 
-   **push** dz_onGameStart

#### 推送参数

```typescript
{
  showCard:  { "type": number,  "required": true, "default":1 "desc": "明牌" },
  gameStart: { "type": number,  "required": false, "default":2 "desc": "开始" },
  multiple:  { "type": number,  "required": false, "default":5 "desc": "倍数" }
}
```
---
### 发牌中点击明牌

-   **desc** 发牌中点击明牌
-   **push** dz_onShowCard

#### 推送参数

```typescript
{
  cards:  { "type": array<string>,  "required": true, "desc": "用户的手牌" },
  sid:    { "type": number,  "required": true, "desc": "位置ID" },
  uid:    { "type": string,  "required": true, "desc": "用户ID" }
}
```
---
### 发牌

-   **desc** 发牌
-   **push** dz_onOutput_

#### 推送参数

```typescript
{
  cards:  { "type": array<string>,  "required": true, "desc": "用户的手牌" },
  cardsCount:{"type":number,"require":true,"desc":"手牌数量"},
  showCards:[{
    cards:{ "type": array<string>,  "required": true, "desc": "用户的手牌" },
    sid:{ "type": number,  "required": true, "desc": "位置ID" },
    uid:{ "type": string,  "required": true, "desc": "用户ID" },
    cardCount:{ "type": number,  "required": true, "desc": "用户手牌数量" },
  }],
   JiPaiQI:{
    '3':["03","13","23","33"],
    '4':["03","13","23","33"],
    'X':['4X'],
    'Y':['4Y'],
  }
}
```
---
### 推送倍数

-   **desc** 推送倍数
-   **push** dz_onMultiple

#### 推送参数

```typescript
{
  playerInfo:{
    sid:{ "type": number,  "required": true, "desc": "位置ID"} ,
    mutiple:{ "type": number,  "required": true, "desc": "倍数"} ,
    uid: { "type": number,  "required": true, "desc": "用户ID"} 
  }
}
```
---
### 叫地主

-   **desc** 叫地主
-   **push** dz_onCallZhuang

#### 推送参数

```typescript
{
  action:{
    "state":{ "type": string,  "required": true,"default":"landOwner/callPoints/landGrab", "desc": "landOwner 叫地主 | callPoints 叫分 | landGrab 抢地主"},
    "action": {
      "landOwner|landGrab": { "type": string|array,  "required": true,"default":"landOwner/[1,2,3]/landGrab", "desc": "landOwner 叫地主 | [1,2,3] 叫分 | landGrab 抢地主"}, 
      "notCall":  { "type": string,  "required": true,"default":"notCall", "desc": "notCall 不叫/不抢"}    //不叫地主
    }
    "sid":{ "type": number,  "required": true, "desc": "位置ID"},
  }
}
```

---
### 确定地主

-   **desc** 确定地主
-   **push** dz_onMakeLandlord_

#### 推送参数

```typescript
{
  action:{
    "isFile":{ "type": boolean,  "required": true,"default":"true", "desc": "是否需要翻拍 true 否 | false 是"},
    "action": {
      "kick|sendCard": { "type": string,  "required": true,"default":"kick|sendCard", "desc": "kick 踢 | sendCard 出牌"}, 
      "notKick":  { "type": string,  "required": true,"default":"notKick", "desc": "notKick 不踢"}   
    }
    "state":{ "type": string,  "required": true,"default":"kick|sendCard", "desc": "kick 踢 | sendCard 出牌"},
    "speakSid":{ "type": number,  "required": true, "desc": "说话位置ID"},
    "speakUid":{ "type": string,  "required": true, "desc": "说话的uid"},
    "cards":{ "type": array<string>,  "required": true, "desc": "地主牌或者是翻牌 ","note":"只要本人能收到"},
    "identity":{ "type": string,  "required": true, "desc": "身份 landlord 地主 farmers 农名"},
    "landlordSid":{ "type": number,  "required": true, "desc": "说话位置ID"},
    "landlordUid":{ "type": string,  "required": true, "desc": "说话的uid"},
    "zhuangCards":{ "type": array<string>,  "required": true, "desc": "底牌"}
  }
}
```

---
### 叫地主|踢拉|出牌 广播

-   **desc** 广播
-   **push** dz_onRadio

#### 推送参数

```typescript
{
  "choosed":{ "type": string,  "required": true,"default":"kick|sendCard|landOwner|landGrab|notCall", "desc": "kick 踢 | sendCard 出牌 | landOwner 叫地主 | landGrab 抢地主|notCall | 不抢"}
  "sid":{ "type": number,  "required": true, "desc": "位置ID"},
}
```

---
### 踢拉

-   **desc** 踢拉/加倍
-   **push** dz_kickPush

#### 推送参数

```typescript
{
  "action": {
    "kick|sendCard|follow|pull|addTimes": { "type": string,  "required": true,"default":"kick|sendCard|follow|pull", "desc": "kick 踢 | sendCard 出牌|follow 跟|pull 拉| addTimes 加倍"}, 
    "notKick|notFollow|notPull| notAddTimes":  { "type": string,  "required": true,"default":"notKick|notFollow|notPull", "desc": "notKick 不踢|notFollow 不跟 |notPull 不拉|notAddTimes 不加倍"}   
  }
  "state":{ "type": string,  "required": true,"default":"kick|sendCard|follow|pull", "desc": "kick 踢 | sendCard 出牌|follow 跟|pull 拉|addTimes 加倍"},
  "sid":{ "type": number,  "required": true, "desc": "说话人的位置ID"},
  "playerId":{ "type": string,  "required": true, "desc": "说话的uid"},
}
```

---
### 打牌 

-   **desc** 打牌
-   **push** dz_onInput

#### 推送参数

```typescript
{
  top:{
    playerId:{ "type": string,  "required": true, "desc": "当前用户ID"},
    cards:{"type": array,  "required": true, "desc": "当前人出的牌"},
    lastCards:{"type": array,  "required": true, "desc": "上一个人出的牌"},
    cardType:{"type": array,  "required": true, "desc": "上一个人出的牌的类型"},
    "sid":{ "type": number,  "required": true, "desc": "当前位置ID"},
    "nextSid":{"type":number,"required": true, "desc": "下一个人的位置ID"}
    "lookCard":{"type": array,  "required": true, "desc": "当前人选择的是明牌"}
  },
  next:{
        "restart":{"type":bool,"required": false, "desc": "这一轮每人压的主开始下一轮"}
        "cards":{"type":array,"required": false, "desc": "下个人的手牌"}
        "action":{"type":array,"required": false, "desc": "用户按钮状态 具体参考按钮状态文档"}
  },
  JiPaiQI:{
    '3':["03","13","23","33"],
    '4':["03","13","23","33"],
    'X':['4X'],
    'Y':['4Y']
  }
}
```

---
### 流局 

-   **desc** 流局
-   **push** dz_onLiuJu

#### 推送参数

```typescript
{
  
    flowBureau:{"type":number,"required": true,default:1, "desc": "流局"}
  
}
```

---
### 结算 

-   **desc** 结算
-   **push** dz_onResult

#### 推送参数

```typescript
{
    playerId:{"type":number,"required": true,default:1, "desc": "用户ID"}
    type:{ "type": string,  "required": true, "desc": "身份 landlord 地主 farmers 农名"}
    win:{"type":number,"required": true,default:1, "desc": "赢取的积分"}
    victory:{"type":number,"required": true,default:1, "desc": "1胜利 0失败"}
    sid:{"type":number,"required": true,default:1, "desc": "位置ID"}
    cards:{"type":array,"required": true,default:1, "desc": "用户手牌"}
    isFlowBureau:{"type":number,"required": true,default:1, "desc": "是否流局 1流局 0 非流局"}
    grabLandlord:{"type":number,"required": true,default:1, "desc": "抢地主倍数"}
    bomb:{"type":number,"required": true,default:1, "desc": "炸弹"}
    spring:{"type":number,"required": true,default:1, "desc": "春天"}
    brandCard:{"type":number,"required": true,default:1, "desc": "明牌"}
    lowCard:{"type":number,"required": true,default:1, "desc": "抓底"}
    friedBomb:{"type":number,"required": true,default:1, "desc": "连炸"}
}
```

---
### 记牌器

-   **desc** 记牌器
-   **push** dz_onJiPaiQi

#### 推送参数

```typescript
{
    JiPaiQI:{
    '3':["03","13","23","33"],
    '4':["03","13","23","33"],
    'X':['4X'],
    'Y':['4Y']
  },
  sid:{"type":number,"required": true,default:1, "desc": "位置ID"},
  uid:{"type":number,"required": true,default:1, "desc": "用户ID"},
  JiPaiQi:{"type":boolen,"required": true, "desc":"true 开启| false 关闭"}
}
```