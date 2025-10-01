---
title: Set up bank accounts (Russia)
description: Learn how to set up bank accounts for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/29/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.search.form: BankGroup, BankAccountTable
---

# Set up bank accounts (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to set up bank accounts for Russia in Microsoft Dynamics 365 Finance.

Before working in the **Bank management** workspace, you should complete the following procedures to ensure that you have the prerequisites needed for using bank accounts in Russian legal entities.

## Manually create a bank or update information for a bank

To manually create a bank or update information for a bank, follow these steps.

1. In Dynamics 365 Finance, go to **Cash and bank management** \> **Setup** \> **Bank groups**.
1. Select a bank or create a new one. 
1. Enter Russia-specific information for the bank.  
   - **BIC** – Bank identification code. 
   - **Corr. Bank account** – Corresponding bank account.
   - **Bank type** – Select either **Main**, **Foreign**, or **Branch**. If you select, **Foreign**, select a **Vendor account** on the **General** FastTab. If you select **Branch**, select a value in the **Main bank** field.
1. (Optional) Select the .docx template to use in the **Payment order in currency** field on the **Setup** FastTab. If defined, this will be the default template for the payment order in currency for all foreign bank accounts related to this bank.

> [!NOTE]
> Before defining a document template, create the templates as files and attach them to the record. You can determine if a document is attached by using the number indicator on the **Document attachment** symbol.

## Create banks by importing a list of banks

### Prerequisites

To fulfill the prerequisites, follow these steps.

1. In Microsoft Dynamics Lifecycle Services (LCS), import the **Bank BIC catalog (RU)** electronic reporting (ER) configuration file. Learn more in [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).
1. In Dynamics 365 Finance, go to **Cash and bank management** \> **Setup** \> **Cash and bank management parameters**.
1. On the **General** FastTab, in the **Import list of banks** fields group, in the **Import format configuration** field, select the **Bank BIC catalog (RU)** ER configuration.

### Import a list of banks

To import a list of banks, follow these steps.

1. In Dynamics 365 Finance, go to **Cash and bank management** \> **Setup** \> **Bank groups**.
1. Select **Load bank list** to open the **Import of data** dialog.

    > [!NOTE]
    > You can only update the bank list for marked states or for chosen banks.

1. In the upper pane of **Import of data** dialog, mark states for importing/updating all banks from the marked state.
1. In the lower pane of **Import of data** dialog, use the following buttons to select the banks included in the update:
    - **Select existing** - Select and update the banks that exist in the system.
    - **Select all** - Select and update all selected banks.
    - **Deselect all** - Clear all banks. 

## Create and configure a bank account

To create and configure a bank account, follow these steps.

1. In Dynamics 365 Finance, go to **Cash and bank management** \> **Bank accounts** \> **Bank accounts**.
1. Create a new bank account.
1. Complete all required fields. The following list includes some fields that might be required. 
    - **Bank account** (code)
    - **Bank account number**
    - **Main account** - This is the general ledger account that is used for posting.
    - **Currency**
    - **SWIFT code** 

    Learn more in [Bank management workspace](../../cash-bank-management/bank-management-workspace.md).

1. Specify and confirm the following Russia-specific information: 
    1. Select **Bank** in the **Bank groups** field.
    1. Confirm that the **BIC** and **Corr. Bank account** fields are correct. Also, confirm **Address** and **Contact information** on the respective FastTabs and update accordingly.
    1. In the **P/O numeration** field, define the number series for payment order generation.
    1. For bank accounts in foreign currency, you can also define .docx templates for generation of payment orders in paper format in the following fields: **Payment order in currency**, **Order template (currency sale)**, and **Order template (currency purchase)**. 

> [!NOTE]
> Before defining a document template, create the templates as files and attach them to the record. You can determine if a document is attached by using the number indicator on the **Document attachment** icon.

![Bank account.](../media/rus-bank-account.jpg)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
