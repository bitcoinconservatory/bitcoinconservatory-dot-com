---
title: "The Puritans of the Protocol"
collection: lessons
categories:
  - history
tags:
  - ordinals
  - relay-policy
  - bip110
  - soft-fork
  - hard-fork
  - replay-attack
---

*A BTC Conservatory Special Report*

There is a story Bitcoin likes to tell about itself: that it is pure engineering, immune to ideology, governed only by code and consensus. It's a comforting story. It is also, as the last three years have shown, incomplete. Beneath the surface of "rough consensus and running code" a very old human pattern reasserted itself - a movement that started as a technical disagreement and hardened, block by block, into something closer to a religious schism. What follows is the story of how that happened, told through the timeline of arbitrary data, relay policy, a soft fork, and finally a hard fork - and why the puritanical instinct at the center of it was never really about protecting Bitcoin at all.

## 2023: Arbitrary data as the Original Sin

Every schism needs an original sin, and Bitcoin's was arbitrary data. In 2023, developers discovered that a "superstructure" could be layered on top of ordinary Bitcoin transactions - a scheme for numbering and tracking individual satoshis, turning the world's hardest money into a substrate for digital collectibles. The Ordinals meta-protocol runs on imagination atop the Timechain, and the spam therein comes and goes in phases.

To one camp, this was simply the network doing exactly what it was built to do: a user paid a fee, a miner included the transaction, the protocol didn't care what the data meant. As our interviewee put it, "if you paid a fee, it is the software working as expected." More importantly, there was no clean, principled way to *stop* this kind of transaction without appointing a gatekeeper - some authority, however informal, that got to decide which transactions were legitimate Bitcoin use and which were not.

To the other camp, Ordinals wasn't a feature discovery. It was a bug exploit - "cheating the code," in their words, "tricking the code" into running basically an invalid operation. And that framing is the hinge on which everything else turns. Once you convince yourself that a fully valid, fee-paying transaction is actually invalid - that the software has a bug rather than a use case you personally dislike - you've given yourself permission to fix it. By fork, if necessary.

Bitcoin Core, to its credit, declined to build a new software-based gatekeeper into the base protocol. It did not "two-horn" the problem, forcing a binary choice between banning a use case outright or blessing it. That restraint could have been the end of the story. It wasn't.

## Enter the Filtering Movement: Relay Policy as an Ineffective Weapon

After Core declined to 'fix' the perceived problem, the puritan faction moved to try to influence *relay policy* - the rules individual nodes use to decide which transactions they'll forward across the network before they're ever mined. This is the crucial technical distinction the movement exploited and, frankly, the one most casual observers miss: **policy is not consensus.** A node operator can refuse to relay a transaction type they dislike, but that refusal has zero binding force on the rest of the network. Miners who want the fee can still include it. Other nodes who want to contribute to the network can still relay it.

This is where the alternative puritanical node software called 'Knots' became more popular with claims to filter and discourage transaction types its authors found distasteful. Framed publicly as a matter of taste, of protecting node operators from "spam," the project was in practice a coordination point for a social and cultural movement that wanted the *appearance* of technical legitimacy for what was, underneath, a moral campaign against how other people were choosing to use their own money on their shared chain.

Filtering at the relay layer is, by itself, mostly theater - an inconvenience miners can route around. But theater has a purpose: it builds a movement, normalizes the idea that certain transactions are illegitimate, and lays the psychological groundwork for the next, more consequential step. That step arrived in the form of BIP110, a proposed change to consensus rules itself - an attempt to take what had only ever been a voluntary, unenforceable relay preference and hard-code it into what the network would accept as valid at all. A downgrade in law to Bitcoin's functionality, wrapped in the language of an 'update'.

## The Soft Fork That Wasn't Soft Enough

A soft fork narrows the rules - it makes previously valid blocks invalid under the new rules, while old nodes still accept new blocks. It's the traditional, conservative way to change Bitcoin, and it requires overwhelming consensus precisely because it imposes a new restriction on everyone, including people who never agreed to it.

