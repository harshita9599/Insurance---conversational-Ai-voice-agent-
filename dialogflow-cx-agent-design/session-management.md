# Session Management

## Overview

Session management is a critical component of the **Insurance Voice Agent**. It enables the agent to maintain conversation context, preserve customer information across multiple conversation flows, and provide a seamless user experience without repeatedly requesting the same information.

After successful authentication, customer-specific details are stored as **Dialogflow CX Session Parameters**. These parameters are shared across all business flows, allowing the agent to deliver personalized and context-aware responses throughout the conversation.

---

# Objectives

The session management design aims to:

- Preserve conversation context throughout the session.
- Eliminate repetitive information collection.
- Share customer information across multiple conversation flows.
- Support multi-policy handling.
- Enable smooth transitions between subagents.
- Maintain conversation history for human escalation.
- Improve the overall customer experience.

---

# Session Lifecycle

The session follows the lifecycle illustrated below.

```
Conversation Started
        │
        ▼
Authentication
        │
        ▼
Store Session Parameters
        │
        ▼
Intent Routing
        │
        ▼
Business Flows
        │
        ▼
Update Session Parameters
        │
        ▼
Conversation Complete
        │
        ▼
Session Cleared
```

During the session, parameters are continuously updated as the customer navigates through different services.

---

# Authentication Parameters

These parameters are collected during customer authentication.

| Parameter | Description |
|------------|-------------|
| phone_number | Stores the registered mobile number provided by the customer. |
| dob | Stores the customer's date of birth. |
| verification_answer_1 | Stores the response to the first verification question. |
| verification_answer_2 | Stores the response to the second verification question. |
| auth_status | Indicates whether authentication was successful. |
| retry_count | Tracks the number of authentication attempts. |

These parameters are primarily used by the Authentication Flow to validate customer identity before providing access to insurance services.

---

# Customer Parameters

After successful authentication, customer details retrieved from the backend are stored in session parameters.

| Parameter | Description |
|------------|-------------|
| customer_id | Unique customer identifier. |
| customer_name | Authenticated customer's name. |

These parameters remain available throughout the conversation and are reused by all business flows.

---

# Policy Parameters

Policy-related information is maintained to support policy services.

| Parameter | Description |
|------------|-------------|
| policy_list | Stores all insurance policies linked to the customer. |
| selected_policy_id | Stores the policy selected by the customer. |

If multiple policies exist, the selected policy is stored and reused by subsequent requests.

---

# Claim Parameters

Claim-related information is maintained for claims management services.

| Parameter | Description |
|------------|-------------|
| claim_list | Stores all claims associated with the selected policy. |
| selected_claim_id | Stores the claim selected by the customer. |

These parameters enable claim status retrieval and new claim processing.

---

# Customer Onboarding Parameters

The onboarding flow stores customer selections during policy purchase.

| Parameter | Description |
|------------|-------------|
| product_type | Selected insurance product type (Motor, Health, Life). |
| vehicle_number | Vehicle registration number for Motor Insurance. |
| chassis_number | Chassis number used for verification. |

These parameters are used while creating new customer profiles and insurance policies.

---

# Update Request Parameters

These parameters support customer information update requests.

| Parameter | Description |
|------------|-------------|
| request_type | Type of update requested by the customer. |
| new_value | New information submitted by the customer. |
| request_id | Unique update request identifier. |

The generated request ID is later used to track the update request status.

---

# Human Escalation Parameters

When conversations are transferred to a live support representative, additional parameters are maintained.

| Parameter | Description |
|------------|-------------|
| escalation_reason | Reason for escalation. |
| ticket_id | Support case number generated during escalation. |
| conversation_summary | Summary of the customer conversation transferred to the support agent. |

These parameters ensure that the support representative receives sufficient context before interacting with the customer.

---

# Parameter Usage Across Flows

The following table summarizes how session parameters are used throughout the conversation.

| Flow | Parameters Used |
|------|-----------------|
| Authentication Flow | phone_number, dob, verification answers, auth_status, retry_count |
| Intent Routing Flow | customer_id, customer_name |
| Policy Services Flow | selected_policy_id, policy_list |
| Claims Management Flow | selected_policy_id, selected_claim_id, claim_list |
| Customer Onboarding Flow | product_type, vehicle_number, chassis_number |
| Update Request Flow | request_type, request_id, new_value |
| Human Escalation Flow | escalation_reason, ticket_id, conversation_summary |

---

# Context Preservation

Session parameters enable the agent to preserve customer context throughout the conversation.

Examples include:

- Reusing authenticated customer details without requesting them again.
- Retaining the selected insurance policy across multiple services.
- Maintaining claim information during claim processing.
- Tracking update requests using the generated request ID.
- Sharing conversation history during human escalation.

This minimizes repetitive interactions and improves customer satisfaction.

---

# Session Timeout

For security purposes, customer sessions expire after a period of inactivity.

When a session expires:

- All active session parameters are cleared.
- Authentication status is reset.
- The customer is redirected to the Authentication Flow.
- The customer must authenticate again before accessing protected services.

---

# Benefits of Session Management

The session management design provides several advantages:

- Maintains conversation continuity.
- Eliminates repetitive data collection.
- Enables context-aware responses.
- Supports seamless transitions across business flows.
- Improves multi-policy handling.
- Enhances customer experience.
- Simplifies backend integration.
- Facilitates efficient human escalation.

---

# Summary

The Insurance Voice Agent uses Dialogflow CX session parameters to preserve customer context across authentication, policy services, claims management, onboarding, update requests, and human escalation. This centralized session management approach enables secure, efficient, and personalized conversations while ensuring a smooth transition between different business capabilities.
