##coderfengyun's review
Master Ethereum chapter9 Security
1. External Contract Reference: the reference Contract code may be malicious.
   Preventative tech: new the contract, use it at deployment time. Another is hard code a Contract address, not as a param.
2. Short Address/Parameter Attack: according to the encode under AbI spec, may be sent with shorter than expected length, evm will pad with 0 to the params end.
   Preventative tech: check the params length, reject shorter ones.
3. Unchecked Call Return Values: Call and send function return a boolean result indicating success or failed. When fail, transactions won't revert. 
   Preventative tech: use transfer or check the send's return value. More robust way us to adopt withdraw pattern.
4. Withdraw pattern: one Transaction mark the pending withdraw, a second transaction to do the real withdraw. To escape from 'unusable state, when callee failed the fallback function.'
5. Race condition/front running: attacker watch the trans pool, modify the solver's permission or change state in a Contract, then submit with a higher gasPrice. 
   Preventative tech: place the highest gas. Or use the commit-reveal pattern.
6. Explanation of why front running will happen, though the transaction will be encoded through private key, everyone can see the trans can decode the msg with public key. So they can put a higher gasPrice transaction before the under-attack trans.


##dingding's review:
1、今天继续学习第八章的内容，以太坊智能合约
