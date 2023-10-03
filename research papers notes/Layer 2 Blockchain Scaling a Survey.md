
# Summary and Notes: **Layer 2 Blockchain Scaling: a Survey**


# **1 Page Summary:**


## **Message**

The paper examines current L2 blockchain solutions addressing scalability challenges and their effect on performance.


## **Highlights**

The first section of the paper introduces blockchain technology, discusses the scalability issue, and presents Layer 2 as a solution.

Second section of the paper discusses 3 different solutions:



* Lightning Network
* Plasma
* Rollups

It also discusses the impact of these solutions on 5 different aspects of blockchain technology and layer 2.



1. Scalability
2. Decentralization
3. Security
4. Privacy
5. Fee & Micro-payments


## **Result**

None surpass the others, and each has unique implications. Their use varies based on the situation, but all enhance scalability.


## Authors:

Cosimo Sguanci, Roberto Spatafora and Andrea Mario Vergani


# Section 1:


## Overview and Blockchain Intro

Blockchain technology consists of a decentralized public ledger capable of keeping a record of immutable (and linked) information.

Though, the actual goal as discussed in the original Bitcoin whitepaper is to provide a trustless electronic payment system that does not rely on any third party. Thus, the trust that is needed in traditional transactional systems is replaced by cryptography.

Implementation Logic:



* Design Peer-to-peer network of nodes.
* Bundle a certain number of tx into blocks.
* Blocks are hashed to generate timestamps.
* Each block contains the hash of the previous block.
* This mechanism generates a chain of timestamped information represented by transactions.
* These blocks are then propagated across nodes.
* Nodes then store each block.
* This way, each node acts as a validator of the block.

For the payments using p2p:



* Transactions should not be reversible.
* This is done by proof of work.
* In PoW, nodes interested in generating new blocks search for values that have certain properties when they’re hashed using some hashing algo.
* Miners are incentivized by collecting fees that are spent by users to execute transactions.
* Only the longest chain is considered as the valid state.
* Changing the block after it is generated would require redoing the PoW for the specific and all subsequent blocks.
* As long as honest nodes hold the majority of network computational power, the system is considered secure.


## Blockchain scalability issue

Scalability is considered one of the bottlenecks of blockchain infrastructure.


<table>
  <tr>
   <td>Data
   </td>
   <td>Visa
   </td>
   <td>Bitcoin
   </td>
   <td>Ethereum
   </td>
  </tr>
  <tr>
   <td>TPS(tx per sec)
   </td>
   <td>1736 (can go upto 47000)
   </td>
   <td>4.6
   </td>
   <td>14.3
   </td>
  </tr>
  <tr>
   <td>Block Generation Time OR processing time
   </td>
   <td>5-15 sec
   </td>
   <td>10 minutes
   </td>
   <td>12-15 seconds
   </td>
  </tr>
  <tr>
   <td>Block size
   </td>
   <td>-
   </td>
   <td>1MB
   </td>
   <td>1.5M Gas upto 3M (2x) depending on network demand
   </td>
  </tr>
  <tr>
   <td>Tx Size
   </td>
   <td>-
   </td>
   <td>380 bytes
   </td>
   <td>Max about 780KB
   </td>
  </tr>
</table>



## Layer 2 Solutions

Primary issues with Scalability (Scalability trilemma), improvements in scalability can be inversely proportional to:



* Security
* Decentralization
* Both

L2 Solution is usually built on top of existing blockchain. Core concept, irrespective of the framework used, is the same; host transactions and report summary to the main chain.


### Different L2 Solutions:



* Channels: \
  Create direct or indirect off-chain communication channels between nodes; transactions between “connected” nodes are managed on Layer 2, reporting on the main chain only two of them (the one “opening” the channel and the one which “closes” it).
* Sidechains: \
  Children chains anchored to a parent chain that run in parallel to the parent chain.
* Rollups: \
  Execute transaction off chain and report data about it on-chain. These provide a smaller amount of data for every state changed off-chain.


### Overview

These solutions result in higher tx speed, lower fees due to higher tx speeds and no need of modification on the main chain.


#### Sharding:



* Partitioning of the main chain into subsets of nodes.
* Each node is responsible for a portion of the whole network.
* Each node only processes information about its shard.
* Dividing the load of the chain among different partitions without actually dividing the main chain results in higher tx speed.
* Not an actual L2 solution since nothing happens off-chain.
* Shards can share information between them.


# Section 2


<table>
  <tr>
   <td>
   </td>
   <td>Lightning Network
   </td>
   <td>Plasma
   </td>
   <td>Rollups
   </td>
  </tr>
  <tr>
   <td>Scalability
   </td>
   <td>
<ul>

<li>Increased scalability with theoretically reaching upto 10,000 TPS.

<li>Delays due to certain circumstances are possible.
</li>
</ul>
   </td>
   <td>
<ul>

<li>Can go upto 7,200 TPS.

<li>Current throughput upto 175 TPS.

<li>Results possible due to using multiple consensus mechanisms.

<li>Higher block gas limit and shorter block time.
</li>
</ul>
   </td>
   <td>
<ul>

<li>Can go upto 4,500 TPS (for <strong>ZK</strong>) and 800 TPS (for <strong>Optimistic</strong>)

<li>All optimal conditions are difficult.

<li>Can reach about 30% of throughput.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Security
   </td>
   <td>
<ul>

<li>Uses <strong>hash-lock</strong> and <strong>time-lock </strong>for security.

<li> Attackers can lose all funds.
</li>
</ul>
   </td>
   <td>
<ul>

<li><strong>Merkle root commitments </strong>to L1 chain that prevents malicious behavior.

<li>Open issues related to block-withholding and mass-exit.
</li>
</ul>
   </td>
   <td>
<ul>

<li>ZK focuses on <strong>validity proof </strong>using SNARK.

<li>Optimistic rollups are based on <strong>fraud proofs</strong>. 
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Decentralization
   </td>
   <td>
<ul>

<li>Theoretically decentralized.

<li>Real structures may have active channels between users and hubs connected to nodes.
</li>
</ul>
   </td>
   <td>
<ul>

<li>Less decentralized than L1.
</li>
</ul>
   </td>
   <td>
<ul>

<li>High decentralization but still managed by a limited number of contracts thereby increasing centralization.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Privacy
   </td>
   <td>
<ul>

<li>Highly confidential

<li>Confidentiality increases as the path between intermediaries.
</li>
</ul>
   </td>
   <td>
<ul>

<li>Privacy depends on the child chain.
</li>
</ul>
   </td>
   <td>
<ul>

<li>Less private since summary of all tx is published on main chain.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Fees & Micropayments
   </td>
   <td>
<ul>

<li>No fee for direct channel transactions.

<li>Intermediate nodes may ask for an incentive.
</li>
</ul>
   </td>
   <td>
<ul>

<li>Much cheaper than L1.

<li>Still needed to discourage spam attacks.

<li>L1 fees are still needed for deposits and withdrawals.
</li>
</ul>
   </td>
   <td>
<ul>

<li>ZK: Negligible off-chain fees that are typically lower for transfers and slightly higher for withdrawals. 

<li>On-Chain fee is still required for deposits.

<li>Optimistic: Higher fee compared to ZK but lower compared to L1.
</li>
</ul>
   </td>
  </tr>
</table>


This article is part 1 of a 2 part article. Second part will go in more depth of Section 2.