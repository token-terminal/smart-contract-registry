# Smart contract registry

## Introduction

The smart contracts of a protocol contain the relevant information regarding how the protocol works, and how its tokenholders can propose, vote, and implement changes to the protocol over time.

An up-to-date registry of a protocol’s smart contracts makes it easy for different stakeholders to learn more about the different functions of a protocol, and analyse how those evolve over time.

## How this repo is structured

The registry file contains a list of objects with the following example data (from `compound.json`):

```
{
    "name": "cAAVE",
    "address": "0xe65cdB6479BaC1e22340E4E755fAE7E509EcD06c",
    "chain": "ethereum",
    "version": "v2",
    "type": "core",
    "description": "Includes the logic for the AAVE lending market and the associated cAAVE token",
    "explorers": [
        "https://etherscan.io/address/0xe65cdb6479bac1e22340e4e755fae7e509ecd06c"
    ]
}
```

Each project has a registry file under `projects/` folder with their respective name, e.g. `compound.json`. Each smart contract addition is a new entry to a project's registry file.

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

We want the naming of projects to be consistent and identical to our main [website](https://www.tokenterminal.com/)'s project pages.

We enforce a case style called "kebab-case" for projects: names are lowercase and each space in the name is separated by a hyphen.

Few examples:

- MakerDAO: `makerdao`
- Alpha Finance: `alpha-finance`
- Pie DAO: `pie-dao`
- Binance Smart Chain: `binance-smart-chain`

If you're adding a project that's already on the site, you can check out the individual project page's url: https://www.tokenterminal.com/terminal/projects/binance-smart-chain.

## How to add smart contracts with factory contracts

Some projects make use of a Factory pattern in their smart contract design. This means that there's a contract that dynamically creates new contracts.

For the registry to be practical we don't necessarily want to track all the factory-instantiated contracts.

That's why we'd like to track only the factory contract and one example of a factory-instantiated contract. You can check Uniswap's `uniswap.json` registry for an example.

## How to contribute

First of all, thank you for being awesome and taking the time to contribute. Being able to gather all relevant smart contracts in the ecosystem is a community-effort, which you are part of.

### Forking the repo

In order for you to contribute, you will have to fork our repo. Check this [guide](https://docs.github.com/en/get-started/quickstart/fork-a-repo) on how to do that.

### Creating a branch

We want to encourage best practices in the creation of branches. Having consistent branch naming makes the intial step of the review clear. We focus on two main naming conventions: `feature type` and `description`.

In this repo we have two feature types: the ones that add a new project (`add`) to the repo and the ones that update an existing project (`update`).

An example branch name could be: `update-compound-comptroller`. A bad one would be `test2`.

### Creating a commit

We enforce the usage of `commitlint`. It has same principles as in the creation of a branch. You can check out https://commitlint.js.org/ for more info.

### Creating a Pull Request

Creating a Pull Request from a fork is as easy as creating one within the repo. You can check out more info from [here](https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork).
