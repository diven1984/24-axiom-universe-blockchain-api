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
# 24 公理宇宙区块链开发说明

## 一、简介
24 公理宇宙区块链项目旨在打造一个基于 24 条核心公理的去中心化区块链系统，用于永久记录人类文明、科学发现和技术成果。本开发说明将详细介绍该区块链系统的开发环境搭建、核心代码结构、开发流程以及测试部署等方面的内容，帮助开发者快速上手进行相关开发工作。

## 二、开发环境搭建

### 2.1 硬件要求
- **CPU**：建议使用多核处理器，如 Intel Core i7 或 AMD Ryzen 7 及以上，以满足区块链节点运行时的计算需求。
- **内存**：至少 8GB 内存，若要同时运行多个节点或进行大规模数据处理，建议 16GB 及以上。
- **存储**：由于区块链数据会不断增长，需要至少 200GB 的可用硬盘空间，推荐使用固态硬盘（SSD）以提高读写速度。
- **网络**：稳定的网络连接，带宽建议不低于 100Mbps，以确保节点之间的数据传输和同步。

### 2.2 软件依赖
- **操作系统**：支持 Linux（如 Ubuntu 18.04 及以上）、Windows 10 及以上或 macOS 10.14 及以上。
- **编程语言**：主要使用 Python 3.9 及以上版本进行开发，部分核心算法可能会使用 C++ 进行优化。
- **数据库**：采用 MySQL 或 PostgreSQL 作为存储节点信息和交易数据的数据库，同时使用 IPFS 进行文件存储。
- **开发工具**：推荐使用 Visual Studio Code 或 PyCharm 作为代码编辑器，方便进行代码编写、调试和版本管理。

### 2.3 安装步骤

