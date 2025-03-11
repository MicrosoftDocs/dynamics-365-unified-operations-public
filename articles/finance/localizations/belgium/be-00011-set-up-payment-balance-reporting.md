---
title: Set up payment balance reporting (Belgium)
description: This article describes how to set up BLWI information in Belgium with Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/11/2025
ms.reviewer: johnmichalak
ms.search.region: Belgium
ms.search.validFrom: 2016-06-30
---

# Set up payment balance reporting (Belgium)

[!include [banner](../../includes/banner.md)]

This article describes how to set up Belgisch Luxemburgs Wissel Instituut (BLWI) information in Belgium with Microsoft Dynamics 365 Finance.

Use the following procedures to set up BLWI information for Belgium. These procedures were created using the USSI demo data company.

This functionality is available for legal entities that have their primary address in Belgium. Before you can complete this procedure, you must set up the registration ID for Belgium and enter the registration number that should be used to create the BLWI declaration.

## Set up a BLWI country/region group

To set up a BLWI country/region group, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Foreign trade \> BLWI country/region groups**.
1. Select **New**.
1. In the **Group ID** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Add**.
1. In the **Country/region** field, enter or select a value.
1. In the **Description** field, enter a value.
1. Select **Translations**.
1. In the **Language** field, enter or select a value.
1. Close the page.

## Set up BLWI currencies

To set up BLWI currencies, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Foreign trade \> BLWI currencies**.
1. Select **New**.
1. In the **Currency** field, enter or select a value.
1. Select the **Report in this currency** checkbox.
1. In the **Column number** field, enter a number.

## Set up BLWI parameters

To set up BLWI parameters, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Foreign trade \> BLWI parameters**.
1. In the **BLWI** field, select **Yes**. This parameter should be activated before you post customer/vendor transactions, so that the transactions are transferred to the payment balance.  
1. In the **Email** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Telephone** field, enter a value.
1. In the **Fax** field, enter a value.
1. In the **Check BLWI code on journals** field, select an option. Select the rule for checking that a payment purpose code is specified in documents. The available options are None, Warning, and Error. If a transaction has a customer/vendor that's located in a foreign country/region (that is, the country/region of the customer/vendor differs from the country/region of the legal entity), the transaction doesn't have an assigned payment purpose code, and the rule is set to **Warning** or **Error**, either a warning or error message is shown during posting. This validation is applied for all customer/vendor transactions except payment transactions.  
1. In the **Format mapping** field, enter or select a value. Prerequisite: You must first upload the BLWI format (BE) configuration for electronic reporting (ER) from Microsoft Dynamics Lifecycle Services (LCS).  

## Set up payment survey codes

To set up payment survey codes, follow these steps.

1. In Dynamics 365 Finance headquarters, go to **Tax \> Setup \> Foreign trade \> Payment survey codes**.
2. Select **New**.
3. In the **Survey code** field, enter a value.
4. In the **Month/Quarter** field, select an option.
5. In the **Calculation type** field, select an option. If you select the **Turnover in the Calculation type** option, the customer/vendor transactions posted during the reporting period are transferred to the payment balance, and the amount that's reported is the total amount of the posted transaction. If you select the **Balance** option, customer/vendor transactions that are open (not fully settled/closed) at the end of the reporting period are transferred to the payment balance, and the amount that's reported is the open (unsettled) amount of the posted transaction as of the end of the reporting period.  
6. In the **Description** field, enter a value.
7. In the **Summary country/region** field, enter a value.
8. Select **Add**.
9. In the **Central bank purpose code** field, enter or select a value.
10. Select the **Include payment** checkbox. Payment transactions aren't transferred to the payment balance survey by default. You must first activate the **Include payment** field for purpose codes.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
