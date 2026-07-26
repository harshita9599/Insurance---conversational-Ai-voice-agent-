# System Architecture

## Overview

The Insurance Conversational AI Voice Agent follows a modular architecture built using Google Dialogflow CX (CX Agent Studio) and Google Cloud Platform. The solution authenticates users, identifies customer intent, routes requests to the appropriate service, retrieves information through backend APIs, and escalates conversations to human agents whenever required.

## High-Level Architecture

```text
                    Customer
                        │
                        ▼
          Insurance Voice Agent
      (Authentication + Intent Routing)
                        │
     ┌────────────┬────────────┬────────────┬──────────────┐
     │            │            │            │              │
Policy Services  Claims    Customer    Update Request   Human
                          Onboarding                  Escalation
     │            │            │            │              │
     └────────────┴────────────┴────────────┴──────────────┘
                        │
                        ▼
               Backend Webhook APIs
                        │
                        ▼
                 BigQuery Dataset
                        │
                        ▼
              Human Support Agent
```

## Components

### Customer
Interacts with the conversational AI through voice.

### Insurance Voice Agent
Responsible for authentication, intent detection, session management, and routing user requests.

### Business Services

- Policy Services
- Claims Management
- Customer Onboarding
- Update Request Processing
- Human Escalation

### Backend APIs

Backend services are accessed using REST APIs and webhooks to retrieve policy, customer, and claim information.

### BigQuery

Stores customer, policy, and claim datasets used by backend services.
