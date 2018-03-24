<!-- TOC -->

- [diZhuHandler](#diZhuHandler)
  - [明牌开始](#明牌开始)
    - [请求参数](#请求参数)
    - [返回参数](#返回参数)
  - [叫地主](#叫地主)
    - [请求参数](#请求参数)
    - [返回参数](#返回参数)
  - [踢拉](#踢拉)
    - [请求参数](#请求参数)
    - [返回参数](#返回参数)
  - [打牌](#打牌)
    - [请求参数](#请求参数)
    - [返回参数](#返回参数)
## diZhuHandler

### 明牌开始

-   **desc** 明牌开始
-   **request** fgame.diZhuHandler.showCards

#### 请求参数
```typescript
{
  "multiple": { "type": number, "required": false, "desc": "倍数默认1" }
  "state":{"type": number, "required": true, "min":1,"max":3 "desc": "1 明牌 | 2 开始 | 3 发牌后点击明牌"}
}
```
#### 返回参数

---

### 叫地主

-   **desc** 
-   **request** fgame.diZhuHandler.call

#### 请求参数
```typescript
{
  "choosed": { "type": string, "required": true, "desc": "landOwner 叫地主| notCall 不叫 | landGrab 抢地主 | 1  2  3 代表的1分 2分 3分" }
}
```
#### 返回参数

---

### 踢拉

-   **desc** 
-   **request** fgame.diZhuHandler.kickPull

#### 请求参数
```typescript
{
  "choosed": { "type": string, "required": true, "desc": "kick 踢| notKick 不踢 | follow 跟 | notFollow 不跟 | pull 拉 | notPull 不拉" }
}
```
#### 返回参数

---

### 打牌

-   **desc** 
-   **request** fgame.diZhuHandler.input

#### 请求参数
```typescript
{
  "cards": { "type": array<string>, max:20  "required": true, "desc": "出的牌" },
  "cardsType":{"type": string  "required": false, "desc": "出的牌类型" },
  
}
```
#### 返回参数
```typescript

{
  code: 4012,
  msg: "还没有轮到你" 
}

{
  code: 4012,
  msg: "还没有轮到你" 
}
```
---

### 打牌

-   **desc** 
-   **request** fgame.diZhuHandler.JiPaiQi

#### 请求参数
```typescript
{
  "choosed": { "type": boolen, "default":true, "desc": "开启记牌器 true开启 false 关闭" }
}
```
#### 返回参数
```