#### 2.3.1 安装 Python
- **Linux**：
```bash
sudo apt update
sudo apt install python3 python3-pip
```
- **Windows**：从 [Python 官方网站](https://www.python.org/downloads/) 下载并安装 Python 3.9 及以上版本，安装过程中勾选“Add Python to PATH”选项。
- **macOS**：可以使用 Homebrew 进行安装：
```bash
brew install python3
```

#### 2.3.2 安装数据库
- **MySQL**：
    - **Linux**：
```bash
sudo apt install mysql-server
```
    - **Windows**：从 [MySQL 官方网站](https://dev.mysql.com/downloads/installer/) 下载并安装 MySQL 社区版。
    - **macOS**：使用 Homebrew 安装：
```bash
brew install mysql
```
- **PostgreSQL**：
    - **Linux**：
```bash
sudo apt install postgresql postgresql-contrib
```
    - **Windows**：从 [PostgreSQL 官方网站](https://www.postgresql.org/download/windows/) 下载并安装。
    - **macOS**：使用 Homebrew 安装：
```bash
brew install postgresql
```

#### 2.3.3 安装 IPFS
- **Linux**：
```bash
wget https://dist.ipfs.io/go-ipfs/v0.12.2/go-ipfs_v0.12.2_linux-amd64.tar.gz
tar xvfz go-ipfs_v0.12.2_linux-amd64.tar.gz
cd go-ipfs
sudo bash install.sh
```
- **Windows**：从 [IPFS 官方网站](https://dist.ipfs.io/go-ipfs/v0.12.2/go-ipfs_v0.12.2_windows-amd64.zip) 下载并解压，将 `ipfs.exe` 所在目录添加到系统环境变量中。
- **macOS**：
```bash
wget https://dist.ipfs.io/go-ipfs/v0.12.2/go-ipfs_v0.12.2_darwin-amd64.tar.gz
tar xvfz go-ipfs_v0.12.2_darwin-amd64.tar.gz
cd go-ipfs
sudo bash install.sh
```

#### 2.3.4 克隆项目代码
```bash
git clone https://github.com/24axiom-universe-blockchain/24axiom-blockchain.git
cd 24axiom-blockchain
pip install -r requirements.txt
```

## 三、核心代码结构

### 3.1 项目目录结构
```
24axiom-blockchain/
├── config/          # 配置文件目录
│   ├── node_config.py  # 节点配置文件
│   ├── db_config.py    # 数据库配置文件
│   └── ipfs_config.py  # IPFS 配置文件
├── core/            # 核心代码目录
│   ├── block.py      # 区块类定义
│   ├── transaction.py  # 交易类定义
│   ├── consensus.py  # 共识算法实现
│   └── blockchain.py # 区块链类定义
├── api/             # API 接口目录
│   ├── block_api.py  # 区块查询 API
│   ├── transaction_api.py  # 交易查询与提交 API
│   └── node_api.py   # 节点信息 API
├── utils/           # 工具函数目录
│   ├── crypto_utils.py  # 加密工具函数
│   ├── db_utils.py   # 数据库操作工具函数
│   └── ipfs_utils.py # IPFS 操作工具函数
├── tests/           # 测试代码目录
│   ├── test_block.py  # 区块类测试
│   ├── test_transaction.py  # 交易类测试
│   └── test_consensus.py  # 共识算法测试
└── main.py          # 项目入口文件
```

### 3.2 核心类和函数说明

#### 3.2.1 `core/block.py`
- **`Block` 类**：表示区块链中的一个区块，包含区块头和区块体信息。
```python
class Block:
    def __init__(self, index, previous_hash, timestamp, transactions, nonce=0):
        self.index = index
        self.previous_hash = previous_hash
        self.timestamp = timestamp
        self.transactions = transactions
        self.nonce = nonce
        self.hash = self.calculate_hash()

    def calculate_hash(self):
        # 计算区块的哈希值
        pass
```

#### 3.2.2 `core/transaction.py`
- **`Transaction` 类**：表示一笔交易，包含交易的发送方、接收方、金额等信息。
```python
class Transaction:
    def __init__(self, sender, receiver, amount, timestamp):
        self.sender = sender
        self.receiver = receiver
        self.amount = amount
        self.timestamp = timestamp
        self.signature = None

    def sign_transaction(self, private_key):
        # 对交易进行签名
        pass

    def verify_signature(self):
        # 验证交易签名
        pass
```

#### 3.2.3 `core/consensus.py`
- **`ProofOfWork` 类**：实现工作量证明共识算法。
```python
class ProofOfWork:
    def __init__(self, block):
        self.block = block
        self.difficulty = 4

    def mine_block(self):
        # 挖矿过程
        pass

    def validate_block(self, block):
        # 验证区块是否合法
        pass
```

#### 3.2.4 `core/blockchain.py`
- **`Blockchain` 类**：表示整个区块链，包含添加区块、验证区块链等功能。
```python
class Blockchain:
    def __init__(self):
        self.chain = [self.create_genesis_block()]
        self.transactions = []

    def create_genesis_block(self):
        # 创建创世区块
        pass

    def add_block(self, new_block):
        # 添加新的区块到区块链
        pass

    def add_transaction(self, transaction):
        # 添加新的交易到交易池
        pass

    def mine_transactions(self, miner_address):
        # 挖矿处理交易池中的交易
        pass

    def is_chain_valid(self):
        # 验证区块链的完整性
        pass
```

## 四、开发流程

### 4.1 需求分析与设计
在开始开发之前，需要对项目的需求进行详细分析，明确系统的功能和性能要求。根据需求设计系统的架构和模块划分，确定各个模块之间的接口和交互方式。

### 4.2 代码编写与实现
根据设计文档，按照项目的代码结构和规范进行代码编写。在编写代码过程中，要注意代码的可读性、可维护性和可扩展性，遵循编程最佳实践。

### 4.3 单元测试
编写单元测试代码，对各个模块和函数进行测试，确保其功能的正确性。可以使用 Python 的 `unittest` 或 `pytest` 框架进行单元测试。例如，在 `tests/test_block.py` 中对 `Block` 类进行测试：
```python
import unittest
from core.block import Block

class TestBlock(unittest.TestCase):
    def test_calculate_hash(self):
        block = Block(0, "0", 1630435200, [])
        hash_value = block.calculate_hash()
        self.assertEqual(type(hash_value), str)

if __name__ == '__main__':
    unittest.main()
```

### 4.4 集成测试
在单元测试通过后，进行集成测试，验证各个模块之间的交互是否正常。可以模拟不同的场景和数据，检查系统的整体功能和性能。

### 4.5 优化与调试
根据测试结果，对代码进行优化和调试，解决发现的问题和漏洞。优化代码的性能，提高系统的稳定性和可靠性。

## 五、测试与部署

### 5.1 测试环境搭建
可以使用本地虚拟机或云服务器搭建测试环境，部署多个节点进行测试。确保测试环境与生产环境尽量一致，以便发现潜在的问题。

### 5.2 功能测试
对系统的各项功能进行全面测试，包括区块查询、交易提交、共识算法验证等。使用测试工具和脚本模拟不同的用户操作和数据，检查系统的响应和处理结果。

### 5.3 性能测试
使用性能测试工具，如 Apache JMeter 或 Gatling，对系统的性能进行测试。测试系统在高并发情况下的响应时间、吞吐量和资源利用率等指标，评估系统的性能瓶颈和可扩展性。

### 5.4 安全测试
进行安全测试，检查系统的安全性和漏洞。可以使用漏洞扫描工具，如 Nmap、Metasploit 等，对系统进行漏洞扫描和渗透测试，及时发现并修复安全隐患。

### 5.5 部署到生产环境
在测试通过后，将系统部署到生产环境。可以使用容器化技术，如 Docker 和 Kubernetes，进行应用的打包和部署，提高部署的效率和可管理性。同时，要做好生产环境的监控和维护工作，及时处理系统的异常情况。


This API documentation provides a comprehensive guide on how to interact with the 24 Axiom Universe Blockchain. Developers can use these endpoints to build various applications on top of the blockchain, such as data retrieval tools, data submission platforms, and node management systems.
