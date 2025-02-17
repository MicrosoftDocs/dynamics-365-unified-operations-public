---
title: Credit limit holds FAQ
description: Access answers to some frequently asked questions about credit checks, credit holds, and the warning and error messages that you might receive in Credit management.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 01/27/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2023-11-29
ms.search.form: 
ms.dyn365.ops.version: 10.0.35
---

# Credit limit holds FAQ

This article answers some frequently asked questions about credit checks, credit holds, and the warning and error messages that you might receive in Credit management.

To open the **Credit and collections parameters** page, go to **Credit and collections** \> **Setup** \> **Credit and collections parameters**. To set up the blocking rules, go to **Credit and collections** \> **Setup** \> **Credit management setup** \> **Blocking rules**.

For more information, see [Finance troubleshooting and FAQs](../finance-troubleshooting.md).

### After I upgrade to version 10.0.35 or later, the credit check is no longer working. However, it worked before the upgrade.

Blocking rules and credit management checkpoints are required to check the customer credit limit on a sales order. However, because of a bug in version 10.0.34 and earlier, the credit check worked even when blocking rules weren't set up. This bug is fixed in version 10.0.35 and later. Confirm that a blocking rule is set up for the credit limit that's used (or another blocking rule), and that the credit management checkpoints are selected on the **Credit and collections parameters** page. For more information about blocking rules, see [Credit holds for sales orders](cm-sales-order-credit-holds.md).

### I'm receiving a warning or error message on a sales order. However, the sales order isn't on credit hold, and I don't see it in the Credit management hold list.

You might receive the following message as either a warning (in yellow) or an error (in red). In both cases, the message is from earlier credit functionality.

> Sales order \<*order number*\> Credit limit exceeded Open balance: \<*balance amount*\> Current order: \<*order amount*\> New balance: \<*balance amount*\> Credit limit: \<*limit amount*\> Credit excess: \<*excess amount*\>

The following illustration shows an example of a warning message and an error message.

[![Screenshot that shows examples of sales order warning and error messages.](./media/SalesOrderWarning.png)](./media/SalesOrderWarning.png)

The type of message (error or warning) depends on the value of the **Message when exceeding credit limit** field on the **Credit limits** FastTab on the **Credit** tab of the **Credit and collections parameters** page. The message is shown because the **Check credit limit on sales order** option is set to **Yes** to specify that the credit limit should be checked on sales orders. 

These warning/error messages can't be suppressed, because they're the same messages that are used with free text invoices. They appear regardless of whether Credit management is enabled or disabled in Feature management. However, when Credit management is enabled, they can be ignored.

### If the warning/error message isn't used, how can I tell whether a sales order was put on credit hold?

When a sales order is sent to the Credit management hold list, the following posting message is shown in **Message details**:

> Order has been sent to credit management

[![Screenshot that shows an example of a Credit managment error message.](./media/CreditManagementError.png)](./media/CreditManagementError.png)

The order appears in the Credit management hold list at **Credit and collections** \> **Credit management hold list** \> **All credit holds** or **Open credit holds**.

### If I set a credit limit of 0.00 USD for a customer, does that customer have unlimited credit?

When Credit management is enabled in Feature management, a credit limit of 0.00 indicates that the customer has *no* credit. If the customer should have unlimited credit, set the **Unlimited credit limit** option to **Yes** on the **Credit and collections** FastTab of the customer record.

A credit limit of 0.00 indicates unlimited credit only when Credit management is disabled. This behavior is part of the "old" credit functionality.

### I set up credit management groups, but sales orders still aren't blocked based on the credit limit.

Sales orders are blocked if blocking rules and credit management checkpoints are set up, even when you use customer credit groups. For more information about how credit is calculated when credit limit groups are used, see [Credit limit scenarios](credit-limit-scenarios.md).

### Credit limit check skipped for intercompany sales orders 

Starting in Dynamics 365 Finance version 10.0.43, if the **Intercompany sales order exclusion from credit management** feature is enabled, the credit limit check for an intercompany sales order is skipped. The **Exclude from credit management** is enabled by default on the sales order header for intercompany sales order. If you want to enforce credit limit checks for specific orders, disable the exclusion property. 
