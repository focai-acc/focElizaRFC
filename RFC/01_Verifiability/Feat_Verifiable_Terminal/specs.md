# **focEliza Verifiable Terminal Specification**

## **1. Overview**
The focEliza Verifiable Terminal is a web-based interface for monitoring and verifying AI agent activities within a Trusted Execution Environment (TEE). The system provides real-time log viewing, TEE attestation verification, and searchable activity logs with cryptographic signatures for authenticity verification.

## **2. Key Components**

### **Main Application (app/page.tsx)**
- **Purpose:** Entry point of the application, sets up React Query for data management
- **Dependencies:** 
  - Next.js framework
  - React Query for data fetching
  - Content component

### **Content Component (app/component/content.tsx)**
- **Purpose:** Core UI component handling the display and interaction logic
- **State Management:**
  - Agent list management
  - Log viewing and searching
  - TEE attestation data
  - UI state (tabs, search, animations)
- **Features:**
  - Real-time log updates (20-second polling interval)
  - Search functionality for verifiable logs
  - TEE attestation display
  - Signature verification display

### **API Layer (app/api/index.ts)**
- **Purpose:** Handles all backend communication
- **Endpoints:**
  - `GET /verifiable/agents` - Retrieves list of AI agents
  - `POST /verifiable/logs` - Fetches verifiable logs with search capability
  - `POST /verifiable/attestation` - Retrieves TEE attestation data
- **Parameters:**
  - Logs API: Supports pagination (page, pageSize) and content search
  - Attestation API: Requires agentId and publicKey

## **3. Usage Instructions**

### **Development Setup**
1. Environment Configuration:
   ```bash
   # Create .env file with:
   NEXT_PUBLIC_API_URL=http://...
   ```

2. Installation:
   ```bash
   npm install
   # or yarn install
   # or pnpm install
   ```

3. Development Server:
   ```bash
   npm run dev
   # or yarn dev
   # or pnpm dev
   ```

### **API Integration**
To interact with the verifiable terminal:

1. Agent List Retrieval:
   ```typescript
   const response = await fetch(`${apiUrl}/verifiable/agents`, {
     method: 'GET',
     headers: { 'Content-Type': 'application/json' }
   });
   ```

2. Log Querying:
   ```typescript
   const response = await fetch(`${apiUrl}/verifiable/logs`, {
     method: 'POST',
     headers: { 'Content-Type': 'application/json' },
     body: JSON.stringify({
       query: { contLike: searchQuery },
       page: 1,
       pageSize: 35
     })
   });
   ```

3. Attestation Verification:
   ```typescript
   const response = await fetch(`${apiUrl}/verifiable/attestation`, {
     method: 'POST',
     headers: { 'Content-Type': 'application/json' },
     body: JSON.stringify({
       agentId: agent_id,
       publicKey: public_key
     })
   });
   ```

## **4. Security Considerations**

### **TEE Integration**
- The system operates within a Trusted Execution Environment
- CPU generates a secure root key inaccessible to humans
- Autonomous operation similar to smart contract execution
- Cryptographic signatures verify content authenticity

### **Verification Features**
- Real-time log verification through cryptographic signatures
- TEE attestation proof verification
- Secure wallet control limited to the AI agent
- Verifiable state tracking and monitoring

## **5. Additional Notes**

### **Upcoming Features**
1. Multi-agent Support:
   - Simultaneous monitoring of multiple focEliza AI agents
   - Enhanced agent management capabilities

2. Blockchain Integration:
   - DA (Data Availability) module support
   - Blockchain-based verifiable log storage

### **Technical Requirements**
- Node.js environment
- Next.js 15.1.2
- React 18.2.0
- TypeScript support
- TailwindCSS for styling 
