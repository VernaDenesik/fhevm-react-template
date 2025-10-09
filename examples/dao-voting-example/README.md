# DAO Voting Example

This example demonstrates a complete dApp using FHEVM SDK - a secure DAO voting system with commit-reveal mechanism.

## Overview

This is a privacy-preserving DAO voting platform that uses cryptographic commit-reveal schemes to ensure fair, manipulation-resistant governance.

## Features

- **Commit-Reveal Voting** - Two-phase voting prevents manipulation
- **Weighted Voting** - Token-based voting power
- **Proposal System** - Community-driven governance
- **Privacy Protection** - Votes hidden during voting period

## Smart Contract

The `SecureDAOVoting.sol` contract implements:

1. **Proposal Creation** - Create governance proposals
2. **Vote Commitment** - Submit encrypted vote hash
3. **Vote Revelation** - Reveal and verify votes
4. **Proposal Execution** - Execute approved proposals

## Usage

### Deploy Contract

```bash
npm install
npm run compile
npm run deploy
```

### Vote on Proposal

```javascript
import { FhevmClient } from 'fhevm-sdk';
import { ethers } from 'ethers';

// Initialize
const provider = new ethers.BrowserProvider(window.ethereum);
const signer = await provider.getSigner();

const client = new FhevmClient({
  provider,
  signer,
  contractAddress: CONTRACT_ADDRESS
});

await client.init();

// Create proposal
const contract = new ethers.Contract(ADDRESS, ABI, signer);
await contract.createProposal(
  "Upgrade Protocol",
  "Proposal to implement new features"
);

// Commit vote (hidden)
const nonce = Math.floor(Math.random() * 1000000);
const support = true; // Your vote

const voteHash = ethers.keccak256(
  ethers.AbiCoder.defaultAbiCoder().encode(
    ['bool', 'uint256', 'address'],
    [support, nonce, await signer.getAddress()]
  )
);

await contract.commitVote(proposalId, voteHash);

// Save nonce for later reveal
localStorage.setItem(`nonce_${proposalId}`, nonce.toString());

// Later: Reveal vote
const savedNonce = localStorage.getItem(`nonce_${proposalId}`);
await contract.revealVote(proposalId, support, savedNonce);
```

## Integration with FHEVM SDK

While this example uses traditional commit-reveal, it can be enhanced with FHEVM:

```javascript
// Encrypt vote before committing
const encrypted = await client.encrypt({
  contractAddress: CONTRACT_ADDRESS,
  callerAddress: await signer.getAddress(),
  value: { support: true }
});

// Submit encrypted vote
await contract.commitEncryptedVote(
  proposalId,
  encrypted.handles[0],
  encrypted.inputProof
);
```

## Contract Flow

1. **Create Proposal**
   - User creates proposal with title and description
   - Voting period starts (7 days)

2. **Commit Phase**
   - Users submit vote hashes
   - Actual votes remain hidden
   - Prevents manipulation

3. **Reveal Phase**
   - Users reveal their votes with nonce
   - Contract verifies hash matches
   - Votes are tallied

4. **Execution**
   - After reveal period ends
   - Proposal executes if approved
   - Results are final

## Security Features

- **Hash Verification** - Ensures vote integrity
- **Time Locks** - Enforced voting periods
- **Weight Management** - Owner-controlled voting power
- **Pause Mechanism** - Emergency controls

## Files

- `contracts/SecureDAOVoting.sol` - Main voting contract
- `package.json` - Dependencies and scripts
- `README.md` - This file

## Learn More

- See the main [README](../../README.md) for SDK documentation
- Check [EXAMPLES.md](../../docs/EXAMPLES.md) for integration patterns
- Watch [demo.mp4](../../demo.mp4) for walkthrough
