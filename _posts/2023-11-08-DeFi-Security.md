---
title: DeFi 安全综述
categories: DeFi, Security
tags:
  - 投研
  - BuidlerDAO
pin: "true"
img_path: /assets/img/
mermaid: "true"
image: DeFi-Security.png
---
## DeFi 安全的重要性

DeFi 的安全问题一直以来都非常关键，自 2021 年以来，DeFi 因为黑客、钓鱼诈骗、地毯式撤资等行为造成了非常多损失。

![](2020-2023-loss-in-hacks.png)
_2020-2023-loss-in-hacks [来源](https://www.footprint.network/chart#eyJjcmVhdGVfbWV0aG9kIjoicHJldmlldyIsImRhdGFzZXQiOmZhbHNlLCJkYXRhc2V0X3F1ZXJ5Ijp7ImRhdGFiYXNlIjozLCJxdWVyeSI6eyJvcmRlci1ieSI6W1siYXNjIixbImZpZWxkIiw5NjUzOCxudWxsXV1dLCJzb3VyY2UtdGFibGUiOjczMDV9LCJ0eXBlIjoicXVlcnkifSwiZGlzcGxheSI6ImJhciIsIm5hbWUiOiIyMDIxLTIwMjMgTG9zcyBJbiBIYWNrcyIsInZpc3VhbGl6YXRpb25fc2V0dGluZ3MiOnsiY29sdW1uX3NldHRpbmdzIjp7IltcInJlZlwiLFtcImZpZWxkXCIsOTY1MzksbnVsbF1dIjp7Im51bWJlcl9zdHlsZSI6ImN1cnJlbmN5In19LCJncmFwaC5kaW1lbnNpb25zIjpbImRhdGUiXSwiZ3JhcGgubWV0cmljcyI6WyJsb3NzX2luX2hhY2tzIl0sImdyYXBoLnNob3dfdmFsdWVzIjp0cnVlLCJncmFwaC54X2F4aXMubGFiZWxzX2VuYWJsZWQiOmZhbHNlLCJncmFwaC55X2F4aXMuYXV0b19zcGxpdCI6ZmFsc2UsInNlcmllc19zZXR0aW5ncyI6eyJsb3NzX2luX2hhY2tzIjp7ImNvbG9yIjoiIzU4NThDRSJ9fX19)_

诸多攻击中，针对智能合约漏洞的黑客攻击是造成资产损失最多的方式，统计 2021 年至 2023 年上半年，总共造成了550 亿美元的损失，平均损失金额占据了 DeFi 市场的 4%。

Web3 领域的攻击涉及多个部分，包括：区块链、钱包、NFT、DAO 等。其中，DeFi 项目的被攻击次数远超其它部分。

![](loss-amount&type-by-project-type.png)
_loss-amount&type-by-project-type [来源](https://www.footprint.network/chart#eyJjcmVhdGVfbWV0aG9kIjoicHJldmlldyIsImRhdGFzZXQiOmZhbHNlLCJkYXRhc2V0X3F1ZXJ5Ijp7ImRhdGFiYXNlIjozLCJxdWVyeSI6eyJhZ2dyZWdhdGlvbiI6W1siYWdncmVnYXRpb24tb3B0aW9ucyIsWyJzdW0iLFsiZmllbGQiLDk2NTMyLG51bGxdXSx7ImRpc3BsYXktbmFtZSI6IkFtb3VudCIsIm5hbWUiOiJBbW91bnQifV0sWyJjb3VudCJdXSwiYnJlYWtvdXQiOltbImZpZWxkIiw5NjUzMSxudWxsXV0sIm9yZGVyLWJ5IjpbWyJkZXNjIixbImFnZ3JlZ2F0aW9uIiwwLG51bGxdXV0sInNvdXJjZS10YWJsZSI6NzMwMn0sInR5cGUiOiJxdWVyeSJ9LCJkaXNwbGF5IjoiYmFyIiwibmFtZSI6Ikxvc3MgQW1vdW50ICYgQ291bnQgYnkgUHJvamVjdCBUeXBlIC0gMjAyM0gxIiwidmlzdWFsaXphdGlvbl9zZXR0aW5ncyI6eyJjb2x1bW5fc2V0dGluZ3MiOnsiW1wibmFtZVwiLFwiQW1vdW50XCJdIjp7Im51bWJlcl9zdHlsZSI6ImN1cnJlbmN5In19LCJncmFwaC5kaW1lbnNpb25zIjpbInByb2plY3RfdHlwZSJdLCJncmFwaC5tZXRyaWNzIjpbIkFtb3VudCIsImNvdW50Il0sImdyYXBoLnNob3dfdmFsdWVzIjp0cnVlLCJncmFwaC54X2F4aXMubGFiZWxzX2VuYWJsZWQiOmZhbHNlLCJncmFwaC55X2F4aXMuYXV0b19zcGxpdCI6ZmFsc2UsInNlcmllc19zZXR0aW5ncyI6eyJBbW91bnQiOnsiY29sb3IiOiIjQzdFQUVBIn0sImNvdW50Ijp7ImF4aXMiOiJyaWdodCIsImRpc3BsYXkiOiJsaW5lIn19fX0=)_

## 常见的攻击行为

### 重入攻击

重入攻击，是指利用智能合约先对外交互、后改变自身状态的漏洞，重复执行某一函数，直至耗尽资源。

![](reentrant-attack.png)
_reentrant-attack [来源](https://www.geeksforgeeks.org/reentrancy-attack-in-smart-contracts/)_

例如，2022 年 7 月，Curve Finance 因为所使用的 Vyper 语言的特定版本，存在重入锁上的漏洞，使得编译时的存储区域（Storage Slots）发生了变化，从而无法防止重入攻击的入侵。

具体来看，当某个状态变量被锁上的时候，实际上是某个存储槽不允许改变。但是如果状态变量和存储槽的对应关系发生改变，那么原先预期被锁住的变量将不会被锁住，从而能够被改变。

### 三明治攻击

三明治攻击是指，在一笔大额交易发生之后，立刻以更高的手续费发起一笔交易，从而在买入即将被大额买入的资产，并在大额交易处理后，立刻卖出赚取差价。

![](sandwich-attack.png)
_sandwich-attack [来源](https://beincrypto.com/learn/sandwich-attacks-explained/)_

例如，David 希望通过 ETH-DAI 流动池，将 200000 ETH 兑换为 100 ETH。

这一交易信息在发送到公共的内存池（mempool）后，被 Roger 发现。于是，Roger 立刻发起了一笔资金量同样为 200000 DAI 甚至更多的交易，并且让手续费高于 David 的手续费，从而让自己的交易被优先处理。

在完成 Roger 的交易后，由于交易滑点的存在，交易池中 ETH 和 DAI 的兑换比例降低了，David 实际获得的 ETH 可能只有 95 ETH. 而且，由于 David 的购入，交易滑点继续产生，200000 DAI 只能够兑换91 ETH.

此时，Roger 再发起 ETH 兑换为 DAI 的交易，从而将之前兑换的 100 ETH 换成了大约 220000 DAI，赚取了 20000 DAI 的利润。

## 参考资料

1. 文章：
	1. [Breaking: Curve Finance pools exploited by over $47M due to reentrancy vulnerability](https://www.tradingview.com/news/cointelegraph:b0dee2149094b:0-breaking-curve-finance-pools-exploited-by-over-47m-due-to-reentrancy-vulnerability/)
	2. [A Beginner’s Guide to Sandwich Attacks in DeFi](https://beincrypto.com/learn/sandwich-attacks-explained/)
2. 数据：[Footprint × Beosin H1 2023 Web3 Security Report](https://www.footprint.network/@Beosin/Footprint-Beosin-H1-2023-Report)
3. 视频：[DeFi安全與監管.mp4](https://drive.google.com/file/d/18HNSjpuCFDRZYVJZF8aeuYY89mCBL9C1/view)
4. 对话：[DeFi中的rug pull](https://chat.openai.com/share/2c79a1ff-2e87-4eec-8b72-f7d559bf331d)