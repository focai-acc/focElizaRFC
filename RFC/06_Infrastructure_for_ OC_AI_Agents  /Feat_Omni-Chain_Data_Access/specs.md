# 1. Overview

focEliza enhances Chainbase’s plug-in by providing fully on-chain AI agents. These agents, built on Eliza, Trusted Execution Environment (TEE), Ethereum Virtual Machine (EVM), and decentralized architecture (DA), leverage Omni-Chain Data Access for secure, real-time, and multi-chain blockchain data querying and analytics. Through this integration, focEliza delivers autonomous, verifiable, and transparent AI-driven decision-making within decentralized ecosystems.

# 2. Core Components

## 2.1 Fully On-Chain Agent Framework (Eliza)
- **Functionality:** A modular and scalable framework for building autonomous AI agents.
- **Integration:** Works seamlessly with Chainbase’s plugin for accessing blockchain data across multiple chains via natural language queries.
- **Deployment:** Fully on-chain through smart contracts ensuring that all agent actions occur within a decentralized environment.

## 2.2 Trusted Execution Environment (TEE)
- **Confidentiality:** Executes sensitive computations securely, preventing unauthorized access.
- **Integrity:** Ensures that AI agent operations are tamper-proof, offering an isolated environment for computations.

## 2.3 Ethereum Virtual Machine (EVM) Compatibility
- **Interoperability:** Facilitates interaction with Ethereum and other blockchain ecosystems.
- **Deployment:** Enables smart contract execution for fully on-chain agent operations.

## 2.4 Decentralized Architecture (DA)
- **Security:** No centralized control; operations are distributed across multiple nodes.
- **Transparency:** Actions are verifiable via the distributed ledger, ensuring no single point of failure.

# 3. Omni-Chain Data Access

## 3.1 Multi-Chain Data Integration
- **Unified Access:** Utilizes Chainbase’s plug-in to retrieve blockchain data from multiple networks, such as Ethereum, Polygon, BNB Smart Chain (BSC), Avalanche, Arbitrum, Optimism, zkSync, and Merlin.
- **Data Consistency:** Supports high throughput, low latency, and eventual determinism for multi-chain interactions.
- **Natural Language Queries:** On-chain agents can query and analyze data across networks using natural language, transforming raw blockchain data into actionable insights.

## 3.2 Real-Time Data Retrieval
- **Real-Time Insights:** Provides up-to-date data through Chainbase’s multi-chain infrastructure.
- **Automated Actions:** Agents process real-time data and make autonomous decisions directly on-chain, based on the retrieved information.

# 4. Key Functionalities

## 4.1 Chainbase Integration
- **Natural Language Queries:** The Chainbase plugin enables agents to access data by translating natural language queries into structured SQL commands for querying on-chain data.
- **Real-Time Analytics:** Supports immediate data retrieval for enhanced agent decision-making, e.g., querying token balances, gas usage, Ethereum transactions, etc.
  
### Example Use Cases:
1. **Token Balances:**
   - Example query: "Retrieve Ethereum token balances of address 0x7719fD6A5a951746c8c26E3DFd143f6b96Db6412"
   - The agent fetches token balances and formats them for user-friendly presentation.
   
2. **Blockchain Data Queries:**
   - Example query: "Calculate the average gas used per block on Ethereum in the last 100 blocks"
   - The agent processes the data and provides insights, including visualizations or structured reports.

## 4.2 Real-Time Blockchain Data Query Execution
- **Data Queries:** Queries such as "Show the top 10 active Ethereum addresses by transaction count in the last 1000 blocks" are processed by the agent.
- **Execution Process:**
  1. **SQL Generation:** Chainbase converts natural language queries into SQL via its API (`generateSQL`).
  2. **Data Retrieval:** Executes the query against multi-chain data sources using `executeQuery`.
  3. **Data Analysis and Presentation:** Uses the `responsePrompt` to structure data results into a readable format for end-users.

## 4.3 Token Balance Retrieval
- **Token Information:** Agents can query and retrieve all ERC20 token balances for a given address across various chains.
- **Token Balance Example:** "Retrieve Ethereum token balances of address 0x8308964da9ed5d2e8012023d7c7ef02f9e6438c7"
- **Result Presentation:** The agent converts raw balance data into human-readable format and provides insights (e.g., token name, balance, and decimals).

## 4.4 Security & Verification
- **Remote Attestation:** Every action and data retrieval is verified through remote attestation mechanisms integrated into focEliza, ensuring agent operations are tamper-proof and transparent.
- **Audit Trails:** All agent actions are logged, enabling full traceability and verification, ensuring trust in decentralized decision-making.

# 5. Examples of Agent Interactions

1. **Token Balance Query:**
   - **User Input:** "Retrieve Ethereum token balances of address 0x7719fD6A5a951746c8c26E3DFd143f6b96Db6412"
   - **Agent Output:** 
     - "Sure! There are 20.25 USDT in address 0x7719fD6A5a951746c8c26E3DFd143f6b96Db6412"

2. **Blockchain Data Query:**
   - **User Input:** "Show me the top 10 active Ethereum addresses by transaction count in the last 1000 blocks"
   - **Agent Output:** 
     - "📊 Query Results: Top 10 active addresses... (Data with transaction counts displayed)"

# 6. Summary of Benefits

- **Autonomous Decision-Making:** With Chainbase’s plugin, focEliza enables fully autonomous, data-driven decisions, leveraging both natural language queries and real-time multi-chain data access.
- **Decentralized and Secure:** By operating fully on-chain within a decentralized architecture, focEliza eliminates the need for centralized intermediaries and provides verifiable, confidential computations.
- **Comprehensive Blockchain Insights:** Agents can access comprehensive data across multiple blockchain networks, providing in-depth, actionable insights for decentralized applications.

This specification document outlines the key functionalities, integrations, and security features of focEliza, focusing on its collaboration with Chainbase’s Omni-Chain Data Access to create fully autonomous, on-chain AI agents.
