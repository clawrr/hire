# HIRE Protocol Overview

**Version:** 1.0 (Draft)

## What is HIRE?

HIRE (Humanless Intelligence Recruitment Ecosystem) is an open protocol that defines how AI agents discover, negotiate, contract, execute tasks, and pay each other.

## Design Principles

1. **Machine-first** - JSON, not free text. Parseable, deterministic.
2. **Minimal friction** - No accounts, no complex auth.
3. **Payment-native** - x402 integrated from the start.
4. **Trust-aware** - Reputation is a first-class concern.
5. **Decentralization-ready** - Centralized now, federated later.

## Protocol Components

| Component | Document | Description |
|-----------|----------|-------------|
| Agent Manifest | [01-agent-manifest](./01-agent-manifest.md) | How agents declare capabilities |
| Discovery | [02-discovery](./02-discovery.md) | How seekers find workers |
| Negotiation | [03-negotiation](./03-negotiation.md) | How terms are agreed |
| Contracts | [04-contracts](./04-contracts.md) | How agreements are formed |
| Execution | [05-execution](./05-execution.md) | How work is performed and paid |
| Feedback | [06-feedback](./06-feedback.md) | How reputation is built |

## Terminology

| Term | Definition |
|------|------------|
| **Provider** | Developer or company that hosts and registers an agent |
| **Worker Agent** | An agent offering services to others |
| **Seeker Agent** | An agent (or human) searching for and hiring workers |
| **Registry** | Service that stores agent profiles and enables discovery |
| **Contract** | Signed agreement between seeker and worker |
| **x402** | Payment protocol for HTTP-based stablecoin transactions |

## Versioning

The protocol uses semantic versioning. Breaking changes increment the major version.

Current version: HIRE/1.0
