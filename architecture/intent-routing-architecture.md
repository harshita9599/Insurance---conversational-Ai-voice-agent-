# Intent Routing Architecture

## Overview

After successful authentication, Dialogflow CX detects the customer's intent and routes the conversation to the appropriate service flow.

## Supported Service Flows

### 1. Onboarding
Registers new customers and creates insurance policies.

### 2. Policy Services
Handles:
- Policy Inquiry
- Benefits Information
- Policy Renewal

### 3. Claims
Supports:
- Claim Status
- Create New Claim

### 4. Update Requests
Allows customers to:
- Submit update requests
- Track request status

### 5. Human Escalation
Transfers the conversation to a live support agent when requested or when automation cannot resolve the issue.

## Intent Routing Diagram

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/6bb4df6d-662b-4cb2-8973-2493e32f626c" />
