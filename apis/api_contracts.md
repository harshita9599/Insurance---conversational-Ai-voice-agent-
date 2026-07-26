# API Contracts

## Overview

This document defines the API contracts used by the **Insurance Conversational AI Voice Agent**. The APIs simulate backend insurance services and enable secure communication between Google Dialogflow CX and backend systems using REST-based JSON requests and responses.

The APIs support customer authentication, policy management, claims processing, onboarding, customer profile updates, product information retrieval, and human escalation workflows.

---

## API Summary

| API | Purpose |
|------|---------|
| validateUser() | Authenticate customer before accessing insurance services |
| getPolicyDetails() | Retrieve policy details |
| getClaimsStatus() | Retrieve claim status |
| initiateClaim() | Create a new insurance claim |
| getBenefitsInfo() | Retrieve policy benefits |
| renewPolicy() | Renew an existing policy |
| getProductCoverage() | Retrieve insurance product information |
| onBoardUser() | Register a new customer |
| requestUpdate() | Submit customer update requests |
| getRequestStatus() | Retrieve update request status |
| createCase() | Create a support case |

---

# 1. validateUser()

## Purpose

Authenticate a customer using their registered phone number, date of birth, and verification answers before granting access to insurance services.

### Request

```json
{
  "phone": "9876543210",
  "dob": "1990-05-15",
  "verificationAnswers": [
    "Greenfield School",
    "Sharma"
  ]
}
```

### Response

```json
{
  "authenticated": true,
  "customerId": "C001",
  "customerName": "Amit Verma"
}
```

---

# 2. getPolicyDetails()

## Purpose

Retrieve the complete details of an insurance policy for an authenticated customer.

### Request

```json
{
  "policyId": "P101"
}
```

### Response

```json
{
  "policyId": "P101",
  "type": "Vehicle Insurance",
  "status": "Active",
  "coverageDetails": "Accident Cover, Cashless Garage, Roadside Assistance",
  "expiryDate": "2027-01-15"
}
```

---

# 3. getClaimsStatus()

## Purpose

Retrieve the latest status and details of an existing insurance claim.

### Request

```json
{
  "claimId": "CLM12345"
}
```

### Response

```json
{
  "claimId": "CLM12345",
  "status": "In Progress",
  "amount": 25000,
  "lastUpdate": "2025-05-10"
}
```

---

# 4. initiateClaim()

## Purpose

Create a new insurance claim for the specified policy.

### Request

```json
{
  "policyId": "P101"
}
```

### Response

```json
{
  "status": "Claim Initiated",
  "claimId": "CLM12345"
}
```

---

# 5. getBenefitsInfo()

## Purpose

Retrieve the list of benefits and coverage included in an insurance policy.

### Request

```json
{
  "policyId": "P101"
}
```

### Response

```json
{
  "benefits": [
    "Accident Cover",
    "Cashless Garage",
    "Roadside Assistance"
  ]
}
```

---

# 6. renewPolicy()

## Purpose

Renew an existing insurance policy and return the updated policy validity.

### Request

```json
{
  "policyId": "P101"
}
```

### Response

```json
{
  "status": "Renewed",
  "validTill": "2028-01-15"
}
```

---

# 7. createCase()

## Purpose

Create a customer support case when an issue requires human assistance or further investigation.

### Request

```json
{
  "issue": "Customer requested human assistance",
  "customerId": "C001"
}
```

### Response

```json
{
  "status": "Case Created",
  "ticketId": "T56789"
}
```

---

# 8. getProductCoverage()

## Purpose

Retrieve coverage details, eligibility criteria, and premium information for an insurance product.

### Request

```json
{
  "productType": "Vehicle Insurance"
}
```

### Response

```json
{
  "productType": "Vehicle Insurance",
  "coverage": [
    "Accident Cover",
    "Third Party Liability",
    "Cashless Garage",
    "Roadside Assistance"
  ],
  "eligibility": "Vehicle must be registered in India",
  "startingPremium": 4500
}
```

---

# 9. onBoardUser()

## Purpose

Register a new customer and create an insurance policy after successful onboarding.

### Request

```json
{
  "customerName": "Amit Verma",
  "phone": "9876543210",
  "dob": "1990-05-15",
  "productType": "Vehicle Insurance",
  "email": "amit.verma@example.com",
  "address": "Delhi, India"
}
```

### Response

```json
{
  "status": "Success",
  "customerId": "C001",
  "policyId": "P101",
  "message": "Customer onboarded successfully."
}
```

---

# 10. requestUpdate()

## Purpose

Submit a request to update customer or policy information for review and approval.

### Request

```json
{
  "customerId": "C001",
  "requestType": "Update DOB",
  "newValue": "2003-04-12"
}
```

### Response

```json
{
  "requestId": "REQ1001",
  "status": "Submitted",
  "message": "Your update request has been received and is under review."
}
```

---

# 11. getRequestStatus()

## Purpose

Retrieve the latest status of a previously submitted customer update request.

### Request

```json
{
  "requestId": "REQ1001"
}
```

### Response

```json
{
  "requestId": "REQ1001",
  "status": "Approved",
  "lastUpdated": "2026-07-11",
  "remarks": "Customer address updated successfully."
}
```

---

## Notes

- All APIs exchange data using JSON request and response payloads.
- The APIs are intended for demonstration and testing purposes.
- Mock backend implementations are available in `mock_api_responses.md`.
- Authentication is required before accessing protected insurance services such as policy retrieval, claims management, and customer updates.
