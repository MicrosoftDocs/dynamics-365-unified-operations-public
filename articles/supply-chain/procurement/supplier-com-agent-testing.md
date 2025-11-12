---
title: Test the Supplier Communications Agent (production ready preview)
description: Learn how to effectively test the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management, ensuring smooth implementation and optimal performance.
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

This article provides advice for how to test the Supplier Communications Agent.

The agent has two indepependent features, *Follow-up with vendors* (writing reminders) and *Updates from vendors* (reading vendor emails). Test the feature you need first.

If you plan to use both, start by testing the *follow-up with vendors* feature because it's easier to set up, configure, and test.

## Test the "Follow-up with vendors" (writing reminders) feature

To test this feature, use the user interface to [set up the feature](supplier-com-agent-follow-up.md) to fit your needs and then test to make sure that the emails work as expected.

## Test the "Updates from vendors" (reading emails) feature second

This feature requires more setup in terms of permissions, test email addresses, and multiple scenarios. Start from the smallest scope and then expand, as described in the following subsections.

### Phase 1: Forward some emails to a testing email address in a sandbox environment

This phase lets you test the smallest possible scope. Regardless of whether you use the purchaser's email when you go to production or use a common mailbox for the purchasing department where the vendors write to, start by using a test email address so you can test without any risk.

Ask your Microsoft Exchange admin to create the test email address. Then connect that email address to the sandbox environment where you will do the testing.

To make sure that the system matches the emails, refresh your data (copy your production data to the sandbox). Alternatively, you could forward older emails so the system matches them.

Forward a few emails so you can see that the connection is set up correctly and can evaluate the results from the agent. You can forward emails in batches—for example, forward five emails, see the results, note if there's anything unexpected, and continue until you have a good idea of how it performs.

### Phase 2: Forward certain vendors' emails to a testing email address in your sandbox environment

Now that you have a few emails available on your system, start working with messages from those vendors that you communicate with the most or that have the most confirmations that you want the agent to handle.

Use the same setup as before, but this time auto-forward a set of emails from a real vendor email address to the testing email address that you set up.

Remember to do a data refresh or import purchase orders and products before you do the test, especially if your testing should last for a few weeks. The agent can't match an email to a purchase order if the purchase order isn't in the system.

For this phase, you might want to involve one or more of your purchasers.

### Phase 3: Forward all vendor emails to sandbox

Now forward all of your vendor emails to the testing email address. Create an auto-forwarding rule for all emails to the testing email.

For this phase, involve one or more of your purchasers if you didn't already.

### Phase 4: Use real email address in production

Now you're ready for the final test: testing in production. Set up the agent in production using real email addresses. You can stop the agent from working in your sandbox.

Although it might sound counterintuitive to test in production, this feature doesn't interfere with standard business processes, so it's completely safe to test in production. In the best case, the agent does the work the purchaser would do manually. In the worst case, the agent doesn't understand something correctly, so the purchaser still needs to do it manually.

This is a production-ready preview feature, which means it has the quality of a generally available (GA) feature and you can go live with it. The reason it's not fully GA is that the agent is under continuous development. We keep it designated as a production-ready preview so we can continue to implement improvements in the short term.

For this test, we recommend that purchasers work with the agent to do their daily work. You might want to start with just one or a few purchasers. You might even filter to include messages from just a few vendors if you want to start small.
