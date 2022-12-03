# Smart contract registry demo

## Introduction

The smart contracts of a protocol define how it works and how its tokenholders can propose, vote, and implement changes to the protocol.

An up-to-date registry of a protocol’s smart contracts helps different stakeholders to learn more about the protocol and how it evolves over time.

## How this repo is structured

Each project has a registry file under the `projects` folder with its respective name (e.g. `compound.json`). Each entry in the registry file corresponds to a project's smart contract and relevant metadata.

Here's an example of a smart contract entry (cCOMP token) from the `compound.json` registry file:

```
{
    "name": "cCOMP",
    "address": "0x70e36f6BF80a52b3B46b3aF8e106CC0ed743E8e4",
    "chain": "ethereum",
    "version": "v2",
    "type": "core",
    "description": "Logic for the COMP lending market and the associated cCOMP token",
    "explorers": [
      "https://etherscan.io/address/0x70e36f6bf80a52b3b46b3af8e106cc0ed743e8e4"
    ]
}
```

Check out the `template.json` to see a field-by-field example.

### Explaining the template.json

- `name`: Should be something short and easy to understand, spaces are allowed.
- `address`: We prefer the `address` in the template to be [checksummed](https://coincodex.com/article/2078/ethereum-address-checksum-explained/).
- `chain`: Check the `template.json` for a valid `chain`. We've chosen `polygon` over `matic` for 0xPolygon as an example. If the chain doesn't exist, let's check it out together in the Pull Request.
- `version`: Smart contracts evolve and new versions get developed constantly. For tokens the version should default to `v1`, although exceptions exist.
- `type`: Every smart contract is either core to the business or related to governance of the project. That's why we want to categorize each smart contract with either `core` or `governance` for standardization purposes.
- `description`: A one-liner that explains what the smart contract does.
- `explorers`: A list of explorers that can be used to deep dive into the smart contracts.

## How to add a new project.json

The naming of projects must match our main [website](https://www.tokenterminal.com/)'s project pages, which adopt the "kebab-case" naming convention: names are lowercase and spaces are replaced by hyphens.

Examples:

- MakerDAO: `makerdao`
- Alpha Finance: `alpha-finance`
- Pie DAO: `pie-dao`
- Binance Smart Chain: `binance-smart-chain`
- yearn.finance: `yearn-finance`

If you're adding a project that's already listed on Token Terminal, you can check out the individual project page's URL: [tokenterminal.com/terminal/projects/binance-smart-chain](https://www.tokenterminal.com/terminal/projects/binance-smart-chain).

## How to add smart contracts with factory contracts

Some projects make use of a Factory pattern in their smart contract design. This means that there's a contract that dynamically creates new contracts.

For the registry to be practical we don't necessarily want to track all the factory-instantiated contracts.

That's why we'd like to track only the factory contract and one example of a factory-instantiated contract. You can check Uniswap's `uniswap.json` registry for an example.

## How to contribute

First of all, thank you for being awesome and taking the time to contribute. Being able to gather all relevant smart contracts in the ecosystem is a community-effort, which you are part of.

### Forking the repo

In order for you to contribute, you will have to fork our repo. Check this [guide](https://docs.github.com/en/get-started/quickstart/fork-a-repo) on how to do that.

### Creating a branch

We want to encourage best practices in the creation of branches. Having consistent branch naming makes the initial step of the review clear. We focus on two main naming conventions: `feature type` and `description`.

In this repo we have two feature types: the ones that add a new project (`add`) to the repo and the ones that update an existing project (`update`).

An example branch name could be: `update-compound-comptroller`. A bad one would be `test2`.

### Creating a commit

We enforce the usage of `commitlint`. It has same principles as in the creation of a branch. You can check out [commitlint.js.org](https://commitlint.js.org/) for more info.

### Creating a pull request

Creating a pull request from a fork is as easy as creating one within the repo. You can check out more info from [here](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork).
