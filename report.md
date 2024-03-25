# **Blast Futures Exchange Audit Competition on Hats.finance** 


## Introduction to Hats.finance


Hats.finance builds autonomous security infrastructure for integration with major DeFi protocols to secure users' assets. 
It aims to be the decentralized choice for Web3 security, offering proactive security mechanisms like decentralized audit competitions and bug bounties. 
The protocol facilitates audit competitions to quickly secure smart contracts by having auditors compete, thereby reducing auditing costs and accelerating submissions. 
This aligns with their mission of fostering a robust, secure, and scalable Web3 ecosystem through decentralized security solutions​.

## About Hats Audit Competition


Hats Audit Competitions offer a unique and decentralized approach to enhancing the security of web3 projects. Leveraging the large collective expertise of hundreds of skilled auditors, these competitions foster a proactive bug hunting environment to fortify projects before their launch. Unlike traditional security assessments, Hats Audit Competitions operate on a time-based and results-driven model, ensuring that only successful auditors are rewarded for their contributions. This pay-for-results ethos not only allocates budgets more efficiently by paying exclusively for identified vulnerabilities but also retains funds if no issues are discovered. With a streamlined evaluation process, Hats prioritizes quality over quantity by rewarding the first submitter of a vulnerability, thus eliminating duplicate efforts and attracting top talent in web3 auditing. The process embodies Hats Finance's commitment to reducing fees, maintaining project control, and promoting high-quality security assessments, setting a new standard for decentralized security in the web3 space​​.

## Blast Futures Exchange Overview

Blast Futures Exchange is the first orderbook perpetuals DEX with native yield.

## Competition Details


- Type: A public audit competition hosted by Blast Futures Exchange
- Duration: 10 days
- Maximum Reward: $10,000
- Submissions: 75
- Total Payout: $7,500 distributed among 11 participants.

## Scope of Audit

## Project overview

Blast Futures Exchange is a hybrid decentralised orderbook perpetual futures exchange with native yield. 
Blast Futures Exchange introduces native yield, allowing users’ balances to automatically compound, and provide a high-quality trading experience with easy onboarding, advanced charting, and efficient order execution. The platform also features a Fusion Dynamic Automated Market Maker (AMM) to efficiently and optimize liquidity provision by using up-to-date market data, making it more seamless and profitable for users to provide liquidity to the exchange.

## Audit competition scope

Put here a list of all the folders/files that are inside the scope of this audit competition.

```
|-- Blast-Futures-Exchange/
     |-- foundry
          |-- src
               |-- Bfx.sol
               |-- BfxVault.sol
               |-- EIP712Verifier.sol
               |-- IPoolDeposit.sol
               |-- IVault.sol
               |-- PoolDeposit.sol
```

## Low severity issues


- **Issue with `_tokenCall()` Handling Contracts Without Deployed Code**

  The issue pertains to three contracts that process payment tokens through the function `_tokenCall()`. The function is incapable of handling a contract address with no deployed code, which may cause problems if contract operators misconfigure the paymentToken address. This could allow a malicious address to call functions like deposit or stake, disrupting protocol accounting balances. A proof of concept and a solution for only one contract are provided, but the fix reportedly applies to all involved contracts.


  **Link**: [Issue #14](https://github.com/hats-finance/Blast-Futures-Exchange-0x97895c329b950755566ddcdad3395caaea395074/issues/14)


- **Issue with Transferring uint256.max Tokens Without Sufficient User Balance**

  The issue concerns tokens, such as cUSDCv3, that on transferring uint256.max amount of tokens, instead of reverting if the user doesn't hold that amount of balance, transfers the whole user balance. This happens when a user has approved uint256.max to the contract but only has 100 tokens. The contract tries to transfer uint256.max tokens from the user, only receiving 100 tokens, but the accounting interprets this as the user has transferred uint256.max tokens. This could lead to potential loss of funds to the protocol.


  **Link**: [Issue #28](https://github.com/hats-finance/Blast-Futures-Exchange-0x97895c329b950755566ddcdad3395caaea395074/issues/28)



## Conclusion

The audit competition on Hats.finance for Blast Futures Exchange, a decentralized orderbook perpetual futures exchange, was successful, evidenced by 75 submissions and a payout of $7,500 among 11 participants. The competition leveraged the collective experience of multiple auditors to identify vulnerabilities in the smart contracts of Hats.finance, ensuring a proactive approach to bug hunting. It revealed two low-severity issues related to tokens and contract processing, which were resolved effectively. The methodology of the competition, based on a pay-for-results principle, highlights Hats.finance’s commitment to reduce fees, maintain project control, and promote high-quality security assessments. This approach sets a new benchmark for decentralized security in the web3 domain, demonstrating that dematerialized audit competitions can promptly enhance the security of smart contracts.

## Disclaimer


This report does not assert that the audited contracts are completely secure. Continuous review and comprehensive testing are advised before deploying critical smart contracts./n/n
The Blast Futures Exchange audit competition illustrates the collaborative effort in identifying and rectifying potential vulnerabilities, enhancing the overall security and functionality of the platform.


Hats.finance does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.

