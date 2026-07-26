# Mock API Responses

## Overview

This document contains Python-based mock backend implementations used during the development and testing of the **Insurance Conversational AI Voice Agent**.

The mock APIs simulate backend insurance services without requiring a live database or production server. They return predefined JSON responses that allow the conversational agent to validate authentication, retrieve policy information, manage claims, process customer requests, and support end-to-end testing.

These implementations were primarily used for:
- Functional testing
- Happy path validation
- Edge case testing
- Webhook integration
- API response simulation
- Demonstration purposes

---

## Technologies

- Python
- JSON
- Mock REST APIs
- Google Dialogflow CX
- Google Cloud Platform

---

## Mock API Implementations

```python
def validateUser(phone, dob):
    """
    Authenticate a customer using registered phone number and date of birth.
    """

    return {
        "authenticated": True,
        "customerId": "C001",
        "customerName": "Amit Verma"
    }


def getPolicyDetails(policy_id):
    """
    Retrieve customer policy details.
    """

    return {
        "policyId": policy_id,
        "type": "Vehicle Insurance",
        "status": "Active",
        "coverageDetails": "Accident Cover, Cashless Garage, Roadside Assistance",
        "expiryDate": "2027-01-15"
    }


def getClaimsStatus(claim_id):
    """
    Retrieve insurance claim status.
    """

    return {
        "claimId": claim_id,
        "status": "In Progress",
        "amount": 25000,
        "lastUpdate": "2025-05-10"
    }


def initiateClaim(policy_id):
    """
    Create a new insurance claim.
    """

    return {
        "status": "Claim Initiated",
        "claimId": "CLM12345"
    }


def getBenefitsInfo(policy_id):
    """
    Retrieve policy benefits.
    """

    return {
        "benefits": [
            "Accident Cover",
            "Cashless Garage",
            "Roadside Assistance"
        ]
    }


def renewPolicy(policy_id):
    """
    Renew an existing insurance policy.
    """

    return {
        "status": "Renewed",
        "validTill": "2028-01-15"
    }


def createCase(issue):
    """
    Create a customer support ticket.
    """

    return {
        "status": "Case Created",
        "ticketId": "T56789"
    }


def getProductCoverage(product_type):
    """
    Retrieve insurance product coverage details.
    """

    return {
        "productType": product_type,
        "coverage": [
            "Accident Cover",
            "Third Party Liability",
            "Cashless Garage",
            "Roadside Assistance"
        ],
        "eligibility": "Vehicle must be registered in India",
        "startingPremium": 4500
    }


def onBoardUser(customer_name, phone, dob, product_type, email, address):
    """
    Register a new insurance customer.
    """

    return {
        "status": "Success",
        "customerId": "C001",
        "policyId": "P101",
        "message": "Customer onboarded successfully."
    }


def requestUpdate(customer_id, request_type, new_value):
    """
    Submit a customer profile update request.
    """

    return {
        "requestId": "REQ1001",
        "status": "Submitted",
        "message": "Your update request has been received and is under review."
    }


def getRequestStatus(request_id):
    """
    Retrieve the status of an update request.
    """

    return {
        "requestId": request_id,
        "status": "Approved",
        "lastUpdated": "2026-07-11",
        "remarks": "Customer address updated successfully."
    }
```

---

## Notes

- These implementations are **mock services** and do not communicate with a production backend.
- All responses are predefined to simulate successful API execution during development and testing.
- The mock APIs were used to validate conversational flows, webhook integrations, and backend interactions within Google Dialogflow CX.
- In a production environment, these functions would be replaced with secure REST APIs connected to insurance databases and business services.