The attempted soft fork built on the BIP110 filtering logic tried to take the informal, software-settings, policy-level gatekeeping and enshrine it as a rule of the network itself. It failed to gather the kind of broad, cross-constituency support that legitimate soft forks require - because, at bottom, it wasn't solving a security problem or a scaling problem. It was solving a *taste* problem, and taste doesn't command consensus. Miners had no incentive to adopt it. Users who valued permissionless use of the base layer - for any purpose, popular or not - saw it correctly as the puritanical gatekeeper now arriving through the back door, after Core wouldn't answer through the front. 

## The Hard Fork: When Consensus Fails, Some Choose Exit

When a faction cannot win consensus, it has two honest choices: accept the outcome, or leave. The puritan movement chose to leave - but leaving Bitcoin's consensus rules while keeping Bitcoin's name, history, and existing UTXO set is exactly what a hard fork is. Every wallet that held a balance on the original chain woke up holding an identical balance on the new, forked chain - the same inventory of sats, mirrored, the moment the chains split. Two ledgers, one shared past, and from that block forward, two divergent futures.

This is the part of the story that deserves the most scrutiny, because it is the part most often laundered as "just another implementation." It was not neutral. It was the culmination of a filtering ideology that began as a complaint about arbitrary data, escalated through unenforceable relay policy, tried and failed to become a soft fork, and - when Bitcoin's actual governance process (rough consensus among users, node operators, and miners) refused to ratify it - split off entirely rather than accept the network's answer. Today, we are in a Tower of Babylon where even supporters of the fork live in confusion about which one to call 'BTC'. When seen with clarity of hindsight, that was an attack on Bitcoin, dressed in the language of protecting it.

## Where Things Stand Now

Bitcoin's main chain continued exactly as designed: permissionless, fee-market-governed, indifferent to whether a given transaction encodes a payment, arbitrary data, or anything else a user is willing to pay to include: they are all transactions that must pay a fee to use the block space. The forked chain persists as a separate network, with its own miners, its own difficulty, and, tellingly, its own struggles: mining on the forked chain has been erratic  and a demo that walking away from accumulated hashpower and security has costs that ideology doesn't pay for you.


## Protecting Yourself From a Fork while Shitcoining - Avoiding Replay Attacks

Because forks share a common transaction history up to the split, any UTXO you held before the split exists, identically, on both chains. That sounds convenient - until you realize a transaction broadcast on one chain can often be **replayed** on the other, moving coins you didn't intend to move on a chain you never meant to transact on. If you ever find yourself holding balances across a contentious fork, here are some known ways to keep your transactions from crossing over:

1. **Use locktime as a timing barrier.** Set a locktime on your transaction so the UTXO cannot be spent before a specific future block or time - one that hasn't yet been reached on the "real" chain you intend to use, but that the forked chain (with its own erratic, out-of-sync block production) has already passed. A transaction that's only valid going forward in time on your target chain simply can't be dragged backward and replayed against it. 

2. **De-purify the transaction with an oversized OP_RETURN.** When doing a self-send to split your coins safely, attach an OP_RETURN output that's deliberately too large to be valid under the forked chain's rules. That makes the transaction invalid and unspendable on Purity-chain while remaining valid on your intended chain, safely sent to a new address of your own as a safe harbor. Once you've done this, you can reopen a wallet like Sparrow, connect it to the other chain using their forked mempool server, and confirm the same UTXO still shows as unspent there, meaning your coins are ready to separated and spend to the shitcoin casino. Or you can do a self-send and hodl, just in case it takes off. 

Neither technique requires special software - just deliberate use of the tools already built into Bitcoin's transaction format, visible in Sparrow or EntropyLab. 

In a landscape where forks driven by ideology rather than necessity may recur, the nature of basic self-custody and these kinds of advanced UTXO tricks can be worth knowing before you need them, if for nothing else but to know what is possible when playing with your Bitcoins. 
