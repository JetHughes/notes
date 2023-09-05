---
title: "veracity-summary"
tags: 
---

Bullet list



### Aim
The aim of this project was to consider aspects of a closed public permissioned blockchain. Currently, some believe there is an issue with current permissioned blockchains in that they are not sufficiently decentralised. On the other hand, open permissionless blockchains such as Bitcoin are cumbersome to use due to their need for an associated cryptocurrency.

### Scenarios
There were three main scenarios that spend time to explore: Adding a new member, removing a member and accidental transactions. This process helped me to understand some of the intricacies of the system I was trying to conceptualise. Before this process, I was lost in the infinite number of forms that a solution to our problem could take. By focusing one single aspect of the system, I was forced to accept a basic framework of what the solution could be and use it to explore how a given scenario might occur

#### Adding a participant
This was the first scenario I considered. Initially I wanted to explore how a group of participants might band together to create a fork of the chain. However, this seemed like an necessarily complex scenario to begin with.  The idea I came up with was to have a smart contract which is triggered when an application arrives, which then collects votes from the existing participants and accepts or rejects the application based on the outcome of the vote. We would also need to find some way of protecting the application process from a sort of DoS attack where the attacker flooded the system with applications. 

#### Removing a participant
This scenario occurs in two situations. Firstly when a participant wants to leave voluntarily, which can be handled easily, and secondly when a participant or group of participants agree to forcefully remove another participant or group of participants. To accomplish this we could use a similar system to the add participant but in reverse. 

### Solidity Contract
Near the end of the project before my break, I decided to try to test the Add New Participant scenario. I decided to do this by making a smart contract that would run on the Iroha Blockchain. I could use the Hyperledger Burrow integration to run a smart contract in the Ethereum Virtual Machine, which could interact with Iroha. 

This contract would be called when a new member ==how would it be called?== needed to be added to the chain. When it was called, it would wait ==for what amount of time?== for all ==(or some percentage of)== existing voting members to vote on whether to accept the new member. Based on the outcome of the vote, the contract would then either reject the applicant or add them to the chain. ==how to add?==

### Security Issues
Dos attack on the chain targeted at the system of adding new participants. By creating numerous request to join the chain, the voting system would become inundated with request and legitimate applicants would be ==hidden?==. 