# MAF Agentic Concierge - Hospitality Industry

This repository contains the configuration and orchestration logic for the **Agentic Concierge**, a high-touch AI agent network built on **MuleSoft Agent Fabric (MAF)**. It provides a governed, multi-agent ecosystem designed to deliver a "white-glove" guest experience through seamless API-led orchestration.

## 🏨 Network Architecture

The project implements a **Broker-Specialist** pattern. The central Intelligence Layer (Broker) orchestrates complex guest requests by delegating tasks to specialized agents and retrieving deep context from multiple internal and external data sources via the **Model Context Protocol (MCP)**.

### 🧠 The Agentic Concierge Broker
The primary guest interface and orchestrator (`agentic-concierge-broker`). It is configured to:
* **Maintain State:** Full transition history and push notification capabilities.
* **Persona-Driven:** Uses a Lead Concierge persona that communicates in fluid narrative prose.
* **Coordinate:** Acts as the single "hub" for the specialists listed below.

### 🤖 Specialized Agents (A2A)
The Broker coordinates with three key specialists over the **Agent-to-Agent (A2A)** protocol:
* **Planning Specialist:** Manages scheduling, resource allocation, and the **Booking API**.
* **Rewards Specialist:** Handles loyalty points and guest entitlements via the **Incentive API**.
* **Logistics Service Specialist:** Coordinates physical deliveries (luggage/tags) and orchestrates external dining/event reservations.

## 🚀 Key Workflows (Skills)

| Skill ID | Name | Description |
| :--- | :--- | :--- |
| `completeCheckInWorkflow` | **End-to-End Arrival** | Verifies identity, applies loyalty upgrades, and coordinates luggage delivery. |
| `experienceDiscoveryWorkflow` | **Event Planning** | Matches preferences to external dining and show ticket inventory. |
| `serviceStatusWorkflow` | **Unified Inquiry** | Provides a single view of point balances and real-time item delivery status. |

## 🛠 Model Context Protocol (MCP) Integrations

The network leverages a wide array of MCP servers to provide the agents with real-time "tools" and context:
* **Internal Tools:** Guest Profiles, VIP Metadata, Booking Systems, and Reward Systems.
* **Logistics Tools:** Delivery and Provisioning trackers.
* **External Partners:** Real-time connectivity to **Dining Service Partners** and **Event Ticket Services**.

## ⚙️ Configuration & Deployment

The network behavior is defined in `agent-network.yaml`. Key configurations include:

1.  **LLM Provider:** Powered by **Gemini** (configured via `concierge-gemini`) with a temperature of `0.1` for high precision.
2.  **System Guardrails:** The Lead Concierge is strictly constrained to narrative output—no lists, no headers, and no mechanical formatting in guest responses.
3.  **Security & Policies:** Includes message logging and header inspection via MuleSoft Flex Gateway policies on agent connections.

### Deployment Steps:
1.  Ensure **MuleSoft Agent Fabric** is enabled in your Anypoint environment.
2.  Configure the environment variables for `${ingressgw.url}` and `${gemini.key}`.
3.  Deploy the agent network bundle using the MAF CLI or Anypoint Code Builder.

```bash
# Example deployment via MAF CLI
maf deploy --file agent-network.yaml --env production
