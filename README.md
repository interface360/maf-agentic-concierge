# MAF Agentic Concierge - Hospitality Industry

This project leverages **MuleSoft Agent Fabric (MAF)** to build a governed, multi-agent concierge system for the hospitality sector. By utilizing MAF, this repository demonstrates how to discover, manage, and orchestrate specialized agents that interact with enterprise data through the MuleSoft ecosystem. 

## 🏨 Project Overview

The **Hospitality Agentic Concierge** is built on the **MuleSoft Agent Fabric**, providing a centralized control plane for AI agents. Rather than relying on a single monolithic bot, this architecture uses a network of specialized agents that leverage MuleSoft's API-led connectivity to perform real-world actions like managing room bookings, coordinating guest services, and handling financial transactions.

### The MAF Foundation:
* **Agent Registry:** A central catalog for discovering hospitality-specific agents and their capabilities.
* **Agent Broker:** Orchestrates hand-offs between specialized agents (e.g., transitioning a guest from a room upgrade request to a dinner reservation).
* **Governance & Security:** Applies enterprise-grade policies to agent interactions, ensuring guest PII is protected and LLM "hallucinations" are mitigated via API constraints.
* **Observability:** Provides a clear view of agent reasoning and tool execution through the Anypoint Platform.

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

## 🚀 Key Features

* **API-Led Agency:** Automatically transforms existing MuleSoft System and Process APIs into "Tools" that agents can reason over and execute.
* **Unified Control Plane:** Manage agents across different environments and LLM providers under one secure fabric.
* **Contextual Hand-offs:** MAF manages the state and memory of a guest's journey as they move between different specialized agents.
* **Enterprise Guardrails:** Ensures agents operate within the bounds of defined API specifications and organizational policies.

## 🛠 Prerequisites

* **Anypoint Platform Account** with Agent Fabric enabled.
* **Anypoint Code Builder (ACB)** or your preferred IDE.
* **Flex Gateway** for agent traffic management and governance.

## ⚙️ Setup & Implementation

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/interface360/maf-agentic-concierge.git
    cd maf-agentic-concierge
    git checkout hospitality-industry
    ```

2.  **Configure Agent Registry:**
    Register your hospitality APIs in the **Agent Registry** within the Anypoint Platform. Ensure each API has clear descriptions to allow the LLM to understand when to invoke them.

3.  **Define Orchestration:**
    Use the **Agent Broker** configuration to define how requests are routed. (e.g., routing a "spa booking" intent to the Experience Agent).

4.  **Deploy & Monitor:**
    Deploy your agents to the MAF runtime and use the **Agent Visualizer** to monitor the "thought process" and execution paths of each guest interaction.

## ⚙️ Configuration & Deployment

The network behavior is defined in `agent-network.yaml`. Key configurations include:

1.  **LLM Provider:** Powered by **Gemini** (configured via `concierge-gemini`) with a temperature of `0.1` for high precision.
2.  **System Guardrails:** The Lead Concierge is strictly constrained to narrative output—no lists, no headers, and no mechanical formatting in guest responses.

## Sample JSON Input Request
```json
{
 "jsonrpc": "2.0",
 "id": "4",
 "method": "message/send",
 "params": {
   "message": {
     "kind": "message",
     "messageId": "908627f8-fe22-4367-8d9b-6a5ed8571333",
     "role": "user",
     "parts": [
       {
         "kind": "text",
         "text": "I'm checking in now. My email is ray@codecrates.xyz and my account id is ACC-001. I’d like to know my current loyalty points and have my luggage sent up to the room once it's ready."
       }
     ]
   }
 }
}
```

