---
# required metadata

title: What's new or changed in Finance and Operations apps version 10.0.5 (October 2019)
description: This topic describes features that are either new or changed in Finance and Operations apps version 10.0.5. This version releases in October.
author: tonyafehr
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
ROBOTS: NOINDEX, NOFOLLOW
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom:  
ms.dyn365.ops.version: Release 10.0.5

---
# What's new or changed in Finance and Operations apps version 10.0.5 (October 2019)

[!include [banner](../includes/banner.md)]


This topic describes features that are either new or changed in Finance and Operations apps, including Microsoft Dynamics 365 Finance and Microsoft Dynamics 365 Supply Chain Management version 10.0.5. This version has a build number of 10.0.197. While the general availability date is in October, the new features are available for early release in August. For more information about version 10.0.5, see [Additional resources](whats-new-changed-10-0-5.md#additional-resources).


To learn about the new features and changes in the latest releases of Dynamics 365 Retail, see [What's new or changed in Dynamics 365 for Retail version 10.0.5](../../../commerce/get-started/whats-new-10-0-5.md).


## Revenue recognition

Revenue recognition allows you to define revenue prices and revenue schedules for multi-element sales of hardware, software, support, and subscriptions to fulfill US Generally Accepted Accounting Principles (GAAP) and International Financial Reporting Standards (IFRS) requirements.

- **Revenue prices** - Revenue prices can be defined on released products and then used to determine the price at which to recognize revenue. The revenue price can differ from the sale price that is offered to the customer.

- **Revenue schedules**- Revenue schedules determine the number of months for the revenue deferral. Options are available to create the schedule based on actual days of the month, splitting equally across the month, or based on a set number of occurrences.

- **Multiple sales order reallocation** - Reallocation allows the revenue price to be recalculated after a new sales order line is added to an invoiced sales order or to a new sales order. The new line will be reallocated if the additional item should be have been included in the original contractual agreement.

- **Workspace** - The new workspace is used to review the status of the revenues schedule records created for deferred revenue.

## Cancel bank reconciliation

Users will be able to cancel bank reconciliations in chronological order of reconciliation starting with the most recent. History is tracked to show when and by whom the reconciliation was reversed. This will prevent users from having to manually adjust journals to correct any errors that occurred during the periodic process.

## Create checks with a blank status on the Checks page

The **Checks** page is where you perform maintenance tasks on checks, such as creating new check numbers and deleting checks. When this feature is enabled, you cannot create checks with a blank status during the payment process, which results in wasted check stock.

## Reset workflow status for vendor invoices

You can use the Workflow history page to reset the workflow status to Draft. This page can be opened from the **Vendor invoice** page or by going to **Common > Inquires > Workflow**. To reset the workflow status to Draft, select **Recall**. You can also reset the workflow status to Draft by selecting the **Recall** action on either the **Vendor invoice** or **Pending vendor invoices** page. After the workflow status is reset to Draft, it becomes available for editing on the **Vendor invoice** page.

## Dual currency consolidation

This feature helps you control the currency (either the accounting or reporting currency) that is used as the transaction currency in the consolidation company. You can also automatically copy amounts from the source company to the consolidation company, if the currencies are the same.

- **Add the “Select consolidation amount from” control on the consolidate online form** - When this feature is enabled, the user can choose whether the accounting currency or the reporting currency from the source company will be used as the transaction currency in the consolidation company.

- **Directly copy amounts from the source company to the consolidation company if the currencies are the same** - When the feature is enabled, the accounting or reporting currency amounts from the source company will be copied directly to the accounting or reporting currency amounts in the consolidation company if either of the currencies are the same. The accounting and reporting currency amounts in the consolidation company are calculated using the exchange rate if neither of the currencies is the same.

## Gender in currency declension for Eastern Europe 

You can now define the currency gender. On **Currencies** page, select **Declension**. In the **Gender** field, select **Masculine**, **Feminine**, or **Neuter**. This parameter may have influence on declension of the amount written in text in local language on a Cash order. For example, if the amount of 1,01 EUR is written in English text as *One euro 01 cent* on a cash order, when you set up **Gender** for EUR currency as **Neuter**, this amount will be translated to Czech language and written on a cash order as *Edno euro 01 cent*.

For information about existing functionality, see [Update how amounts are displayed on reports and documents](../../../finance/localizations/emea-amount-printing-forms.md).

## Cash control (Public Sector)

Cash control lets you define a limit (threshold) to prevent transactions from being posted if no cash balance is available, or if the transaction will cause the balance to fall below the defined limit. Accounts payable vendor invoices and General ledger advanced ledger entries are validated when they are created, edited, and posted. If transaction posting will cause the related cash account's balance to be reduced below the limit that is defined for the account, the user receives an error message and must change the account to continue.

## Forecast position distribution (Public Sector)

You can maintain financial dimension default templates for forecast positions by using the controls on the **Financial dimensions** FastTab on the **Forecast position** page. The grid in the upper part of the FastTab shows all the distribution lines together with their percentage. The lower part of the FastTab shows the forecast position's default dimensions.

You can validate whether the default dimensions for a forecast position are correct for your organization's chart of accounts. For any forecast position, on the **Forecast position** page, select **Validate** on the Action Pane to determine whether the setup of financial dimensions for that forecast position is valid. This validation is quick and can help you identify errors before you generate a budget plan from a forecast position. You can also validate multiple forecast positions at the same time on the **Forecast positions** page.

## Deferred put
The deferred processing functionality lets warehouse workers continue to do other work while the put operation is processed in the background. Deferred processing is useful when many work lines must be processed and the worker can let that work be processed asynchronously. It's also useful when the server can have ad-hoc or unplanned increases in processing time, and the increased processing time might affect the user's productivity.

For more information, see [Deferred processing of warehouse work](/dynamics365/unified-operations/supply-chain/warehousing/deferred-put)

## Journal unlock
A new button is available on the journal page to unlock a journal that has a status of **Locked by system** set to Yes. This unlock can be performed by an administrator of the system who has analyzed any executing batch jobs and confirmed this journal is no longer actively being processed by a batch job. This button is enabled by the feature named **Journal Unlock button** on the **Feature management** page.

## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of version 10.0.5, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=348248&dbType=3&qc=71f7c009fafc56f21399d05a7062454208256c806b7f5c706a89f4452964c26e).

### Platform update 29
Version 10.0.5 includes Platform update 29. To learn more about Platform update 29, see [What's new or changed in Platform update 29 for Finance and Operations apps (October 2019)](whats-new-platform-update-29.md).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for Finance and Operations](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for Finance and Operations](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
