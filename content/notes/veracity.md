---
title: "Veracity"
aliases: 
tags: blockchain
---
# Abstract
Blockchain technology falls into two distinct classes: open (permissionless) blockchains such as those underlying bitcoin, Ethereum and Cardano; and closed (permissioned) blockchains such as implemented in the Hyperledger Fabric project. To motivate decentralised participation, open blockchains (presently) require an associated cryptocurrency, which can be a risky distraction. However, closed blockchains are considered by some to be insufficiently decentralised.This summer project aims to prototype a compromise: a closed blockchain system that encodes voting rules about self-governance, so that closed blockchain technology can be used in a more open manner. Experience in programming blockchain systems is not assumed. Depending on the student involved, the project will balance work between design and modelling of the blockchain governance rules, and implementation of such a rule set over an existing closed blockchain system.

# Questions	
[answered-questions](notes/answered-questions.md)

- [ ] What happens if a participant is caught being untruthful? 
	- Can they be automatically kicked out or is a vote required? 
	- How can we distinguish between mistakes and intentional deceit?
		- Maybe a reputation system. This way one mistake is not fatal, and a reputation can be restored over time
- [ ] Should the central/initiating groups retain higher privileges even after other participants have joined?
- [ ] Do members of a private consortium blockchain enter into a legal agreement?

# Notes
- [[veracity-summary]]
- [think-writing/log](veracity-think-writing.md)
	- [[veracity-week01|week1]]
	- [[veracity-week02|week2]]
	- [[veracity-week03|week3]]
	- [[veracity-week04|week4]]
- [[scenarios|scenarios]]
- [veracity-chain](notes/veracity-chain.md)
- [reading-papers](notes/reading-papers.md)
- [blockchain-terms](notes/blockchain-terms.md)

[412-lectures](notes/412-lectures.md), [hyperledger](hyperledger.md), [governance](notes/governance.md) , [decentralized-autonomous-organization](notes/decentralized-autonomous-organization.md), [DeFi](notes/DeFi.md), [dApps](notes/dApps.md), [sybil-problem](notes/sybil-problem.md), [smart-contracts](smart-contracts.md), [transaction-finality](transaction-finality.md), [consensus](notes/consensus.md), [CPR-governance](notes/CPR-governance.md), [eth-governance](notes/eth-governance.md), [food-manufacturing](notes/food-manufacturing.md), [bitcoin](bitcoin.md), [[YAC]], [[holochain]], [[quadratic voting]]

# Reading

## Blockchain Papers
**Good**
- [[a systematic literature review on blockchain governance]]
- [[A novel framework for policy based on-chain governance of blockchain networks]]
- [[Application of Blockchain and Internet of Things to Ensure Tamper-Proof Data Availability for Food Safety]]
- [[Defining Blockchain Governance — A Framework for Analysis and Comparison]]
- [[A blockchain architecture for industrial applications]]

**Read**
- [[YAC — BFT Consensus Algorithm for Blockchain]]
- [[Parallel Governance for Decentralized Autonomous Organizations enabled by Blockchain and Smart Contracts]]
- [[Vulnerabilities on Hyperledger Fabric]]
- [[Blockchain as a confidence machine — The problem of trust & challenges of governance]]
- [[Governance in the Blockchain Economy — A Framework and Research Agenda]]
- [[Now the Code Runs Itself — On-Chain and Off- Chain Governance-of- Blockchain Technologies]]
- [[Decision Problems in Blockchain Governance — Old Wine in New Bottles or Walking in Someone Elses Shoes]]
- [[Fork-free hybrid consensus with flexible Proof-of-Activity]]
- [[A renewable energy microgrids trading management platform based on permissioned blockchain]]
- [[research-on-the-reciprocal-mechanism-of-hybrid-governance-in-blockchain]]
- [[zkCrowd — A Hybrid Blockchain-Based Crowdsourcing Platform]]
- [[Toward an Interoperability Architecture for Blockchain Autonomous Systems]]
- [[Blockchain Technology and Decentralized Governance – Is the State Still Necessary]]
- [[Blockchain Based Wine Supply Chain Traceability System]]
- [[Enhanced immutability of permissioned blockchain networks by tethering provenance with a public blockchain network]]
- [[Blockchain Governance Challenges — Beyond Libertarianism]]
- [[Decentralized Network Governance — Blockchain Technology and the Future of Regulation]]
- [[A review on blockchain governance]]
- [[Permissionless and Permissioned, Technology-Focused and Business Needs-Driven — Understanding the Hybrid Opportunity in Blockchain Through a Case Study of Insolar]]  
- [[The Generic Blockchain Ecosystem and its Strategic Implications]]
- [[LACChain Framework for Permissioned Public Blockchain Networks – From Blockchain Technology to Blockchain Networks]]

