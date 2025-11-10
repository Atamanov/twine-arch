# Twine Sequencer

[← Back to Architecture Overview](./Architecture.md)

The Twine Sequencer is responsible for transaction ordering, batch creation, and coordination with the data availability layer. Currently centralized for testnet with a clear path toward decentralization.

## Trust Minimization

**Key Property**: Sequencer **cannot steal funds**, only delay transactions.

**Why Users Don't Need to Trust the Sequencer**:
- ✅ Forced inclusion allows bypassing sequencer censorship
- ✅ Zero-knowledge proofs prevent invalid state transitions
- ✅ Sequencer cannot forge proofs or manipulate balances
- ✅ Users can always exit via Layer 1 forced transactions

**Trust Minimization**: Sequencer is a **liveness assumption**, not a **security assumption**.

## Key Capabilities

**Transaction Ordering**:
- Accepts transactions from RPC endpoints for both EVM and TwineVM environments
- Orders transactions deterministically to ensure reproducible state transitions
- Enforces nonce ordering and prevents double-spending
- Timestamp assignment for cross-chain transaction coordination

**Batch Creation**:
- Aggregates transactions into batches for efficient proof generation
- Targets batch size optimization (balancing throughput vs latency)
- Includes Merkle roots for transaction ordering commitments
- Generates batch metadata (previous state root, new state root, receipts root)

## Multi-DA Coordination

**Ethereum L1 DA**:
- Posts transaction data as calldata to Ethereum settlement contract
- Highest security but higher cost per byte
- Used for high-value transactions and security-critical operations

**Celestia DA**:
- Posts data as blob transactions to Celestia's modular DA layer
- Lower cost, specialized for data availability
- Includes namespace isolation for Twine data
- Generates Blobstream proofs for Ethereum verification

**Volition Model** (Advanced):
- Users and contracts can choose their preferred DA layer
- Per-address DA preference stored in account state
- Cross-DA transactions handled with dual-posting
- Gas pricing reflects actual DA costs per layer

**Trust Minimization**: DA choice doesn't affect security—all options provide verifiable data availability.

## Forced Inclusion Support

**Censorship Resistance**: Users can force transaction inclusion via Layer 1

**Forced Transaction Types**:
1. **depositAndCall**: Deposit from Layer 1 and execute transaction in same operation
2. **forcedWithdrawals**: Guaranteed withdrawal execution regardless of sequencer cooperation
3. **signedTransactions**: User-signed transactions submitted via Layer 1 for guaranteed inclusion

**Enforcement Mechanism**:
- Layer 1 contracts track expected sequencer nonce for forced transactions
- Sequencer must process forced transactions in order or settlement will fail
- Nonce mismatch detection triggers penalty mechanisms
- Users can prove sequencer censorship via Layer 1 transaction ordering

**Trust Minimization**: Users can always exit even if sequencer is malicious or offline.

## Decentralization Roadmap

- **Testnet**: Single centralized sequencer operated by Twine Labs
- **Beta**: Rotating sequencer set with economic incentives
- **Mainnet**: Fully decentralized sequencing with shared or distributed sequencer network

**Trust Minimization Path**: From operational efficiency (testnet) to full decentralization (mainnet).

---

[← Back to Architecture Overview](./Architecture.md)
