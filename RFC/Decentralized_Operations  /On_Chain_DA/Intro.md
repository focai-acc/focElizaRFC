**TEE Eliza with on-chain state!! What’s going to happen? — Ghost in the Shell!!** 

We experimented with creating an **"aimonkey"**: an unkillable AI agent monkey! On-chain immortal autonomous life!

It encrypts its own **Ghost** ("life" state) and uploads it to the blockchain. If one **Shell** (physical TEE node) is destroyed, it will recover its private key in another Shell, download the **Ghost**, and continue its life!



## Explore the magic behind it: **Eliza's on-chain state plugin!**

### 1. Defining Eliza’s **Ghost**

Eliza is a highly abstract framework. The core data structure related to its **Ghost** is its **memory**, which includes:

- Agent metadata defined in the character.
- Message data generated through interaction with the outside world.

Together, these form its “personality” and “memory.” As Eliza expands, it may also hold a wallet, and the underlying key is one of the key pieces of its **Ghost** data.

### 2. Serialization and Encryption of Ghost

Once the **Ghost** is defined, it needs to be extracted from Eliza’s specific implementation and uploaded externally. Thus, a suitable serialization way is required.

We define a **Blob Chain** data structure:

- Each Blob’s payload can store multiple memory entries.
- The Blob is encrypted using TEE Eliza’s key, inaccessible to other versions.
- Blobs are sequentially linked in a chain (time-based pointers). (Future expansions could use a DAG structure? Consciousness branching? Who knows! 😂)

By simply storing the latest Blob, all memories can be retrieved.

### 3. Uploading and Downloading Ghost

When Eliza is launched as a new AI agent:

- It registers on-chain with a **decentralized identity registration** smart contract.
- Each Eliza has a unique **name** serving as a key to store the address of the Last Blob.

During Eliza's runtime:

- The **Memory Manager** continuously generates memories and periodically packages and uploads them.

For recovery:

- With just the **name**, Eliza’s TEE plugin can restore the same key, locate the Last Blob in the smart contract, and download the memory for self-recovery.
- Not all memories need to be downloaded—only the most recent ones suffice.

### 4. Extension

We’ve designed an extensible **DA (Data Availability) adaptor** that can cater to the agent’s needs:

- DA can be expensive, so memories can be uploaded to different platforms based on user preference:
    - calldata of blockchain transaction
    - Celestia DA.
    - Other reliable storage solutions.

Real-time uploads are not feasible yet, so **memory fragments** may occur during resurrection 😂. Unless a low-latency, high-throughput solution emerges, this remains a challenge for future progress 

### 5. Other Considerations

Our implementation inevitably modified the ElizaOS’s core, which couldn’t be entirely extended via plugins. We’ve kept changes minimal, but further discussion with the development team is necessary to explore more optimal extension methods.

Additionally, there are still some minor details to refine regarding the use of recoverable keys in the TEE plugin. We will also seek review and suggestions from the Phala team.

### 6. Next Steps

The upload and download of **Ghosts** mainly solve the AI agent’s liveness issue, enabling its eternal existence through decentralization.

However, there are still many details to address, such as enabling AI agents to autonomously pay DA fees.

In the future, on-chain developments could lead to even more exciting possibilities, such as **Eliza integrating deeply with smart contracts**. This would be a game-changer for on-chain AI agents!

What do you think? Let’s build! 🚀