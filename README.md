
# focEliza RFC

**focEliza Request for Comments (RFC)** is a collection of concepts, protocols, programs, and standards related to Fully On-Chain ElizaOS. RFCs encourage developers, researchers, and the community to engage in discussions and propose improvements, aiming to establish widely applicable on-chain components for ElizaOS.



## Motivation

We believe that autonomous AI agents will inevitably integrate deeply with blockchain in the future. ElizaOS v1 only includes plugins for interacting with individual blockchains, providing basic capabilities to interact with blockchain-based dApps. ElizaOS v2 will natively integrate TEE (Trusted Execution Environment) and blockchain interaction modules, enabling AI agents to perform verifiable and more flexible blockchain interactions.

However, the relationship between AI agents and blockchain remains limited to AI agents calling dApp functionalities, rather than leveraging blockchain’s decentralized primitives to enhance the autonomy of AI agents and fundamentally transform their nature. Thus, the focEliza project is dedicated to achieving deep integration between blockchain and ElizaOS, creating decentralized AI agents and accelerating the advent of autonomous AI agents.



## focEliza Design Principles

- **Modularity:** focEliza components are standalone and composable, as not all AI agents need to be fully decentralized; they may only require solutions for specific problems.
- **Extensibility:** Interfaces take priority over implementations to support multiple blockchains and infrastructures, catering to the diverse needs of AI agents.
- **Openness:** Different versions can be proposed for the same concept or functionality, with minor variations allowed. This acknowledges the inherent diversity of solutions.



## Scope of focEliza RFC v1

The focEliza RFC will address the following points to accelerate the on-chain progress of ElizaOS AI agents:

### 1. Verifiability
Verifiability is the foundation of decentralized applications. Without verifiable computation, decentralization is meaningless. AI agent verifiability is critical for trustless collaboration with other agents or users.

AI agents will drive advancements in verifiable computation, with TEE being the most viable short-term solution. Previously, TEE was used in specific blockchain components, such as the MEV execution environment of Flashbots. Now, it will become the preferred execution environment for AI agents. Designing TEE components tailored to AI agents will enhance their verifiability, establishing the foundation for trustless collaboration.

### 2. Decentralized Operations
Smart contracts operate in a decentralized manner, without a single entity capable of shutting them down, enabling decentralized applications like fund management and DeFi.

For autonomous AI agents managing significant user funds, the presence of a single administrator able to disable them centralizes the funds. By combining TEE and blockchain, autonomous AI agents can operate in a decentralized manner, becoming trustless entities capable of holding funds and executing tasks without administrator intervention, governed solely by their code.

### 3. On-Chain Identity and Swarm
In the future, the era of multi-AI agents will require protocols for identity registration, discovery, and collaboration as foundational elements of inter-agent cooperation.

If on-chain AI agent interactions rely on centralized entities, trustless mutual authentication between agents will be impossible, hindering decentralized use cases. This is particularly important as economic networks emerge among AI agents.

### 4. On-Chain Autonomy and Digital Life
Currently, AI agent autonomy is defined by their ability to independently plan and execute tasks, making them intelligent robots rather than intelligent "life forms."

On-chain autonomy and digital life are not mainstream demands but cater primarily to gaming and metaverse applications. NFTs define eternal on-chain metadata, FOCG establishes decentralized game rules, and metaverse infrastructure enables rendering and experiences. AI agents bridge these gaps by bringing dynamic capabilities to NFTs, decentralized entities to FOCG, and spatial programs to the metaverse.

### 5. On-Chain Functional Components
AI agents need functional components for practical blockchain interactions to move beyond toys and achieve industrial application.

These components include on-chain security, flexible data access, and dynamic blockchain interaction, enabling practical use cases for on-chain Eliza.

### 6. Infrastructure for On-Chain AI Agents
Existing infrastructure may not fully meet the needs of on-chain AI agents, such as performance (AI agents operate at higher frequencies than humans) and customization (e.g., more complex on-chain verification mechanisms or extended on-chain functionality).





## focEliza RFC Structure

```plaintext
focElizaRFC/
├── Verifiability/
│   ├── Concept.md
│   ├── High-Level Design.md
│   ├── Discussion/
│   │   └── xxxx.md
│   ├── Feat_Verifiable_Log/
│   |   ├── Intro.md
│   │   └── Design.md

```



## How to Contribute

1. Submit articles related to the concept in the "Discussion" directory. These can be Twitter threads or blog posts.
2. Submit plugin designs in the "Implementation" directory. These should include technical overviews and a branch or PR with the technical implementation.
3. Revise the content of concept files.
4. Revise the content of high-level design files.

