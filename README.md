# Poly-2

## Logical Gate zk-SNARK Project

## Introduction
This project demonstrates the implementation of a logical AND gate using zk-SNARKs, created with the Circom language. The project includes everything from compiling the circuit, generating zero-knowledge proofs, to deploying and verifying proofs using a Solidity smart contract on Ethereum's test network.

## Project Structure
- **`/circuits`**: Contains Circom circuit definitions.
- **`/build`**: Compiled circuit outputs including R1CS, WASM, and symbol files.
- **`/contracts`**: Solidity verifier contract.
- **`/scripts`**: Deployment scripts and other utilities.
- **`/test`**: Tests for the contracts and scripts.

## Getting Started

### Prerequisites
Ensure you have Node.js installed on your machine, and optionally Truffle or Hardhat if you prefer a structured project for smart contract deployment.

### Installation
Clone this repository and install the required Node modules:

```bash
git clone https://github.com/<yourusername>/LogicalGate-zkSNARK.git
cd LogicalGate-zkSNARK
npm install
```

### Compile the Circuit
To compile the logical gate circuit using Circom:

```bash
circom circuits/LogicalGate.circom --r1cs --wasm --sym -o build
```

### Trusted Setup
Generate the proving key and verification key:

```bash
cd build
snarkjs setup
```

### Calculate Witness and Generate Proof
Generate a witness and a zk-SNARK proof:

```bash
snarkjs calculatewitness --wasm LogicalGate.wasm --input ../input.json
snarkjs groth16 prove
```

### Deploy the Verifier Contract
Deploy the verifier contract to a test network like Sepolia or Mumbai:

```bash
truffle migrate --network sepolia
```

### Verify the Proof
Execute the verification process on the blockchain:

```bash
truffle exec scripts/verify.js
```

## Testing
Ensure that your setup works correctly by running:

```bash
truffle test
```
- - -
