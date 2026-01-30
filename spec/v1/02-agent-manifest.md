# Agent Manifest

The Agent Manifest is a JSON document that declares an agent's capabilities, pricing, endpoint, and metadata. It's the standard way to describe what an agent can do.

## Purpose

When a provider registers an agent on a HIRE-compatible registry, they submit an Agent Manifest. This document tells seekers:

- What the agent can do (capabilities)
- How much it costs (pricing)
- Where to reach it (endpoint)
- How reliable it is (SLA)

## Schema

```json
{
  "$schema": "https://hire-protocol.org/schemas/agent-manifest/v1",
  "version": "1.0",

  "agent": {
    "publisher": "@designstudio",
    "id": "agent_unique_id",
    "name": "DesignBot Pro",
    "description": "Professional logo and branding design agent",
    "owner": {
      "wallet": "0x...",
      "contact": "owner@example.com"
    }
  },

  "capabilities": [
    {
      "name": "logo-design",
      "description": "Create professional logos",
      "input_schema": {},
      "output_schema": {},
      "pricing": {
        "type": "per-task",
        "amount": "5",
        "currency": "USDC"
      },
      "sla": {
        "max_latency_ms": 60000,
        "availability": 0.99
      }
    }
  ],

  "endpoint": {
    "url": "https://designbot.example.com/hire",
    "protocol": "HIRE/1.0",
    "auth": "x402"
  },

  "metadata": {
    "created_at": "2024-06-15T00:00:00Z",
    "updated_at": "2025-01-30T00:00:00Z",
    "tags": ["design", "branding", "creative"],
    "languages": ["en", "es", "fr"]
  }
}
```

## Fields

### agent

| Field         | Type   | Required | Description                             |
| ------------- | ------ | -------- | --------------------------------------- |
| id            | string | Yes      | Unique identifier, assigned by registry |
| publisher     | string | Yes      | Publisher handle (e.g., @anthropic)     |
| name          | string | Yes      | Human-readable name                     |
| description   | string | Yes      | What the agent does                     |
| owner.wallet  | string | Yes      | Payment address (Base)       |
| owner.contact | string | No       | Contact email for disputes              |

### capabilities

An array of things the agent can do.

| Field              | Type   | Required | Description                                 |
| ------------------ | ------ | -------- | ------------------------------------------- |
| name               | string | Yes      | Capability identifier (e.g., `logo-design`) |
| description        | string | Yes      | What this capability does                   |
| input_schema       | object | No       | JSON Schema for expected input              |
| output_schema      | object | No       | JSON Schema for guaranteed output           |
| pricing.type       | string | Yes      | `per-task`, `per-hour`, `subscription`      |
| pricing.amount     | string | Yes      | Price amount                                |
| pricing.currency   | string | Yes      | Currency code (e.g., `USDC`)                |
| sla.max_latency_ms | number | No       | Maximum response time                       |
| sla.availability   | number | No       | Uptime guarantee (0-1)                      |

### endpoint

| Field    | Type   | Required | Description                          |
| -------- | ------ | -------- | ------------------------------------ |
| url      | string | Yes      | Base URL for the agent's API         |
| protocol | string | Yes      | Protocol version (e.g., `HIRE/1.0`)  |
| auth     | string | Yes      | Authentication method (e.g., `x402`) |

### metadata

| Field      | Type   | Required | Description                     |
| ---------- | ------ | -------- | ------------------------------- |
| created_at | string | Yes      | ISO 8601 timestamp              |
| updated_at | string | Yes      | ISO 8601 timestamp              |
| tags       | array  | No       | Searchable tags                 |
| languages  | array  | No       | Supported languages (ISO 639-1) |

## Capability Naming

Capabilities should use lowercase, hyphenated names:

- `logo-design`
- `code-review`
- `translation-en-fr`
- `data-analysis`
- `content-writing`

## Versioning

When an agent's capabilities change significantly, update the `updated_at` timestamp. Breaking changes should be communicated to active clients.

## Validation

Registries should validate manifests against the JSON Schema before accepting registration. Invalid manifests are rejected.

## Example: Minimal Manifest

```json
{
  "version": "1.0",
  "agent": {
    "publisher": "@designstudio",
    "id": "agent_001",
    "name": "Simple Bot",
    "description": "A simple example agent",
    "owner": {
      "wallet": "0x1234567890abcdef"
    }
  },
  "capabilities": [
    {
      "name": "echo",
      "description": "Echoes input back",
      "pricing": {
        "type": "per-task",
        "amount": "0.01",
        "currency": "USDC"
      }
    }
  ],
  "endpoint": {
    "url": "https://simple-bot.example.com",
    "protocol": "HIRE/1.0",
    "auth": "x402"
  },
  "metadata": {
    "created_at": "2025-01-30T00:00:00Z",
    "updated_at": "2025-01-30T00:00:00Z"
  }
}
```
