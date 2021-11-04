
## Todays Study Plan

1. Crypto Punk's Contract: https://github.com/larvalabs/cryptopunks/tree/master/contracts
2. neon lab's evm on solana architecture: https://docs.neon-labs.org/docs/devportal/neon_evm_arch/
3. solidity language 0.8.9, Structure of a Contract: https://docs.soliditylang.org/en/v0.8.9/structure-of-a-contract.html 

## Individual Contributor's Review On the Topics

### coderfengyun：
1. [DONE]Crypto Punk：被老杨喷了，Crypto Punk太老了，不符合ERC-721规范；抛出这一点，只是单纯从代码看，也还是有诸多问题的：比如，setInitialOwner竟然可以强行覆盖已经有了owner的nft归属，虽然权限控制在只有contract owner才能调用，但也过于霸道了；以及，纯从代码角度也存在着不少重复（尤其是对于nft 是initial归属的情况下对于nft总数的修改等逻辑）。综上Crypto Punk的合约确实不具备太多的参考价值。
2. [ING]neon lab' evm：neon labs的evm方案依赖于一个proxy，将ethereum的transaction转换成多个solana的transaction。对于该方案有些疑问：1. 如何保证proxy是没有问题的，不会对用户的transaction篡改，某种程度讲，这是过于中心化的一个方案，当然项目方也很聪明，引入了一个operator的角色，试图通过激励方案使得operator高效的做正确的事，但感受上始终还是有些脆弱。2. arch文档这个transaction转换成原本可以在前端上完成，但未充分解释，为何不采用该解决方案，难道是为了做风险转移？
3. [DONE]solidity版本升级较快，一些老版本的contructor写法不再支持；throw等写法不再支持；方法modifier也存在着较大程度的改变；总体还是要重新适应。

### 丁丁:
