<!-- TOC -->

- [gateHandler](#gatehandler)
  - [获取路由服务器地址端口号](#获取路由服务器地址端口号)
    - [请求参数](#请求参数)
    - [返回参数](#返回参数)

<!-- /TOC -->

## gateHandler

### 获取路由服务器地址端口号

-   **desc** 获取路由服务器地址端口号
-   **request** gate.gateHandler.queryEntry

#### 请求参数
#### 返回参数
```javascript
{
  "host": { "type": string, "required": true, "desc": "IP地址" },
  "port": { "type": number, "required": true, "desc": "端口号" },
}
```
---