---
title: LSD 综述【Buidler DAO 投研系列第五课笔记】
categories: [DeFi, LSD]
tags:
  - 投研
  - BuidlerDAO
pin: "true"
img_path: /assets/img/
mermaid: "true"
image:
---
## LSD 概述

LSD 全称 Liquid Staking Derivative，代表流动性挖矿及其衍生品。它主要代指为以太坊网络提供 ETH 质押及其衍生的服务，例如降低质押门槛、获得质押凭证、完善质押凭证的金融市场等。

### LSD 发展历程

![LSD Development Roadmap](<LSD-Development-Roadmap.png>)
_LSD Development Roadmap_

LSD 起源于 ETH 提出要转为 POS 共识机制。但是，当时只有满足32个 ETH 门槛才能进行质押，并且在上海升级之前无法提取流动性。

为了解决这一问题，Lido, Binance staked ETH 和 Rocket Pool 相继给出了自己的解决方案。以 Lido 为例，散户可以质押任意金额的 ETH，并且可以获得质押凭证，散户可以随时利用这些凭证进行交易，这样便解决了高门槛和低流动性的问题。

随着 LSD 的发展，又出现了新的金融活动，例如 EigentLayer 所提出的 Restaking。

这些新金融场景的出现，让 LSD 越来越繁荣，也成为了当前 DeFi 领域中 TVL 排名第二的赛道。

### LSD 层次架构

![Ethereum Staking Ecosystem](<Ethereum-Staking-Ecosystem.png>)
_Ethereum Staking Ecosystem_

LSD 从层次上看，可以从底层到顶层划分成为4个层次：

1. Node Operation(NoOpS): 这一层是实际执行网络验证的层次，验证者会在这一层级基于 POS 的共识机制对交易进行验证。
2. Staking Layer Protocal(LSP): 这一层用来收集低于32ETH验证门槛的资金，将散户的钱集中在一起，从而满足 32 ETH 的验证门槛。
3. Liquid Staking Token(LST): 这一层指代用户质押代币后，所获得的代币质押证明。用户可以将这一证明用于 DEX 的流动性提供，也可以用借贷，从而提高资本利用效率。
4. LSD DeFi(LSDFi): 这一层指代专门基于 LST 和 LSP 来提供服务的应用，其中又可以分成多个子类。

> todo:
> 1. LSD 分类
> 2. LSDFi 概述
> 3. LSDFi 分类

## 参考资料

1. 视频：[Buidler DAO 第五课视频](https://drive.google.com/file/d/1fMv2mXzRctNl93s9hzr9tEiKIoM8znfu/view)