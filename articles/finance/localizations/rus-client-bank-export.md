---
# required metadata

title: Client-Bank interface and reconciliation procedure
description: This article provides information about  user settings for electronic outgoing payments and the reconciliation procedure.
ms.date: 07/05/2022
ms.topic: article
ms.prod: 
author: akroshkina
ms.technology: 
manager: anayash

# optional metadata

#ms.search.form:
audience: IT Pro, Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.suite: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: 
# ms.search.industry: 
ms.author: anasyash
ms.dyn365.ops.version: 
ms.search.validFrom: 
---

# Client-Bank interface and reconciliation procedure

This article provides information about user settings for exporting electronic outgoing payments that are created in the payment journals using the Client-Bank system. You can use the Client-Bank interface to automatically reconcile bank payments and statement data instead of completing a manual reconciliation. Payment formats for a specific bank are customized using Electronic reporting (ER) configurations.

## Set up

### Import configurations

Before you start using Client-Bank functionality, import ER configurations from the Global repository of Configuration service.

1. In the Global repository, import the following configurations:

    - **Payment model mapping 1611**
    - **Payment model mapping to destination RU**
    - **Bank statement (RU)**
    - **Payment order (RU)**

    For more information, see [Import configurations from GR](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

2. Go to **Workspaces** > **Electronic reporting**.
3. In the **Configurations** section, select **Reporting configurations**.
4. On the Action Pane, select **Edit**.
5. In the navigation list, in the **Payment model** section, set the main payment model as the default. For example, select **Payment model mapping 1611**.
6. On the **Configurations** page, set **Default for model mapping** to **Yes**.
7. On the Action Pane, select **Save**.

### Set up kinds of documents

1. Go to **Cash and bank management** > **Setup** > **Payment order setup** > **Kinds of document**.
2. On the Action Pane, select **New**.
3. In **The code of document kind** field, enter the unique a two-digit code.
4. In the **Description** field, enter the description of the document.
5. In the **Document type** field, select one of the following:

    - **Pay document**
    - **Memorial order**
    - **Currency transfer**
    - **Currency sale**
    - **Currency purchase**

    ![Graphical user interface, application Description automatically generated.](media/a553a2c0e5cbc3e70cbe2cd20f9e7b70.png)

### Set up methods of payment for export

To set up a matching format to export a payment and the specified payment method, complete the following steps.

1. Go to **Accounts payable** > **Payment setup** > **Methods of payment**.
2. On the Action Pane, select **New** and enter information about the new method of payment.
3. In the **Payment status** field, select **Sent**.
4. In the **Payment type** field, select **Electronic payment**.
5. On the **General** FastTab, in the **Posting** section, in the **Account type** field, select **Bank**. 
6. In the **Payment account** field, select the account that was set earlier.
7. On the **File formats** FastTab, in the **File formats** section, in the **Export format** field, select the custom export format.

   > [NOTE!] 
   > If the drop-down menu is empty, on the **File formats** FastTab, select **Setup**. Select available formats and add them to the **Selected** column. On the Action Pane, select **Save**. Close this page and add a value to the **Export format** field.

8. In the **Generic electronic Export format** field, set **Enable** to **Yes**.
9. In the **Export format configuration** field, select the custom export format.
10. In the **Client-bank** section, set **Enable** to **Yes**.
11. In the **Export format** field, select the export format.

### Set up the exchange interface

The Client-Bank functionality uses **txt** format for export payments. You can customize electronic format. For more information, see [Formula designer in Electronic reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting-formula-designer.md).

By default, all downloaded payments are stored in the **Downloads** folder. To select a different location, see [Electronic reporting (ER) destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

## Operations in the Client-Bank functionality for export

### Create outgoing payments before export

Outgoing payments can be, payments to vendors, or the purchase, sale, or transfer of currency and cash-bank operations.
To create and set up outgoing payments, follow these steps.

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal** for payments to vendors.
2. Create and set up **Vendor payment journal**. For more information, see [Set up and process payment orders for Russia](rus-payment-order-settings-processing.md#create-payment-order-lines).
3. On the Action Pane, select **Lines**.
4. On the **List** tab, set the following fields:

    - In the **Date** field, select an operation date.
    - In the **Account** field, select a counteragent account.
    - In the **Debit** field, write the amount of payment.
    - In the **Currency** field, select currency payment code.
    - In the **Offset account type** field, select **Bank**.

5. On the **Payment** tab, set the following fields:

    - In the **Document type** section, in the **The code of document kind** field, select the code that was created earlier.
    - In the **Method of payment** field, select the payment method that corresponds to the payment. To successfully export a payment into the Client-Bank system, you must use the payment method set up earlier. The **Payment status**, **Offset account type**, and **Offset account** fields are filled automatically if they were set when creating the method of payment.

> [!NOTE]
> The **Offset account type** must be equal to **Bank**.

    - To set the parameters of the currency contract for which the currency is sold or purchased, enter or select a value in the **Payment specification**, **Payment ID**, and **Vendor account** fields.

6. On the **Bank** tab, set the following fields:

    - For currency transactions: In the **Bank** section, select a value in the **Bank transaction type** field.
    - For non-currency transactions: In the **Print payment order** section, in the **Payment documented on** field, select a counteragent account. For currency transactions, a transit account is used.

7. On the Action Pane, select **Save**.

### Export payments to the Client-Bank 

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**.
2. Mark the necessary lines.

   > [!NOTE] 
   > A separate export file is created for each bank account. If an error occurs, the system proceeds to processing lines for the next bank account.

3. On the Action Pane, select **Generate payments**.
4. In the **Generate payments** pane, select **Payment method**.
5. Fill in **Method of payment** and **Bank account** fields as were set earlier.
6. Enter or select a value in the **File name** field.
7. Select **OK** and then select **OK** again. The payment order is created.

    ![Graphical user interface, application, Word Description automatically generated.](media/98738a614030a0a814a8a380a6741d77.png)

### Cancel payment export

1. Go to **Cash and bank management** > **Periodic tasks** > **Third party bank** > **Exported payments**. You can see all exported payments or payments whose export was canceled. On the **Overview** tab you can view the following fields and field values:

    - **Document type**: The **The code of document kind** field from the payment journal.
    - **Account type**: **Vendor**
    - **Payment order number**: The **Check number** field from the vendor payment journal.
    - **Payment order date**: The **Date** field from the payment journal.
    - **Counteragent**: The **Account** field from the payment journal.
    - **Amount in transaction currency**: The **Debit** field from the payment journal.
    - **Currency**, **Method of payment**, and **Bank account** fields: From the corresponding payment journal lines.
    - **Payment order status** is **Created** for exported payments or **Rejected** for canceled exported payments.

    ![Graphical user interface, text, application Description automatically generated](media/326aac792acd49f2929b0752fc8501df.png)

2. On the **General** tab, in the **File** section, in the **Date and time** field, view the date and time when the payment was exported.
3. Select a payment line and on the Action Pane, select **Exported payments** > **Void payment order**. The **Payment order status** field changes to **Rejected**.
4. To open the source line in not-posted journal of payment, on the Action Pane, select **Exported payments** > **Journal line**.

### Registry of payment orders

= Go to **Accounts payable** > **Inquiries and reports** > **Payment** > **Payment order register**. The page shows the payment documents sent in electronic format or on paper. For general information about the **Registry of payment orders** page, see [Set up and process payment orders for Russia](rus-payment-order-settings-processing.md#review-registry-of-payment-orders).

    >[!NOTE] 
    > Currency transactions aren’t displayed on the **Registry of payment orders** page.

    ![Table Description automatically generated](media/6b61456744fff219f17d49ae14f5b633.png)

For payments exported to the Client-Bank system, on the **General** tab, in the **Client-Bank** section the following fields are filled in:

-   **Electronic payment** is set to **Yes**.
-   **Date and time**: the date and time when the payment was exported.

![Registry pf payment orders page.](media/d00a29d8ca1163cc8bbf98471d5a3162.png)
