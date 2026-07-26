# Authentication Workflow

## Overview

Authentication is performed before customers can access policy-related services. This ensures that only verified users can retrieve or modify insurance information.

## Authentication Steps

1. Customer provides registered mobile number.
2. Customer provides date of birth.
3. System validates customer details using the backend.
4. Additional verification questions are asked when required.
5. Successful authentication creates a secure session.
6. Failed authentication triggers retry logic.
7. After multiple failures, the conversation is escalated to a human agent.

## Security Features

- Mobile number verification
- Date of birth validation
- Verification questions
- Retry handling
- Human escalation after repeated failures
