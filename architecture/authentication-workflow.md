# Authentication Flow

## Overview

Before accessing any insurance service, every customer must complete a secure authentication process. The voice agent verifies the customer's identity using backend validation before allowing access to policy or claim information.

## Authentication Steps

1. Customer starts the call.
2. Voice agent welcomes the customer.
3. Customer provides registered mobile number.
4. Customer provides date of birth.
5. Voice agent asks verification questions.
6. Backend validates customer information using the `validateUser` API.
7. If authentication succeeds:
   - Customer profile is fetched.
   - Authentication status is stored.
   - Request proceeds to intent routing.
8. If authentication fails:
   - Retry count increases.
   - Maximum of three attempts are allowed.
   - After three failures, the conversation is escalated to a live support agent.

## Authentication Flow Diagram

<img width="1122" height="1402" alt="image" src="https://github.com/user-attachments/assets/51d8fdd3-d1d1-4242-aa32-2d6caa896ed2" />
