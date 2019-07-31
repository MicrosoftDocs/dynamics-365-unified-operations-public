---
# required metadata

title: Preview features in Finance and Operations version 10.0.5 (August 2019)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 10.0.5. This version will be released in August.
author: tonyafehr
manager: AnnBe
ms.date: 07/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom:  
ms.dyn365.ops.version: Release 10.0.5

---
# Preview features in Finance and Operations version 10.0.5 (August 2019)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 10.0.5. This version will be released in August and has a build number of 10.0.xxx. For more information about version 10.0.5, see [Additional resources](whats-new-changed-10-0-5.md#additional-resources).

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 for Retail, see [Preview features in Dynamics 365 for Retail version 10.0.5](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/get-started/whats-new-10-0-5).

## Gender in currency declension for Eastern Europe 

You can now define the currency gender. 
On **Currecnies** page, click **Declension**. In the **Gender** field, select **Masculine**, **Feminine**, or **Neuter**. This parameter may have influence on declension of amount written in text in local language on Cash order. For example, amount 1,01 EUR is written in English text as *One euro 01 cent* on Cash order. When you set up **Gender** for EUR currency as **Neuter**, this amount will be translated to Czech language and written on Cash order as *Edno euro 01 cent*

For more information about existing functionality, see [Update how amounts are displayed on reports and documents](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/emea-amount-printing-forms).

## Cash Control (Public Sector)

Cash control lets you define a limit (threshold) to prevent transactions from being posted if no cash balance is available, or if the transaction will cause the balance to fall below the defined limit. Accounts payable vendor invoices and General ledger advanced ledger entries are validated when they are created, edited, and posted. If transaction posting will cause the related cash account's balance to be reduced below the limit that is defined for the account, the user receives an error message and must change the account to continue.

For more information, see [Cash Control](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/public-sector/cash-control).

## Forecast position distribution (Public Sector)

You can maintain financial dimension default templates for forecast positions by using the controls on the Financial dimensions FastTab of the Forecast position page. The grid in the upper part of the FastTab shows all the distribution lines together with their percentage. The lower part of the FastTab shows the forecast position's default dimensions.

You can validate whether the default dimensions for a forecast position are correct for your organization's chart of accounts. For any forecast position, on the Forecast position page, select Validate on the Action Pane to determine whether the setup of financial dimensions for that forecast position is valid. This validation is quick and can help you identify errors before you generate a budget plan from a forecast position. You can also validate many forecast positions at the same time on the Forecast positions list page.

For more information, see [Forecast position distribution](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/public-sector/forecast-positions).

## Journal unlock
A new button is available on the journal page to unlock a journal that has a status of "locked by system" set to yes. This unlock can be performed by an administrator of the system who has analyzed any executing batch jobs and confirmed this journal is no longer actively being processed by a batch job. This button is enabled by the feature named 'Journal Unlock button' in the feature management page. 

## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0.4, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=320385&dbType=3&qc=d5539716f56ccea45e2187c269570772af20e1f10a78371811220da6315a3c34).

### Platform update 28
Microsoft Dynamics 365 for Finance and Operations version 10.0.4 includes Platform update 28. To learn more about Platform update 28, see [Preview features in Finance and Operations platform update 28 (July 2019)](whats-new-platform-update-28.md).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
