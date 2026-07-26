# Manual Testing Report

## Overview

Manual testing was performed to verify the functionality, reliability, and usability of the **Insurance Conversational AI Voice Agent** before conducting automated evaluations. The objective was to ensure that the chatbot correctly handled customer requests, maintained conversation context, invoked the appropriate backend APIs, and produced accurate responses under normal and exceptional conditions.

Testing was conducted in **Google Cloud Dialogflow CX (CX Agent Studio)** using predefined test cases and real user interaction scenarios.

---

# Testing Objectives

The primary objectives of manual testing were:

- Verify end-to-end business workflows.
- Validate customer authentication.
- Test intent recognition and routing.
- Verify backend API execution.
- Validate conversation continuity.
- Test fallback and retry mechanisms.
- Evaluate chatbot responses for common insurance services.
- Identify defects before automated evaluations.

---

# Test Environment

| Parameter | Details |
|-----------|---------|
| Platform | Google Cloud Dialogflow CX |
| Environment | CX Agent Studio |
| Testing Type | Manual Functional Testing |
| Application | Insurance Conversational AI Voice Agent |
| Backend | Mock REST APIs |
| Evaluation Method | Manual User Interaction |

---

# Scope of Testing

The following modules were manually validated:

## Authentication

- Customer verification
- Mobile number validation
- Date of birth verification
- Security questions
- Retry mechanism
- Session creation

## Policy Services

- Policy Details
- Policy Benefits
- Policy Renewal

## Claims

- Claim Status
- New Claim Registration

## Customer Onboarding

- Vehicle Insurance
- Health Insurance
- Life Insurance

## Customer Update Requests

- Update Address
- Update Mobile Number
- Update Date of Birth

## Human Escalation

- Agent Transfer
- Case Creation

---

# Testing Process

Each feature was validated using predefined manual test cases.

The following checkpoints were verified during every conversation:

- Correct intent recognition
- Authentication success
- Context preservation
- Backend API invocation
- Response generation
- Error handling
- Conversation completion

Execution results were documented in the Manual Testing spreadsheet together with execution status and tester observations.

---

# Edge Case Testing

Several negative and edge case scenarios were executed to verify chatbot robustness.

### Authentication

- Invalid mobile number
- Incorrect date of birth
- Incorrect verification answers
- Maximum authentication retries exceeded

### Policy Services

- Invalid policy ID
- Expired policy
- Policy not found

### Claims

- Invalid claim ID
- Closed claim
- No claims available

### API Behaviour

- API timeout
- Empty response
- Invalid response
- Backend failure

### Conversation Behaviour

- User changes intent
- User remains silent
- Unrelated questions
- Multiple requests in one conversation
- Repeated escalation requests

---

# Sample Test Results

| Module | Test Case | Result |
|---------|-----------|--------|
| Authentication | Valid Customer Login | ✅ Pass |
| Authentication | Invalid DOB | ✅ Pass |
| Policy Services | Retrieve Policy Details | ✅ Pass |
| Policy Services | Retrieve Benefits | ✅ Pass |
| Claims | Claim Status | ✅ Pass |
| Claims | New Claim Registration | ✅ Pass |
| Policy Renewal | Renew Policy | ✅ Pass |
| Human Escalation | Transfer to Live Agent | ✅ Pass |
| Intent Routing | Route to Correct Service | ✅ Pass |

---

# Test Summary

Successfully validated:

- Customer authentication
- Policy inquiry
- Benefits information
- Claim status
- New claim registration
- Policy renewal
- Customer onboarding
- Human escalation
- Intent routing
- Error handling

The chatbot correctly handled both expected customer journeys and edge case scenarios while maintaining conversation context.

---

# Deliverables

The following artifacts were produced during manual testing:

- Manual Test Cases
- Test Execution Report
- Pass/Fail Results
- Testing Observations
- Defect Log
- Test Summary

---

# Conclusion

Manual testing confirmed that the Insurance Conversational AI Voice Agent was functionally stable and capable of supporting core insurance workflows. Authentication, policy services, claims management, onboarding, and escalation scenarios were successfully validated.

The successful completion of manual testing established a reliable baseline for conducting Golden Evaluations and Scenario-Based Evaluations.
