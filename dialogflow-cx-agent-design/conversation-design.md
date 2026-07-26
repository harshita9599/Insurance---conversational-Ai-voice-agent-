# Conversation Design

## Overview

The **Insurance Voice Agent** follows a structured conversation design built using **Google Cloud Dialogflow CX (CX Agent Studio)**. The conversation architecture is organized into multiple independent flows, allowing each business capability to be managed separately while maintaining a seamless customer experience.

The Root Agent authenticates the customer, identifies the requested service, preserves session context, and routes the conversation to the appropriate business flow. This modular design improves maintainability, scalability, and reusability while ensuring a consistent conversational experience across all insurance services.

---

# Conversation Architecture

The conversation follows a hierarchical flow structure where authentication is completed before protected insurance services are accessed.

```
Customer Starts Conversation
           │
           ▼
Authentication Flow
           │
           ▼
Intent Routing Flow
           │
           ▼
 ┌─────────┼─────────┬──────────┬──────────────┬─────────────┐
 │         │         │          │              │
 ▼         ▼         ▼          ▼              ▼
Policy   Claims   Customer   Update      Human
Services Management Onboarding Request   Escalation
```

Each flow performs a dedicated business function while sharing customer authentication and session context.

---

# Flow Design

## Authentication Flow

The Authentication Flow serves as the default entry point for existing customers.

### Responsibilities

- Collect registered mobile number
- Verify date of birth
- Ask security verification questions
- Validate customer identity
- Create authenticated session
- Handle authentication failures

After successful authentication, customers are automatically redirected to the **Intent Routing Flow**.

New customers bypass authentication and are redirected to the **Customer Onboarding Flow**.

---

## Intent Routing Flow

The Intent Routing Flow identifies the customer's request and routes the conversation to the appropriate business flow.

Supported requests include:

- Policy Inquiry
- Benefits Information
- Claim Status
- New Claim Initiation
- Policy Renewal
- Customer Update Request
- Product Coverage
- New Policy Purchase
- Human Escalation

When multiple policies are associated with the authenticated customer, the Multi-Policy Selection Flow is invoked before processing the request.

---

## Customer Onboarding Flow

The Customer Onboarding Flow handles new customer registration and policy creation.

### Responsibilities

- Present available insurance products
- Display product coverage information
- Collect customer information
- Create customer profile
- Generate insurance policy

Supported insurance products include:

- Vehicle Insurance
- Health Insurance
- Life Insurance

---

## Policy Services Flow

This flow manages policy-related services for authenticated customers.

### Supported Services

- Policy Details
- Benefits Information
- Policy Renewal

When multiple policies exist, the customer is prompted to select the relevant policy before continuing.

---

## Multi-Policy Selection Flow

If more than one policy is associated with a customer account, the chatbot requests the customer to choose the appropriate policy.

### Responsibilities

- Retrieve all linked policies
- Present available policy options
- Capture selected policy
- Store selected policy in session
- Continue requested business flow

---

## Claims Management Flow

This flow manages insurance claims.

### Supported Services

- Claim Status
- New Claim Initiation

The selected policy is used to retrieve or create claim information.

---

## Customer Update Request Flow

Allows customers to submit and track update requests.

### Supported Services

- Update Mobile Number
- Update Date of Birth
- Update Security Question
- Check Update Request Status

---

## Human Escalation Flow

Transfers customers to a live support representative when chatbot assistance is insufficient.

### Escalation Triggers

- Customer explicitly requests a human agent
- Authentication failure after maximum retries
- Webhook failure
- Repeated No-Match events
- Unsupported customer requests

During escalation, conversation context is transferred to avoid requiring the customer to repeat information.

---

# Event Handlers

Global event handlers improve conversation reliability by managing unexpected situations.

---

## No-Match

### Trigger

Customer input cannot be matched to any configured intent.

### Response

> Sorry, I didn't understand your request. Could you please say it again?

If repeated:

> I'm still unable to understand your request. I'll transfer you to a live support agent for further assistance.

---

## No-Input

### Trigger

Customer provides no response.

### Response

> I didn't receive any response. Please say that again.

If repeated:

> Since I haven't received a response, I'll connect you to a live support agent.

---

## Webhook Error

### Trigger

Backend service or API failure.

### Response

> I'm unable to retrieve the requested information at the moment due to a temporary system issue. I'll transfer you to a live support agent.

---

## Authentication Failure

### Condition

Maximum authentication retries reached.

```
retry_count >= 3
```

### Actions

- Create support case
- Transfer conversation to live agent
- Preserve authentication context

---

## Session Timeout

### Trigger

Customer session expires.

### Response

> Your session has expired for security reasons. Please authenticate again to continue.

### Actions

- Clear session parameters
- Restart Authentication Flow

---

## Invalid Policy Selection

### Trigger

Customer selects an invalid policy.

### Response

> I couldn't find the selected policy. Please provide a valid policy ID or choose one of your available policies.

### Action

- Reprompt customer
- Display available policies again

---

## Multiple Policies Found

### Trigger

Customer account contains multiple insurance policies.

### Actions

- Display available policies
- Ask customer to choose one
- Store selected policy in session
- Continue requested workflow

---

## Invalid Update Request

### Trigger

Customer requests an unsupported update.

### Response

> I'm sorry, that information cannot be updated through this service. I'll connect you to a live support agent for further assistance.

### Actions

- Create support case
- Transfer conversation to live agent

---

## Escalation Request

### Trigger

Human assistance requested or conversation cannot continue.

### Actions

- Create support case
- Generate support ticket
- Transfer complete conversation context
- Connect customer to live support

---

# Conversation Design Principles

The conversation architecture was designed using the following principles:

- Modular conversation flows
- Secure authentication before protected services
- Context-aware conversations
- Intelligent intent routing
- Reusable conversational components
- Consistent customer experience
- Graceful error recovery
- Seamless human escalation

---

# Benefits of the Conversation Design

The modular conversation design provides several advantages:

- Independent business flows simplify maintenance.
- New insurance services can be added without affecting existing workflows.
- Session context is preserved across multiple conversation turns.
- Authentication is performed once and reused throughout the session.
- Event handlers improve conversational robustness and user experience.
- Human escalation transfers complete conversation context for a seamless customer handoff.

---

# Summary

The Insurance Voice Agent uses a modular conversation architecture in Dialogflow CX, where independent business flows work together under a centralized authentication and intent routing mechanism. The design supports secure customer interactions, scalable business services, reliable error handling, and seamless transitions between automated assistance and live agent support.
