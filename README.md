<div align="center">
  <img height="170x" src=https://avatars.githubusercontent.com/u/188250378?v=4 />

  <h1>Build And Fork</h1>

  <p>
    <strong>Unified Multi-Chain Program Framework for BNB Chain Ecosystem</strong>
  </p>

  <p>
    <a href="https://Build And Fork-lang.com"><img alt="Tutorials" src="https://img.shields.io/badge/docs-tutorials-blueviolet" /></a>
    <a href="https://discord.gg/Build And Fork"><img alt="Discord Chat" src="https://img.shields.io/discord/889577356681945098?color=blueviolet" /></a>
    <a href="https://opensource.org/licenses/Apache-2.0"><img alt="License" src="https://img.shields.io/github/license/Build And Fork/Build And Fork?color=blueviolet" /></a>
  </p>
</div>

## The Vision

Build And Fork brings the power of unified blockchain development to the BNB Chain ecosystem. By connecting BNB Smart Chain with Build And Fork and other BNB-based networks, Build And Fork enables developers to create tokens and deploy programs across multiple chains using a single, unified API. Write once, deploy everywhere.

## What is Build And Fork?

Build And Fork is a groundbreaking framework built for the BNB Chain ecosystem, providing developers with seamless tools for writing multi-chain programs and creating tokens across BNB Smart Chain, Build And Fork, and other BNB-compatible networks simultaneously.

