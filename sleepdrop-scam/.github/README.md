# Sleepdrop scams detection

## Description

A sleepdrop token is an ERC20 token contract whose allocation is associated with a known legitimate contract.
The owner of the contract proceeds to distribute the token, such that they appear to be coming from the legitimate contract.

For instance, https://etherscan.io/tx/0xefa9492d7d85d59c2eba3c47645364d3bf7529c8437f6648233b70508ef5f1cd#eventlog shows a thLink token being airdropped to users from the legitimate Chainlink contract.

The sleepdrop bot should identify these sleepdrop token contracts upon deployment (low severity alert with likely lower precision, which trigger on a token contract creation where a large portion of tokens are automatically assigned to a legitimate contract) and upon distribution (e.g. through an airdrop function call) that emits events where the token is transferred from the legitimate contract to a set of addresses (high severity).
The metadata of the bot should contain information about the holder, the token contract name, victims, deployer, etc. Corresponding scammer and victim labels should be emitted.

## Supported Chains

- Ethereum
- List any other chains this agent can support e.g. BSC

## Alerts

Describe each of the type of alerts fired by this agent

- FORTA-1
  - Fired when a transaction contains a Tether transfer over 10,000 USDT
  - Severity is always set to "low" (mention any conditions where it could be something else)
  - Type is always set to "info" (mention any conditions where it could be something else)
  - Mention any other type of metadata fields included with this alert

## Deployment

The code is bundled in a Docker container.

## Tests

### Data

The agent behaviour can be verified with the following transactions:

- 0x3a0f757030beec55c22cbc545dd8a844cbbb2e6019461769e1bc3f3a95d10826 (15,000 USDT)
