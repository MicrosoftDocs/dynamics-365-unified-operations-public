---
# required metadata

title: Cross-company data sharing for gift cards
description: This topic describes how to configure Microsoft Dynamics 365 Commerce to use Microsoft Dynamics 365 Finance data sharing functionality across data areas for syncing gift card data.
author: BrianShook
ms.date: 08/23/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2022-06-20

---

# Cross-company data sharing for gift cards

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes how to configure Microsoft Dynamics 365 Commerce to use Microsoft Dynamics 365 Finance data sharing functionality to synchronize gift card data. The data record sharing functionality can then be used to share data cross-company between two data areas, which enables the Commerce internal gift table to share data between two company entities. For more information about Dynamics 365 Finance cross-company data sharing, see [Cross-company data sharing](/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing).

## Key terms

| Term | Description |
|---|---|
| Company | The legal entity within the Dynamics 365 Finance environment. |
| Gift card | The Dynamics 365 Commerce internal gift card product. |

## Prerequisites

Users must configure their environment for cross-company data sharing as described in [Cross-company data sharing](/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing).

The **RetailGiftCardTable** must have the **DataSharingType** set to "Duplicate", which enables duplicate record sharing (DRS) for the gift card table. For more information, see [Cross-company data sharing for developers](/dynamics365/fin-ops-core/dev-itpro/sysadmin/drs-srs-dev).

## Configure cross-company data sharing for gift cards

To configure cross-company data sharing for gift cards, follow these steps.

1. In headquarters, go to **System administration \> Setup \> Configure cross-company data sharing**.
1. On the action pane, select **+New** to add a new data sharing record.
1. Under **Name**, enter a name for the data sharing record (for example, "Gift Cards").
1. In the **TABLES AND FIELDS TO SHARE** section, select **+Add**.
1. In the **Share new table** dialog box, under **Table name**, enter "RETAILGIFTCARDTABLE" (the table for retail gift cards). The value of **Table label** should now be **Gift card table**.
1. Ensure that the **Save data per company**, **Has unique index**, and **Not shared yet** checkboxes are all selected. These are validations that will occur with the data sharing functionality.
1. Select **Add table**. The **Gift card table (RetailGiftCardTable)** record should now appear under **TABLES AND FIELDS TO SHARE**. Selecting the caret symbol will display all the table fields automatically associated with the table for sharing.
1. In the **COMPANIES WHICH SHARE THE RECORDS IN THESE TABLES** section, select **+Add** to add a company to share data across.
1. In the row under **Company**, select a company from the drop-down list.
1. Under **Name**, enter the company name.
1. To add additional company rows, repeat steps 8-10.
1. When finished adding company rows, on the action pane select **Enable**. The following two warning dialog boxes will appear that need to be agreed to:

    - "It is recommended to only perform this action during non-business hours. Any concurrent transaction operations will fail for tables in the policy. Do you want to continue?"
    - "Would you like to copy all existing data across all shared companies now?"

1. After agreeing to both questions, tables will begin to copy data across the configured companies. Balances occurring against one company gift card will then be visible to the other company.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module]../(add-checkout-module.md)

[Payment module](../payment-module.md)
