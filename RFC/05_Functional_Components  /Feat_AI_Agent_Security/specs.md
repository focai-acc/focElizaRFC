# 1. Overview

The **GoPlus Security plugin** provides a comprehensive Web3 security solution designed to protect users across a wide range of blockchain networks. Built with a decentralized architecture, it is seamlessly integrated into the **FocEliza** ecosystem, enhancing the **ElizaOS** AI agent framework with cutting-edge, decentralized blockchain security. This plugin aims to enable AI agents to autonomously detect and mitigate risks during on-chain interactions, providing protection across transactions and various blockchain services.

# 2. Objectives

The GoPlus Security plugin for FocEliza has been developed with the following objectives:
- Enable **AI agents** to automatically assess and respond to security risks on blockchain platforms.
- Enhance **Web3 security** with a focus on token, contract, wallet, and website safety.
- Integrate seamlessly into the **FocEliza plugin architecture**, utilizing GoPlus' extensive coverage of over 30 blockchain networks.
- Provide critical **security features** for decentralized applications (dApps), community management, and user wallet protection.

# 3. Integration Points

## 3.1 GoPlus Security API

The GoPlus Security plugin integrates directly with the **GoPlus API**, which supports a range of security checks:
- **Token Security Detection**: Identifies malicious or high-risk tokens.
- **NFT Security Detection**: Analyzes NFT contracts and metadata for vulnerabilities.
- **Phishing Website Detection**: Identifies phishing domains and unsafe websites.
- **Authorization and Signature Security**: Verifies risky contract authorizations and signatures.

Supported blockchains include **Ethereum, Solana, Sui**, and more.

## 3.2 AI Agent Interaction

The plugin enables **AI agents** to perform security checks as part of their operation. These security checks occur through an automated flow where the AI agent interacts with GoPlus API to:
- **Analyze input data** (such as wallet addresses, contract addresses, and URLs).
- **Determine risk levels** for assets and interactions.
- **Provide recommendations** or actions to mitigate identified risks, such as revoking approvals or blocking malicious interactions.

# 4. Core Functionalities

## 4.1 Token Security Checks
- **Action**: [EVMTOKEN_SECURITY_CHECK], [SOLTOKEN_SECURITY_CHECK], [SUITOKEN_SECURITY_CHECK]
- **Description**: The plugin can automatically assess the security of tokens based on their blockchain network. This includes analysis of smart contract risk, permissions, transaction mechanisms, and more.
- **Supported Networks**: Ethereum (EVM), Solana, Sui, and others.

## 4.2 Rug Pull Detection
- **Action**: [RUGPULL_SECURITY_CHECK]
- **Description**: Detects potential rug pull risks in tokens or projects by analyzing contract permissions, liquidity settings, and other critical indicators.
- **Supported Networks**: Ethereum, BSC, Solana, etc.

## 4.3 NFT Security Analysis
- **Action**: [NFT_SECURITY_CHECK]
- **Description**: Provides a security analysis of NFT projects by evaluating contract permissions, minting mechanisms, and potential trading risks.
- **Supported Networks**: Ethereum, Polygon, Solana, etc.

## 4.4 Address Security Monitoring
- **Action**: [ADRESS_SECURITY_CHECK]
- **Description**: Monitors specific addresses to identify known malicious addresses, high-risk addresses, or scam addresses across supported blockchains.

## 4.5 Approval Security Checks
- **Action**: [APPROVAL_SECURITY_CHECK], [ACCOUNT_ERC20_SECURITY_CHECK], [ACCOUNT_ERC721_SECURITY_CHECK], [ACCOUNT_ERC1155_SECURITY_CHECK]
- **Description**: Evaluates and monitors contract authorizations to prevent risky approvals of third-party transactions.
- **Supported Tokens**: ERC20, ERC721, ERC1155.

## 4.6 Phishing Detection
- **Action**: [URL_SECURITY_CHECK]
- **Description**: Detects phishing websites by analyzing URLs for known malicious patterns.

# 5. Security Framework

- **Decentralized Security Model**: Built upon GoPlus' decentralized security network, ensuring security is omnipresent throughout the Web3 ecosystem. This model leverages the scalability of decentralized security across all transaction types.
- **Continuous Monitoring**: The plugin allows AI agents to continuously monitor risk factors, flagging any dangerous activities in real-time.
- **Risk Mitigation**: Upon detecting risks, AI agents can autonomously take corrective actions like revoking permissions, blocking malicious tokens, or sending alerts to users about potential threats.

# 6. Use Cases

## 6.1 Trading and Investment
- **Automatic Token Screening**: The plugin will automatically scan tokens before initiating trades or investments to assess their risk level.
- **Rug Pull Detection**: If a potential rug pull is detected, the AI agent can warn users or automatically prevent transactions.

## 6.2 Asset Management
- **Risk Monitoring**: The plugin ensures that authorized contracts and token holdings are continuously monitored for new risks or unauthorized changes.
- **Revocation and Alerts**: The AI agent can autonomously revoke permissions for risky contracts or warn users about potential security issues.

## 6.3 Community Management
- **Phishing Link Detection**: The AI agent will automatically remove phishing links from community channels, safeguarding participants from malicious websites.
- **Project Safety Alerts**: Alerts users about high-risk projects or trending scams within the community.

# 7. Deployment and Configuration

## 7.1 Service Initialization
- The plugin will be initialized with the GoPlus API key, which is required for authenticating security requests. The AI agent runtime will handle the API key securely, ensuring no leaks of sensitive information.

## 7.2 Integration with FocEliza
- The GoPlus Security plugin integrates seamlessly into the FocEliza environment, where it can be called directly by AI agents within FocEliza's architecture. The plugin is accessible as a service in the agent's runtime, making security checks a core part of its operations.
