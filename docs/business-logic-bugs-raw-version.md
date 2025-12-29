___
### 1 - Workflow / Step Bypass

**Category:** Workflow / Step Bypass

**Description:** The system allows a user to bypass steps, because the system does not validate the previous steps to ensure that the user has completed them.

**Broken Invariant:** The step may be skipped if the previous steps are not validated and system trusts client input.

**Example Flow:**
Many of us receive some type of "club/loyalty points" for purchases from grocery stores and gas stations. 
Suppose a user was able to start a transaction linked to their account and then after points have been added to their club/loyalty account cancel out of the transaction or remove items from their "basket" and tender. 
In this case the system either should not apply points/credits to the account until it is tendered or points/credits should be "rolled back" if the point/credit increment does not match the final tender. 
With this in mind, an attacker may start transactions and cancel them to build their point levels without actually buying anything.

**Why scanners miss it:** Vulnerability scanners often miss because they focus on technical flaws, not how the app works.
___
### 2 - State Desynchronization
Category: 
Description: 
Broken Invariant: 
Example Flow: 
Why scanners miss it: 
___
### 3 - Limit / Quota Bypass

**Category:** Limit / Quota Bypass

**Description:** The system allows business actions to be performed out of the time limit quota

**Broken Invariant:** The system should deny out of limit requests

**Example Flow:**
1. User opens a cart with products
2. User applies infinity coupons
3. System calcs all coupons together
4. Price become almost 0
5. The invariant is violated: price go down via applying all coupons together

**Why scanners miss it:** This issue cannot be detected by automated scanners because all requests are valid, no malformed input is involved, and detecting the flaw requires understanding of business workflow dependencies and cart state rather than request analysis 
___
### 4 - Price / Value Manipulation
Category: 
Description: 
Broken Invariant: 
Example Flow: 
Why scanners miss it: 
___
### 5 - Replay Attacks
Category: 
Description: 
Broken Invariant: 
Example Flow: 
Why scanners miss it: 
___

### 6 - Concurrency / Race Conditions

**Category:** Concurrency / Race Conditions

**Description:** Race Conditions occur when websites process requests concurrently without adequate safeguards. This can lead to multiple distinct threads interacting with the same data at the same time, resulting in a "collision" that causes unintended behavior in the application. A race condition attack uses carefully timed requests to cause intentional collisions and exploit this unintended behavior for malicious purposes.

**Broken Invariant:** A user must never be able to perform same request with already applied action

**Example Flow:**
1. User apply multiple coupons
2. more than 1 coupon are applied
3. The invariant is violated: the same bonus is applied more than 1 time

**Why scanners miss it:** 
The issue cannot be detected by automated scanners because all requests are valid, and difference may be seen only by person
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




