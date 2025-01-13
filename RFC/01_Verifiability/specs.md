# Verifiability for AI Agents

## Overview

Verifiability is a foundational requirement for AI agents operating within decentralized and trustless environments. Ensuring that the actions, states, and logs of AI agents can be validated not only enhances their trustworthiness but also establishes them as credible participants in Web3 ecosystems. This document outlines the essential verifiable features for AI agents and provides a roadmap for achieving robust verifiability.

![img1.png](./Feat_Verifiable_Log/img1.png)



## Verifiability Levels

Depending on the use case, not all AI agents require the same level of verifiability. Some may only need to prove that their computations take place in a secure environment (Level 1), while others handling sensitive data or financial transactions may need to provide detailed logs (Level 2) or even verifiable operational states (Level 3). Carefully assessing the operational context, security requirements, and trust model of each AI agent can help determine the most appropriate verifiability level.



## Level 1: TEE Report

At this level, it can be confirmed that the AI agent operates within a TEE.

The foundation of verifiability lies in Trusted Execution Environments (TEE). A TEE report serves as the baseline proof that a computation occurred within a secure and isolated environment. However, this level of verification is limited to proving that something happened inside the TEE, without offering insights into what was computed or the results of the computation.

Example: Dstack Remote Attestation

Dstack's remote attestation provides certain technical fields that confirm operations are being executed within a TEE. However, it does not reveal specific details about the program's operational state, such as:

* The parameters used for initialization.
* The current application state.
* Execution logs or runtime behavior.



## Level 2: Verifiable Logs
At this level, it can be verified what specific actions the AI agent has executed.

Building upon the TEE report, verifiable logs represent the next tier of verifiability. These logs do more than just confirm the AI agent is running in a secure enclave; they outline a cryptographically secured record of the agent’s operations. Specifically, v_logs enable external parties to:

1. **Access Detailed Execution Logs**
   - External entities can query time-stamped records of the AI agent’s actions, including function calls, updates to internal state, and other notable events.
   - The logs can be stored on-chain, off-chain, or in hybrid solutions, providing flexible storage options depending on performance and cost constraints.
2. **Verify Authenticity via Cryptographic Signatures**
   - Each log entry is signed by the AI agent’s private key, which resides securely within the TEE.
   - Verifiers can use the corresponding public key to ensure that the logs have not been tampered with and indeed originate from the correct TEE instance.
3. **Ensure Integrity with the Agent’s Public Key**
   - By matching the log signatures against the agent’s known public key, any attempt to alter, insert, or delete log entries can be immediately detected.
   - This guarantees an unbroken chain of trust, allowing auditors or stakeholders to trace every execution step.
4. **Facilitate Auditing and Traceability**
   - These verifiable logs form a transparent audit trail, simplifying compliance with regulations or internal governance requirements.
   - They enable stakeholders to pinpoint anomalies, investigate system behaviors, and confirm that all executed actions adhere to specified rules and policies.

By providing verifiable logs, AI agents offer users tangible proof of operational integrity. This level of transparency enhances trust in autonomous decision-making processes and fosters a higher degree of accountability—especially critical in financial, healthcare, or other sensitive domains.



## Level 3: Verifiable States

At this level, it is possible to verify the AI agent's state data, including externally readable and verifiable operational parameters, configuration items, and critical business fields.

This entails not just confirming that the agent is running securely (Level 1) or that it performed specific actions (Level 2), but also that its internal configurations and data align with its claimed functionality.

For example, if an AI agent holds a TEE wallet, its public key must be verifiably queryable. In another case, when the AI agent charges users fees based on specific rates, these rates should be verifiably accessible.

Specifically, verifiable States enable external parties to:

* **Transparent and Queryable State Data**

  - External entities can programmatically query the AI agent’s critical parameters (e.g., fee structures, access policies, or wallet information) and receive cryptographically signed proofs.

  - Ensures operational transparency for sensitive or business-critical data, such as exchange rates, resource limits, or algorithmic thresholds.

* **Consistency and Trustworthiness**

  - The agent’s state is cryptographically verifiable and secured within the TEE, preventing unauthorized modifications.
  - State changes are captured in conjunction with verifiable logs (Level 2), forming a cohesive record of how and when the state was updated.

  

**Comparisons to Smart Contract World State**

- In blockchain environments, a smart contract’s “world state” provides a single source of truth for all contract-related data.
- Verifiable states for AI agents serve a similar purpose, allowing them to operate with equivalent levels of trust and transparency—*but within the flexibility of an off-chain or hybrid environment.*
- This parallel to smart contract behavior helps integrators reason about the AI agent’s data integrity and reliability.



By integrating verifiable states, AI agents achieve the highest level of transparency and accountability. Not only can external parties confirm that an agent runs securely and follows a clear audit trail of actions, but they can also inspect and trust the agent’s current operational parameters—empowering the agent to participate in ecosystems that demand rigorous proof of integrity.
