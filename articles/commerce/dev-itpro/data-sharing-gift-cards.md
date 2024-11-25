---
# required metadata

title: Cross-company data sharing for gift cards
description: This article describes how to configure Microsoft Dynamics 365 Commerce to use Dynamics 365 Finance data sharing functionality across data areas to sync gift card data.
author: BrianShook
ms.date: 08/26/2022
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2022-06-20
ms.custom: 
  - bap-template
---

# Cross-company data sharing for gift cards

[!include [banner](../includes/banner.md)]

This article describes how to configure Microsoft Dynamics 365 Commerce so that it uses Dynamics 365 Finance data sharing functionality to sync gift card data. The data record sharing functionality can then be used to share data cross-company between two data areas. In this way, the Commerce internal gift table can share data between two company entities. For more information about Dynamics 365 Finance cross-company data sharing, see [Cross-company data sharing](/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing).

## Key terms

| Term | Description |
|---|---|
| Company | The legal entity in the Dynamics 365 Finance environment. |
| Gift card | The Dynamics 365 Commerce internal gift card product. |

## Prerequisites

Users must configure their environment for cross-company data sharing as described in [Cross-company data sharing](/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing).

**RetailGiftCardTable** must have the **DataSharingType** field set to **Duplicate** to enable duplicate record sharing (DRS) for the gift card table. For more information, see [Cross-company data sharing for developers](/dynamics365/fin-ops-core/dev-itpro/sysadmin/drs-srs-dev).

## Configure cross-company data sharing for gift cards

To configure cross-company data sharing for gift cards, follow these steps.

1. In Commerce headquarters, go to **System administration \> Setup \> Configure cross-company data sharing**.
1. On the Action Pane, select **New** to add a data sharing record.
1. In the **Name** field, enter a name for the data sharing record (for example, **Gift Cards**).
1. In the **Tables and fields to share** section, select **Add**.
1. In the **Share new table** dialog box, in the **Table name** field, enter **RETAILGIFTCARDTABLE** (the table for retail gift cards). The **Table label** field should automatically be set to **Gift card table**.
1. Ensure that the **Save data per company**, **Has unique index**, and **Not shared yet** checkboxes are all selected. Selection of these checkboxes triggers validations that are related to the data sharing functionality.
1. Select **Add table**. The **Gift card table (RetailGiftCardTable)** record should now appear under **Tables and fields to share**. Select the caret (^) symbol to view all the table fields that are automatically associated with the table for sharing.
1. In the **Companies which share the records in these tables** section, select **Add** to add a company to share data with.
1. In the row under **Company**, select a company in the drop-down list.
1. In the **Name** field, enter the company name.
1. Repeat steps 8 through 10 to add more company rows.
1. When you've finished adding company rows, on the Action Pane, select **Enable**.
1. You receive a warning message that states, "It is recommended to only perform this action during non-business hours. Any concurrent transaction operations will fail for tables in the policy. Do you want to continue?" Select **Yes** to agree.
1. You receive a warning message that states, "Would you like to copy all existing data across all shared companies now?" Select **Yes** to agree.

After you agree to both messages, tables will start to copy data across the configured companies. Balances that occur against one company gift card will then be visible to the other company.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
