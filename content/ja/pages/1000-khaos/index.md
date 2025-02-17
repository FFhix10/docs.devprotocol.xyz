---
title: Khaos
date: 2021-05-07
permalink: /{{ locale }}/khaos/index.html
subtitle: Dev Protocol's oracle that confidentially authenticates off-chain data for on-chain use cases.
eleventyNavigation:
  key: Khaos
  order: 1000
  title: Khaos
---

## What's Khaos?

Khaos is an oracle service designed to bring Internet data into blockchains while keeping secret information, such as secret tokens, under wraps. Initially, we will only support Dev Protocol, but we plan to open it up in the future.

## How does it work?

Khaos has two interfaces, Authentication, and Oraclize. The authentication interface authenticates that the user is a credential holder and returns a unique public key. The oraclize interface brings data across the Internet to the blockchain while hiding secret information through public keys.

## How Khaos's authentication interface works

When Khaos receives an authentication request from a user, it executes an authentication method. The authentication request contains secret information for authentication (usually a secret token) and a message(like a user ID) that expects to be authenticated by that secret information. If the authentication method is passed, Khaos returns the public key paired with the secret information. By retrieving the message with its public key, it guarantees the message's authenticity while hiding the secret information. An authentication method executed by an authentication request is freely extendable by the user.

![How Khaos Stores Confidentials](/content/{{ locale }}/images/khaos/how-khaos-stores-confidentials.png)

[Created by SequenceDiagram.org](https://sequencediagram.org/index.html#initialData=C4S2BsFMAIAkHsDu0DSALAhvAztAysPAE6S4DC8AdgGYgAmkloG42AUGwCICCADr9ABiRKsEZ0AtAD5APBuAYffRZceSEQBuqgFwAlSAEcArqWC4MB4GkagAxhlBU2leGOjwNRaPMU58q95u5zNEpoAFtIC3g6XAAjAE9oA2xVCUgADzFKBjpoNi9MHxV1FKkASSZVSgidfSNsYDZysSIq4Gl8pV9iohrsXipkx2cYN1VPBQLlPy0CYhhrKloGJhAWPInOovdpHn4hEQqsmuADFtxeDBASHN4DGPAQa2gAa0g4oA)

## How Khaos's oraclize interface works

Khaos monitors some contract events in batches. The target of the monitoring can be any address that a user deploys to. The user-deployed contract makes an oraclize request to Khaos by emitting an event according to the interface; when Khaos receives the oraclize request, it fetches some data from the Internet the event messages. The data is fetched into blockchains by calling the contract's callback method according to the user-defined functions. The data fetching method executed by the oraclize request is freely extendable by the user. An authentication method executed by an authentication request is freely extendable by the user.

![How Khaos Oraclizes](/content/{{ locale }}/images/khaos/how-khaos-oraclizes.png)

[Created by SequenceDiagram.org](https://sequencediagram.org/index.html#initialData=C4S2BsFMAIAkHsDu0DSALAhvAztA8gE4YDG4IAXpNgFDUAiAggA5PQBiB8AdsJFwCYBaAHwBhbsCLFg2AFwAlSAEcArlRnR+GYBmgAzSMGJpqAI3gAPaPABukAtHE8pM2QFEAtmFnQABgEU1AgBPX2hIOx5qcHh4VgBZbjB4Bwi+GWpAHg3AGH30LFwAZXs7AhEnSRJXNkNjaGALanKXbBEcvJxoIoIShUMVAi5ceuo+fizczA6ukpEASR57LkNe1XVqed4Bw1aJ-M7i+17sJm5sSHH2woPSsQlm2VEMcHBTEgBrRrvKluFGFnZOAsBL1gP1BvoamhIPxNNoMNQgA)
