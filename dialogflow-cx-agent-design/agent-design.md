# Agent Design

## Overview

The **Insurance Voice Agent** is a Conversational AI solution developed using **Google Cloud Dialogflow CX (CX Agent Studio)** to automate insurance-related customer interactions. It serves as the central orchestration layer, managing authentication, conversation flow, intent detection, session context, backend integrations, and request routing.

The agent enables customers to access policy information, manage claims, purchase insurance products, update customer information, renew policies, and connect with a human support representative when required.

---

# Agent Architecture

The Insurance Voice Agent follows a **modular architecture** where a Root Agent authenticates the customer, manages conversation state, detects user intent, and delegates requests to specialized subagents.

## Responsibilities

The Root Agent is responsible for:

- Customer authentication
- Intent detection
- Session management
- Context preservation
- Multi-policy handling
- Customer onboarding
- Request routing
- Human escalation
- Fallback handling
- Conversation handoff

---

# Supported Customer Services

The chatbot supports the following insurance services:

| Service | Description |
|---------|-------------|
| New Policy Purchase | Create a new insurance policy |
| Product Coverage | Display insurance product coverage |
| Policy Details | Retrieve customer policy information |
| Policy Benefits | Display policy benefits |
| Claim Status | Check insurance claim status |
| New Claim | Register a new claim |
| Policy Renewal | Renew an existing policy |
| Customer Update Request | Update customer information |
| Human Escalation | Transfer conversation to a live agent |

---

# System Entities

Dialogflow CX system entities were used for extracting common user inputs.

| Entity | Purpose |
|---------|----------|
| @sys.phone-number | Customer phone number |
| @sys.date | Date of birth and policy dates |
| @sys.any | Free-form user requests |

---

# Custom Entities

Custom entities were created to capture insurance-specific information.

| Entity | Example Values |
|---------|----------------|
| @customer_id | CUST-001, CUST-002 |
| @policy_id | POL-MOTOR-001 |
| @claim_id | CLM-2026-001 |
| @insurance_product_type | Vehicle, Health, Life |
| @policy_type | Motor, Health, Life |
| @vehicle_number | DL01AB1234 |
| @chassis_number | CHS123456789 |
| @request_type | Update Mobile Number |
| @request_id | REQ1001 |
| @yes_no | Yes, No, Continue, Stop |

---

# Intents

The agent uses multiple intents to identify customer requests.

| Intent | Purpose |
|---------|---------|
| new_user_onboarding | Purchase a new insurance policy |
| policy_inquiry | Retrieve policy information |
| benefits_information | Display policy benefits |
| claim_status | Retrieve claim status |
| initiate_claim | Register a new insurance claim |
| policy_renewal | Renew an insurance policy |
| update_request | Submit customer update request |
| request_status | Track update request |
| agent_escalation | Connect customer with human agent |

Each intent contains multiple training phrases to improve intent recognition and conversational accuracy.

---

# Authentication Workflow

Authentication is performed by the Root Agent before any insurance service is accessed.

The authentication process consists of:

1. Verify registered mobile number.
2. Validate customer's date of birth.
3. Verify security question.
4. Create customer session.
5. Route request to the appropriate subagent.

Authentication failures trigger retry logic before human escalation.

---

# Subagent Architecture

The solution follows a modular subagent architecture where each subagent is responsible for a dedicated business capability.

## Policy Services Subagent

Responsibilities

- Policy inquiry
- Policy benefits
- Policy renewal
- Multi-policy handling

Backend APIs

- getPolicyDetails()
- getBenefitsInfo()
- renewPolicy()

---

## Claims Management Subagent

Responsibilities

- Claim registration
- Claim status tracking

Backend APIs

- initiateClaim()
- getClaimsStatus()

---

## Customer Onboarding Subagent

Responsibilities

- Product coverage
- New customer registration
- Policy creation

Backend APIs

- getProductCoverage()
- onBoardUser()

---

## Update Request Subagent

Responsibilities

- Submit update requests
- Track update request status

Backend APIs

- requestUpdate()
- getRequestStatus()

---

## Human Escalation Subagent

Responsibilities

- Create support cases
- Transfer conversation
- Preserve customer context

Escalation is triggered when:

- Customer requests human assistance
- Authentication repeatedly fails
- Backend services are unavailable
- User requests cannot be resolved

Backend APIs

- createCase()
- escalateToAgent()

---

# Conversation Routing

Customer requests follow the workflow below:

Customer Request

↓

Authentication

↓

Intent Detection

↓

Session Context Validation

↓

Route to Appropriate Subagent

↓

Backend API Invocation

↓

Response Generation

↓

Conversation Completion

---

# Design Principles

The Insurance Voice Agent was designed using the following principles:

- Modular architecture
- Reusable conversational components
- Secure customer authentication
- Context-aware conversations
- Scalable service architecture
- Backend API integration
- Consistent user experience
- Efficient human handoff

---

# Design Benefits

The implemented architecture provides several advantages:

- Modular design allows independent enhancement of services.
- Shared authentication simplifies security management.
- Session parameters preserve conversation context.
- Backend APIs are reusable across multiple workflows.
- Human escalation transfers complete conversation history.
- New insurance services can be integrated with minimal architectural changes.

---

# Technologies Used

- Google Cloud Dialogflow CX
- CX Agent Studio
- REST APIs
- Webhooks
- Mock Backend Services
- Session Parameters
- Intent Routing
- Entity Extraction

---

# Summary

The Insurance Voice Agent uses a modular, scalable architecture that combines customer authentication, intelligent intent routing, session management, backend integrations, and specialized subagents to automate end-to-end insurance services. The design enables secure, context-aware conversations while maintaining flexibility for future enhancements and additional business capabilities.
