---
title: Test the Supplier Communications Agent (production ready preview)
description: Learn how to test the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management, for smooth implementation and optimal performance.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/27/2025
ms.custom:
  - bap-template
---

# Test the Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Learn how to test the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management.

The agent has two independent features:

- *Follow-up with vendors* (writing reminders)
- *Updates from vendors* (reading vendor emails).

Test the feature you need first.

If you plan to use both, start with *Follow-up with vendors* feature because it's easier to set up, configure, and test.

## Test the "Follow-up with vendors" (writing reminders) feature

Use the user interface to [set up the feature](supplier-com-agent-follow-up.md) to fit your needs and then test to make sure that the emails work as expected.

## Test the "Updates from vendors" (reading emails) feature

This feature needs more setup permissions, test email addresses, and multiple scenarios. Start small and then expand, as described in the following subsections.

### Phase 1: Forward some emails to a testing email address in a sandbox environment

This phase lets you test the smallest possible scope. Start with a test email address so you can test without risk. It doesn’t matter if you plan to use the purchaser’s email in production or a common mailbox for the purchasing department.

- Ask your Microsoft Exchange admin to create the test email address. 
- Connect that email address to the sandbox environment where you'll do the testing.
- Refresh your data (copy production data to the sandbox) or forward older emails so the system can match them.
- Forward emails in batches—for example, five emails at a time. Check results and note if there's anything unexpected, and continue until you have a good idea of how it performs.

### Phase 2: Forward emails from selected vendors

Now that you have a few emails available on your system, start working with messages from those vendors that you communicate with the most or that have the most confirmations that you want the agent to handle.

- Use the same setup as before, but this time auto-forward a set of emails from real vendor email addresses to the test address.
- Refresh data or import purchase orders and products before you do the test, especially if your testing should last for a few weeks. The agent can't match an email to a purchase order if the purchase order isn't in the system.

For this phase, you might want to involve one or more of your purchasers.

### Phase 3: Forward all vendor emails to sandbox

Create an auto-forwarding rule for all vendor emails to the testing address. Involve one or more of your purchasers if you haven't already.

### Phase 4: Use real email addresses in production

Now you're ready for the final test: testing in production. Set up the agent in production using real email addresses. Stop the agent from working in your sandbox.

Testing in production is safe. The feature doesn't interfere with standard business processes. At best, the agent does the work automatically. At worst, if the agent doesn't understand something correctly, the purchaser still needs to do it manually.

This is a production-ready preview feature. It has the quality of a generally available (GA) feature and you can go live with it. The reason it's not fully GA is that the agent is under continuous development. We keep it designated as a production-ready preview so we can continue improving it.

For this test, we recommend that you: 

- Have purchasers work with the agent to do their daily tasks.
- Start with just one or a few purchasers.
- Optionally filter messages from a few vendors to start small.
