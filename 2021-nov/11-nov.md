##fengyun's review
Smart Contract Security
1. 对其他合约调用发生在状态修改之前：处理方法，应用检查-生效-交互模式。
2. 依赖合约中的以太币数量：因为在destruct时可以随便转账切不会失败。不使用this.balance, 用单独的数据结构存储。
3. Delegatecall: 环境变量覆盖，与solidity状态或变量存储方式有关。使用library关键字，并保证库合约是无状态和不会以我销毁的。

##dingsing's review
1、继续看钱包这一章，接着看了三分之一
