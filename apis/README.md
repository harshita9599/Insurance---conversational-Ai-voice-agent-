# APIs

## Overview

This folder contains the API documentation and mock backend implementations used by the **Insurance Conversational AI Voice Agent**. These APIs simulate backend insurance services and enable seamless communication between the conversational AI platform and insurance systems.

The APIs support customer authentication, policy management, claims processing, onboarding, customer profile updates, policy renewals, product information retrieval, and human escalation workflows.

The backend services are designed using REST principles with JSON request and response payloads. During development and testing, mock API implementations were used to simulate backend behaviour without connecting to production systems.

---

## Folder Structure

| File | Description |
|------|-------------|
| **api_contracts.md** | API specifications including request payloads, response payloads, and functional descriptions. |
| **mock_api_responses.md** | Python-based mock backend implementations used during development and testing. |

---

## Available APIs

| API | Description |
|------|-------------|
| validateUser() | Authenticates customers before accessing insurance services. |
| getPolicyDetails() | Retrieves customer policy information. |
| getClaimsStatus() | Retrieves insurance claim status. |
| initiateClaim() | Creates a new insurance claim. |
| getBenefitsInfo() | Retrieves policy benefits and coverage details. |
| renewPolicy() | Renews an existing insurance policy. |
| getProductCoverage() | Retrieves insurance product details. |
| onBoardUser() | Registers a new customer and creates a policy. |
| requestUpdate() | Creates customer information update requests. |
| getRequestStatus() | Retrieves the status of submitted update requests. |
| createCase() | Creates a support case for human assistance. |

---

## Technologies Used

- Google Dialogflow CX
- Google Cloud Platform
- REST APIs
- JSON
- Python
- Webhooks

---

## Purpose

These APIs were developed to simulate backend insurance services required by the conversational AI application. They provide a standardized communication layer between the Dialogflow CX agent and backend systems, enabling secure authentication, policy retrieval, claims management, onboarding, and customer support workflows.
