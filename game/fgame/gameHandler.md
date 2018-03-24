<!-- TOC -->

- [gameHandler](#gamehandler)
    - [游戏未开始前销毁房间](#游戏未开始前销毁房间)
        - [请求参数](#请求参数)
        - [返回参数](#返回参数)
    - [解散房间](#解散房间)
        - [请求参数](#请求参数-1)
        - [返回参数](#返回参数-1)
    - [解散房间投票](#解散房间投票)
        - [请求参数](#请求参数-2)
        - [返回参数](#返回参数-2)
    - [创建游戏](#创建游戏)
        - [请求参数](#请求参数-3)
        - [返回参数](#返回参数-3)
    - [加入房间](#加入房间)
        - [请求参数](#请求参数-4)
        - [返回参数](#返回参数-4)
    - [离开房间](#离开房间)
        - [请求参数](#请求参数-5)
        - [返回参数](#返回参数-5)
    - [房间内坐下](#房间内坐下)
        - [请求参数](#请求参数-6)
        - [返回参数](#返回参数-6)
    - [房间内站起](#房间内站起)
        - [请求参数](#请求参数-7)
        - [返回参数](#返回参数-7)
    - [游戏玩家准备](#游戏玩家准备)
        - [请求参数](#请求参数-8)
        - [返回参数](#返回参数-8)
    - [游戏房主准备](#游戏房主准备)
        - [请求参数](#请求参数-9)
        - [返回参数](#返回参数-9)
    - [玩家系统文字&表情聊天](#玩家系统文字表情聊天)
        - [请求参数](#请求参数-10)
        - [返回参数](#返回参数-10)
    - [玩家自定义聊天](#玩家自定义聊天)
        - [请求参数](#请求参数-11)
        - [返回参数](#返回参数-11)
    - [获取聊天记录](#获取聊天记录)
        - [请求参数](#请求参数-12)
        - [返回参数](#返回参数-12)
    - [房主踢人](#房主踢人)
        - [请求参数](#请求参数-13)
        - [返回参数](#返回参数-13)

<!-- /TOC -->

## gameHandler

### 游戏未开始前销毁房间

-   **desc** 游戏未开始前销毁房间
-   **request** fgame.gameHandler.destroy

#### 请求参数

#### 返回参数

---

### 解散房间

- **desc** 解散房间
- **request** fgame.gameHandler.dissolve

#### 请求参数
#### 返回参数

---

### 解散房间投票

- **desc** 解散房间投票
- **request** fgame.gameHandler.dissolveVote

#### 请求参数
```typescript
{
  "vote": { "type": boolean, "required": true, "desc": "true: 同意 | false: 拒绝" }
}
```

#### 返回参数

---

### 创建游戏

- **desc** 创建游戏
- **request** fgame.gameHandler.create

#### 请求参数
```typescript
{
  "fakeIds": {
  	"type": Array<number>,
    "required": false,
    "desc": "测试牌组ID",
    "keys": [{ "type": number, "required": true, "desc": "true: 同意 | false: 拒绝" }]
  },
  "config": {
  	"type": object,
    "required": true,
    "desc": "创建房间配置选项",
    "keys": {
      "type": {"type": string, "required": true, "desc": "游戏类型" },
      "expendIndex": { "type": number, "required": true, "desc": "局数索引" },
      "payway": { "type": string, "required": true, "desc": "支付方式 AA|owner|winner" },
      "join": { "type": boolean, "default": true, "desc": "是否直接加入房间" }
    }
  }
}
```
#### 返回参数
---
### 加入房间

- **desc** 加入房间
- **request** fgame.gameHandler.join

#### 请求参数
```typescript
{
  "roomId": { "type": string, "required": true, "desc": "加入房间ID"}
}
```
#### 返回参数
---
### 离开房间

- **desc** 离开房间
- **request** fgame.gameHandler.leave

#### 请求参数
#### 返回参数
---
### 房间内坐下

- **desc** 房间内坐下 (限拼三张&牛牛等非固定人数游戏)
- **request** fgame.gameHandler.sitdown

#### 请求参数
#### 返回参数
---
### 房间内站起

- **desc** 房间内站起 (限拼三张&牛牛等非固定人数游戏)
- **request** fgame.gameHandler.standup

#### 请求参数
#### 返回参数
---
### 游戏玩家准备

- **desc** 游戏玩家准备
- **request** fgame.gameHandler.ready

#### 请求参数
#### 返回参数
---
### 游戏房主准备

- **desc** 游戏房主准备 (限拼三张&牛牛等非固定人数游戏)
- **request** fgame.gameHandler.ownerReady

#### 请求参数
#### 返回参数
---
### 玩家系统文字&表情聊天

- **desc** 玩家系统文字&表情聊天
- **request** fgame.gameHandler.chat

#### 请求参数
```typescript
{
  "type": { "type": number, "required": true, "desc": "0: 文字 1: 表情" },
  "index": { "type": number, "required": true, "desc": "选择索引" }
}
```
#### 返回参数
---
### 玩家自定义聊天

- **desc** 玩家自定义聊天
- **request** fgame.gameHandler.chatText

#### 请求参数
```typescript
{
  "text": { "type": string, "required": true, "desc": "文字内容" }
}
```
#### 返回参数
---
### 获取聊天记录

- **desc** 获取聊天记录
- **request** fgame.gameHandler.chatHistory

#### 请求参数
#### 返回参数
---
### 房主踢人

- **desc** 房主踢人
- **request** fgame.gameHandler.kick

#### 请求参数
```typescript
{
  "uid": { "type": string, "required": true, "要踢出玩家的uid" }
}
```
#### 返回参数
---