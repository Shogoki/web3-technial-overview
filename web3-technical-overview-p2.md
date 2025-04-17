---
marp: true
theme: default
paginate: true
#header: "Web3 Technical Overview | Sherlock | Shogoki"
footer: "Monday, March 31, 2025 | Sherlock | Shogoki"
style: |
  /* Sherlock-inspired theme with corrected purple and readable table */
  section {
    background-color: #1E2525; /* Dark gray background */
    color: #FFFFFF; /* White text */
    font-family: 'Inter', 'Roboto', sans-serif; /* Clean sans-serif */
    padding: 40px;
  }
  h1 {
    color: #A855F7; /* Purple for headings */
    font-size: 2.5em;
    font-weight: bold;
    margin-bottom: 0.5em;
  }
  h2 {
    color: #A855F7; /* Purple for headings */
    font-size: 1.8em;
    font-weight: bold;
    margin-bottom: 0.4em;
  }
  h3 {
    color: #A855F7; /* Purple for headings */
  }
  p, li {
    color: #A1A1A1; /* Light gray for body text */
    font-size: 1.0em;
    line-height: 1.5;
  }
  strong {
    color: #FFFFFF; /* White for bold text */
  }
  table {
    width: 90%;
    margin: 20px auto;
    border-collapse: collapse;
    background-color: #2A3232; /* Slightly lighter gray for table background */
  }
  th {
    background-color: #A855F7; /* Purple for table headers */
    color: #FFFFFF; /* White text in headers for better contrast */
    padding: 12px;
    font-weight: bold;
  }
  td {
    padding: 12px;
    color: #E5E7EB; /* Light gray (#E5E7EB) for table cells - high contrast */
    background-color: #2A3232; /* Consistent dark gray background */
    border: 1px solid #4B5563; /* Lighter gray border for visibility */
  }
  /* Pagination, header, footer styling */
  .marp-pre {
    background-color: transparent;
    color: #A1A1A1;
  }
  header, footer {
    color: #A1A1A1;
    font-size: 0.9em;
    padding: 10px;
  }
---

# Web3 Technical Overview - Part2

**Date:** Monday, March 31, 2025  

A technical overview about the Web3 and Blockchain ecosystems.

---

## 1. Blockchain Ecosystem Overview - Non-EVM Chains

---

### Solana: Why It Exists
- **Problem**: Most blockchains are too slow for mass adoption of dApps.  
- **Solution**: Solana delivers high throughput (up to 65,000 TPS) and low latency.  
- **Impact**: Supports high-performance applications at scale.  
- **Example**: Serum DEX powers high-frequency trading on Solana.  

<!-- Speaker Notes:  
Solana is all about speed—think 65,000 transactions per second versus Ethereum’s 15. It’s built to handle dApps like Serum DEX, where every millisecond counts.  
-->

---

### Solana: What’s Unique
- **Key Feature**: Proof of History (PoH).  
  - Timestamps transactions to streamline consensus and boost speed.  
- **Advantage**: Enables massive scalability without heavy reliance on sharding.  
- **Storage Account System**: Solana Programs are associated with a Storage Account and need to borrow storage.  
- **Security Note**: High throughput introduces concurrency risks in smart contracts.  


<!-- Speaker Notes:  
Proof of History is Solana’s secret sauce—it’s like a built-in clock for transactions, cutting consensus overhead. But that speed means smart contracts need extra scrutiny for timing bugs. Sherlock audits Solana’s Rust-based contracts to catch these issues.  
-->

---

### Cosmos: Why It Exists
- **Problem**: Blockchains operate in isolation, unable to communicate natively.  
- **Solution**: Cosmos enables developers to build custom, sovereign blockchains that interoperate via the Inter-Blockchain Communication (IBC) protocol.  
- **Impact**: Creates an "Internet of Blockchains" for seamless cross-chain functionality.  
- **Example**: Osmosis DEX runs as a standalone chain but connects to others via IBC.  

<!-- Speaker Notes:  
Cosmos tackles the silos in blockchain tech. Think of blockchains as isolated islands—Cosmos builds bridges with IBC, letting custom chains like Osmosis for DeFi thrive independently yet connect with others.  
-->

---

### Cosmos: What’s Unique
- **Key Feature**: Inter-Blockchain Communication (IBC) protocol.  
  - Allows sovereign chains to exchange data and assets securely.  
- **Advantage**: Developers can tailor blockchains to specific needs without sacrificing connectivity.  

<!-- Speaker Notes:  
IBC is Cosmos’s standout feature—it’s like the internet’s TCP/IP for blockchains. Each chain is independent, so a bug in one won’t crash all, but those IBC bridges need to be rock-solid. Sherlock audits these connections to prevent cross-chain exploits.  
-->

---

![bg contain](img/cosmos.jpg)

---

### Polkadot: Why It Exists
- **Problem**: New blockchains struggle to establish their own security.  
- **Solution**: Polkadot offers shared security through its Relay Chain, connecting specialized parachains.  
- **Impact**: Reduces the burden of bootstrapping security for individual chains.  
- **Example**: Acala (DeFi) and Moonbeam (EVM-compatible) leverage this model.  

<!-- Speaker Notes:  
Polkadot fixes the security startup problem. Instead of every chain building its own defenses, they tap into the Relay Chain’s shared security, letting them focus on their unique jobs—like Acala for DeFi.  
-->

---

### Polkadot: What’s Unique
- **Key Feature**: Shared security via the Relay Chain.  
  - Parachains inherit robust security without building it from scratch.  