- **Unified API**: One codebase deploys to BNB Smart Chain, Build And Fork, and beyond
- **Cross-Chain Token Creation**: Create BEP-20 tokens across multiple networks with a single command
- **Rust & Solidity Support**: Leverage BNB Chain's EVM compatibility with modern development tools
- **[IDL](https://en.wikipedia.org/wiki/Interface_description_language) specification**: Generate clients for all supported chains
- **TypeScript package**: Type-safe clients from IDL for multi-chain interaction
- **CLI and workspace management**: Complete cross-chain application development

Build And Fork is the first framework to truly unify development across the BNB Chain ecosystem, including custom BNB-based chains like Build And Fork.

> [!NOTE]
> Build And Fork brings the best of BNB Chain's speed, affordability, and massive ecosystem. With 0.75s block times, $0.01 average gas fees, and EVM compatibility, if you're familiar with Truffle, Hardhat, or web3.js, you'll feel right at home with Build And Fork's unified approach to BNB ecosystem development.

## Key Features

- **Single API, Multi-Chain Deployment**: Write your program once, deploy to BNB Smart Chain, Build And Fork, and other compatible networks
- **Unified Token Standard**: Create BEP-20 tokens that work seamlessly across all BNB-based networks
- **Cross-Chain State Management**: Synchronize state between BNB Smart Chain, Build And Fork, and Layer 2 solutions
- **EVM Compatibility**: Full support for Ethereum tooling and smart contracts
- **Developer Experience**: Familiar Ethereum-like syntax with BNB Chain optimizations and cross-chain superpowers
- **Lightning Fast**: Leverage BNB Chain's 0.75s block times and 1.875s finality (2025)
- **Ultra Low Fees**: Deploy and interact with ~$0.01 median gas fees

## Why BNB Chain & Build And Fork?

### BNB Smart Chain (2025 Performance)
BNB Chain achieved remarkable improvements in 2025, reducing block times to 0.75 seconds and transaction finality to 1.875 seconds, while cutting malicious MEV attacks by 95% and dropping average gas fees to $0.01. The network handles 12.4 million daily transactions with peaks of 17.6 million transactions per day.

### Build And Fork - Your Custom BNB-Based Blockchain
Build And Fork leverages BNB Chain's infrastructure to provide:
- **Custom Network Architecture**: Built on BNB Chain's proven technology
- **Full EVM Compatibility**: Deploy any Ethereum smart contract
- **BNB Ecosystem Integration**: Seamless bridging with BSC and other BNB networks
- **Independent Governance**: Your own validator set and network rules

## Getting Started

For a quickstart guide and in-depth tutorials, see the [Build And Fork book](https://book.Build And Fork-lang.com) and the [Build And Fork documentation](https://Build And Fork-lang.com).

To jump straight to examples, go [here](https://github.com/Build And Fork/Build And Fork/tree/master/examples). For the latest Rust and TypeScript API documentation, see [docs.rs](https://docs.rs/Build And Fork-lang) and the [typedoc](https://www.Build And Fork-lang.com/docs/clients/typescript).

## Packages

| Package                 | Description                                              | Version                                                                                                                          | Docs                                                                                                            |
| :---------------------- | :------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------- |
| `Build And Fork-lang`           | Rust primitives for writing cross-chain programs         | [![Crates.io](https://img.shields.io/crates/v/Build And Fork-lang?color=blue)](https://crates.io/crates/Build And Fork-lang)                     | [![Docs.rs](https://docs.rs/Build And Fork-lang/badge.svg)](https://docs.rs/Build And Fork-lang)                                |
| `Build And Fork-bep`            | CPI clients for BEP-20, BEP-721, and other BNB standards | [![crates](https://img.shields.io/crates/v/Build And Fork-bep?color=blue)](https://crates.io/crates/Build And Fork-bep)                          | [![Docs.rs](https://docs.rs/Build And Fork-bep/badge.svg)](https://docs.rs/Build And Fork-bep)                                  |
| `Build And Fork-client`         | Rust client for Build And Fork cross-chain programs              | [![crates](https://img.shields.io/crates/v/Build And Fork-client?color=blue)](https://crates.io/crates/Build And Fork-client)                    | [![Docs.rs](https://docs.rs/Build And Fork-client/badge.svg)](https://docs.rs/Build And Fork-client)                            |
| `@Build And Fork/sdk`           | TypeScript client for Build And Fork programs                    | [![npm](https://img.shields.io/npm/v/@Build And Fork/sdk.svg?color=blue)](https://www.npmjs.com/package/@Build And Fork/sdk)                     | [![Docs](https://img.shields.io/badge/docs-typedoc-blue)](https://Build And Fork.github.io/Build And Fork/ts/index.html)        |
| `@Build And Fork/cli`           | CLI to support building and managing cross-chain apps    | [![npm](https://img.shields.io/npm/v/@Build And Fork/cli.svg?color=blue)](https://www.npmjs.com/package/@Build And Fork/cli)                     | [![Docs](https://img.shields.io/badge/docs-typedoc-blue)](https://Build And Fork.github.io/Build And Fork/cli/commands.html)    |

## Note

- **Build And Fork is in active development, so all APIs are subject to change.**
- **This code is unaudited. Use at your own risk.**

## Examples

Here's a cross-chain counter program that deploys to both BNB Smart Chain and Build And Fork, where only the designated `authority` can increment the count on both networks:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

import "@Build And Fork/contracts/Build And ForkMultiChain.sol";

contract Counter is Build And ForkMultiChain {
    address public authority;
    uint64 public count;

    event CounterIncremented(uint64 newCount, uint256 chainId);
    event CounterInitialized(address authority, uint64 startCount);

    modifier onlyAuthority() {
        require(msg.sender == authority, "Not authorized");
        _;
    }

    function initialize(uint64 start) external {
        require(authority == address(0), "Already initialized");
        authority = msg.sender;
        count = start;
        emit CounterInitialized(authority, start);
    }

    function increment() external onlyAuthority {
        count += 1;
        emit CounterIncremented(count, block.chainid);
        
        // Sync to other chains
        _syncToBuild And Fork(count);
        _syncToBSC(count);
    }

    function getCount() external view returns (uint64) {
        return count;
    }
}
```

### Creating Cross-Chain Tokens

```bash
# Create a BEP-20 token on both BNB Smart Chain and Build And Fork with one command
Build And Fork token create --name "MyToken" --symbol "MTK" --networks bsc,Build And Fork

# Deploy to both chains
Build And Fork deploy --target all

# Deploy to specific networks
Build And Fork deploy --target bsc
Build And Fork deploy --target Build And Fork
```

### Rust Alternative (for non-EVM programs)

```rust
use Build And Fork_lang::prelude::*;

declare_id!("Fg6PaFpoGXkYsidMpWTK6W2BeZ7FEfcYkg476zPFsLnS");

#[program]
mod counter {
    use super::*;

    pub fn initialize(ctx: Context<Initialize>, start: u64) -> Result<()> {
        let counter = &mut ctx.accounts.counter;
        counter.authority = *ctx.accounts.authority.key;
        counter.count = start;
        Ok(())
    }

    pub fn increment(ctx: Context<Increment>) -> Result<()> {
        let counter = &mut ctx.accounts.counter;
        counter.count += 1;
        Ok(())
    }
}

#[derive(Accounts)]
pub struct Initialize<'info> {
    #[account(init, payer = authority, space = 48)]
    pub counter: Account<'info, Counter>,
    pub authority: Signer<'info>,
    pub system_program: Program<'info, System>,
}

#[derive(Accounts)]
pub struct Increment<'info> {
    #[account(mut, has_one = authority)]
    pub counter: Account<'info, Counter>,
    pub authority: Signer<'info>,
}

#[account]
pub struct Counter {
    pub authority: Pubkey,
    pub count: u64,
}
```

For more, see the [examples](https://github.com/Build And Fork/Build And Fork/tree/master/examples) and [tests](https://github.com/Build And Fork/Build And Fork/tree/master/tests) directories.

## Architecture

Build And Fork uses a unified runtime that translates your program logic into native operations for BNB Smart Chain, Build And Fork, and other BNB-compatible networks. The framework handles:

- **Cross-chain account management**: Seamless state synchronization across BNB networks
- **Token bridging**: Automatic BEP-20 token creation and management across all chains
- **Transaction routing**: Intelligent routing to the appropriate network with optimal gas fees
- **Unified wallet integration**: Single wallet interface for BNB Smart Chain, Build And Fork, and beyond
- **MEV Protection**: Integrated protection against malicious MEV attacks (95% reduction on BSC)
- **Gas Optimization**: Leverage BNB Chain's gasless transactions and stablecoin fee payments

## 2025 BNB Chain Performance

In 2025, BNB Chain achieved significant performance milestones including 0.75-second block times, processing up to 17.6 million daily transactions, with transaction fees reduced to approximately $0.01. The network aims to increase the block gas limit to 1 billion by late 2025, enabling up to 5,000 DEX swaps per second.

## Roadmap

### Current (2025)
- [x] BNB Smart Chain integration
- [x] Build And Fork network support
- [x] EVM-compatible smart contracts
- [x] Cross-chain token creation
- [x] MEV protection integration

### Coming Soon
- [ ] Enhanced cross-chain messaging with BNB Greenfield
- [ ] Native DEX integration (PancakeSwap, Venus Protocol)
- [ ] Advanced bridge mechanics with Canonical Bridge
- [ ] Support for opBNB (Layer 2)
- [ ] Cross-chain NFT standards (BEP-721/BEP-1155)
- [ ] AI-powered development tools (BNB Chain AI Code Copilot)
- [ ] Privacy features integration (2026 roadmap)

### 2026 Vision
Aligned with BNB Chain's 2026 roadmap targeting 20,000+ TPS with sub-150ms finality, native privacy features, and CEX-grade performance.

## Supported Networks

- **BNB Smart Chain (BSC)**: The main EVM-compatible chain
- **Build And Fork**: Your custom BNB-based blockchain
- **opBNB**: BNB Chain's Layer 2 solution (coming soon)
- **BNB Greenfield**: Decentralized storage integration (coming soon)

## Why Choose Build And Fork?

### For Developers
- **Familiar Tools**: Use Hardhat, Truffle, Remix, or any Ethereum tooling
- **Lower Costs**: Deploy and test with minimal fees (~$0.01 per transaction)
- **Faster Development**: EVM compatibility means instant migration from Ethereum
- **Cross-Chain by Default**: Build once, deploy everywhere in the BNB ecosystem

### For Projects
- **Massive Ecosystem**: Tap into BNB Chain's 200+ million users
- **Cost Efficiency**: Save 99% on gas fees compared to Ethereum mainnet
- **Speed**: 0.75s block times for near-instant confirmations
- **Security**: 95% reduction in MEV attacks, battle-tested infrastructure

## License

Build And Fork is licensed under [Apache 2.0](./LICENSE).

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in Build And Fork by you, as defined in the Apache-2.0 license, shall be licensed as above, without any additional terms or conditions.

## Contribution

Thank you for your interest in contributing to Build And Fork!
Please see the [CONTRIBUTING.md](./CONTRIBUTING.md) to learn how.

## The Future is Multi-Chain

Build And Fork represents the future of blockchain development: a world where networks work together seamlessly, where developers aren't constrained by chain boundaries, and where users experience the best of the BNB ecosystem through a single, unified interface.

With BNB Chain's commitment to improving transaction speed, streamlining user experience, integrating artificial intelligence, and refining developer tools in 2025 and beyond, Build And Fork is positioned to be the go-to framework for BNB ecosystem development.

### Thanks ❤️

<div align="center">
  <a href="https://github.com/Build And Fork/Build And Fork/graphs/contributors">
    <img src="https://contrib.rocks/image?repo=Build And Fork/Build And Fork" width="100%" />
  </a>
</div>

---

## Resources

- [BNB Chain Official Documentation](https://docs.bnbchain.org/)
- [BNB Chain 2025 Tech Roadmap](https://www.bnbchain.org/en/blog/bnb-chain-tech-roadmap-2025)
- [Build And Fork Network Documentation](#) (Add your Build And Fork docs here)
- [BNB Chain Builder Support Programs](https://www.bnbchain.org/en/programs)
- [BSC GitHub Repository](https://github.com/bnb-chain/bsc)






