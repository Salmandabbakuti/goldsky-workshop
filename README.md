# Goldsky Subgraph Workshop

This workshop is designed to help you get started with deploying subgraphs on Goldsky using various methods.

## About Goldsky

Goldsky is a decentralized indexing protocol for querying blockchain data offering high-performance subgraph hosting and realtime data replication pipelines. Goldsky offers two core self-serve products that can be used independently or in conjunction to power your data stack. Get live blockchain data in your database with Mirror and flexible indexing and querying with Subgraphs.

## Subgraphs - Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/en/) v16.0.0 or later
- [Goldsky Account](https://app.goldsky.com/)

#### CLI Installation

```bash
curl -fsSL https://cli.goldsky.com/install | bash
```

#### CLI Authentication

```bash

# Login to Goldsky and paste your API key when prompted
goldsky login
```

### 1. Deploying from Source code:

In your existing Subgraph project directory, run the following commands:

```bash
# Generate the subgraph code with graph cli
graph codegen

# Build the subgraph
graph build

# Deploy the subgraph to Goldsky
goldsky subgraph deploy <subgraph name>/<version> --path .
```

### 2. Deploying/Migrating From TheGraph:

Migrate existing subgraph from TheGraph's Hosted Service/Decentralized Network to Goldsky with the following command:

```bash
goldsky subgraph deploy <your-subgraph-name>/<your-version> --from-url <your-subgraph-query-url>
```

### 3. No-code Deployment:

For no code deployment, you need contract address, ABI and chain name of the contract. You can get these details from the explorer of the chain where the contract is deployed. For example, if you want to deploy a subgraph for a contract deployed on Ethereum, you can get the details from [Etherscan](https://etherscan.io/).

Once you have the details, you need to prepare config file with the details of your contract, ABI. You can refer to the sample file `ft_config.json` in this repository.

```bash
goldsky subgraph deploy <name>/<version> --from-abi <path-to-config-file-not-abi>

```

## Mirror - Getting Started

Mirror is a serverless data pipeline platform that allows you to get real-time data into your database with one .yaml definition file.

### 1. Creating Database Secret

```bash
# Keep your db connection string handy, follow the prompts
goldsky secret create --name <your-db-secret-name>
```

### 2. Creating Pipeline:

1. Interactively: through guided CLI
2. Programmatically: through a `.yaml` definition file

```bash
# Interactively, follow the prompts
goldsky pipeline create <your-pipeline-name>

# Programmatically
goldsky pipeline create <your-pipeline-name> --definition-path ./gs_pipeline.yaml --status ACTIVE
```

# Additional Resources

- [Goldsky Website](https://goldsky.com/)
- [Goldsky Docs](https://docs.goldsky.com/get-started/subgraphs)
- [Goldsky Subgraph Docs](https://docs.goldsky.com/get-started/subgraphs)
- [GoldSky Mirror Docs](https://docs.goldsky.com/mirror/create-a-pipeline)
- [Mirror Pipeline Config Reference](https://docs.goldsky.com/reference/config-file/pipeline)
- [Goldsky Reference](https://docs.goldsky.com/reference/cli)

# License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
