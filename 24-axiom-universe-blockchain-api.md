# 24公理宇宙区块链API文档

## 一、概述
本API文档用于描述24公理宇宙区块链系统所提供的接口，该系统致力于将符合24公理的人类文明记录数据、发现数据、科学成果数据进行区块链接，形成人类文明的宇宙区块链主链。

## 二、基础信息
### 2.1 协议
HTTP/HTTPS

### 2.2 数据格式
请求和响应数据均采用JSON格式。

### 2.3 错误处理
所有错误响应都会包含一个`error`字段，其值为错误信息的字符串。例如：{
    "error": "Invalid request parameters"
}
## 三、API接口

### 3.1 区块信息查询
#### 3.1.1 获取指定区块信息
- **接口地址**：`/block/{blockHash}`
- **请求方法**：GET
- **请求参数**：
  | 参数名 | 类型 | 描述 |
  | ---- | ---- | ---- |
  | blockHash | string | 区块的哈希值 |
- **响应示例**：{
    "blockHash": "0x123456789abcdef",
    "height": 100,
    "timestamp": 1630425600,
    "data": {
        "civilizationRecord": "Some civilization record data",
        "discoveryData": "Some discovery data",
        "scientificResult": "Some scientific result data"
    },
    "previousBlockHash": "0x0987654321abcdef",
    "merkleRoot": "0xabcdef123456789"
}
#### 3.1.2 获取最新区块信息
- **接口地址**：`/block/latest`
- **请求方法**：GET
- **响应示例**：{
    "blockHash": "0x987654321abcdef",
    "height": 200,
    "timestamp": 1630425900,
    "data": {
        "civilizationRecord": "New civilization record data",
        "discoveryData": "New discovery data",
        "scientificResult": "New scientific result data"
    },
    "previousBlockHash": "0x123456789abcdef",
    "merkleRoot": "0xdef123456789abc"
}
### 3.2 数据上链
#### 3.2.1 提交文明记录数据
- **接口地址**：`/data/civilizationRecord`
- **请求方法**：POST
- **请求参数**：
  | 参数名 | 类型 | 描述 |
  | ---- | ---- | ---- |
  | civilizationRecord | string | 文明记录数据 |
- **响应示例**：{
    "success": true,
    "message": "Civilization record data submitted successfully",
    "blockHash": "0xabcdef987654321"
}
#### 3.2.2 提交发现数据
- **接口地址**：`/data/discoveryData`
- **请求方法**：POST
- **请求参数**：
  | 参数名 | 类型 | 描述 |
  | ---- | ---- | ---- |
  | discoveryData | string | 发现数据 |
- **响应示例**：{
    "success": true,
    "message": "Discovery data submitted successfully",
    "blockHash": "0xdef987654321abc"
}
#### 3.2.3 提交科学成果数据
- **接口地址**：`/data/scientificResult`
- **请求方法**：POST
- **请求参数**：
  | 参数名 | 类型 | 描述 |
  | ---- | ---- | ---- |
  | scientificResult | string | 科学成果数据 |
- **响应示例**：{
    "success": true,
    "message": "Scientific result data submitted successfully",
    "blockHash": "0x987654321abcdef"
}
### 3.3 节点信息查询
#### 3.3.1 获取节点列表
- **接口地址**：`/nodes`
- **请求方法**：GET
- **响应示例**：{
    "nodes": [
        {
            "nodeId": "node1",
            "ip": "192.168.1.100",
            "port": 8080
        },
        {
            "nodeId": "node2",
            "ip": "192.168.1.101",
            "port": 8081
        }
    ]
}
#### 3.3.2 获取指定节点信息
- **接口地址**：`/nodes/{nodeId}`
- **请求方法**：GET
- **请求参数**：
  | 参数名 | 类型 | 描述 |
  | ---- | ---- | ---- |
  | nodeId | string | 节点的ID |
- **响应示例**：{
    "nodeId": "node1",
    "ip": "192.168.1.100",
    "port": 8080,
    "status": "active",
    "lastSeen": 1630425600
}
## 四、总结
本API文档详细描述了24公理宇宙区块链系统提供的主要接口，涵盖了区块信息查询、数据上链和节点信息查询等功能。通过这些接口，开发者可以方便地与区块链系统进行交互，实现数据的存储和查询等操作。    