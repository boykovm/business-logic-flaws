___
### Category: Workflow / Step Bypass

**Description**  
The system allows business actions to be performed out of the intended order because it assumes that users will follow the predefined workflow, but does not explicitly enforce step dependencies.

**Broken Invariant**  
A business step must never be executed unless all required previous steps have been successfully completed.

**Example Flow**
1. User starts a purchase transaction linked to a loyalty account.
2. System awards loyalty points before the transaction is finalized.
3. User cancels the transaction or removes items before payment.
4. Loyalty points remain credited despite no completed purchase.
5. The invariant is violated: rewards are granted without a finalized transaction.

**Why scanners miss it**  
This issue cannot be detected by automated scanners because all requests are valid, no malformed input is involved, and detecting the flaw requires understanding of business workflow dependencies and transaction state rather than request-level analysis.
___
### Category: Limit / Quota Bypass

**Description**  
The system allows a user to perform a business action more times than intended because it assumes that usage limits will be respected, but does not strictly enforce them as a core business rule.

**Broken Invariant**  
A user must never be able to perform a limited business action more than the allowed number of times.

**Example Flow**
1. User is allowed to claim a promotional bonus once per account.
2. System grants the bonus after a successful claim.
3. User repeats the same action by replaying or slightly modifying the request.
4. System grants the bonus multiple times.
5. The invariant is violated: the bonus is issued more times than allowed.

**Why scanners miss it**  
This issue cannot be detected by automated scanners because all requests are valid, no malformed input is involved, and detection requires tracking business-level usage counters and understanding intended limits rather than analyzing individual requests.
___
### Category: Replay Attacks

**Description**  
The system allows a previously valid business action to be executed multiple times because it does not enforce action uniqueness or one-time execution as a business rule.

**Broken Invariant**  
A business action that is intended to be executed only once must never be successfully processed more than once.

**Example Flow**
1. User requests a password reset and receives a reset link.
2. The system processes the password reset when the link is used.
3. The user reuses the same reset link after the password has already been changed.
4. The system processes the request again.
5. The invariant is violated: a one-time action is executed multiple times.

**Why scanners miss it**  
This issue cannot be detected by automated scanners because all requests are valid, no malformed input is involved, and detecting the flaw requires tracking action state and understanding one-time business semantics rather than analyzing individual requests.
___
### Category: Concurrency / Race Conditions

**Description**  
The system allows a business action to be executed concurrently, resulting in an inconsistent or impossible business state that would not occur if the actions were processed sequentially.

**Broken Invariant**  
A business resource must never be consumed more times than it actually exists.

**Example Flow**
1. A user initiates a refund for a completed order.
2. The system validates that the order is refundable.
3. The user sends two refund requests at the same time.
4. Both requests are processed concurrently and pass validation.
5. The system issues two refunds for the same order.
6. The invariant is violated: a single refundable order results in multiple refunds.

**Why scanners miss it**  
This issue cannot be detected by automated scanners because all requests are valid, no malformed input is used, and exploiting the flaw requires precise timing and understanding of business state transitions rather than request-level analysis.
___

[//]: # (### 7 - Trusting Client-Controlled State)

[//]: # (Category:)

[//]: # (Description:)

[//]: # (Broken Invariant:)

[//]: # (Example Flow:)

[//]: # (Why scanners miss it:)

[//]: # (___)

[//]: # (### 8 - Broken Business Assumptions)

[//]: # (Category:)

[//]: # (Description:)

[//]: # (Broken Invariant:)

[//]: # (Example Flow:)

[//]: # (Why scanners miss it:)

[//]: # (___)

[//]: # (### 9 - Privilege Escalation via Flow)

[//]: # (Category:)

[//]: # (Description:)

[//]: # (Broken Invariant:)

[//]: # (Example Flow:)

[//]: # (Why scanners miss it:)

[//]: # (___)

[//]: # (### 10 - Missing or Undefined Invariants)

[//]: # (Category:)

[//]: # (Description:)

[//]: # (Broken Invariant:)

[//]: # (Example Flow:)

[//]: # (Why scanners miss it:)

[//]: # (___)




