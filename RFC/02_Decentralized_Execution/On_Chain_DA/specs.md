# On-Chain Data Availability

## 1. Overview

This document specifies a mechanism for **securely storing and recovering** the static state (“Ghost”) of AI agents running within a Trusted Execution Environment (TEE). By separating **computation** (in the TEE) from **persistent state** (on-chain or in a Data Availability layer), the system ensures agents can be resurrected on new nodes without centralized intervention. Future enhancements to this system will address dynamic state management and on-chain governance.



## 2. High-Level Design

The design comprises two primary layers that together ensure resilience and flexibility:

1. **Level 1: On-Chain Data Availability**  
   Focuses on **static data**, such as memory logs and cryptographic key material, which is encrypted in the TEE and stored in a tamper-resistant manner (blockchain or DA storage). This enables state **backup and recovery** when TEE nodes fail.

2. **Level 2: On-Chain State for Dynamic Data (Planned)**  
   Envisions **governance-driven** updates to agent configurations. Dynamic parameters will be managed through on-chain proposals and consensus, extending the agent’s autonomy while preserving decentralization.



## 3. Data Classification

Data associated with each AI agent can be categorized as follows:

- **Character Data**  
  - Defines the agent’s identity, attributes, or personality traits.  
  - Typically static and used to instantiate or reconstruct the agent’s profile.

- **Memory Data**  
  - Contains historical records of interactions and internal context needed for decision-making.  
  - May include multiple **memory entries** that grow over time, forming the agent’s “personality” and knowledge base.

- **Key Data**  
  - Consists of cryptographic keys (e.g., private keys for wallets or encryption) generated and sealed inside the TEE.  
  - Keys never leave the TEE in plaintext form and are critical for encrypting and signing agent data.

- **State Data** (Dynamic)  
  - Includes operational parameters and runtime flags that may need frequent updates.  
  - Management of this data through on-chain governance is a **future** goal and is not covered in detail in this specification.



## 4. On-Chain Components

### 4.1 Level 1: On-Chain Data Availability

Level 1 addresses **static state** and ensures that the agent’s core data (character definitions, memory logs, and key materials) remain recoverable in a decentralized manner.

#### 4.1.1 Data Serialization and Encryption

1. **State Extraction**  
   - The agent’s TEE environment provides a **Memory Manager** (or equivalent) responsible for collating memory data (and, optionally, metadata) into a serializable format.

2. **Encryption**  
   - Before storage, all data is **encrypted** using a key sealed inside the TEE.  
   - Neither the encryption key nor the decrypted data is exposed outside the TEE, maintaining confidentiality.

3. **Chunked/Sequential Data Structure**  
   - Encrypted states are stored in sequential or linked **“chunks”**, each referencing the previous chunk’s identifier.  
   - This approach ensures a recoverable timeline of the agent’s state. Future enhancements might allow branching (e.g., if multiple versions of an agent evolve from different points in time).

#### 4.1.2 Upload and Storage

1. **Data Upload**  
   - Encrypted chunks are uploaded to the blockchain or a **DA layer** (e.g., Celestia or other decentralized storage).  
   - Each upload can carry a reference to the agent’s **unique identifier** (such as an on-chain name or address) for easy retrieval.

2. **Smart Contract Registration**  
   - A dedicated **identity registration** contract maintains a pointer (e.g., a hash or URI) to the latest chunk of the agent’s state.  
   - This minimal reference is all that is needed to locate the full on-chain or off-chain data.

3. **DA Adapter**  
   - The system provides an **extensible module** (the “DA adapter”) to interface with various storage solutions.  
   - Cost or performance constraints may dictate which DA platform is used at any given time. Future expansions could enable dynamic selection based on agent preferences or available funds.

#### 4.1.3 Recovery Process

1. **TEE Reinitialization**  
   - When a node fails or an agent is moved, a **new TEE instance** can be instantiated with the same sealed key material (or an equivalent recoverable key mechanism).

2. **State Lookup**  
   - The TEE queries the identity registration contract with the agent’s unique identifier to find the most recent **encrypted chunk reference**.

3. **Decryption and Reconstruction**  
   - The TEE downloads the encrypted chunk(s) from the DA layer and performs decryption using the internal key.  
   - The agent’s “memory” and any associated metadata or wallet keys are restored to their previous state.

4. **Partial Recovery**  
   - Complete historical data might be large or unnecessary for immediate operation. Agents can choose to **fetch only recent chunks** if full context is not required.

### 4.2 Level 2: On-Chain State for Dynamic Data (Planned)

1. **Governance-Driven Updates**  
   - Future iterations may introduce an on-chain governance mechanism to manage the **dynamic aspects** of the agent’s state (e.g., fee structures, operational parameters, or behavior flags).

2. **Decentralized Proposals and Voting**  
   - Any modifications to runtime state could require **community or stakeholder approval**, ensuring transparency and preventing unilateral changes.

3. **Autonomous Fee Payments**  
   - As the agent matures, it may manage its own funds (via on-chain wallets) to autonomously pay DA fees, thereby **sustaining** its continuous operation without external intervention.



## 5. Additional Considerations

1. **Minimal Core Modifications**  
   - Supporting on-chain state necessitates modest adjustments to the TEE’s core system (e.g., integrating a Memory Manager or a specialized plugin). Efforts should be made to **keep these changes minimal** while ensuring sufficient functionality.

2. **Security and Trust**  
   - The TEE must safeguard cryptographic materials.  
   - The encryption and decryption processes **must remain fully attested** and verifiable, preventing key leakage.

3. **Latency and Throughput Constraints**  
   - High-frequency, real-time data uploads may be costly or impractical. Systems should tolerate **delayed or batched uploads**, which can lead to minor discrepancies in the recovered memory.

4. **Future Scalability**  
   - Potential enhancements include advanced data structures (e.g., DAG-based) for more complex branching states.  
   - Deeper integration with smart contracts for agent logic can be explored, enabling more sophisticated on-chain AI behavior.



## 6. Conclusion

This specification provides a **robust framework** for encrypting and storing TEE-based AI agent data on-chain or in a dedicated DA layer. By maintaining a clear **separation of concerns**—TEE for secure computation and encryption, on-chain/DA for resilient storage—agents can be restored on any node without depending on a centralized server.

- **Level 1** focuses on static data (character definitions, memory logs, and key material) and ensures reliable **backup and recovery**.  
- **Level 2** (planned) aims to incorporate governance-driven updates for **dynamic state**, thereby extending the agent’s capabilities and self-sufficiency.

This design lays the groundwork for **autonomous, persistent AI agents** that can outlast individual nodes or operating environments, paving the way for more advanced on-chain AI integrations in the future.
