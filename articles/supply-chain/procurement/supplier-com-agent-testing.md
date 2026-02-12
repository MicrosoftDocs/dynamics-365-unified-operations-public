---
title: Test the Supplier Communications Agent (production ready preview)
description: Learn how to test the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management for smooth implementation and optimal performance.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/27/2026
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

Test the feature you need first. If you plan to use both features, start with *Follow-up with vendors* because it's easier to set up, configure, and test.

## Test the "Follow-up with vendors" (writing reminders) feature

Use the user interface to [set up the feature](supplier-com-agent-follow-up.md) to fit your needs. Then test to make sure that the emails work as expected.

## Test the "Updates from vendors" (reading emails) feature

The agent works by matching incoming vendor emails to existing purchase orders. Therefore, to test this feature, your test environment must have both:

- **Purchase orders** – Synchronize recent purchase orders from production to your test environment. For instructions, see [Synchronize purchase orders between production and test environments](#synchronize-purchase-orders-between-production-and-test-environments).
- **Vendor emails** – Forward or send test emails that reference those purchase orders. For instructions, see [Forward emails](#forward-emails).

### Synchronize purchase orders between production and test environments

When testing in a sandbox environment (Phase 1 or Phase 2 below), the agent needs purchase order data to match against vendor emails. You can export purchase orders from your production environment and import them into your test environment by using the Data management framework.

#### Export purchase orders from the production environment

Follow these steps in the production environment.

1. Go to **Data management**.
1. Create a new export project.
1. Select the **Purchase orders composite V3** entity.
1. Select the **XML-Element** format.
1. Create a filter by selecting the filter icon in the **Filter** column.
1. Add a range for the **Created date and time** field.
1. Set the filter value to `(DayRange(-14, 0))`. Modify the first argument (`-14`) to control how many days back to export. A higher value exports more data, which could exceed the import capacity of the test environment.
1. Run the export in batch mode.

#### Prepare the test environment (one-time setup)

To avoid number sequence conflicts when importing purchase orders, enable manual numbering for purchase orders in the test environment.

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
1. Select the **Number sequences** tab.
1. Find the number sequence that is used for purchase orders and navigate to it.
1. On the **General** FastTab, set **Manual** to *Yes*.

#### Import purchase orders into the test environment

Repeat these steps on a regular basis (for example, weekly) to keep the test environment up to date.

1. Go to **Data management**.
1. Create a new import project.
1. Select the **Purchase orders composite V3** entity.
1. Start the import in batch mode.

### Forward Emails

This feature requires more setup permissions, test email addresses, and multiple scenarios. Start small and then expand, as described in the following subsections.

#### Phase 1: Forward some emails to a testing email address in a sandbox environment

This phase lets you test the smallest possible scope. Start with a test email address so you can test without risk. It doesn't matter if you plan to use the purchaser's email in production or a common mailbox for the purchasing department.

- Ask your Microsoft Exchange admin to create the test email address.
- Connect that email address to the sandbox environment where you'll do the testing.
- Refresh your data (copy production data to the sandbox) or forward older emails so the system can match them.
- Forward emails in batches—for example, five emails at a time. Check results and note if there's anything unexpected, and continue until you have a good idea of how it performs.

#### Phase 2: Forward emails from selected vendors

Now that you have a few emails available on your system, start working with messages from those vendors that you communicate with the most or that have the most confirmations that you want the agent to handle.

- Use the same setup as before, but this time auto-forward a set of emails from real vendor email addresses to the test address.
- Refresh data or import purchase orders and products before you do the test, especially if your testing should last for a few weeks. The agent can't match an email to a purchase order if the purchase order isn't in the system. Collaborate with one or more of your purchasers if you haven't already.

For this phase, you might want to involve one or more of your purchasers.

### Phase 3: Use real email addresses in production

Now you're ready for the final test: testing in production. Set up the agent in production using real email addresses. Stop the agent from working in your sandbox.
Testing in production is safe. The feature doesn't interfere with standard business processes. At best, the agent does the work automatically. At worst, if the agent doesn't understand something correctly, the purchaser still needs to do it manually.

This is a production-ready preview feature. It has the quality of a generally available (GA) feature and you can go live with it. The reason it's not fully GA is that the agent is under continuous development. We keep it designated as a production-ready preview so we can continue improving it.

For this test, we recommend that you:

- Have purchasers work with the agent to do their daily tasks.
- Start with just one or a few purchasers.
- Optionally filter messages from a few vendors to start small.

### Phase 4: Expand the number of vendors in production

Keep adding more vendors to the configuration so you can gradually increase the value provided by the agent.