- **Advantage**: Enables specialized chains under a unified security umbrella.  
- **Security Note**: Relay Chain bugs can affect all parachains, requiring thorough checks.  

<!-- Speaker Notes:  
Shared security is Polkadot’s edge—parachains get a head start by leaning on the Relay Chain. But if the Relay Chain has a flaw, it’s a network-wide risk, so auditing is critical. Sherlock ensures these systems are bulletproof.  
-->

---

![bg contain](img/polkadot.webp)

---

## 2. DeFi Protocols and Mechanisms

---


### DEXes: On-Chain
- **Uniswap**:  
  - AMM model, liquidity pools.  
  - Risks: Impermanent loss, oracle manipulation.  
- **Security Focus**:  
  - Audit pool logic, price feeds.  

<!-- Speaker Notes: Uniswap’s AMM is revolutionary but not without risks. Impermanent loss can drain liquidity providers, and bad oracles can skew prices. Sherlock audits these components. -->

---

### DEXes: Off-Chain
- **dYdX**:  
  - Off-chain order books, on-chain settlement.  
  - Risks: Front-running, off-chain data integrity.  
- **Security Focus**:  
  - Audit matching engines, settlement logic.  

<!-- Speaker Notes: dYdX offers speed but off-chain components introduce trust assumptions. Sherlock ensures the off-chain logic can’t be gamed. -->

---

### Lending & Borrowing
- **Key Features**:  
  - Overcollateralized loans (e.g., Aave, Compound).  
  - Flash loans (Aave): Borrow without collateral, repay instantly.  
  - Algorithmic interest rates (Compound): Rates adjust by supply/demand.  
- **Risks**:  
  - Flash loan attacks, liquidation bugs, rate manipulation.  
- **Sherlock’s Role**:  
  - Audits loan logic, collateral systems, rate models.  

<!-- Speaker Notes: Lending protocols like Aave and Compound let users borrow crypto by locking collateral. Aave’s flash loans are powerful but risky—used in attacks if not coded right. Compound’s rates adapt dynamically but can be gamed. Sherlock audits these to prevent exploits. -->

---

### DAOs and Governance
- **What Are They?**  
  - Decentralized Autonomous Organizations: Community-run protocols.  
  - Governance: Token holders vote on protocol changes.  
- **Key Features**:  
  - On-chain voting (e.g., via governance tokens).  
  - Proposals for upgrades, fee changes, etc.  
- **Risks**:  
  - Governance attacks (e.g., vote manipulation), proposal exploits.  
- **Sherlock’s Role**:  
  - Audits governance contracts for secure voting and execution.  

<!-- Speaker Notes: DAOs let communities govern protocols via token voting—think of it as a decentralized boardroom. But governance systems can be attacked if votes are manipulated or proposals are malicious. Sherlock audits these to ensure fair, secure decision-making. -->

---

### Stablecoins
- **DAI/USDS, or LUSD**:  
  - Decentralized, collateral-backed.  
  - Risks: Peg stability, oracle failures.  
- **USDC or USDT**:  
  - Centralized, fiat-backed.  
  - Risks: Custodial risk, regulatory pressure.  

<!-- Speaker Notes: Stablecoins are DeFi’s backbone. DAI’s peg relies on code and oracles—bugs can break it. USDC’s centralization is a different risk—Sherlock focuses on the code side. -->


---

## 3. Programming Languages in Web3

---

### Smart Contracts: Solidity
- **Use**: Ethereum, EVM chains.  
- **Security Challenges**:  
  - Reentrancy, integer overflows, gas limits.  
- **Sherlock’s Role**:  
  - Audit Solidity code for vulnerabilities.  

<!-- Speaker Notes: Solidity is the most common smart contract language, but it’s tricky. Common bugs like reentrancy can drain funds. Sherlock’s auditors are experts in spotting these. -->

---

### Smart Contracts: Rust
- **Use**: Solana, Polkadot.  
- **Security Challenges**:  
  - Memory safety, concurrency issues.  
- **Sherlock’s Role**:  
  - Audit Rust-based programs for logic flaws.  

<!-- Speaker Notes: Rust is safer than Solidity but not immune to bugs. Concurrency in Solana can lead to race conditions—Sherlock audits these high-performance contracts. -->

---

### Clients/L2s: Go and Rust
- **Go**:  
  - Ethereum Geth, Optimism.  
  - Risks: Consensus bugs, DoS attacks.  
- **Rust**:  
  - Parity, Solana.  
  - Risks: Memory corruption, performance bottlenecks.  

<!-- Speaker Notes: Client software is the backbone of blockchains. Bugs here can crash networks or enable attacks. Sherlock audits client code to prevent such failures. -->

---

### AppChains: Go
- **Cosmos SDK**:  
  - Build custom chains with Tendermint.  
- **Security Focus**:  
  - Audit chain-specific logic, IBC connections.  

<!-- Speaker Notes: Cosmos chains are modular but each has unique risks. IBC connections must be secure—Sherlock audits these custom implementations. -->

---

## 4. Quick Q&A
- **Key Takeaways**:  
  - Web3 is diverse, each part has unique security needs.  
  - Sherlock audits smart contracts, L2s, and more.  
- **Next**: Web3 Security & Cryptograhy (ZK, FHE, ...) Deep Dive.  

<!-- Speaker Notes: Let’s open the floor for questions. Remember, Sherlock’s audits cover the full spectrum—from smart contracts to L2s and beyond. Tomorrow, we’ll dive deeper into security techniques. -->

---
