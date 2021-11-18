
##coderfengyun's review
Master Ethereum Chapter 11
1. Why need oracleizer? Randomness, truth outside of block chain.
2. Blockchain can't support native real random.
3. Oraclizer's design pattern: requst-response pattern, pub-sub, read immediately.
4. Read-immediately: oraclizer save outside truth on chain, other Contract read from it.
5. Pub-sub: use ethereum's event log to watch change.
6. Req-resp: data too huge, cannot save on chain.
7. Data verification: auth proof + trust exercise env. TLSNotary Proof: verify client and a server has net interaction, tls control pri key, get data and sign it. Town Crier: use Intel sgx, sign in the safe zone.
