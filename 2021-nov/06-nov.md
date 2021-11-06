## Today's Topic
1. 精通以太坊第一章 或 第六章


## Individual Contributor's Review

### coderfengyun: 
1. Ethereum Transaction是一个签名后的消息，从一个EOA账号触发，被Ethereum网络传递并记录在Ethereum区块链上。
2. EVM状态极是个全局单例状态机，ETH transaction是驱动EVM状态机的唯一方式。
3. Transaction包含以下信息：Nonce，Gas Price，Gas limit，Recipient，Value，Data，v｜r｜s；from不包含在Transaction信息中，因为可以从v，r中推算而来。
4. Transaction信息通过RLP序列化，RLP是个简单的序列化算法，每个字段其实时都表明自己的长度，该长度读完后，则是下一个字段。
5. Nonce：标识发出transaction的账号，至今为止发出的transaction总数。Nonce用于保证transction的执行顺序，以及防止复制transaction攻击。可以通过web3.eth.getTransactionCount来获取当前账户已创建的transaction数量。**Nonce之间不能有Gap**，比如不能是nonce=1，nounce=3，ethereum会等待nounce=2的transaction到来，而不会执行nounce=3的transaction。**重复的Nounce只有一个transaction会被执行**。在一个transaction创建并发量要求很大的场景下，一般先由大量机器生成不包含nounce的transaction，再放入队列中，由一台机器进行顺序生成nounce。
6. Gas：Gas的比喻很明确，就是evm状态机的燃料。Gas的单位为wei。Gas与Eth是独立的，二者间的汇率会动态调整。Gas的存在适用于衡量一个Transaction对于EVM状态机的计算，内存，以及存储的消耗程度；与此同时也用于防止对EVM状态机发起的拒绝服务攻击。可以通过web3.eth.getGasPrice(console.log)查询当前的汇率。
7. Recipient：即Ethereum地址。如果该地址是一个没有对应私钥的地址（比如地址0），那么转账过去就相当于将eth销毁。对于地址0来说，它的一个特别作用是来创建contract。
8. Value And Data：二者可以分别存在，或者共同存在。共同存在是表明执行transaction的同时转账。转账可以给EOA转账，也可以给Contract转账。转账可以认为是每个account都有的一个合约，功能就是把对应的value加到account余额中。
9. Data的序列化方式：包含两个信息，方法选择器（方法原型的Keccak-256hash后的前4字节）和方法参数（按照ABI规范中定义的各种基本类型标准来编码）。
10. 创建Contract是一种特殊的transaction：recipient是地址0，data是一个具体合约的ABI信息。
11. 数字签名：ECDSA，基于椭圆形曲线的公司钥机制。数字签名用于解决3个问题，**签名代表私钥的拥有者确认了这个transaction**；且**无法抵赖**；**任何人都无法在签名之后修改transaction data**。数字签名的工作原理Sig=Fsig(Fkeccak256(m), k)，m是RLP编码后的transaction，k是私钥，Fkeccak256是keccak256 hash算法，Fsig是签名算法，Sig是生成的签名。同时Sig=(r,s)。
12. ECDSA签名算法Fsig的数学原理：签名算法首先会以一种加密安全的方式生成一个临时私钥，用以保证用户的真实私钥没办法通过签名后的transactions计算出来。根据该临时私钥再推到出临时公钥：生成一个加密安全的随机数q，用来作为临时私钥，对应的临时公钥Q，通过q和椭圆曲线生成点G计算出来。数字签名中的r就是临时公钥Q的x坐标。然后，通过下面的公式计算签名：s=q^-1(Keccak256(m) + r\*k) (mod p)，其中q是临时私钥，r是临时公钥的x坐标，k是真实私钥，m是transaction data，p是椭圆型曲线的素数阶。整个解密过程就是反方向计算，检查所有的输入；计算w=s^-1 mod p；计算u1 = Keccak256(m) \* w mod p；计算u2=r\*w mod p; 最后计算Q=u1 * _G + u2 \* k; r是数字签名，K时签名者的公钥，m是签名后数据，G是椭圆形曲线生成器的点，p是椭圆形曲线的素数阶。如果Q点的x坐标等于r，那么该签名就是有效的。
13. 实践中的Transaction签名：Sign the Transaction = Sign(Keccak256Hash(RLPSerialize(transaction)))。
