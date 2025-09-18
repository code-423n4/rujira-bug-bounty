# Rujira Bug Bounty

Welcome to the Rujira bug bounty program!

## Max Payout
 - Max Critical Severity Payout: Up to $25,000
 - Max High Severity Payout: Up to $2,000

### Areas of focus/interest

Please note that we are mostly interested in Critical severity reports, i.e. bugs that could lead to:
 - Direct theft of funds or NFTs
 - Permanent freezing of funds or NFTs
 - Protocol insolvency
 - Unauthorized Minting / Burning of Tokens

We will also consider High severity reports, but with a much lower payout, i.e. bugs that could lead to:
 - Temporary freezing of funds
 - Theft of unclaimed funds (e.g., yield, royalties)
 - Permanent freezing of unclaimed funds
 - Material Oracle Manipulation (materially influencing on-chain price feeds or data sources)

## Background on Rujira

### What Is Rujira?

Rujira is the App Layer on THORChain built using CosmWasm, offering an integrated suite of DeFi dapps, accessible with native assets from all connected chains in the form of ["Secured Assets"](https://docs.thorchain.org/thorchain-finance/secured-assets) powered by THORChain technology.

For more information, please check the [How it works](https://docs.rujira.network/how-it-works/understanding-the-app-layer) sections of our docs.

### Further Technical Resources & Links
- [**Rujira Docs**](https://docs.rujira.network)
- [**Rujira Gitlab**](https://gitlab.com/thorchain/rujira)
- [**Rujira Website**](https://rujira.network/)
- [**Twitter**](https://x.com/RujiraNetwork)
- [**Discord**](https://discord.gg/ddWCkJjD4u)

# Scope & Severity Criteria

The severity and hence payout of smart contract vulnerabilities depends on the amount of funds at risk due to the vulnerability. This will be determined by the maximum value of funds at risk in the impacted contract(s) at the time of report submission, per the following formula:
 - Max Payout for Critical report = MIN(10% * value of funds at risk, $25,000)
 - Max Payout for High report = MIN(10% * value of funds at risk, $2,000)

Payouts are handled by the Rujira team directly and are denominated in USD. Payouts will be made in USDC or USDT at the team's discretion.

## Smart Contracts in Scope

Rujira aims to offer a complete suite of DeFi dapps and tools. The following applications are currently part of the scope. We will add more overtime as we continue to develop the ecosystem and launch new protocols:

| Name | Description | Example (with thor address) | Repo | Docs |
|------|-------|-------|-------|-------|
| FIN (RUJI Trade) | A 100% on-chain orderbook DEX | [BTC/USDC pair](https://thorchain.net/address/thor1dwsnlqw3lfhamc5dz3r57hlsppx3a2n2d7kppccxfdhfazjh06rs5077sz). There are as many contracts as there are pairs |  [rujira-fin](https://gitlab.com/thorchain/rujira/-/tree/main/contracts/rujira-fin) | [docs](https://docs.rujira.network/core-products/ruji-trade) |
| BOW (RUJI Pools) | Multi-strategy Automated Market Maker (AMM) built to add liquidity to the Orderbook DEX | [BTC/USDC xyk strategy](https://thorchain.net/address/thor1g97844v7wuvz58m6p3vqp3u28nxaglqsag4dte2wrrry7sge9llq0t5tav). There are as many contracts as there are strategies per pair | [rujira-bow](https://gitlab.com/thorchain/rujira/-/tree/main/contracts/rujira-bow) | [docs](https://docs.rujira.network/core-products/ruji-pools) | 
| Ghost (RUJI Lending) | Decentralized money market | [USDC Lending vault](https://thorchain.net/address/thor1hs6wzyk4tf25ujd7lu07hhnkj4tl38m3wpp6qqw50y5r3e3x7zksnvj3qr). There are as many contracts as there are tokens available for lending | [rujira-ghost-vault](https://gitlab.com/thorchain/rujira/-/tree/main/contracts/rujira-ghost-vault) | [docs](https://docs.rujira.network/core-products/ruji-lending) | 
| Rujira Revenue Converter | Collect reward tokens and convert them into a smaller number of assets to be distributed to stakers | [Revenue Collector 1](https://thorchain.net/address/thor1mcy9jtp4kzl8q2lvdgfgsl8jvqrf504uphkf0pz2p9wud8tsntesjvccew). There are multiple instances of Revenue Converter deployed | [rujira-revenue](https://gitlab.com/thorchain/rujira/-/tree/main/contracts/rujira-revenue) | NA | 
| Rujira Staking | Generic staking contract for revenue distribution with inbuilt liquid staking | [RUJI single-sided staking](https://thorchain.net/address/thor13g83nn5ef4qzqeafp0508dnvkvm0zqr3sj7eefcn5umu65gqluusrml5cr). There are several instances of Staking Contracts deployed | [rujira-staking](https://gitlab.com/thorchain/rujira/-/tree/main/contracts/rujira-staking) | NA |
| RUJI Launchpad (PILOT) | Fundraising platform for new projects using an innovative Dutch auction mechanism | Out-of-scope for now, not live on mainnet yet | Coming soon | [docs](https://docs.rujira.network/core-products/ruji-launchpad) | 

## Out-of-Scope

Anything outside the source folders listed above is out of scope.

### Known Issues

Bug reports covering previously-discovered bugs (listed below) are not eligible for a reward within this program. This includes known issues that the project is aware of but has consciously decided not to “fix”, necessary code changes, or any implemented operational mitigating procedures that can lessen potential risk. Every issue opened in the repo, closed PRs, previous contests and audits are out of scope.

The following are known issues and therefore are out of scope:
 - FIN (RUJI Trade): Swap overpayment leads to loss for buyers. When a user submits a swap above an exact multiple of the base asset’s price, the excess amount is not refunded or adjusted properly.

### Previous Audits

Any **previously reported** vulnerabilities mentioned in past audit reports are out of scope and not eligible for a reward.

Rujira previous audits can be found below:
 - [RUJI Trade (FIN) by Halborn](https://www.halborn.com/audits/thorchain/ruji-trade-fin-4604e5)
 - [RUJI Pools (BOW) by Halborn](https://www.halborn.com/audits/thorchain/ruji-pools-bow-19e51f)
 - [Revenue Converter & Staking contracts by Zellic](https://github.com/Zellic/publications/blob/master/Rujira%20-%20Zellic%20Audit%20Report.pdf)
 - [Revenue Converter & Staking contracts by Halborn](https://www.halborn.com/audits/thorchain/rujira-staking-319044)

### Specific Types of Issues

- Informational findings.
- Design choices related to protocol. For example, the ability to deploy permissionless pools.
- Issues that are ultimately user errors and can easily be caught in the frontend. For example, transfers to address(0).
- Rounding errors.
- Relatively high gas consumption.
- Attacks requiring access to leaked keys/credentials.
- Attacks requiring access to privileged addresses (governance, strategist).
- Vulnerabilities related to 3rd party services (AWS, Google, etc).
- Any denial of service attacks.
- Documentation errors.
- Issues in example or demo applications.
- Issues that take an infeasible amount of computation to exploit.
- Risk of loss due to decline in pool asset prices.
- Price manipulation on third-party exchanges.
- Exploits based on delayed or extreme price feed updates.
- Attacks that are not economically feasible.
- Attacks requiring a malicious behaviour from THORChain node operators.

# Additional Context

### Trusted Roles
- Rujira Deployer Multisig (admin/owner) is responsible for storing, deploying and upgrading smart contract code, as well as setting/updating contracts' parameters. Other deployer addresses could be whitlisted by THORChain node operators.
- THORChain node operators have the ability via governance (mimir) to pause the entire layer, or specific contracts, e.g. in the event of an exploit.

### Miscellaneous
- All valid reports must have valid proof of concept included.
- Current and former employees, contractors and contributors to Rujira, and their family members, are ineligible for bounties.
