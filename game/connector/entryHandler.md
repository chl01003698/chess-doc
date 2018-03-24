<!-- TOC -->

- [connector](#connector)
  - [获取路由地址](#获取路由地址)
    - [请求参数](#请求参数)
    - [返回参数](#返回参数)

<!-- /TOC -->

## connector

### 获取路由地址

-   **desc** 获取路由地址
-   **request** connector.entryHandler.login

#### 请求参数

```javascript
{
  "token": { "type": string, "required": true, "desc": "登录口令"}
}
```

#### 返回参数

```typescript
{ 
  "shortId": { "type": number, "required": true, "desc": "玩家ShortId" },
  "nickname": { "type": string, "required": true, "desc": "玩家昵称" },
  "isGuest": { "type": boolean, "required": true, "desc": "是否游客" },
  "sex": { "type": number, "required": true, "desc": "性别 1: 男 | 2: 女" },
  "coin": { 
    "card": { "type": number, "required": true, "desc": "当前房卡数量" }
  },
  "headimgurl": { "type": string, "required": true, "desc": "玩家头像URL" },
  "loginAt": { "type": Date, "required": true, "desc": "玩家登录时间" }
}
```
