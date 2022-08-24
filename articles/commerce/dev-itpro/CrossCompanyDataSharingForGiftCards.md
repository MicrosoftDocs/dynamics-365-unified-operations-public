---
# required metadata

title: Cross-company data sharing for gift cards
description: This topic reviews the capability to use data sharing functionality in Finance and Operations for syncing gift card data between two Data Areas.
author: BrianShook
ms.date: 07/12/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom:
ms.dyn365.ops.version: AX 7.0.1

---

# Cross-Company data sharing for gift cards

This topic provides an overview of the Microsoft Dynamics 365 Commerce usage of the Finance and Operations (F&O) data sharing functionality across Data Areas for gift cards. Data Record Sharing can be used to share data between two data areas, also referred to as cross-company, to enable the Commerce (Internal) gift table to share data between two company entities. More information about F&O cross-company data sharing can be found at [this article](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing).

## Key terms

| Term | Description |
|---|---|
| company | The legal entity within the Dynamics Finance and Operations environment |
| gift card | The Dynamics 365 Commerce internal gift card product and |



## Prerequisites
Users must configure their environment for cross-company data sharing as described in the F&O [cross-company data sharing article](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/cross-company-data-sharing).

The RetailGiftCardTable will need the 'DataSharingType' set to "Duplicate". This will enable Duplicate Record Sharing (DRS) for the Gift Card Table. Additional details can be found in the following [cross-company data sharing for developers](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/drs-srs-dev) article.

## Configure cross-company data sharing for Gift Cards
In Headquarters, navigate to **Navigation pane > Modules > System administration > Setup > Configure cross-company data sharing**.

From this page:
- Click **New** to add a new data sharing record
- Give the data sharing record a **Name** (example: 'Gift Cards')
- Once a name is provided, under the **Tables And Fields To Share** section, click the **Add** button.
- The **Share new table** dialogue will show, enter the **Table name** for retail gift cards: **RETAILGIFTCARDTABLE** (note: **Table label** should show as 'Gift card table').
- Ensure **Save data per company**, **Has unique index**, and **Not shared yet** values are all selected. These are validations that will occur with the data sharing.
- Click **Add table**

The Gift card table record should now show in the **Tables and Fields to Share** section of the page. Dropping down the context will show all the table fields automatically associated to the table for sharing.

Now under the **Companies Which Share the Records In These Tables** section of the page, click **Add**, adding a row for the companies to share data across.

When ready, proceed by clicking **Enable**.

When enabling, two warning dialogues will appear that need to be agreed to:

- "It is recommended to only perform this action during non-business hours. Any concurrent transaction operations will fail for tables in the policy. Do you want to continue?"
- "Would you like to copy all existing data across all shared companies now?"

Once verifying, the tables will begin to copy data across the configured companies. Balances occurring against one company gift card will be visible to the other company.




## Additional resources

- [Payments FAQ](dev-itpro/payments-retail.md)
- [Checkout module](add-checkout-module.md)
- [Payment module](payment-module.md)
