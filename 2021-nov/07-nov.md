## Today's Recommended Topic
1. Solidity Types: https://docs.soliditylang.org/en/v0.8.9/types.html
2. 《Master Etherium》Chapter 7

## Individual Contributors' Review
### coderfengyun's review

coderfengyun's review On Master Ethereum Chapter 7
1. Smart Contract is not controlled by an EOA, controlled by itself.
2. S M's main properties: program; Immutable; Deterministic; Can access to evm context; run on world computer.
3. SM's lifecycle: create->constructor->run->destruct. Contract only run if they are called by a transaction. Transactions are atomic. Transaction act as Contract calls. EVM is a single-threaded machine.
4. Eth high level language: solidity vyper etc.
5. abi: IDL language.
6. Predifined: Transaction Call Context:msg.sender, msg.value, msg.gas, msg.sig. Transaction Context: tx.gasprice, tx.origin. Block Context: block.blockhash, block.coinbase, block.difficulty, block.gaslimit, block.number, block.timestamp. Address Object: address.balance, address.transfer, address.send, address.call, address.delegatecall.
7. Built in funds: this etc.
8. Library: deployed once, delegatecall by contracts.
9. Function modifier: external: only can be called from outside. Internal act as java's protected. Constant: won't modify. Pure: neither read or write storage vars.
10. User defined modifier: act as wrap around.
11. Inheritance: support multi-inheritance.
12.Error handling: assert used to test function's output. Require used to test input.
13. Events: can be watched through res.logs[0].event. 
14. Call other Contract: create a new instance, eg. new Faucet(); Call existing Contract through address eg. Faucet(addr). 
15.call and delegatecall: sender is caller Contract oe the origin EOA.

### dingding's review
1、今天改看《精通以太坊》了，看完了1~3章。有些新知识是之前没留意的，比如内部转账。
