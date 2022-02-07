### Noir Pay v0
> Built on Light Protocol

Noir Pay will be directly built ontop of the Light Protocol SDK and provide users with a beautifully simple private payments solution via our frontend. Have you ever thought about privately paying via [Solana Pay.](https://github.com/solana-labs/solana-pay/) This repo represents a fork of the light protocol program which is built as a single unfractured shielded pool for SPL tokens. This purpose of this fork is to work on local optimisations and bug testing as contribution towards the Light Protocol SDK. 

#### DISCLAIMER: THIS SOFTWARE IS NOT AUDITED. Do not use in production!

### Testing the Program
First **clone** the repo locally. 
```
git clone https://github.com/Lightprotocol/light-protocol-program.git
```
Then run these commands **in order**, it is important that you run the tests one after the other as this is how the functional flow of zk-PROOFs work. You cannot withdraw funds that no proof was ever generated for. 
```
bash cd ./program && cargo test-bpf deposit_should_succeed
```
```
 ./program && cargo test-bpf withdrawal_should_succeed
```
> Please note this will only currently work on Linux/Mac OSX environment's due to the need for the Solana Rust BPF Toolchain. - I have tested it from within WSL2 and it works there also. 

### Light Protocol Description

The Light Protocol program verifies zkSNARK (Zero-Knowledge Succinct Non-Interactive Argument of Knowledge) Proofs to enable anonymous transactions on Solana. 

Zero-knowledge proofs verify that the owner of recipient address B has deposited tokens to a shielded pool (similar to Zcash) from another address A before.
Light Protocol is trustless: the zero-knowledge proof includes meta data such as the recipient address. If this data is tampered with the zero-knowledge proof becomes invalid and the withdrawal fails.

- The implementation of the groth16_verifier is based on the arkworks libraries, mainly [ark_bn254](https://docs.rs/ark-bn254/0.3.0/ark_bn254/), [ark_ec](https://docs.rs/ark-ec/0.3.0/ark_ec/) and [ark_ff](https://docs.rs/ark-ff/0.3.0/ark_ff/).
- The implementation of the [poseidon hash](https://docs.rs/arkworks-gadgets/0.3.14/arkworks_gadgets/poseidon/circom/index.html) is based on [arkworks_gadgets](https://github.com/webb-tools/arkworks-gadgets).
- Light uses a circuit based on [tornado_pool](https://github.com/tornadocash/tornado-pool/tree/onchain-tree/circuits).

If you like to directly contact Light Protocol you can do so via their [Twitter](https://twitter.com/LightProtocol)

### 888 Anon Club Bounty
> Bounty currently @ 88 SOL [$10,500] At time of writing. 
If you are a keen web3 developer and would love to build a beautiful frontend for 'Noir Pay' with integration into Solana Pay - then lets do that today! 
To claim / start working on this bounty please reach out to sleepdev#6905 on discord or alternatively [@0xnicoj](https://twitter.com/0xnicoj) on twitter. 