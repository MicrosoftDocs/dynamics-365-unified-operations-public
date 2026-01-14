---
title: Audit file (XML Auditfile Financieel, XAF)
description: Learn how to set up and generate the Audit file for legal entities in the Netherlands in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/02/2026
ms.reviewer: johnmichalak
ms.search.region: Netherlands
ms.search.validFrom: 2016-06-30
ms.search.form: TaxEvatParameters_NL
---

# Audit file (XML Auditfile Financieel, XAF)

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the Audit file for legal entities in the Netherlands in Microsoft Dynamics 365 Finance.

This functionality is available for legal entities whose primary address is in the Netherlands.

## Set up Audit File Financial XAF 4.0 for the Netherlands

To set up the Audit File Financial XAF 4.0 for the Netherlands, follow these steps:

1. [Import Electronic reporting configurations.](#import)
2. [Configure RGS (ReferentieGrootboekSchema, standard chart of accounts)](#coa)

### <a name="import"></a>Import Electronic reporting configurations

To prepare Microsoft Dynamics 365 Finance to generate the Audit file, you must first import the following electronic reporting (ER) configurations.

| Number | ER configuration name         | Type                                 | Description |
|--------|-------------------------------|--------------------------------------|-------------|
| 1      | Audit file model              | Model                                | A model for the Audit file for Netherlands. |
| 2      | Audit File Financial XAF 4.0 in XML (NL) - starting January 1, 2026<br> Audit file (NL) - before December 31, 2025 | Format (exporting) | ER format for XML Auditfile Financieel, XAF. |

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that the configuration version introduces.

### <a name="coa"></a> Configure RGS (ReferentieGrootboekSchema, standard chart of accounts)

In the Audit File Financial XAF 4.0 for Netherlands, you must associate main accounts that you use in Finance with Dutch RGS (ReferentieGrootboekSchema, standard chart of accounts). Use the [consolidation account groups and additional consolidation accounts](../../budgeting/consolidation-account-groups-consolidation-accounts.md) functionality to create this association.

1. Create a [consolidation account group](../../general-ledger/tasks/create-consolidation-groups.md#create-a-consolidation-account-group). For example, create a group named **RGS**.
2. [Add accounts to the consolidation account group](../../general-ledger/tasks/create-consolidation-groups.md#add-accounts-to-consolidation-account-group). In the **Consolidation account** field, specify a standard account. This value is reported in the `<RGScode>` element of XAF 4.0 under the **company** \> **generalLedger** \> **ledgerAccount** node. In the **Consolidation account name** field, optionally specify the standard account name or description. This value isn't used in XAF 4.0.

## Generate the Audit file

To generate the Audit file, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Periodic tasks** \> **Audit file**.
2. In the **From date** field, enter a date. 
3. In the **To date** field, enter a date.
4. In the **Consolidation account group** field (support in "Audit File Financial XAF 4.0 in XML (NL)" ER format), select the name of the consolidation account group that you created and set up for Dutch RGS (ReferentieGrootboekSchema). This parameter is optionally required in Audit File Financial XAF 4.0 as of January 1, 2026.
5. In the **Format mapping** field, enter "Audit File Financial XAF 4.0 in XML (NL)" to report XAF 4.0 starting January 1, 2026, or "Audit file (NL)" to report XAF 3.2 before December 31, 2025.
6. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
