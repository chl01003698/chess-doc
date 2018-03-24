<!-- TOC -->

- [sanZhangHandler](#sanzhanghandler)
  - [玩家看牌操作](#玩家看牌操作)
    - [请求参数](#请求参数)
    - [返回参数](#返回参数)
  - [玩家弃牌操作](#玩家弃牌操作)
    - [请求参数](#请求参数-1)
    - [返回参数](#返回参数-1)
  - [玩家跟注,加注,比牌操作](#玩家跟注加注比牌操作)
    - [请求参数](#请求参数-2)
    - [返回参数](#返回参数-2)

<!-- /TOC -->
## sanZhangHandler

### 玩家看牌操作

-   **desc** 玩家看牌操作
-   **request** fgame.sanZhangHandler.checked

#### 请求参数

#### 返回参数

---
### 玩家弃牌操作

-   **desc** 玩家弃牌操作
-   **request** fgame.sanZhangHandler.giveup

#### 请求参数

#### 返回参数

---
### 玩家跟注,加注,比牌操作

-   **desc** 玩家跟注,加注,比牌操作
-   **request** fgame.sanZhangHandler.input

#### 请求参数
```typescript
{
  "type": { "type": number, "required": true, "desc": "0: 跟注 1: 加注 2: 比牌"},
  "param": { "type": number | string, "desc": "1: 填写加注选项 2: 填写比牌玩家ID"}
}
```
#### 返回参数

---
