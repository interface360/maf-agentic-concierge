# MAF Agentic Concierge - Hospitality Industry

This project leverages **MuleSoft Agent Fabric (MAF)** to build a governed, multi-agent concierge system for the hospitality sector. By utilizing MAF, this repository demonstrates how to discover, manage, and orchestrate specialized agents that interact with enterprise data through the MuleSoft ecosystem.

## 🏨 Project Overview

The **Hospitality Agentic Concierge** is built on the **MuleSoft Agent Fabric**, providing a centralized control plane for AI agents. Rather than relying on a single monolithic bot, this architecture uses a network of specialized agents that leverage MuleSoft's API-led connectivity to perform real-world actions like managing room bookings, coordinating guest services, and handling financial transactions.

### The MAF Foundation:
* **Agent Registry:** A central catalog for discovering hospitality-specific agents and their capabilities.
* **Agent Broker:** Orchestrates hand-offs between specialized agents (e.g., transitioning a guest from a room upgrade request to a dinner reservation).
* **Governance & Security:** Applies enterprise-grade policies to agent interactions, ensuring guest PII is protected and LLM "hallucinations" are mitigated via API constraints.
* **Observability:** Provides a clear view of agent reasoning and tool execution through the Anypoint Platform.

## 🤖 The Agent Network

| Agent Name | Specialty | Integrated Systems (via MuleSoft) |
| :--- | :--- | :--- |
| **Front Desk Agent** | Check-ins, upgrades, and digital keys. | **Opera PMS / Salesforce Industries** |
| **Experience Agent** | Dining, local tours, and transport. | **OpenTable / Yelp / Custom Concierge APIs** |
| **Operations Agent** | Housekeeping and maintenance requests. | **ServiceNow / Slack / HotSOS** |
| **Folio Manager** | Billing, payments, and checkout. | **Stripe / ERP Financial Systems** |

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
    git clone [https://github.com/interface360/maf-agentic-concierge.git](https://github.com/interface360/maf-agentic-concierge.git)
    cd maf-agentic-concierge
    git checkout hospitality-industry
    ```

2.  **Configure Agent Registry:**
    Register your hospitality APIs in the **Agent Registry** within the Anypoint Platform. Ensure each API has clear descriptions to allow the LLM to understand when to invoke them.

3.  **Define Orchestration:**
    Use the **Agent Broker** configuration to define how requests are routed. (e.g., routing a "spa booking" intent to the Experience Agent).

4.  **Deploy & Monitor:**
    Deploy your agents to the MAF runtime and use the **Agent Visualizer** to monitor the "thought process" and execution paths of each guest interaction.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
*Developed by Interface360 for the MuleSoft AI Community.*
