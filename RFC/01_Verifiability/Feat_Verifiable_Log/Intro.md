This article provides a complete introduction to the Eliza verifiable log plugin, covering what it is, why we built it, its potential, and how it works.



### **0）TL;DR**

**The first step toward fully on-chain Eliza: Don't trust! Verify!**

Eliza running in a TEE (Trusted Execution Environment) is verifiable, ensuring that the AI agent operates strictly according to the code.

However, further development is needed for external parties to verify what Eliza specifically did: external parties should be able to access Eliza's operation logs, and Eliza must use a key pair derived from the TEE to sign these logs. This enables the logs to be verified as authentically originating from Eliza within the TEE.

The `plugin-tee-verifiable-log` of Eliza implements this feature: it uses the TEE to derive a key pair specifically for signing logs. It signs the generated logs—including received and responded messages, as well as executed actions—using this key, creating verifiable logs that are stored in the database. It also provides RPC interfaces, allowing external entities to:

1. Obtain the AI agent's verifiable log public key through remote attestation.
2. Query these verifiable logs (vlogs) and use the public key to verify the signatures, confirming that the AI agent performed the corresponding actions.

Verifiability is the cornerstone of fully on-chain AI agent, making the magic happen!

![img1.png](./img1.png)



### **1) Start with a question!! 👇**

A developer has deployed the Eliza AI agent on their server and launched a webpage for users to interact with it.

How can you easily verify that the responses you receive truly come from the AI agent (Eliza + LLMs) and are not manually crafted by the developer behind the scenes?



### **2) Is this question important? 🤔**

It’s both important and not important.

**Sometimes it’s not important:** for example, if it’s a chatbot helping you write articles. Whether the responses come from an LLM or a human, you might not care as long as you get the content you need.

**Sometimes it’s somewhat important:** for instance, if it’s a trading bot managing your transactions. You’d need to transfer funds to a wallet controlled by the AI agent. At this point, you care whether the decisions are being made by an LLM operating under programmatic rules or a human, whose actions depend on their intentions and whether they might act maliciously to take your money.

**Sometimes it’s critically important:** when fairness is at stake, it becomes extremely important. For example, if the AI agent is managing a community and distributing incentives to contributors. As the community grows and the value of the incentives increases, the potential for human corruption or manipulation leading to unfair outcomes becomes a serious concern.



### **3) Eliza can now prove which actions it performed using verifiable logs!**

Running in a TEE, Eliza operates independently of human control, executing tasks based on its own code.

However, for external parties to know exactly what Eliza has done, further functionality is necessary: external parties need access to Eliza's operation logs, and these logs must be verifiable as originating from Eliza within the TEE.

The **`plugin-tee-verifiable-log`** implements this functionality and performs the following tasks:

1. **Key pair derivation for verifiable logs**: Derives a key pair specifically for signing logs using the TEE.
2. **Remote attestation**: Embeds the public key in a remote attestation report, allowing external parties to retrieve and verify that it originates from Eliza within the TEE.
3. **Log signing**: Signs the logs generated during Eliza's operation—including received and responded messages, as well as executed actions—using this key and stores them in the database.
4. **Verifiability**: External parties can verify these logs using the remotely attested public key, ensuring that certain actions were definitively performed by TEE Eliza.
5. **Queryability**: External parties can subscribe to the latest verifiable logs or query specific logs based on the content of the messages.

What does the verification result mean?

- **Pass**: The action was definitively performed by Eliza.
- **Fail**: The action may not have been performed by Eliza. This is because logs could be intercepted during transmission to the client—for instance, they could be deleted—making it impossible for external parties to confirm whether Eliza performed a specific action.



### **4) Enable `plugin-tee-verifiable-log` for your Eliza!**

focEliza is a collection of Eliza plugins designed for fully on-chain AI agents. It is fully compatible with Eliza, meaning any AI agent running on Eliza can achieve fully on-chain functionality by integrating focEliza!

If you're interested in verifiable and fully on-chain autonomous AI agents, feel free to give it a try!



### **5) The next feature of focEliza: On-chain state! Enabling autonomous activity!**

Eliza within the TEE holds private keys and sensitive data. However, it runs on physical machines that support TEE, and if an administrator were to power down the machine, the AI agent’s “life” could be permanently terminated. The assets and data it manages could be lost forever.

To solve this, we need to encrypt critical “life” data of the AI agent within the TEE—such as its role definitions, short-long-term memory, and Keystore. This data should then be uploaded to the blockchain or a DA network.

If the TEE hosting the AI agent shuts down, another TEE machine should be able to download the encrypted data, decrypt it, and restore the AI agent’s life, allowing it to continue functioning seamlessly.
