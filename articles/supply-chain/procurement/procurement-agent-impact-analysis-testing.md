---
title: Test impact analysis features (production-ready preview)
description: Procurement Agent impact analysis lets you see downstream effects of vendor change requests. Discover how to test it safely in sandbox and production environments.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/26/2026
ms.update-cycle: 180-days
ms.collection:
  - bap-ai-copilot
ms.custom: 
  - bap-template
---

# Test impact analysis features (production-ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Impact analysis helps you understand how vendor change requests affect downstream orders, such as production, sales, and transfer orders, before you take action. This article describes four ways to test impact analysis, depending on whether you want to test with or without supplier communications, and whether you're using a sandbox or production environment:

- **Forward actual vendor emails** to a testing email address in your sandbox environment.
- **Use actual vendor emails** in your production environment.
- **Use the Add vendor messages functionality** in your sandbox or production environment to test without setting up a complete email pipeline.
- **Simulate a purchase order change** in your sandbox or production environment without using supplier communications.

Choose the approach that best matches your current setup and testing goals.

## Test impact analysis with supplier communications

### Test with supplier communications by forwarding actual vendor emails to a testing email address in your sandbox environment

If you're testing supplier communications in your sandbox environment, you can enable impact analysis to see the impact of forwarded change requests. This testing approach corresponds to the supplier communications testing phases *Phase 1* and *Phase 2* outlined in [Test the "Updates from vendors" (reading emails) feature](procurement-agent-supplier-com-testing.md).

### Test with supplier communications on actual vendor emails in your production environment

If you're already using supplier communications in production, you can see impact analysis running on live change requests that you receive and use up-to-date planning data. This testing approach corresponds to the supplier communications testing phase *Phase 3* outlined in [Test the "Updates from vendors" (reading emails) feature](procurement-agent-supplier-com-testing.md), and is the optimal way to test impact analysis with supplier communications.

### Test with supplier communications using the *Add vendor messages* functionality in your sandbox or production environment without a complete email setup

Instead of testing impact analysis on actual change request emails you receive from vendors, use the *Add vendor messages* functionality as described in [Try out the *updates from vendors* feature without a complete email setup (production-ready preview)](procurement-agent-supplier-com-try-out.md). You can write a sample email from one of your vendors or you can copy and paste a real email you received from a vendor. Ensure the message communicates a change request to at least one purchase order line.

When you select **Save**, it takes a few minutes for supplier communications and impact analysis to review the message. Select **Refresh** to update the page, after which the email queue in the left-hand navigation pane of the **(Preview) Emails from vendors** workspace updates to show the new message. The message is labeled a *Change request* and shows a status of *Analyzing impact*. Select **Refresh** again to see the result of the impact analysis, which is shown as *Has impact* or *No impact*. Learn more about navigating and interpreting the impact analysis results in [Review impact of purchase order changes from vendors](procurement-agent-impact-analysis-review-changes.md).

### Testing impact analysis with supplier communications in sandbox vs production

Impact analysis can only find the affected downstream orders when planning data is current. This requirement can cause problems when you test impact analysis with supplier communications in a sandbox environment. If planning data is outdated, you might not find downstream orders such as production, sales, and transfer orders for the purchase order referenced in the incoming email.

You can avoid the risk of a blank result by testing impact analysis with supplier communications in a production environment. In this case, you can use actual vendor emails and up-to-date planning data to see the impact of incoming change requests. Impact analysis doesn't take any action on your behalf—it only runs on incoming change requests that you configure to trigger it. Learn more in [Configure sources that automatically trigger impact analysis](procurement-agent-impact-analysis-setup-wizard.md#trigger-impact-analysis).

If you want to test in a sandbox environment, consider refreshing data immediately before testing and verify that the items on the test purchase order are linked to demand orders such as sales, production, or transfer orders. Check this condition on the **Net requirements** page. If you don't want to refresh data, you can create test demand orders and link them to the purchase order you want to test before you run impact analysis. If you use this approach, remember to rerun planning before trying out impact analysis for the test order.

## Test impact analysis without supplier communications using the simulation capability in your sandbox or production environment

You can test impact analysis without supplier communications by simulating a date and quantity change to a purchase order. Learn more in [Simulate whether purchase order changes have impact](procurement-agent-impact-analysis-simulation.md).

Ensure that the item on the purchase order for which you're simulating a change is linked to downstream demand in **Net requirements**. If you manually add linked orders such as sales orders, remember to rerun planning before running the simulation.
