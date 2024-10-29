# 开发手册

**项目名称**：S-AES算法实现加、解密程序  
**开发人员**：王松妍、李晨雨

## 一、项目概述

### 1.1 背景

随着信息技术的迅速发展，数据安全问题愈发突出。加密技术作为保护信息安全的重要手段，被广泛应用于网络通信、数据存储等领域。本项目旨在实现一种基于对称密钥的加密算法，以满足对信息加密和解密的需求。

### 1.2 目的

本项目的主要目的是开发一个易于使用的加密解密系统，提供安全的数据传输和存储方式。通过实现高效的加密算法，确保用户的敏感信息不被非法访问。同时，系统应具备良好的用户体验，使用户能够方便地进行数据加密和解密操作。

### 1.3 主要功能

1. **数据加密与解密**：支持字符串和二进制数据的加密与解密，确保信息的保密性。
2. **双重和三重加密**：提供双重加密和三重加密功能，增强数据安全性。
3. **CBC模式支持**：实现基于CBC（Cipher Block Chaining）模式的加密，增加数据加密的复杂性和安全性。
4. **暴力破解分析**：提供相遇攻击破解双重加密的功能，帮助用户理解加密的脆弱性。
5. **用户友好的界面**：通过Flask框架实现Web界面，简化用户操作流程，提升使用体验。

## 二、环境设置

### 2.1 操作系统

- Windows 10及以上
- macOS 10.15及以上
- Linux（如Ubuntu 20.04及以上）

### 2.2 软件

- **PyCharm**：推荐使用PyCharm作为IDE，确保下载并安装适合您的操作系统的版本。
- **Python**：安装Python 3.6及以上版本。

### 2.3 库

- **Flask**：Web框架，用于构建应用程序。

## 三、项目结构

### 3.1 目录结构

