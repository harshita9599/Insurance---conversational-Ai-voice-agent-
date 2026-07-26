# 🛡️ Insurance Conversational AI Voice Agent

An AI-powered Insurance Conversational Voice Agent developed as an **Industry Project** using **Google Dialogflow CX (CX Agent Studio)** and **Google Cloud Platform**. The solution automates insurance customer interactions through secure authentication, intelligent intent routing, backend API integration, and conversational workflows.

---

## 📌 Project Overview

The Insurance Voice Agent assists customers with common insurance services such as policy inquiries, claim status tracking, customer onboarding, policy renewal, update requests, and human escalation. It integrates with backend services through REST APIs and webhooks to deliver secure, scalable, and context-aware conversations.

---

## ✨ Key Features

- Secure customer authentication
- Policy inquiry and benefits information
- Claim status tracking
- New claim initiation
- Policy renewal
- Customer onboarding
- Customer information update requests
- Human escalation with conversation context transfer
- REST API and Webhook integration
- Manual, Golden, and Scenario-based testing

---

## 🏗️ Solution Architecture

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

---

## 💻 Technology Stack

| Category | Technology |
|----------|------------|
| Conversational AI | Google Dialogflow CX |
| Cloud Platform | Google Cloud Platform |
| Agent Platform | CX Agent Studio |
| Backend | Python, Cloud Run |
| Database | BigQuery |
| API Integration | REST APIs, Webhooks |
| Data Format | JSON |
| Version Control | Git, GitHub |

---

## 🧪 Testing & Evaluation

The solution was validated using multiple testing approaches to ensure functionality and conversational quality.

- Authentication Testing
- Functional Testing
- Happy Path Testing
- Edge Case Testing
- Golden Evaluations
- Scenario-based Evaluations
- End-to-End Testing

### Evaluation Metrics

- Intent Recognition Accuracy
- Task Completion Rate
- Automation Rate
- Escalation Rate
- Average Handle Time (AHT)

---


## 🚀 Future Enhancements

- Voice input and output support
- Real insurance API integration
- Multi-language support
- Analytics dashboard
- CI/CD deployment pipeline

---

## 👩‍💻 My Contributions

- Designed conversational workflows and authentication logic.
- Developed intent routing for insurance services.
- Performed manual, Golden, and Scenario-based testing.
- Validated REST API and webhook integrations.
- Prepared project documentation and testing reports.

---

