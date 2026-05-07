---
title: ER Design domain specific data model
description: This article describes how to create a new Electronic reporting (ER) configuration that contains a data model for electronic payment documents.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, ERDataModelDesigner, ERDataModelContentsItemCreationDialog, ERDataContainerDescriptorReferenceSwitchDialog
---

# ER design domain specific data model

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains a data model for electronic payment documents. You use this data model as a data source when you create the format of the payment documents.

In this example, you create a configuration for sample company, Litware, Inc. You can perform these steps in any company because ER configurations are shared among companies. To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.

    Select the configuration provider for sample company, Litware, Inc. If you don't see this configuration provider, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure.  

1. Select **Reporting configurations**.

    You create a configuration that contains a data model for electronic payment documents. You use this data model as a data source when you create the format for the payment documents.    

## Create a new data model configuration

1. Select **Create configuration** to open the dialog.
1. In the **Name** field, type *Payments (simplified model)*.
1. In the **Description** field, type *Payment model configuration*.

    The active configuration provider is automatically entered here. This provider can maintain this configuration. Other providers can use this configuration, but can't maintain it.  

1. Select **Create configuration** to complete the configuration creation task.

## Create a data model

Create a new data model for the selected configuration. This configuration version has a status of Draft.  

1. Select **Designer**.

## Define the structure of a party participating in a payment process

1. Select **New** to open the drop dialog.
1. In the **Name** field, type `Party`.
1. Select **Add**.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type `Name`.
1. In the **Item type** field, select `String`.
1. Select **Add**.
1. In the **Find** field, type `Party`.
1. Select **Find previous**.

## Define the bank structure for this model

1. Select **New** to open the drop dialog.
1. In the **Name** field, type `Agent`.
1. In the **Item type** field, select `Record`.
1. Select **Add**.
1. In the **Description** field, enter `Financial institution (for instance, a bank) servicing an account for the party (debtor/creditor).`.

    Financial institution (for instance, a bank) servicing an account for the party (debtor/creditor).  

1. Select **New** to open the drop dialog.
1. In the **Name** field, type `Name`.
1. In the **Item type** field, select `String`.
1. Select **Add**.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type `SWIFT`.
1. Select **Add**.
1. In the **Description** field, enter `Bank identification code`.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type `RoutingNumber`.
1. Select **Add**.
1. In the **Description** field, enter `Routing number`.
1. Select **Find previous**.

## Define the bank account structure for this model

1. Select **New** to open the drop dialog.
1. In the **Name** field, type `Account`.
1. In the **Item type** field, select `Record`.
1. Select **Add**.
1. In the **Description** field, enter `Identification of an account of a party in a financial institution (for instance, a bank).`.

    Identification of an account of a party in a financial institution (for instance, a bank).  

1. Select **New** to open the drop dialog.
1. In the **Name** field, type `Currency`.
1. In the **Item type** field, select `String`.
1. Select **Add**.
1. In the **Description** field, enter `Currency code`.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type `Number`.
1. Select **Add**.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type `IBAN`.
1. Select **Add**.
1. In the **Description** field, enter `International bank account number`.

## Define the payment message structure for credit transfer payment type

1. Select **New** to open the drop dialog.
1. In **New node as a field**, enter *Model root*.
1. In **Name**, type *CustomerCreditTransferInitiation*.
1. Select **Add**.
1. In **Find**, type *CustomerCreditTransferInitiation*.
1. Select **Find previous**.
1. Select **New** to open the drop dialog.
1. In **Name**, type *MessageIdentification*.
1. Select **Add**.
1. In **Description**, enter *The point-to-point reference assigned by the instructing party (and sent to the next party) to identify a message.*.

    The point-to-point reference assigned by the instructing party (and sent to the next party) to identify a message.  

1. Select **New** to open the drop dialog.
1. In **Name**, type *ProcessingDateTime*.
1. In **Item type**, select *DateTime*.
1. Select **Add**.
1. In **Description**, enter *Date and time at which the payment message was created.*.
1. Select **New** to open the drop dialog.

    Define the payment transaction structure for this model.  

1. In **Name**, type *Payments*.
1. In **Item type**, select *Record list*.
1. Select **Add**.
1. In **Description**, enter *Payment lines of the current message*.
1. Select **New** to open the drop dialog.
1. In **Name**, type *Creditor*.
1. In the **Item type** field, select `Record`.
1. Select **Add**.
1. In **Description**, enter *Party to which an amount of money is due.*.
1. Select **Switch item reference**.
1. In the **Find** field, type `Party`.
1. Select **Find next**.
1. Select **OK**.
1. In **Find**, type *Payments*.
1. Select **Find next**.
1. Select **New** to open the drop dialog.
1. In **Name**, type *Debtor*.
1. Select **Add**.
1. In **Description**, enter *Party that owes an amount of money to the (ultimate) creditor.*.
1. Select **Switch item reference**.
1. In the **Find** field, type `Party`.
1. Select **Find next**.
1. Select **OK**.
1. Select **Find next**.
1. Select **New** to open the drop dialog.
1. In **Name**, type *Description*.
1. In the **Item type** field, select `String`.
1. Select **Add**.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type `Currency`.
1. Select **Add**.
1. In the **Description** field, enter `Currency code`.
1. Select **New** to open the drop dialog.
1. In **Name**, type *TransactionDate*.
1. In **Item type**, select *Date*.
1. Select **Add**.
1. In the **Description** field, enter *Transaction date*.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type *InstructedAmount*.  
1. In the **Item type** field, select *Real*.
1. Select **Add**.
1. In the **Description** field, enter *The amount of money to be moved between the debtor and creditor, before deduction of charges. The amount should be expressed in the currency as ordered by the initiating party.*

    The amount of money to be moved between the debtor and creditor, before deduction of charges. The amount should be expressed in the currency as ordered by the initiating party.  

1. Select **New** to open the drop dialog.
1. In the **Name** field, type *End2EndID*.
1. In the **Item type** field, select `String`.
1. Select **Add**.
1. In the **Description** field, enter *The unique identification assigned by the initiating party. This identification is passed on, unchanged, throughout the entire end-to-end chain.*
1. In the **Name** field, type *PaymentModel*.

    The **PaymentModel** name aligns with predefined interfaces of payment forms.  

1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
