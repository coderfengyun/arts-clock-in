##coderfengyun's review
Mark today's problem, and what i think about it.
1. solidity's Library, all the functions must be internal/private, or else, it won't be embedded in the contract generation file.
   * Think about it, it's meaningful, because if you define a public/external method in Library, after the merging operation, EOA's may visit these methods, it will be confusing.
   * After that, why the compiler don't enforce this point?
   * After an elaborate investigation, i will post a PR to ethereum's solidity compiler.
2. solidity's Array, must be initialized with length
   * nothing to say about it, read the fucking manu
3. After tring to use solidity to solve trigonometric problem, i notice the shorthand of solidity, just as a flash.
   * subtly notice why Polkadot use rust as pallet's development language.
4. After a lot of using ether.js and web3.js, I notice why polkadot let the meta of the pallets generating automically.
5. After some reading about eht/btc, they must wait about 12 blocks to make sure the finality, i notice why polkadot will introduce the grandapa as the finalization mechanism.
