
<!-- TOC -->

- [Schema](#schema)
    - [BetInfo](#betinfo)
    - [BeatInfo](#beatinfo)
- [房间规则](#房间规则)
    - [普通玩法](#普通玩法)
- [拼三张推送](#拼三张推送)
    - [通知开始三张游戏](#通知开始三张游戏)
        - [推送参数](#推送参数)
    - [通知第一次跟注|加注|比牌消息](#通知第一次跟注加注比牌消息)
        - [推送参数](#推送参数-1)
    - [看牌](#看牌)
        - [推送参数](#推送参数-2)
    - [群比推送](#群比推送)
        - [推送参数](#推送参数-3)
    - [结算](#结算)
        - [推送参数](#推送参数-4)
    - [广播](#广播)
        - [推送参数](#推送参数-5)
    - [通知玩家发牌消息](#通知玩家发牌消息)
        - [推送参数](#推送参数-6)
    - [通知比牌结果](#通知比牌结果)
        - [推送参数](#推送参数-7)
    - [通知派彩结果](#通知派彩结果)
        - [推送参数](#推送参数-8)
    - [通知游戏结束](#通知游戏结束)
        - [推送参数](#推送参数-9)

<!-- /TOC -->
## Schema

### BetInfo
```typescript
{
  "once": { "type": number, "required": true, "desc": "当前加注额度" },
  "sum": { "type": number, "required": true, "desc": "当前总注" },
  "round": { "type": number, "required": true, "desc": "当前比牌轮数" }
}
```
---
### BeatInfo
```typescript
{
  "win": { "type": boolean, "required": true, "desc": "是否比牌胜利"},
  "info": { "type": Array<object>, "required": true, "desc": "参与比牌玩家", keys: [{
    "uid": { "type": string, "required": true, "desc": "玩家Id" }
  }]}
}
```
---
## 房间规则

### 普通玩法
```typescript
{
  "wanfa": { "type": number, "default": 0, "desc": "0: 普通 1: 闪电玩法" },
  "shunzida": { "type": boolean, "default": false, "desc": "true: 顺子大 false: 同花大" },
  "paicai": { "type": boolean, "default": false, "desc": "是否需要派彩" },
  "menpai": { "type": number, "default": 0, "desc": "闷牌轮数,闷牌轮数范围内无法看牌" },
  "difen": { "type": number, "default": 1, "desc": "游戏底分设置" },
  "lunshu": { "type": number, "default": 5, "desc": "游戏封顶轮数" },
  "ersanwu": { "type": boolean, "default": false, "desc": "是否需要带235" },
  "jiazhu": { "type": number, "default": 0, "desc": "0: 2, 3, 4, 5 1: 2, 3, 5, 10" },
  "fangzuobi": { "type": boolean, "default": false, "desc": "防作弊,看牌之后只能比牌"}
}
```
---

## 拼三张推送

### 通知开始三张游戏

-   **desc** 通知开始三张游戏
-   **push** sz_onGameStart

#### 推送参数

```typescript
{ 
  "beatIds": { "type": Array<string>, "required": true, "desc": "参与游戏的玩家ID数组"},
  "betInfo" { "type": BetInfo, "required": true, "desc": "筹码轮次信息" },
  "zhuangId": { "type": string, "required": true, "desc": "庄家ID" },
  "round": { "type": number, "required": true, "desc": "当前局数" },
  "zhuangSid":{ "type": number, "required": true, "desc": "庄家位置ID" },
  "LzCards": { "type": Array<string>, "required": true, "desc": "懒子牌数组 勾选癞子时便有此字段"},
  "sumScore":{ "type": number, "required": true, "desc": "桌面上的筹码" },
}
```
---
### 通知第一次跟注|加注|比牌消息

-   **desc** 通知第一次跟注|加注|比牌消息
-   **push** sz_onFirstInput

#### 推送参数

```typescript
{ 
  "speakUid": { "type": string, "required": true, "desc": "第一次执行操作的玩家ID" }
  "speakSid": { "type": int, "required": true, "desc": "说话人的位置ID" },
  "qipai": 1, //弃牌
  "jiazhua": 1,//加注
  "gengzhu": 1, //跟注
  "kanpai": 1, //看牌
  "addBets":[1, 2, 4, 5, 10, 20] //下注的筹码
  "huoping":1 //火拼
  "huopinAddBets"[100] //火拼分数
}
```
---
### 看牌

-   **desc** 看牌
-   **push** sz_onShowCards_ 

#### 推送参数

```typescript
{ 
  action:{
    "speakUid": { "type": string, "required": true, "desc": "第一次执行操作的玩家ID" }
    "speakSid": { "type": int, "required": true, "desc": "说话人的位置ID" },
    "qipai": 1, //弃牌
    "jiazhua": 1,//加注
    "gengzhu": 1, //跟注
    "kanpai": 1, //看牌
    "addBets":[1, 2, 4, 5, 10, 20] //下注的筹码
    "huoping":1 //火拼
    "huopinAddBets":[200] //火拼分数
    "bipai":1 //比牌
  },
  cards:['1.2','1.2','1.2'] //牌
}
```
---
### 群比推送

-   **desc** 群比推送
-   **push** sz_onQunBi 

#### 推送参数

```typescript
{ 
  state :"qunbi"
  victory:[{sid:_player.sid,uid:_player.uid,cards:_player.cards}]
  failure:[{sid:_player.sid,uid:_player.uid,cards:_player.cards}]
}
```
---

### 结算

-   **desc** 结算推送
-   **push** sz_onGameResult 

#### 推送参数

```typescript
{ 
  state :"结算"
  victory:[{sid:_player.sid,uid:_player.uid,cards:_player.cards,win:123}]
  failure:[{sid:_player.sid,uid:_player.uid,cards:_player.cards,win:-123}]
}
```
---

### 广播

-   **desc** 广播
-   **push** sz_onRadio 

#### 推送参数

```typescript
{ 
     "state": "follow|bet|bipai|qipai",         //follow 跟注 bet 加注 bipai
      sid: gamePlayer.index,    //跟组的位置ID
      uid: gamePlayer.uid,      //跟住的
      score: gamePlayer.score,  //更注用户的积分
      type: type,               //更正类型
      sumScore:this.sumScore    //桌面的筹码总数
      chip:this.chip            //跟注筹码
      
}
{ 
     "state": "bipai",         //follow 跟注 bet 加注 bipai
      "victory":{              //胜利用户
        sid:1,
        uid:1
      }
      "failure":{             //失败用户
        sid:1,
        uid:1
      }
      
}
```
### 通知玩家发牌消息

-   **desc** 通知玩家发牌消息
-   **push** sz_onOutput

#### 推送参数

```typescript
{ 
  "cards": [{"type": string, "required": true, "desc": "卡牌Id -1代表背面"}]  
  "sid": [{"type": int, "required": true, "desc": "位置ID"}]  
  "uid": [{"type": string, "required": true, "desc": "用户ID"}]  
}
```
---
### 通知比牌结果

-   **desc** 通知比牌结果
-   **push** sz_onBeatGroup

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
### 通知派彩结果

-   **desc** 通知派彩结果
-   **push** sz_onPaiCai

#### 推送参数

```typescript
{ 

}
```
---
### 通知游戏结束

-   **desc** 通知游戏结束
-   **push** sz_onGameOver

#### 推送参数

```typescript
{ 

}
```
---