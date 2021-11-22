##coderfengyun's review
Rust programming section7
1. Tuple: light weight struct, special case is zero tuple (), act as void.
2. Character: string is utf-8 encoded, as a sequence of utf-8bytes, not as chats.
3. Pointer types: local stored objects are not allocated on heap. If need to point to other values, must use pointer types explicitly. 
4. Pointer type-Reference: rust reference are never null. Rust tracks ownership and lifetimes of values. &T, immutable reference, read only. &must T, a mutable, exclusive ref. Enforce single writer or multi-reader, never both at the same time.
5. Boxes: box will allocate men on heap, will freed when goes out of scope, If not be moved.
6. Raw Pointer: unsafe, just like C lang.
丁丁
1、今天开始看第11章dapp
