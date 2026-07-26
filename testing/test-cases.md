# Test Cases

## Overview

This document contains the functional, conversational, and edge-case test cases executed for the Insurance Conversational AI Voice Agent developed using Google Cloud Dialogflow CX (CX Agent Studio). The test cases validate authentication, policy services, claims management, onboarding, backend API integration, intent routing, session management, and error handling.

---

# 1. Authentication Test Cases

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-AUTH-001 | Valid customer login | Customer authenticated successfully | High |
| TC-AUTH-002 | Invalid phone number | Error message displayed | High |
| TC-AUTH-003 | Invalid date of birth | Authentication denied | High |
| TC-AUTH-004 | Incorrect security answer | Verification failed | High |
| TC-AUTH-005 | Maximum retry limit exceeded | Customer account temporarily blocked | High |
| TC-AUTH-006 | Session maintained after login | Session remains active | Medium |
| TC-AUTH-007 | Session timeout | User prompted to authenticate again | Medium |
| TC-AUTH-008 | Empty phone number | Validation message displayed | Medium |
| TC-AUTH-009 | Empty DOB | Validation message displayed | Medium |
| TC-AUTH-010 | Empty security answer | Validation message displayed | Medium |

---

# 2. Customer Onboarding

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-ONB-001 | New customer onboarding | Customer registered successfully | High |
| TC-ONB-002 | Motor policy creation | Motor policy created | High |
| TC-ONB-003 | Health policy creation | Health policy created | High |
| TC-ONB-004 | Life policy creation | Life policy created | High |
| TC-ONB-005 | Existing customer onboarding | Duplicate customer prevented | Medium |
| TC-ONB-006 | Missing mandatory details | Validation displayed | Medium |
| TC-ONB-007 | Invalid email address | Validation displayed | Medium |
| TC-ONB-008 | Invalid mobile number | Validation displayed | Medium |

---

# 3. Policy Services

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-POL-001 | Retrieve policy details | Policy information displayed | High |
| TC-POL-002 | Retrieve premium amount | Premium displayed | Medium |
| TC-POL-003 | Retrieve renewal date | Renewal date displayed | Medium |
| TC-POL-004 | Policy benefits inquiry | Benefits displayed | High |
| TC-POL-005 | Policy expiry inquiry | Expiry date displayed | Medium |
| TC-POL-006 | Active policy status | Active status displayed | Medium |
| TC-POL-007 | Invalid policy number | Validation message | High |
| TC-POL-008 | Expired policy | Appropriate response displayed | Medium |
| TC-POL-009 | No active policy | User informed | Medium |
| TC-POL-010 | Multiple policies | Available policies displayed | Medium |
| TC-POL-011 | Coverage details | Coverage displayed | Medium |
| TC-POL-012 | Vehicle information | Vehicle details displayed | Medium |

---

# 4. Claims Management

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-CLM-001 | Retrieve claim status | Claim status displayed | High |
| TC-CLM-002 | Register new claim | Claim created | High |
| TC-CLM-003 | Invalid claim ID | Validation displayed | Medium |
| TC-CLM-004 | No active claims | Appropriate message displayed | Medium |
| TC-CLM-005 | Closed claim | Closed status displayed | Medium |
| TC-CLM-006 | Multiple claims | All claims listed | Medium |
| TC-CLM-007 | Claim history | Previous claims displayed | Low |
| TC-CLM-008 | Claim document missing | Validation displayed | Medium |
| TC-CLM-009 | Claim already submitted | Duplicate prevented | Medium |
| TC-CLM-010 | Claim acknowledgement | Confirmation displayed | Medium |

---

# 5. Customer Update Requests

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-UPD-001 | Update address | Address updated | Medium |
| TC-UPD-002 | Update phone number | Phone updated | Medium |
| TC-UPD-003 | Update email | Email updated | Medium |
| TC-UPD-004 | Update DOB | DOB updated after verification | Medium |
| TC-UPD-005 | Invalid update request | Validation displayed | Medium |

---

# 6. Human Escalation

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-ESC-001 | Escalate to live agent | Conversation transferred | High |
| TC-ESC-002 | Escalate after repeated failures | Agent assigned | High |
| TC-ESC-003 | Preserve conversation context | Context transferred | High |
| TC-ESC-004 | Escalation unavailable | Appropriate message displayed | Medium |
| TC-ESC-005 | Cancel escalation | Continue chatbot conversation | Low |

---

# 7. Intent Recognition & Routing

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-IR-001 | Route to onboarding | Correct intent detected | High |
| TC-IR-002 | Route to policy inquiry | Correct intent detected | High |
| TC-IR-003 | Route to benefits | Correct intent detected | High |
| TC-IR-004 | Route to claim status | Correct intent detected | High |
| TC-IR-005 | Route to create claim | Correct intent detected | High |
| TC-IR-006 | Route to renewal | Correct intent detected | High |
| TC-IR-007 | Route to escalation | Correct intent detected | High |
| TC-IR-008 | Change intent mid-conversation | Intent switched successfully | High |
| TC-IR-009 | Multiple intents in one query | Primary intent identified | Medium |
| TC-IR-010 | Ambiguous request | Clarification requested | Medium |

---

# 8. Conversation Behaviour

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-CONV-001 | Greeting | Greeting returned | Low |
| TC-CONV-002 | User silence | Reprompt generated | Medium |
| TC-CONV-003 | Fallback conversation | Fallback triggered | High |
| TC-CONV-004 | Repeat information | Information repeated | Medium |
| TC-CONV-005 | Session memory | Context retained | High |
| TC-CONV-006 | Session persistence | Context maintained | High |
| TC-CONV-007 | Conversation interruption | Conversation resumed | Medium |
| TC-CONV-008 | End-to-end happy path | Workflow completed | High |
| TC-CONV-009 | Multi-policy conversation | Correct policy selected | Medium |
| TC-CONV-010 | Conversation termination | Session closed successfully | Low |

---

# 9. API & Backend Validation

| Test ID | Test Scenario | Expected Result | Priority |
|---------|---------------|-----------------|----------|
| TC-API-001 | Successful API response | Correct data returned | High |
| TC-API-002 | API timeout | Graceful error displayed | High |
| TC-API-003 | Empty API response | User informed | High |
| TC-API-004 | Invalid API response | Error handled | High |
| TC-API-005 | Backend unavailable | Appropriate message displayed | High |

---

# 10. Overall Summary

| Category | Test Cases |
|----------|-----------:|
| Authentication | 10 |
| Customer Onboarding | 8 |
| Policy Services | 12 |
| Claims Management | 10 |
| Customer Updates | 5 |
| Human Escalation | 5 |
| Intent Recognition | 10 |
| Conversation Behaviour | 10 |
| API Validation | 5 |
| **Total** | **75** |
