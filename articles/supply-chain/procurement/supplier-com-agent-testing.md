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

If you determine that Supplier Communications can help your company, based on the experience of previous customers and our own internal testing at Microsoft, use the following recommendations to smooth your testing journey and make the best of it.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

## Test the "Follow-up with vendors" (writing emails) feature first

Follow-up with vendors (writing reminders) and Updates from vendors (reading vendor emails) are independent features. Therefore, it makes sense that you test what you need first.

If you would benefit from both features or want to know how they work, start by testing the *follow-up with vendors* feature. It's easier to set up, easier to configure, and easier to test.

Simply set up the agent from the UI to fit what you want to follow up on and test that the emails are like you expect.

## Test the "Updates from vendors" (reading emails) feature second

This feature requires more setup in terms of permissions, test email addresses, and multiple scenarios. We suggest the following steps starting from the smallest scope to then expand.

### Phase 1: Forward some emails to a testing email address in sandbox

The smallest possible scope: no matter if you use the purchaser's email when you go to production or use a common mailbox for the purchasing department where the vendors write to, start with a testing email address. This approach lets you test without any risk.

Ask your Exchange admin to create a test email address. Then connect that email address to the sandbox environment where you will be testing.

To make sure that the emails are matched to the system, you need to refresh your data (copy the production data into sandbox). Or alternatively, forward older emails so they are matched. Note that in sandbox, a flight makes it possible to also match with invoiced purchase orders for testing, but this feature doesn't apply in production.

Forward some emails so you see the connection is correctly set up and evaluate the results from the agent. You can forward emails in batches; for example, forward five emails, see the results, note if there's anything unexpected, and continue until you get a hold of how it performs.

### Phase 2: Forward certain vendors' emails to a testing email address in sandbox

Now that you have a few emails, get started with the set of vendors that you communicate with the most or that have more confirmations that you want the agent to handle.

Use the same setup as before, but this time auto-forward a set of emails from the real procurement email address to the testing email address.

Remember to do a data refresh or import purchase orders and products before you do the test, especially if your testing spans over a few weeks. The agent can't match an email to a purchase order in the system if the purchase order isn't in the system.

For this step, you might want to involve one or more of the purchasers.

### Phase 3: Forward all vendor emails to sandbox

Now forward all vendor emails to the testing email address. Create an auto-forwarding rule for all emails to the testing email.

For this part, involve one or more of your purchasers if you haven't done so already.

### Phase 5: Use real email address in production

Now you're ready for the final test: testing in production. Set up the agent in production by using the real email address. You can stop the agent from working in sandbox.

Although it might sound counterintuitive to test in production, this feature doesn't interfere with standard business processes, so it's completely safe to test in production. In the best case, the agent does the work the purchaser would do manually. In the worst case, the agent doesn't understand something correctly, so the purchaser still needs to do it manually.

This is a production-ready preview feature, which means it has the quality of a generally available (GA) feature and you can go live with it. The reason it's not fully GA is that the agent is a fast moving area that we want to improve further in a short timeframe, so we keep it designated as a production-ready preview so we can make those changes.

For this test, we recommend that purchasers work with it to do their daily work. You might want to start with one or a few purchasers. You might even filter to some vendors if you want to start small.
