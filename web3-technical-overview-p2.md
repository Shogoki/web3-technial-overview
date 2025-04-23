---
marp: true
theme: default
title: "Web3 Technical Overview"
paginate: true
#header: "Web3 Technical Overview | Sherlock | Shogoki"
footer: "Monday, April 17, 2025 | Sherlock | Shogoki"
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

**Date:** Monday, April 17, 2025  

Overview about DeFi

---

## 1. DeFi Protocols and Mechanisms

---

### DeFi Overview: The Money LEGOs
- **What is DeFi?**:  
  - Financial services (borrowing, trading, etc.) without centralized entities, built on blockchains like Ethereum.  
- **Mechanics**:  
  - Smart contracts lock collateral (TVL), enabling trustless services.  

![height: auto](img/Defi_tvl.png)

<!-- Speaker Notes: DeFi replaces banks with smart contracts on blockchains like Ethereum—“Money LEGOs” you can stack. TVL exploded from $275M in 2019 to $86B by 2021, showing its scale. We’ll dive into key categories, focusing on how they work and Sherlock’s role in securing them. (2 min) -->

---

### Stablecoins: Types and Mechanics
- **Centralized (e.g., USDC, USDT)**:  
  - Fiat-backed (1:1 with USD in bank), custodial risks (trust in issuer).  
- **Algorithmic (e.g., UST, pre-crash)**:  
  - Maintain peg via algorithms (e.g., mint/burn mechanics), risks of depeg (e.g., Terra’s collapse).  
- **CDP (Collateralized Debt Position, e.g., DAI)**:  
  - Overcollateralized crypto (e.g., ETH), smart contract mints stablecoin, oracle risks.  
- **Security Focus**:  
  - Audits for peg stability, oracles—Sherlock audited MakerDAO (DAI).  

<!-- Speaker Notes: Stablecoins reduce volatility. Centralized ones like USDC hold USD in banks—trust issues. Algorithmic ones like UST balance supply via code but can fail (Terra crashed). CDPs like DAI use crypto collateral, relying on oracles. Sherlock audited MakerDAO to secure DAI’s peg. (3 min) -->

---

### DEXes: On-Chain (AMM Mechanics)
- **Uniswap**:  
  - Automated Market Maker (AMM): No order books; uses liquidity pools.  
  - **Constant Product Formula**: \( x \* = k \) (e.g., ETH-DAI pool).  
    - \( x \) and \( y \): Token quantities; \( k \): Constant.  
- **Mechanics**:  
  - Liquidity Providers (LPs) deposit token pairs, earn fees (~0.3% per trade).  
  - Risks: Impermanent loss (price divergence), oracle manipulation.  
- **Security Focus**:  
  - Audit pool logic, price feeds—Sherlock audited DODO.  

<!-- Speaker Notes: Uniswap’s AMM replaces order books with pools—LPs deposit pairs like ETH-DAI. The formula \( x \times y = k \) ensures price balance; if ETH’s price rises, LPs face impermanent loss but earn fees. Oracle bugs can skew prices. Sherlock audited Unstoppable DeFi to secure these mechanics. (3 min) -->

---

### DEXes: Off-Chain
- **dYdX**:  
  - Off-chain order books, on-chain settlement—faster, pro-trading focus.  
  - **Mechanics**:  
    - Orders matched off-chain (speed), settled on-chain (security).  
    - LPs not needed; relies on market makers.  
  - Risks: Front-running, off-chain data integrity.  
- **Security Focus**:  
  - Audit matching engines, settlement logic—Sherlock audited 100X.  

<!-- Speaker Notes: dYdX matches orders off-chain for speed, settles on-chain for security—no LPs, just market makers. Front-running can occur if off-chain data is gamed. Sherlock’s audit of dYdX ensures the system’s integrity. (2 min) -->

---

### Lending & Borrowing

- **Protocols (e.g., Aave, Compound)**:  
  - **Mechanics**:  
    - Overcollateralized loans: Lock $150 ETH to borrow $100 DAI.  
    - Flash loans (Aave): Borrow millions, repay in same tx (arbitrage).  
    - Rates (Compound): Adjust via supply/demand (e.g., high demand = higher rates).  
  - Risks: Flash loan attacks, liquidation bugs, rate manipulation.  
- **Security Focus**:  
  - Audits for loan logic, collateral systems—Sherlock audited Aave, Compound-forks...  

<!-- Speaker Notes: Aave and Compound let you borrow by locking crypto—e.g., $150 ETH for $100 DAI. Flash loans allow instant borrowing if repaid in one tx—great for arbitrage, risky if exploited. Rates adjust dynamically but can be gamed. Sherlock audited both protocols. (3 min) -->

-- 


## 4. Quick Q&A

<!-- Speaker Notes: Let’s open the floor for questions. Remember, Sherlock’s audits cover the full spectrum—from smart contracts to L2s and beyond. Tomorrow, we’ll dive deeper into security techniques. -->

---
