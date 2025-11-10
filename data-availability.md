# Data Availability Architecture

[← Back to Architecture Overview](./Architecture.md)

Twine implements a flexible data availability layer supporting multiple DA solutions with an advanced volition model enabling user and contract-level DA choice.

## Trust Minimization

**Key Property**: Data availability ensures state is always recoverable, even without trusting specific DA providers.

**Why DA is Trust-Minimized**:
- ✅ Multiple DA layers provide redundancy
- ✅ Fraud proofs detect data withholding
- ✅ Anyone can reconstruct state from DA data
- ✅ DA failure doesn't compromise security

**Trust Minimization**: DA is for **liveness**, not **security**. State always recoverable.

## Supported DA Layers

**Ethereum L1 Data Availability**:
- Transaction data posted as calldata to Ethereum settlement contract
- Highest security: inherits Ethereum's data availability guarantees
- Higher cost: ~16 gas per byte for calldata
- Ideal for high-value transactions and security-critical applications

**Celestia Modular Data Availability**:
- Transaction data posted as blob transactions to Celestia
- Lower cost: specialized DA layer with lower per-byte cost
- Namespace isolation: Twine data stored in dedicated namespace
- Blobstream integration: Merkle proofs relayed to Ethereum for verification

**Future DA Layers**:
- Modular architecture supports EigenDA, Avail, Near DA
- Per-application DA selection based on cost/security tradeoff
- Hybrid DA strategies for optimal economics

**Trust Minimization**: Multiple DA options provide redundancy without introducing new trust assumptions.

## Celestia Integration

**Data Posting Flow**:
1. Sequencer creates `BatchForDA` structure containing transactions and ZK proofs
2. Data converted to Celestia blob format with namespace identifier
3. Posted to Celestia network via `MsgPayForBlobs` transaction
4. Receive Celestia block height and data share location (span)
5. Twine header with Celestia span metadata posted to Ethereum

**Blobstream Verification**:
- **Data Root Tuple Proof**: Proves Celestia data root is committed in Blobstream contract
- **Namespace Merkle Proof**: Proves shares belong to Twine's namespace
- **Binary Merkle Proof**: Proves row/column inclusion in Celestia's data square
- **Span Validity Proof**: ZK circuit proves data location matches claimed span

**Trust Minimization**: Celestia commitments verified on Ethereum via Blobstream. Cryptographic proof of data availability.

## Volition Model

**Per-Address DA Preference**:
- Account state includes `da_preference` field (Ethereum or Celestia)
- User can update preference via special transaction
- Contracts can set DA preference in constructor or via governance
- Gas pricing reflects actual DA costs per layer

**Trade-offs**:

| Feature | Ethereum DA | Celestia DA |
|---------|-------------|-------------|
| **Security** | Highest (Ethereum consensus) | High (Celestia consensus + Blobstream) |
| **Cost** | ~$0.50 per 1KB | ~$0.01 per 1KB |
| **Finality** | 12-15 minutes | 1-2 minutes |
| **Ideal For** | High-value, security-critical | High-throughput, cost-sensitive |

**Trust Minimization**: User choice empowers users without compromising security.

---

[← Back to Architecture Overview](./Architecture.md)
