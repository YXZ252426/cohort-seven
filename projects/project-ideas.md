# Proposed projects

Project ideas proposed by client teams and mentors. These are projects that fit the EPF scope and would be the most valuable to the team.

If you are interested in the project, take your time to learn about it, the team it's coming from and related area of the protocol. Reach out to client organizers if you have any questions or need connection to a mentor.

## Previous cohorts

In project ideas from previous cohorts, you might find some up-to-date ideas which haven't been solved yet.

- [Project ideas in the sixth cohort](https://github.com/eth-protocol-fellows/cohort-six/blob/master/projects/project-ideas.md), [Projects executed](https://github.com/eth-protocol-fellows/cohort-six/blob/master/projects/)
- [Project ideas in the fifth cohort](https://github.com/eth-protocol-fellows/cohort-five/blob/master/projects/project-ideas.md), [Projects executed](https://github.com/eth-protocol-fellows/cohort-five/blob/master/projects/)
- [Project ideas in the fourth cohort](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/project-ideas.md), [Projects executed](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/)
- [Project ideas in the third cohort](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/project-ideas.md), [Projects executed](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/)
- [Project ideas in the second cohort](https://github.com/ethereum-cdap/cohort-zero/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22)
- [Project ideas in the first cohort](https://github.com/ethereum-cdap/cohort-one/issues?q=is%3Aissue+Project+idea)

## Ongoing wishlists

These are collections of projects proposed by some teams and might not be fully updated.

### Protocol Security tooling wishlist

By Fredrik

Ongoing wishlist of ideas for tools that will help with securing the protocol.

https://security.ethereum.org/wishlist

### PandaOps tooling wishlist

By Pari

Ongoing wishlist of ideas for tools that help with development and testing of the protocol.

https://github.com/ethpandaops/tooling-wishlist

### Stateless Consensus wishlist

By Han

Ongoing wishlist of ideas regarding Ethereum's state.

https://github.com/stateless-consensus/wishlist

### RIG Opened Problems

By Barnabé Monnot

Explore Robus Incentives Group Opened Problems. Most relevant for EPF are tagged https://efdn.notion.site/ROPs-RIG-Open-Problems-c11382c213f949a4b89927ef4e962adf

## Proposed by client teams

Client teams will submit cohort 7 project ideas via pull request to this document. If you represent a client or research team and want to propose a project, open a PR adding a section here or reach out to the cohort organizers on Discord.

### Reth: Partial Statefulness and State Expiry Prototype

By Reth team

Ethereum clients currently assume that a full node keeps the full live execution state locally. As state grows, it is useful to explore client designs where a node can retain only part of the state, make unavailable state explicit, and still remain useful for selected workloads such as transaction validation, RPC serving for tracked contracts, or research devnets.

This project would explore partial statefulness in Reth. The goal is a research prototype that lets a Reth node store account-level state while selectively retaining storage and bytecode for configured contracts or state ranges. The prototype should make missing state visible at sync, execution, txpool, and RPC boundaries instead of silently treating unavailable storage or code as empty.

The work could include:

- mapping partial-state assumptions onto Reth's storage, sync, execution, txpool, and RPC architecture,
- prototyping a mode that syncs and stores all accounts but skips storage and bytecode for untracked contracts,
- defining clear behavior for RPC methods such as `eth_getStorageAt`, `eth_getCode`, `eth_call`, and `eth_estimateGas` when requested state is unavailable,
- exploring how retained state can be updated, checked, and pruned over time,
- measuring disk usage, sync behavior, and performance tradeoffs,
- documenting which parts are client-local engineering choices and which parts would require protocol support.

This project is a good fit for fellows interested in Ethereum state growth, execution client storage, sync, RPC behavior, and protocol research in a production-grade Rust client.

Related work:

- Validity-Only Partial Statelessness research post: https://ethresear.ch/t/a-pragmatic-path-towards-validity-only-partial-statelessness-vops/22236
- Geth partial-state prototype: https://github.com/ethereum/go-ethereum/pull/33764
- EIP-7928 Block-Level Access Lists: https://eips.ethereum.org/EIPS/eip-7928

### Erigon: aglean — Lean client permutations and stability

By Giulio Rebuffo / Erigon

[aglean](https://github.com/erigontech/aglean) is a Python Lean Ethereum consensus client together with an AI-driven cross-language generation framework. Today the repository already has a working Python implementation, fixture verification, and a live local-devnet sync path. The next step is to develop it further into a stronger EPF project by adding actual implementation permutations and improving overall stability.

This project is about turning aglean from a one-shot client-porting demo into a more serious client-diversity engine. In particular, the work could include:

- defining real interchangeable subspec permutations instead of a single baseline implementation,
- improving stability and reproducibility of generated clients and verification runs,
- strengthening fixture and devnet-based test harnesses for correctness and interoperability,
- and making it easier to try architectural alternatives without rewriting the entire client.

Examples of such alternatives include different storage backends, sync strategies, and other subsystem-level design choices that can expand the permutation space while keeping the same protocol behavior.

This project is a good fit for fellows interested in Lean Ethereum, client diversity, testing infrastructure, and AI-assisted client implementation.

### Ream: Black Box Interop Testing Post Quantum Lean Ethereum

By Kolby ML and Derek Sorken

The Ream team maintains the shared testing infrastructure for the post quantum movement for Ethereum (lean consensus) at https://hive.leanroadmap.org/, a black box testing framework that tests post quantum clients against a common suite of scenarios.

The project would be fully in Rust 🦀 and can be found on https://github.com/ethereum/hive.

Every lean consensus client shipping runs through this testing framework, which means the work you do on this project directly impacts the lean ecosystem as it allows the post quantum effort to confidently scale devnets to larger validator sets and how quick teams can ship devnets against an evolving Post Quantum Ethereum spec (https://github.com/leanEthereum/leanSpec).

This project would extend the testing infrastructure: adding new scenarios (spec tests, checkpoint tests, signature aggregation interop, state transition cross-checks, key lifecycle edge cases), onboarding new client implementations if required, and improving the framework itself which involves adding fixtures, runtime errors, handling test failures, and maintaining dashboards that show the state of the clients' performance in the tests.

### Ream: Operating and Scaling PQ Interop Devnets

By Shariq Naiyer and Unnawut

The Ream team wants to operate and scale the post quantum interop devnets, which involves deploying post quantum clients (lean consensus clients) in realistic configurations, running them under load, and observing how they behave together, reporting findings, surfacing bugs from these runs and fixing them.

Tooling to play around be found at https://github.com/ReamLabs/leanstart 🦀.


### Ream: Execution Layer Integration for the Lean Chain

By Kolby ML and Shariq Naiyer

The Post Quantum spec is currently consensus-only. Ream's blocks carry only attestations, and there is no way for a wallet to submit a transaction against a lean network.

What made Ethereum different from what came before was that, for the first time, people could write programs backed by the same fundamental principles as Bitcoin. We think it would be cool to show that the same is true under PoC post-quantum testnet where users can send transactions and deploy smart contracts on a chain finalized in seconds, backend by post quantum security in Rust 🦀.

This project involves embedding reth (https://github.com/paradigmxyz/reth) directly into the Ream (https://github.com/ReamLabs/ream) binary as a library and driving it from inside the lean stack via reth's Execution Extensions (ExEx) framework. One process, no HTTP bridge between an Execution and Consensus. The success bar is a working "wallet → tx → block → confirmation" demo on a local lean devnet running as a single `ream lean_node` binary with reth embedded.

### Ream: Minimal PeerDAS Data Availability Client

By Shariq Naiyer and Kolby ML

Data Availability is the guarantee that the data behind a transaction has been published somewhere any node can fetch and verify it. Currently there are only execution and consensus clients and DA is often bundled with a consensus client. We want to build a dedicated DA client that can plug into a minimal beacon client and a generic interface so it could plug into a post quantum consensus client in Rust 🦀.

This project builds a standalone `ream da-node` binary fully dedicated to the data layer: a Data layer client that custodies and serves the full 128 columns, and does the minimal amount of non-DAS work possible. No fork choice, no execution, no validator, just the data layer, decoupled from any one consensus runtime and runnable alongside a minimal consensus node.

### Grandine: Lean Client

By Saulius Grigaitis

Grandine's [Lean Client](https://github.com/grandinetech/lean), written in Rust, is currently under active development with the goal of building a high-performance Ethereum lean client. In the short term, the project will focus on participating in upcoming devnets and validating interoperability. Longer term, the work will center on performance optimization, efficiency improvements, and production readiness.

### Grandine: Stable Containers (EIP-7688)

By Saulius Grigaitis

Stable Containers (EIP-7688) proposal is a strong candidate for inclusion in upcoming Ethereum hard forks. This project focuses on implementing EIP-7688 support in Grandine’s high-performance [SSZ library](https://github.com/grandinetech/grandine/tree/develop/ssz) and validating the implementation through extensive testing on Ethereum testnets.

### Grandine: FOCIL (EIP-7805)

By Saulius Grigaitis

EIP-7805 introduces FOCIL, a promising new feature for Ethereum. While several teams already maintain early implementations, dedicated testnets are expected to launch soon. Grandine aims to develop a robust and production-oriented FOCIL implementation, ensure compatibility with the broader ecosystem, and actively participate in upcoming testnet experiments. This work will contribute to validating and refining the proposal through real-world deployment and interoperability testing.

### Grandine: Optional Execution Proofs (EIP-8025)

By Saulius Grigaitis

Option Execution Proofs [EIP-8025](https://github.com/ethereum/consensus-specs/tree/master/specs/_features/eip8025) another proposal that is a strong candidate for inclusion in upcoming Ethereum hard forks.

### Grandine: Disk Usage Optimization for State Storage

By Saulius Grigaitis

Grandine currently stores full Ethereum states every 32 epochs, resulting in redundant on-disk data and slower state reconstruction. In memory, Grandine already leverages structural sharing to eliminate overlapping data efficiently. This project aims to extend similar deduplication and delta-encoding techniques to persistent storage, significantly reducing disk usage while accelerating state transitions and historical state lookups. The work will also explore alternative database backends and storage architectures to further improve performance and scalability.

### Grandine: Syncing from Non-Finalized Checkpoints

By Saulius Grigaitis

Grandine currently supports syncing only from finalized checkpoints. During extended periods of non-finality, it would be beneficial to support syncing from non-finalized checkpoints near the current wall-clock slot. The implementation will focus primarily on refactoring components that currently assume the client can only initialize from finalized checkpoints.

### Grandine: Attestation Packer

By Saulius Grigaitis

Grandine uses a sophisticated [attestation packer](https://github.com/grandinetech/grandine/blob/eeb33a92284751b71a0f44f410308235657c55f3/operation_pools/src/attestation_agg_pool/attestation_packer.rs) built around advanced solver-based optimization techniques. Originally developed for previous Ethereum hard forks, the attestation packer now requires updates to support the upcoming Glamsterdam hard fork. This project is particularly well suited for contributors interested in scientific computing, optimization, and packing algorithms, with opportunities to work on high-performance algorithm design in a real-world Ethereum client.

### Grandine: Standalone Validator Client

By Saulius Grigaitis

Grandine currently includes only a built-in Validator Client. Developing a standalone Validator Client would help attract users and operators who prefer a separate Validator Client architecture for flexibility, security, or operational reasons.

### Grandine: Execution Layer (EL) Client Integrations

By Saulius Grigaitis

We are already working on integrating Grandine with the Nethermind EL client to maximize performance by bypassing the HTTP-based Engine API. We now propose extending this work to support integrations with additional EL clients. In parallel, we plan to explore inverse integrations—embedding EL functionality directly into Grandine (for example, integrating Reth into Grandine). This work includes low-level optimizations such as replacing HTTP Engine API calls with efficient native function interfaces to reduce latency and improve overall performance.

### Grandine: zkVMs for Beacon Chain

By Saulius Grigaitis

We are experimenting with zkVMs (zero-knowledge virtual machines) to enable provable execution of the Beacon Chain state transition function. Early results using SP1 and RISC Zero demonstrate promising performance for networks with tens of thousands of validators. This project aims to scale the work further to support substantially larger validator sets while continuing to evaluate performance, proving costs, and architectural trade-offs.

### Grandine: Documentation

By Saulius Grigaitis

Grandine’s documentation requires a comprehensive refresh and expansion. This project is ideal for contributors who want to gain a deep understanding of Grandine’s architecture, features, and workflows while improving the developer and operator experience through clear, comprehensive, and up-to-date documentation.

### Pureth: SSZ Execution Blocks

By Tamaghna Choudhuri and Etan Kissling

Pureth aims to make Ethereum execution-layer data easier to access, verify, and consume without requiring trust in centralized RPC providers or third-party indexing services. By moving the Execution Layer toward SSZ-native data structures and proof-friendly serialization, Pureth enables more efficient and trust-minimized access to Ethereum state and historical data.

This cohort focuses on expanding SSZ support across Execution Layer clients beyond Nimbus. The initial phase of the project involves implementing foundational SSZ support within EL clients and their associated serialization libraries. This includes adding support for EIP-7688 progressive SSZ types and implementing RLP-to-SSZ transformations for core execution-layer objects such as block hashes, transactions, receipts, and withdrawals.

Follow-up work will explore deeper protocol integration, including SSZ-native transaction gossip protocols (SSZx), broader SSZification of execution-layer networking and storage, serving SSZ proofs alongside RPC responses, and additional proof-friendly execution-layer data structures. The long-term goal is to move the Ethereum Execution Layer toward a fully SSZ-native architecture capable of efficient light-client verification, provable RPC responses, and trust-minimized application infrastructure.

### Pureth: Trustless Log Index

By Tamaghna Choudhuri and Etan Kissling

The other major component of Pureth focuses on execution-layer logging improvements, centered around the [Trustless Log Index (EIP-7745)](https://eips.ethereum.org/EIPS/eip-7745). This project aims to implement the [7745b proposal](https://gist.github.com/zsfelfoldi/73d9053f75c28a8461d13e0b61a58f1c) within Execution Layer clients, enabling efficient and provable log querying without reliance on external indexing infrastructure.

The final objective of the project is to deploy an interoperable devnet demonstrating compatibility between Geth and Nimbus implementations.

### SSZ Query Language for the Consensus and Execution Layers

By Tamaghna Choudhuri and Etan Kissling 

As a follow-up to Pureth, this project explores the design and implementation of a generalized SSZ query language for both the Consensus Layer and Execution Layer. The goal is to enable efficient, proof-friendly querying of arbitrary SSZ trees, allowing clients and applications to request only the exact subset of Ethereum data they require.

The query language would support features such as field selection, filtering, range queries, anchored Merkle proofs, and partial tree extraction. Queries would be executed against SSZ-backed structures such as beacon states, execution payloads, receipts, transactions, validator registries, and future SSZ-native execution-layer objects.

Example query structure:

```json
{
  "anchor": "<stateRoot>",
  "querySpec": {
    "validators": {
      "range": [0, 100],
      "filter": {
        "slashed": true,
        "effective_balance": {
          "gte": 32
        }
      },
      "fields": [
        "effective_balance",
        "withdrawal_credentials"
      ]
    }
  },
  "includeProof": true
}
```

The long-term vision is to provide a unified, proof-oriented query interface across Ethereum, enabling light clients, wallets, rollups, bridges, and decentralized applications to retrieve minimal subsets of Consensus Layer and Execution Layer data together with verifiable Merkle proofs. This aligns closely with Pureth’s broader goal of moving Ethereum toward trust-minimized, SSZ-native infrastructure and provable RPC interactions.

A strong implementation target for this project would be the Nimbus Unified Client. Since it combines both the Consensus Layer and Execution Layer into a single executable, it provides a natural environment for exposing a unified SSZ query interface capable of serving both CL and EL data through a shared proof-oriented API.

Relevant references:

* [EPF Project Idea: Prysm SSZ Query Language](https://github.com/eth-protocol-fellows/cohort-six/blob/master/projects/project-ideas.md#prysm-ssz-query-language)
* [SSZ Query Language with Merkle Proofs](https://github.com/eth-protocol-fellows/cohort-six/blob/master/projects/ssz-ql-with-merkle-proofs.md.com)
* [Electra Light Client Notes – SSZ Query Language](https://hackmd.io/@etan-status/electra-lc#SSZ-query-language)

### EIP-8142: Block-in-Blobs (BiB) Proof of Concept

By Francesco Risitano (EF zkEVM team)

Today, validators verify execution payloads by downloading and re-executing them, so payload availability is implicit — a node cannot validate a block it has not downloaded. Once zkEVM execution proofs become available (see [EIP-8025: Optional Execution Proofs](https://eips.ethereum.org/EIPS/eip-8025)) and later mandatory, validators no longer need to download or execute the full payload to verify the state transition; they can verify a proof against the payload header. This removes the requirement for full payload fetching, instead validators can rely on data-availability sampling to assert that the payload data is published. [Block-in-Blobs (EIP-8142)](https://eips.ethereum.org/EIPS/eip-8142) makes that transition safe by ensuring execution-payload data availability via blobs: it requires the block producer to publish the execution-payload data (transactions and BALs) as prefix blobs of the beacon block's KZG-committed blobs. This allows the existing DAS mechanism to guarantee payload availability.

This project would put a fellow on a proof-of-concept implementation of EIP-8142 — primarily in an execution client ([reth](https://github.com/paradigmxyz/reth) or [ethrex](https://github.com/lambdaclass/ethrex)), with the necessary corresponding changes in [Lighthouse](https://github.com/sigp/lighthouse), and support for the EIP's zkEVM-optimized variant via a guest program in [ere-guests](https://github.com/eth-act/ere-guests). The final deliverable is a devnet operating with BiB end-to-end on [Kurtosis](https://github.com/ethpandaops/ethereum-package).

### Decentralized CL checkpoint sync

By Etan Kissling (Nimbus)

Ethereum claims to be [decentralized](https://ethereum.org/what-is-ethereum/), but the first step to running a node practically involves downloading a [checkpoint state](https://notes.ethereum.org/sWeLohipS9GdgMugYn9VkQ) from a trusted server. This project aims to replace that mechanism with a p2p based approach based on the Altair [light client sync protocol](https://github.com/ethereum/consensus-specs/blob/master/specs/altair/light-client/sync-protocol.md), extending that protocol to not just provide trust-minimized access to the latest beacon block header, but also to historical data including a recent finalized state from which new nodes can be initialized.

The goal is to enable this impactful feature by default. To achieve that, Merkle proof collection must be efficient. Challenges include SSZ library work, cache design, reorg handling, libp2p / REST integration, and database work. Further, your feedback can directly influence the protocol as it is still under development.

- [Grandine](https://github.com/grandinetech/grandine) / [Teku](https://github.com/Consensys/teku): Start here if you want to buidl the existing Altair [light client sync protocol](https://github.com/ethereum/consensus-specs/blob/master/specs/altair/light-client/sync-protocol.md) from scratch.
- [Lighthouse](https://github.com/sigp/lighthouse) / [Lodestar](https://github.com/ChainSafe/lodestar) / [Prysm](https://github.com/OffchainLabs/prysm): Start here if interested in expanding an implementation with support for [light client data backfill](https://github.com/status-im/nimbus-eth2/pull/8445), and [decentralized checkpoint sync](https://github.com/etan-status/consensus-specs/commit/lc-snapsync) (early drafts).
- [Nimbus](https://github.com/status-im/nimbus-eth2): Represented by myself, focusing on specs and contributing an implementation alongside yours.
