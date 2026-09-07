---
title: "Verba Volant, Scripta Manent"
collection: lessons
categories:
  - philosophy
tags:
  - permanence
  - timechain
  - proof-of-work
  - inscriptions
  - cultural-memory
---

The Romans had two categories: *verba* and *scripta*. Spoken words fly; written words stay. It was already a lie in Rome — scrolls burned at Alexandria, ink faded, empires that wrote their laws in stone still lost them to sand. "Written" never meant permanent. It meant *harder to erase than air*, nothing more.

Bitcoin adds a third category the Romans had no word for: **committed**.

## Three tiers of durability

**Spoken.** A word exists only while a sound wave propagates and a listener's memory holds it. No copy, no substrate. Gone at the speed of forgetting.

**Written.** A word is fixed to a substrate — clay, papyrus, paper, disk. It persists only as long as the substrate does, and only as long as someone chooses to keep it. Every written archive is a bet on an institution: a library, a state, a company's servers. Institutions burn, get bought, get subpoenaed, get bored. Scripta manent, usually — until they don't.

**Committed.** A Bitcoin transaction containing data — via `OP_RETURN`, a witness commitment, an inscription — gets hashed into a Merkle root, that root gets hashed into a block header, the header is proven-of-work at a specific difficulty, and every subsequent block extends a chain whose cumulative work makes rewriting history more expensive than the original electricity spent creating it. The data doesn't persist because someone *decided* to keep it. It persists because tens of thousands of independent nodes would have to conspire to agree it doesn't exist, and even then, the astronomical proof-of-work already spent stands as evidence that it once did.

This is permanence without a permanent institution. No library, no government, no company required to keep the promise. Just math, electricity already spent, and anyone willing to keep a copy of the chain.

## The Merkle root as a written word that cannot be rewritten quietly

When Satoshi mined block 9 in January 2009, that block's hash committed to everything in it — and every block since has extended that fact. To alter one byte of block 9's contents today, you'd need to redo the proof-of-work for block 9 *and every block after it*, faster than the rest of the network extends the real chain. Durability here comes with a cost function attached: rewriting the past costs more than writing the future.

Contrast this with the burning of the Library of Alexandria. No cost function stood between the fire and the scrolls. The written word's permanence was always contingent on nobody with enough power deciding otherwise. Bitcoin's committed word breaks that contingency, imperfectly and not forever, but for the first time the cost of erasure is computable and public instead of just hoped for.

## What gets inscribed is not automatically what matters

A warning belongs here, or this becomes propaganda instead of a lesson: durability is not the same as significance. An inscription of a JPEG and an inscription of a peace treaty cost the same per byte. Bitcoin does not curate; it only refuses to forget once told to remember. This is the same problem every durable medium has always had — stone tablets recorded both legal codes and grocery lists — except now the selection of what's worth the fee happens at the moment of commitment, not centuries later when an archivist decides what survives the next fire.

Cultural memory has always worked by triage: most speech dies immediately (correctly — most speech doesn't deserve permanence), most writing is later discarded, and a tiny residue outlives its author. Bitcoin doesn't change this triage. It changes what the *final*, uncurated layer of the triage costs to defeat.

## The adage, revised

*Verba volant.* Speech still flies; that has not changed and should not change — ephemerality is a feature of most human speech, not a bug.

*Scripta manent* — mostly, contingently, at the mercy of whoever holds the archive.

And now: *quod inscribitur, manet certius* — what is inscribed remains more certainly. Ink was never stronger than voice. What changed is that the cost of forgetting on purpose finally became a number anyone can check — for OP_RETURN and witness data and ordinal-style inscriptions today, and for whatever CTV, BIP 448, or the next fork lets us commit tomorrow.
