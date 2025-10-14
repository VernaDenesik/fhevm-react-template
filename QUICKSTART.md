# Quick Start Guide

Get started with FHEVM SDK in less than 5 minutes!

## Installation

```bash
npm install fhevm-sdk fhevmjs ethers
```

## Basic Usage (< 10 lines)

```typescript
import { FhevmClient } from 'fhevm-sdk';
import { ethers } from 'ethers';

// Setup
const provider = new ethers.BrowserProvider(window.ethereum);
const signer = await provider.getSigner();

// Initialize
const client = new FhevmClient({
  provider,
  signer,
  contractAddress: '0x...'
});

await client.init();

// ✅ Ready to use!
```

## Encrypt Data

```typescript
const encrypted = await client.encrypt({
  contractAddress: '0x...',
  callerAddress: await signer.getAddress(),
  value: 42
});

// Use in contract call
await contract.submitData(encrypted.handles, encrypted.inputProof);
```

## Decrypt Data

```typescript
const result = await client.userDecrypt({
  handle: 123n,
  contractAddress: '0x...',
  userAddress: await signer.getAddress()
});

console.log('Decrypted:', result.value);
```

## React Integration

```typescript
import { useFhevm } from './hooks/useFhevm';

function MyComponent() {
  const { client, isInitialized } = useFhevm('0x...');

  if (!isInitialized) return <div>Loading...</div>;

  return <div>Ready!</div>;
}
```

## Next Steps

- 📖 [Full Documentation](./README.md)
- 🎯 [API Reference](./docs/API.md)
- 💡 [Examples](./docs/EXAMPLES.md)
- 🎥 [Video Demo](./demo.mp4)

## Examples

Try the included examples:

```bash
# Next.js
cd examples/nextjs-example && npm install && npm run dev

# Vue
cd examples/vue-example && npm install && npm run dev

# Node.js
cd examples/node-example && npm install && npm start
```

## Need Help?

- Check [Setup Guide](./docs/SETUP.md)
- Review [Examples](./docs/EXAMPLES.md)
- Watch [demo.mp4](./demo.mp4)
