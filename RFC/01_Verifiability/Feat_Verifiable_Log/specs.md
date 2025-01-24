# **Feat_Verifiable_Log Specification (Draft)**

## **1. Introduction & Motivation**

When Eliza (an AI agent) runs inside a Trusted Execution Environment (TEE), external parties can trust that the AI agent’s code is **not** tampered with. However, that alone does not let them confirm exactly **what** the AI agent did. For high-stakes scenarios—managing funds, granting rewards, or ensuring fairness—merely trusting the host’s claims is insufficient.  

**Verifiable Logs** solve this gap. They allow Eliza to produce **signed** records of its actions, which can be **queried** and **verified** by any interested party. By binding a key pair to the TEE environment via **remote attestation**, these logs can confidently be traced back to the AI agent rather than a human operator or forged source.

---

## **2. Overview of Key Tasks**

### **(1) Key Pair Derivation**
- Eliza derives a dedicated signing key pair *inside* the TEE.  
- The private key remains in the enclave; the public key is later used for signature verification.

### **(2) Remote Attestation**
- The TEE includes the public key in an attestation report.  
- External parties validate this report to confirm it belongs to the genuine TEE-based Eliza instance.

### **(3) Log Signing**
- As Eliza receives or responds to messages, or performs actions, it signs each log entry with the private key.  
- These **verifiable logs** (vlogs) typically contain a timestamp, event type, payload, and signature.

### **(4) Verifiability**
- Anyone can verify the logs using the **attested public key**.  
- If a log’s signature is valid, that event was provably generated inside the TEE by Eliza. If it fails, it may be forged or tampered with.

### **(5) Queryability**
- The `plugin-tee-verifiable-log` provides an interface (RPC, REST, etc.) for retrieving and filtering logs.  
- This makes auditing, compliance checks, and real-time monitoring feasible.

---

## **3. Detailed Procedures**

### **Procedure 1: Derive the Verifiable Log Signing Key**

1. **TEE Key Generation**  
   - The Verifiable Log plugin requests the TEE to generate a key pair specifically for signing logs.  
   - The private key remains sealed inside the TEE; the public key is exported for verification.

2. **Attestation Binding**  
   - The TEE prepares an attestation report that embeds the **public key**.  
   - External verifiers can validate this report through a vendor service (e.g., Intel SGX DCAP) to ensure authenticity.

---

### **Procedure 2: Eliza Generates Verifiable Logs**

1. **Event Logging**  
   - Whenever Eliza receives user messages, sends responses, or executes actions, it creates a log entry.  
   - Each entry includes at least: timestamp, event type, payload (details of the event), and is signed within the TEE.

2. **Signed Storage**  
   - Each log entry (vlog) carries a signature produced by the private key.  
   - The plugin stores vlogs in a database or other storage medium (e.g., IPFS, an on-chain system, or local DB).

3. **Log Data Example**  
   ```jsonc
   {
     "timestamp": "2025-01-15T12:34:56Z",
     "type": "action_call",
     "payload": {
       "action": "execute_trade",
       "pair": "ETH/USDC",
       "amount": 5
     },
     "signature": "base64_of_signature"
   }
   ```

---

### **Procedure 3: User Queries & Verifies Logs**

1. **Query Interface**  
   - An external party calls the plugin’s endpoint (e.g., `GET /vlogs`) to fetch logs by timeframe, event type, or other filters.  
   - The system returns the matching log entries with their signatures.

2. **Verification**  
   - The user obtains the **attested public key** and checks each vlog’s signature.  
     - **Signature Valid** ⇒ The log is confirmed to be from TEE-based Eliza.  
     - **Signature Invalid** ⇒ The log may be forged or tampered with.

3. **Interpretation**  
   - After confirming validity, the user can rely on these logs for decision-making, audits, or building trust in Eliza’s actions.

---

## **4. Developer Guidelines**

1. **Plugin Activation**  
   - Install and enable `plugin-tee-verifiable-log` in Eliza’s configuration.  
   - Ensure it integrates with the TEE plugin to request key generation and attestation.

2. **Customization of Logged Events**  
   - By default, the plugin may capture major inbound/outbound messages and action calls.  
   - Developers can add or remove event types as needed for specialized scenarios (e.g., only log financial transactions).

3. **Query Endpoint Setup**  
   - Provide a consistent API (REST, GraphQL, or RPC) to retrieve logs.  
   - Include robust filtering or search features for large-scale audits.

4. **Real-Time Streaming** (Optional)  
   - For scenarios requiring immediate verification, consider broadcasting logs to a decentralized network or real-time feed to minimize the chance of withholding.

**Example**:  
A DeFi trading module might configure the plugin to log every trade request and result. Auditors can later query “all trades in the past 24 hours” and verify the TEE signatures to confirm Eliza truly initiated those trades.

---

## **5. Security Considerations**

- **Key Confidentiality**:  
  The private key must remain in TEE custody. Any compromise to the TEE environment could invalidate log authenticity.

- **Log Withholding**:  
  If logs are never surfaced or are selectively withheld, external verifiers only see partial data. Real-time replication (e.g., storing logs on-chain) can mitigate this risk.

- **Attestation Validity**:  
  Attestation certificates and the verification process should be kept up-to-date (no expired certificates, correct vendor endpoints, etc.).

- **Performance**:  
  Generating and signing every event in the TEE can introduce overhead. Evaluate the trade-off between granularity and system throughput.

---

## **6. Co-building with Artela Network and Phala Network**

*(Placeholder: content to be added. Overview of how these networks provide specialized infrastructure or complementary technology for verifiable logs and fully on-chain AI agents. For instance, Artela’s AI-focused stack or Phala’s cryptographic computer paradigm can be highlighted here.)*

---

## **7. Conclusion**

By combining **key derivation, remote attestation, log signing, verifiability,** and **queryability**, the `plugin-tee-verifiable-log` enforces a “Don’t trust—verify!” model for Eliza. This empowers external parties to *confidently* rely on Eliza’s actions without fear of tampering by human operators.  

**Feat_Verifiable_Log** not only strengthens trustless AI agent interactions but also forms a foundation for further **fully on-chain** capabilities—such as verifiable states, on-chain data storage, and more advanced TEE/zk integrations. It’s a vital building block toward a decentralized, self-governing AI ecosystem where each action can be transparently audited and securely verified.
