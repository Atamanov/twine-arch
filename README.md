# Twine Architecture Documentation

**Trust-Minimized Cross-Chain Interoperability via Zero-Knowledge Cryptography**

---

## 🚀 Overview

Twine is a unified settlement network designed to connect heterogeneous blockchain ecosystems without requiring opt-in from participating chains. Unlike traditional Layer 2 solutions that settle on a single base layer, Twine settles on **multiple Layer 1 blockchains simultaneously**—including Ethereum, Solana, Bitcoin, and others.

### Core Innovation

**Replace Trust with Mathematics**: Every cross-chain operation is verified cryptographically. No multi-sig committees, no external oracles, no trusted validators—only zero-knowledge proofs.

---

## 📚 Documentation

### Start Here

**[Architecture Overview](./Architecture.md)** - High-level helicopter view of Twine's architecture

### Core Components

1. **[Execution Environments](./execution-environments.md)**
   - EVM compatibility with zkBridge precompiles
   - TwineVM for verifiable application chains
   - Trust-minimized cross-chain state access

2. **[Consensus Verification System](./consensus-verification.md)**
   - Ethereum BLS signature aggregation
   - First functional Solana ZK light client
   - Bitcoin BitVM fraud-proof verification
   - **No trusted oracles or validators**

3. **[Zero-Knowledge Proof Stack](./zk-proof-stack.md)**
   - SP1/Risc0 ZKVM execution proving
   - Groth16 compression for gas efficiency
   - Proof aggregation pipeline

4. **[Twine Sequencer](./sequencer.md)**
   - Transaction ordering and batch creation
   - Multi-DA coordination (Ethereum, Celestia)
   - Forced inclusion for censorship resistance

5. **[Proof Orchestration](./proof-orchestration.md)**
   - Distributed proof generation
   - Scheduler, workers, and aggregator
   - Multi-chain settlement dispatch

6. **[Merkora (Cross-Chain Relayer)](./merkora.md)**
   - Rust-based event monitoring (actual implementation)
   - Ethereum and Solana listeners
   - **Service, not a trust assumption**

7. **[Bridges & Settlement](./bridges-settlement.md)**
   - Multi-L1 settlement contracts
   - Native asset bridging (no wrapped tokens)
   - Dual-proof verification mechanism

8. **[Data Availability](./data-availability.md)**
   - Ethereum L1 and Celestia DA
   - Volition model for user choice
   - State recovery guarantees

9. **[Security Model](./security-model.md)**
   - Trust-minimized design principles
   - Multi-chain security inheritance
   - Attack scenarios and mitigations

---

## 🔑 Key Concepts

### Trust Minimization

| Traditional Bridges | Twine |
|---------------------|-------|
| Multi-sig committees | ZK proofs verified on-chain |
| External validators | Cryptographic verification |
| Wrapped tokens | Native assets |
| Trust assumptions | Mathematical guarantees |
| Single L1 settlement | Multi-L1 settlement |

### Zero-Knowledge Proofs Everywhere

- ✅ **Consensus Proofs**: Cryptographically verify L1 blockchain states
- ✅ **Execution Proofs**: Verify state transitions without re-execution
- ✅ **On-Chain Verification**: All proofs verified on Layer 1 chains
- ✅ **Publicly Verifiable**: Anyone can regenerate and verify proofs

### Multi-Chain Settlement

- Settle on Ethereum, Solana, and Bitcoin simultaneously
- Attack must compromise **ALL** settlement chains to steal funds
- Security **multiplies** rather than fragments
- Withdrawal safe if **ANY** settlement chain remains honest

---

## 🎯 Why Twine?

### Universal Interoperability (No Opt-In Required)

Traditional solutions (AggLayer, Superchain) create **fragmented ecosystems**:
- Chain in AggLayer cannot access Superchain liquidity
- Requires explicit opt-in from every participating chain
- Limited to chains built on same technology stack

**Twine's Advantage**:
- Connect **any blockchain** through consensus proofs—no permission needed
- Build applications spanning Ethereum, Solana, and Bitcoin ecosystems
- **No wrapped tokens**, **no trust assumptions**
- **Universal access** to all connected chain liquidity

### Native Multi-Asset Support

- `ETH` from Ethereum coexists with `SOL` from Solana in Twine state
- No wrapping: assets maintain their Layer 1 identity
- Smart contracts can operate on heterogeneous asset types
- **Trust-minimized**: Assets locked/released via ZK proofs only

---

## 🏗️ Current Status

**Testnet Live**:
- ✅ Ethereum and Solana consensus provers operational
- ✅ EVM environment with zkBridge precompiles
- ✅ SP1/Risc0 ZKVM integration complete
- ✅ Multi-chain settlement on Ethereum and Solana
- ✅ Merkora cross-chain relayer production-ready

**Roadmap**:
- **Q1 2026**: Bitcoin integration, TwineVM launch, decentralized sequencer testnet
- **Q2 2026**: Mainnet launch with Ethereum, Solana, Bitcoin support
- **Q3 2026**: Full decentralization, advanced proof aggregation

---

## 🔗 Quick Links

- **GitHub**: [github.com/twinexyz](https://github.com/twinexyz)
- **Website**: [twinelabs.xyz](https://twinelabs.xyz)
- **Discord**: [discord.gg/twinexyz](https://discord.gg/twinexyz)

---

## 📖 Reading Guide

**For Developers**:
1. Start with [Architecture Overview](./Architecture.md)
2. Deep dive into [Execution Environments](./execution-environments.md)
3. Understand [Merkora implementation](./merkora.md) (actual source code)

**For Security Researchers**:
1. Read [Security Model](./security-model.md)
2. Examine [Consensus Verification](./consensus-verification.md)
3. Review [ZK Proof Stack](./zk-proof-stack.md)

**For Protocol Designers**:
1. Study [Multi-Chain Settlement](./bridges-settlement.md)
2. Understand [Data Availability](./data-availability.md)
3. Analyze [Proof Orchestration](./proof-orchestration.md)

---

**Twine is building the infrastructure for a unified multi-chain future—powered by zero-knowledge cryptography, not trust assumptions.**

