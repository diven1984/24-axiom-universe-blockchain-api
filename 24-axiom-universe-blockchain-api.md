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
# 24 Axiom Universe Blockchain API Documentation

## 1. Introduction
The 24 Axiom Universe Blockchain is a revolutionary project that aims to permanently chain human civilization records, scientific discoveries, and technological achievements. This API documentation provides detailed information on how to interact with the blockchain, including block queries, data submissions, and node interactions.

## 2. Base URL
The base URL for all API endpoints is: `https://api.24axiom-blockchain.org`

## 3. Authentication
Currently, most endpoints do not require authentication. However, for certain sensitive operations such as submitting large - scale data or joining the observer alliance, authentication may be required in the future. Authentication will be based on digital signatures and public - private key pairs.

## 4. Endpoints

### 4.1 Block Queries

#### 4.1.1 Get a Block by Hash
- **Endpoint**: `/block/{hash}`
- **Method**: `GET`
- **Parameters**:
  - `hash`: The hash of the block you want to retrieve.
- **Response**:
```json
{
    "block_hash": "0x123456789abcdef...",
    "height": 12345,
    "timestamp": 1678901234,
    "previous_block_hash": "0x0987654321abcde...",
    "data": {
        "civilization_records": [
            {
                "id": "1",
                "type": "historical_event",
                "content": "The discovery of America in 1492",
                "observer_tags": ["historian1", "archaeologist2"]
            }
        ],
        "discovery_data": [
            {
                "id": "2",
                "type": "scientific_hypothesis",
                "content": "The theory of relativity",
                "transfinite_recursive_index": "0.1.2.3"
            }
        ],
        "result_validation": [
            {
                "id": "3",
                "type": "theory_verification",
                "content": "The verification result of the theory of relativity",
                "hash_verification": "0xabcdef123456789...",
                "quantum_hash_verification": "0x987654321abcdef..."
            }
        ]
    },
    "hodge_dual_structure": {
        "explicit": "0xabcdef...",
        "implicit": "0xfedcba..."
    }
}
```

#### 4.1.2 Get the Latest Block
- **Endpoint**: `/block/latest`
- **Method**: `GET`
- **Response**: Similar to the response of `/block/{hash}`, but it returns the latest block on the chain.

### 4.2 Data Submissions

#### 4.2.1 Submit Civilization Record
- **Endpoint**: `/data/civilizationRecord`
- **Method**: `POST`
- **Request Body**:
```json
{
    "type": "artwork",
    "content": "The Mona Lisa painting",
    "observer_tags": ["art_critic1", "curator2"]
}
```
- **Response**:
```json
{
    "status": "success",
    "message": "Civilization record submitted successfully",
    "block_hash": "0x123456789abcdef..."
}
```

#### 4.2.2 Submit Discovery Data
- **Endpoint**: `/data/discoveryData`
- **Method**: `POST`
- **Request Body**:
```json
{
    "type": "technical_patent",
    "content": "A new type of battery technology",
    "transfinite_recursive_index": "0.2.4.6"
}
```
- **Response**:
```json
{
    "status": "success",
    "message": "Discovery data submitted successfully",
    "block_hash": "0xabcdef123456789..."
}
```

#### 4.2.3 Submit Result Validation
- **Endpoint**: `/data/resultValidation`
- **Method**: `POST`
- **Request Body**:
```json
{
    "type": "experimental_result",
    "content": "The result of a physics experiment",
    "hash_verification": "0xabcdef123456789...",
    "quantum_hash_verification": "0x987654321abcdef..."
}
```
- **Response**:
```json
{
    "status": "success",
    "message": "Result validation submitted successfully",
    "block_hash": "0x987654321abcdef..."
}
```

### 4.3 Node Interactions

#### 4.3.1 Get the List of Observer Alliance Nodes
- **Endpoint**: `/nodes`
- **Method**: `GET`
- **Response**:
```json
{
    "nodes": [
        {
            "node_id": "node1",
            "ip_address": "192.168.1.100",
            "ethical_curvature_tensor": "0.12345",
            "last_active_time": 1678901234
        },
        {
            "node_id": "node2",
            "ip_address": "192.168.1.101",
            "ethical_curvature_tensor": "0.23456",
            "last_active_time": 1678901235
        }
    ]
}
```

## 5. Error Handling
- **400 Bad Request**: The request is malformed, for example, the parameters are missing or in the wrong format.
- **404 Not Found**: The requested resource (e.g., a block with a non - existent hash) is not found.
- **500 Internal Server Error**: There is an error on the server side. Please try again later or contact the administrator.

## 6. Rate Limiting
To ensure the stability and security of the blockchain, rate limiting is applied to all API endpoints. The current rate limit is 100 requests per minute per IP address. If you exceed the rate limit, you will receive a `429 Too Many Requests` response.

## 7. Versioning
The API is currently in version 1.0. Version numbers will be updated when there are significant changes to the API endpoints, request/response formats, or functionality.


This API documentation provides a comprehensive guide on how to interact with the 24 Axiom Universe Blockchain. Developers can use these endpoints to build various applications on top of the blockchain, such as data retrieval tools, data submission platforms, and node management systems.