![image](https://github.com/Wang-songyan/S-AES/blob/main/S_AES/photos/1.png)

### 3.2 各个模块/文件的主要功能描述

#### 3.2.1 app.py

1. **Flask 应用**：
   - `app = Flask(__name__)`：初始化 Flask 应用。
   - `@app.route("/")`：返回主页面。

2. **加密相关函数**：
   - `stateMatConstruct(arr)`：将输入的 16 位二进制数组构造成状态矩阵。
   - `stateMatDestorey(mat)`：将状态矩阵转换回 1D 数组。
   - `addKey(arr, key)`：对输入数组和密钥进行异或操作。
   - `halfByteSubstitude(arr)` 和 `inverseHalfByteSubstitude(arr)`：对半字节进行替换和逆替换操作。
   - `rowShift(arr)`：行位移操作。
   - `mulGF(a, b)`：有限域中的乘法操作。
   - `mulGFMat(mat1, mat2)`：有限域中的矩阵乘法。
   - `columnMix(arr)` 和 `inverseColumnMix(arr)`：列混淆和逆列混淆操作。
   - `functionG(w, RCON)`：用于密钥扩展的函数。
   - `generate_key(key)`：生成加密密钥。
   - `encode(key, content)` 和 `decode(key, content)`：分别实现加密和解密操作。
   - `doubleEncode(key, content)` 和 `doubleDecode(key, content)`：实现双重加密和解密。
   - `tripleEncode(key, content)` 和 `tripleDecode(key, content)`：实现三重加密和解密。

3. **字符串处理**：
   - `string_change(string)`：将字符串转换为二进制数组。
   - `encode_str(key, string)` 和 `decode_str(key, string)`：实现字符串的加密和解密。

4. **CBC 模式**：
   - `encodeCBCString(key, string)` 和 `decodeCBCString(key, string)`：实现 CBC 模式下的字符串加密和解密。

5. **暴力破解**：
   - `brute_force_sdes(ciphertext, plaintext)`：通过相遇攻击方法尝试破解双重加密，返回可能的密钥。

#### 3.2.2 S-AES.py

1. **状态矩阵构造和析构**：
   - `stateMatConstruct(arr)`：将16位的0/1数组转换为状态矩阵。
   - `stateMatDestorey(mat)`：将状态矩阵转换回一维数组。

2. **密钥处理**：
   - `addKey(arr, key)`：将输入数组与密钥进行异或操作。
   - `generate_key(key)`：扩展密钥，生成多个子密钥。

3. **替代和变换**：
   - `halfByteSubstitude(arr)`：使用S盒对半字节进行替代。
   - `inverseHalfByteSubstitude(arr)`：逆向S盒替代。
   - `rowShift(arr)`：行位移操作。
   - `columnMix(arr)`：列混淆操作。
   - `inverseColumnMix(arr)`：逆列混淆操作。

4. **有限域运算**：
   - `mulGF(a, b)`：实现有限域乘法。
   - `mulGFMat(mat1, mat2)`：实现有限域矩阵乘法。

5. **加密与解密**：
   - `encode(key, content)`：使用指定密钥对内容进行加密。
   - `decode(key, content)`：使用指定密钥对内容进行解密。
   - `doubleEncode(key, content)`：实现双重加密。
   - `doubleDecode(key, content)`：实现双重解密。
   - `tripleEncode(key, content)`：实现三重加密。
   - `tripleDecode(key, content)`：实现三重解密。

6. **字符串处理**：
   - `string_change(string)`：将字符串转换为二进制数组。
   - `encode_str(key, string)`：对字符串进行加密。
   - `decode_str(key, string)`：对字符串进行解密。
   - `encodeCBCString(key, string)`：使用CBC模式对字符串进行加密。
   - `decodeCBCString(key, string)`：使用CBC模式对字符串进行解密。

7. **相遇攻击**：
   - `brute_force_sdes(ciphertext, plaintext)`：使用相遇攻击方法尝试破解双重加密。

#### 3.2.3 static/

静态文件目录，包含前端资源如JavaScript、CSS预处理文件和图片。
- `js/`：存放JavaScript文件，用于处理前端交互逻辑。
- `scss/`：存放CSS预处理器文件，编译后生成最终CSS文件，用于样式管理。
- `vendor/`：存放外部插件或库。

#### 3.2.4 templates/

HTML模板文件目录，使用Jinja2引擎渲染，动态生成网页内容。
- `binary.html`：用于展示二进制加密的页面。
- `main.html`：网站的主页面模板，展示项目的主要信息或导航。
- `string.html`：用于处理字符串加密的页面。
- `advanced.html`：提供更复杂的加密功能，比如双重加密和三重加密。
- `CBC.html`：专门用于 CBC 模式的加密和解密。

## 四、使用说明

### 4.1 启动和运行项目

1. **安装依赖**：确保你已经安装了 Flask 和其他所需的 Python 依赖包。
2. **克隆或下载项目**：确保你的项目文件结构完整（如 `app.py`、`S_AES.py`、`templates` 和 `static` 文件夹都存在）。
3. **运行 Flask 应用**：Flask 服务器将会启动并监听本地的 `http://127.0.0.1:5000/`。
4. **访问 Web 页面**：打开浏览器，访问 `http://127.0.0.1:5000/`，可以看到项目的主界面。

### 4.2 主要功能的使用指南

#### 4.2.1 二进制加密解密

在导航栏选择 "二进制" ，可执行以下操作：
- **加密**：输入16位二进制明文和密钥，点击 "加密" 进行加密。
- **解密**：输入16位二进制密文和密钥，点击 "解密" 进行解密。

#### 4.2.2 字符串加密解密

在导航栏选择 "字符串" ，可执行以下操作：
- **加密**：输入明文和16位二进制密钥，点击 "加密" 进行加密。
- **解密**：输入密文和密钥，点击 "解密" 进行解密。

#### 4.2.3 多重加密

在主页选择 "高级" 选项卡，可执行以下操作：
- **双重加密**：输入16位二进制明文和32位密钥，点击 "加密" 进行加密。
- **三重加密**：输入16位二进制密文和32位密钥，点击 "加密" 进行加密。
- **查找密钥**：输入16位二进制明文和密文，点击 "攻击！" 查找密钥。

#### 4.2.4 CBC 加密解密

在主页选择 "CBC" 选项卡，可执行以下操作：
- **加密**：输入明文和16位二进制密钥，点击 "加密" 进行加密。
- **解密**：输入密文和密钥，点击 "解密" 进行解密。

#### 4.2.5 关于我们

在此页面可以查看课程和共创者相关信息。

![image](https://github.com/Wang-songyan/S-AES/blob/main/S_AES/photos/2.png)
