Rubic钱包提案.md

# 提案：已交付 Rubic 项目的资金申请

**提案：为 Matthew 开发 Rust 版 Qubic 钱包 Rubic 所付出的时间和精力提供资金补偿**

一个健康的加密货币生态系统，其关键组成部分之一是可离线使用的安全原生桌面钱包。迄今为止，还没有一个为此类普通用户设计的钱包。

**Rubic** 是一个用 Rust 语言从零开始编写的 Qubic 钱包和轻节点。它在提供安全性的同时，也兼顾易用性。该项目已完成编写并已开源，可供使用、检查和开发。

欢迎查看代码并下载自动构建的发行版。: [Rubic 币钱包](https://github.com/matthewdarnell/rubic)

---

## 🗳 投票项

- **不支持:**
- **支持:** 批准向 **Matthew** 的钱包支付 (100,000,000,000 (100bn) Qus) 作为开发报酬 `RUBICDEVRDOILARXMHZCUOGLEEKBKUBOEIKCIHDJVAPAWSTDASIZMRGFIVBL`

---

## 🖥 为什么需要 Rubic？

每个加密货币都需要一个直接且安全的方式来存储密钥和生成交易。目前最流行的钱包是基于网页和移动端的，并且大多数应用程序都依赖中心化的 RPC 提供商来查询余额、交易状态等信息。

Rubic 运行在桌面上，使用内存安全的 Rust 语言编写，并且外部依赖极少。它还公开了一个 Web API，可用于构建第三方应用程序。

此外，它维护着一组真实的 Qubic 对等节点网络，这使得 Rubic 不仅是一个桌面钱包，更是 Qubic 的轻节点

---

## 🔏 Rubic 的功能

- 将种子、交易等信息存储在用户计算机上的 SQLite 数据库中。
- 生成 Qu 转账交易
- 跟踪地址余额
- 与 Qubic 节点进行实时通信
- 独立的 Tick 和交易验证
- 完全去中心化

---

## ⚙ 技术说明

1. 存储

- 种子、对等节点 IP 等信息存储在 SQLite3 数据库中
- 始终清楚您的信息存储在哪里：一个独立的 SQL 文件。

2. 密码学

- _功能_：使用 Rust crate sodiumoxide (它[RubicWallet-Proposal-Chinese-modified.md](../../../Downloads/RubicWallet-Proposal-Chinese-modified.md)是 libsodium 的 Binding)
- _钱包密码_：使用 [Argon2](https://docs.rs/sodiumoxide/latest/sodiumoxide/crypto/pwhash/argon2id13/index.html) 进行哈希加盐
- _种子管理_：经钱包密码派生密钥通过 [XSalsa20Poly1305](https://nacl.cr.yp.to/secretbox.html) 进行认证和加密
- _地址_：原生 Rust FourQ 椭圆曲线和 KangarooTwelve 哈希算法实现快速 Qubic 身份生成，无需外部 C 依赖

4. Lite-Node

- Rubic 是去中心化的，不依赖任何中心化 RPC 服务运行。
- 维护一个对等节点集合 (PeerSet)，并通过 TCP 连接到其对等 Qubic 节点
- 动态对等节点发现
- 来自对等节点的实时查询:
  - 实时当前 Tick 数据
  - 账户余额（要求至少 2 [个对等节点结果匹配](https://github.com/MatthewDarnell/rubic/blob/main/store/src/sqlite/identity.rs#L225)）
  - 广播已生成的交易
  - 每个周期（Epoch）的计算器 (Computor)[验证](https://github.com/MatthewDarnell/rubic/blob/main/consensus/src/computor.rs#L40)
  - Tick [验证](https://github.com/MatthewDarnell/rubic/blob/main/consensus/src/quorum_votes.rs#L20)
  - TickData [验证](https://github.com/MatthewDarnell/rubic/blob/main/consensus/src/tick_data.rs#L140)

---

## 🖼 截图

**包含用户界面**:

<img style="max-width: 30%; max-height: 5%;" src="/images/balances.png"/>\
<img style="max-width: 30%; max-height: 5%;" src="/images/peers.png" />\
<img style="max-width: 30%; max-height: 5%;" src="/images/additional_features.png" />

**第三方用户界面（正在开发中)**:

<img style="max-width: 30%; max-height: 5%;" src="/images/tx.png" />\
<img style="max-width: 30%; max-height: 5%;" src="/images/peer.png" />\
<img style="max-width: 20%; max-height: 3%;" src="/images/pw.png" />


---

## 🕞 下一步计划:

- 资产支持
- 与 QX 交互
- 投票功能
- 使 HTTP API 与当前 RPC 接口对齐，以便大多数现有 Qubic 应用程序可以“即插即用”，成为真正的去中心化应用程序

---

## 🔥 总结

本提案可能有些不同寻常，因为它是在产品已交付的前提下提出的。Rubic 的开发源于对 Qubic 项目和社区的支持

这项开发投入了大量的时间进行研究、规划和编码。

我的目标是让它成为一个社区项目，在此基础上可以构建许多去中心化应用程序 (dApps)。

---

非常感谢您的考虑!

♥
<img style="max-width: 3%; max-height: 3%;" src="/images/hz.png" />
♥
