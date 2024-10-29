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