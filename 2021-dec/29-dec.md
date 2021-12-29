##Coderfengyun's review

Substrate's generic Types: https://github.com/shawntabrizi/substrate-trait-tutorial
1. Substrate泛型的复杂总共体现在两个方面：
1) 在Rust语法中"::"的用途较多，容易混淆，比如TA既可以作为namespace的分隔符,eg. let user1: <Runtime as step5::trait>::AccountId = 1; 用可以用来指定泛型的具体类型，eg. step5::BalancesModule::<Runtime>::new();
2) <>的用途比较多，既可以作为类型转换的容器，比如let user1: <Runtime as step5::trait>::AccountId = 1；又用于放置泛型的实际类型, eg.  step4::BalancesModule::<AccountId, Balance>::new();

  
2. 识别以上两点之后，substrate的泛型还是比较容易理解的。
  
3. 另外，rust在实现trait时也需要实现对应type别名定义，也是个不容易理解的点(对于从Java转过来的人来说)：eg.
  ```
  pub trait Trait {
  	type AccountId: Eq + Hash;
	  type Balance: Zero + CheckedAdd + CheckedSub + Copy;
  	type VoteIndex: Eq + Hash;
  }
  ```
  那么对应实现的时候则需要定义上述type别名的具体类型：
  ```
  impl Trait for Runtime {
		type AccountId = u32;
		type Balance = u64;
		type VoteIndex = u8;
	}
  ```
除了上述部分就都是基础rust语法了。
	