**Papers to read**
- DOI:[10.2139/ssrn.2811995](http://dx.doi.org/10.2139/ssrn.2811995) Disrupting Governance: The New Institutional Economics of Distributed Ledger Technology
- https://tezos.com/whitepaper.pdf
- https://www.ndss-symposium.org/wp-content/uploads/2019/02/ndss2019_02A-2_Zhang_paper.pdf A Treasury System for Cryptocurrencies: Enabling Better Collaborative Intelligence
	- Quadratic voting
- https://ieeexplore.ieee.org/document/8818409 # A Full-Spectrum Blockchain-as-a-Service for Business Collaboration
- [systematic review Related papers](notes/a%20systematic%20literature%20review%20on%20blockchain%20governance.md#Related)
- https://doi.org/10.1177/0170840606067250 # Neither Market nor Hierarchy nor Network: The Emergence of Bazaar Governance

From search
- allintitle:(public) (permissioned) (blockchain OR DLT OR "distributed ledger technology")
-  (https://www.igi-global.com/article/designing-the-architecture-of-a-blockchain-platform/259370)
- New permissioned public blockchain based on master-sub chain architecture (http://www.joca.cn/EN/10.11772/j.issn.1001-9081.2021101790)
-  Permissioned public blockchain with high performance (https://journal.szu.edu.cn/en/oa/darticle.aspx?type=view&id=202003003)
-  https://www.researchgate.net/profile/Suna-Kyun/publication/359728024_Design_and_Validation_of_Tertiary_General_Education_System_based_on_Public_Permissioned_Blockchain_and_Smart_Contract/links/624ba62f5e2f8c7a035bb5a0/Design-and-Validation-of-Tertiary-General-Education-System-based-on-Public-Permissioned-Blockchain-and-Smart-Contract.pdf
- https://policycommons.net/artifacts/2437174/gas-distribution-protocol-for-permissioned-public-ethereum-based-blockchain-networks/3458762/

**Other maybe relevant Papers**
- https://www.multichain.com/download/MultiChain-White-Paper.pdf

## Blockchain Articles
**Read**
- ISO Technical Committees. Blockchain and distributed ledger technologies. ISO TC307 WG5 TS23635 
- https://101blockchains.com/blockchain-governance/
- https://coopahtroopa.mirror.xyz/_EDyn4cs9tDoOxNGZLfKL7JjLo5rGkkEfRa_a-6VEWw
- https://101blockchains.com/permissioned-blockchain/
- http://eyler.freeservers.com/JeffPers/jefpco55.htm?ref=hackernoon.com
- https://en.wikipedia.org/wiki/Cyberocracy
- https://en.wikipedia.org/wiki/Government_by_algorithm
- https://medium.com/@Vlad_Zamfir/against-on-chain-governance-a4ceacd040ca
- https://medium.com/@FEhrsam/blockchain-governance-programming-our-future-c3bfe30f2d74
- https://vitalik.ca/general/2017/12/17/voting.html
- https://bitcoin.org/bitcoin.pdf
- https://medium.com/@WayneVaughan/open-vs-closed-blockchains-let-s-end-this-madness-8313e4095ead
- https://medium.com/good-audience/blockchain-governance-101-eea5201d7992
- https://www.ibm.com/blockchain-supply-chain
- https://www.hyperledger.org/wp-content/uploads/2018/08/HL_Whitepaper_IntroductiontoHyperledger.pdf
- https://www.mobycrypt.com/do-we-need-closed-blockchains/
- https://developer.oracle.com/learn/technical-articles/permissioned-blockchain
- https://medium.com/wavesprotocol/what-closed-blockchain-is-for-190534b5951
- https://www.investopedia.com/news/public-private-permissioned-blockchains-compared/
- https://www.forbes.com/sites/forbestechcouncil/2019/06/11/public-vs-private-permissioned-ledgers-and-blockchain-standards/?sh=39aaa258550b
- https://www.linkedin.com/pulse/public-permissioned-blockchains-common-pool-resources-jesus-ruiz/
- https://smithandcrown.com/glossary/transaction-finality-probabilisticdeterministic/
- https://www.r3.com/blog/how-public-permissioned-blockchains-are-not-an-oxymoron-2/
- https://blog.dshr.org/2022/02/ee380-talk.html
- https://ethereum.org/669c9e2e2027310b6b3cdce6e1c52962/Ethereum_Whitepaper_-_Buterin_2014.pdf
- https://www.investopedia.com/terms/b/blockchainasaservice-baas.asp
- https://nodes.com/#blockchain-nodes-types
- https://medium.com/cryptoapis/utxo-and-account-based-blockchains-d1d3c638524
- https://medium.com/crypto-24-7/bitcoin-is-finished-863e5370150
- https://www.hyperledger.org/blog/2017/09/06/abcs-of-open-governance
- https://www2.deloitte.com/us/en/insights/focus/signals-for-strategists/emergence-of-blockchain-consortia.html

**Docs**
- https://iroha.readthedocs.io/en/develop/maintenance/add_peer.html
- 

**Might Read**
- https://stakingfac.medium.com/what-is-nominated-proof-of-stake-889fc22bef8f
- https://en.wikipedia.org/wiki/Futarchy
- https://pluralistic.net/2022/02/14/externalities/#dshr
- https://www.apc.org/en/pubs/network-infrastructures-commons-model-local-participation-governance-and-sustainability
- https://ec.europa.eu/digital-building-blocks/wikis/display/EBSI/Home
- substrate based blockchains

**Blockchain Projects**
- https://ethereum.org/en/governance/
- https://docs.decred.org/governance/overview/
- https://time.com/6142810/proof-of-humanity/
- https://alastria.io/en/what-is-alastria/
- https://www.lacchain.net
- https://swarm.city
	- https://whitepaper.io/document/140/swarm-whitepaper
- https://internetcomputer.org/what-is-the-ic
- https://polymesh.network/permissioned-blockchain
	- https://polymath.network/polymesh-whitepaper
	- [[polymesh]]
- kosama
- edgeware
- Polkadot
- www.kaleido.io
- holochain
- 

## Other Reading
- https://docs.docker.com/config/containers/container-networking/
- http://nzfoodmanufacturer.co.nz/alibaba-blockchain-technology-drive-food-safety-quality/
- https://collegegrad.com/industries/food-manufacturing