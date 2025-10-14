# Project Structure

Complete overview of the FHEVM Universal SDK project structure.

```
fhevm-react-template/
│
├── 📦 packages/                        # SDK packages
│   └── fhevm-sdk/                      # Universal FHEVM SDK
│       ├── src/                        # Source code
│       │   ├── index.ts                # Main exports
│       │   ├── client.ts               # FhevmClient class
│       │   ├── init.ts                 # Initialization
│       │   ├── encrypt.ts              # Encryption utilities
│       │   ├── decrypt.ts              # Decryption utilities
│       │   ├── eip712.ts               # EIP-712 signatures
│       │   ├── types.ts                # TypeScript types
│       │   └── utils.ts                # Helper utilities
│       ├── dist/                       # Compiled output
│       ├── package.json                # SDK package config
│       ├── tsconfig.json               # TypeScript config
│       └── README.md                   # SDK documentation
│
├── 🎯 examples/                        # Example applications
│   │
│   ├── nextjs-example/                 # Next.js 14 app (REQUIRED)
│   │   ├── src/
│   │   │   ├── app/                    # App router
│   │   │   │   ├── page.tsx            # Main page
│   │   │   │   ├── layout.tsx          # Root layout
│   │   │   │   ├── globals.css         # Global styles
│   │   │   │   └── page.module.css     # Page styles
│   │   │   ├── components/             # React components
│   │   │   │   └── ConnectWallet.tsx   # Wallet connection
│   │   │   └── hooks/                  # Custom hooks
│   │   │       └── useFhevm.ts         # FHEVM hook
│   │   ├── public/                     # Static assets
│   │   ├── package.json
│   │   ├── tsconfig.json
│   │   ├── next.config.js
│   │   ├── .env.example
│   │   └── README.md
│   │
│   ├── vue-example/                    # Vue 3 application
│   │   ├── src/
│   │   │   ├── App.vue                 # Main component
│   │   │   ├── main.ts                 # Entry point
│   │   │   └── style.css               # Styles
│   │   ├── index.html
│   │   ├── package.json
│   │   ├── vite.config.ts
│   │   └── README.md
│   │
│   ├── node-example/                   # Node.js CLI app
│   │   ├── index.js                    # Main script
│   │   ├── package.json
│   │   ├── .env.example
│   │   └── README.md
│   │
│   └── dao-voting-example/             # DAO dApp example
│       ├── contracts/
│       │   └── SecureDAOVoting.sol     # Voting contract
│       ├── package.json
│       └── README.md
│
├── 📚 docs/                            # Documentation
│   ├── SETUP.md                        # Setup guide
│   ├── API.md                          # API reference
│   └── EXAMPLES.md                     # Integration examples
│
├── 🎥 demo.mp4                         # Video demonstration
│
├── 📄 Root files
│   ├── README.md                       # Main documentation
│   ├── SUBMISSION.md                   # Competition submission
│   ├── QUICKSTART.md                   # Quick start guide
│   ├── PROJECT_STRUCTURE.md            # This file
│   ├── package.json                    # Root package config
│   ├── LICENSE                         # MIT License
│   └── .gitignore                      # Git ignore rules
```

## File Count

- **Total files:** 29+ source files
- **Documentation:** 10 markdown files
- **Examples:** 4 complete applications
- **SDK source:** 8 TypeScript modules

## Key Directories

### `/packages/fhevm-sdk`
The core SDK package - framework-agnostic, type-safe, modular.

### `/examples`
Complete working examples for different frameworks and use cases.

### `/docs`
Comprehensive documentation covering setup, API, and examples.

## Setup Commands

### Install all dependencies
```bash
npm install
```

### Build SDK
```bash
npm run build:sdk
```

### Run examples
```bash
npm run dev:nextjs    # Next.js
npm run dev:vue       # Vue
npm run dev:node      # Node.js
```

## Features by Directory

### SDK Package (`packages/fhevm-sdk`)
- ✅ Framework agnostic core
- ✅ TypeScript support
- ✅ Wagmi-like API
- ✅ Modular exports
- ✅ Complete type definitions

### Next.js Example (`examples/nextjs-example`)
- ✅ App Router (Next.js 14)
- ✅ React hooks
- ✅ Wallet connection
- ✅ Encrypt/decrypt UI
- ✅ TypeScript

### Vue Example (`examples/vue-example`)
- ✅ Vue 3 Composition API
- ✅ Reactive state
- ✅ Vite build
- ✅ TypeScript

### Node.js Example (`examples/node-example`)
- ✅ CLI application
- ✅ Backend integration
- ✅ Environment variables
- ✅ ES modules

### DAO Example (`examples/dao-voting-example`)
- ✅ Smart contract
- ✅ Commit-reveal voting
- ✅ Integration guide

## Documentation Files

1. **README.md** - Main project documentation
2. **SUBMISSION.md** - Competition submission overview
3. **QUICKSTART.md** - Quick start guide
4. **PROJECT_STRUCTURE.md** - This file
5. **docs/SETUP.md** - Detailed setup instructions
6. **docs/API.md** - Complete API reference
7. **docs/EXAMPLES.md** - Integration examples
8. **packages/fhevm-sdk/README.md** - SDK documentation
9. **examples/*/README.md** - Example-specific docs

## Technology Stack

### SDK
- TypeScript
- fhevmjs
- ethers.js

### Next.js Example
- Next.js 14
- React 18
- TypeScript
- CSS Modules

### Vue Example
- Vue 3
- Vite
- TypeScript

### Node.js Example
- Node.js (ES modules)
- ethers.js
- dotenv

## License

MIT License - See LICENSE file
