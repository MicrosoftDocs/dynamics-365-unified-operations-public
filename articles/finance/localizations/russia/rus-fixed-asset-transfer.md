---
title: Transfer fixed assets (Russia)
description: Learn how to transfer a fixed asset in Microsoft Dynamics 365 Finance in Russia, including a process for transfering multiple assets.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Transfer fixed assets (Russia)

[!include [banner](../../includes/banner.md)]

You can transfer fixed assets from one location or person who is in charge to another location or person who is in charge. You can also transfer fixed assets between companies.

## Transfer multiple assets by using the Fixed asset transfer journal

Follow these steps to transfer a fixed asset or a group of fixed assets from one location or person in charge to another location or person in charge.

1. Select **Fixed assets (Russia) \> Journals \> Transfer journals \> FA transfer**.
2. Select **New**, and enter the required details.
3. Select **Lines** to open the **Transfer journal lines creation** dialog box.
4. Select **Filter** to open the **Assets** dialog box, where you can select the required criteria.
5. Select **OK** to transfer the details to the **Transfer journal lines creation** dialog box.
6. Select **OK** to open the **Lines of FA transfer journal** page.

    > [!NOTE]
    > In the journal, records are created for all assets or inventory assets that have values in the **Location** and **Previous person in charge** fields. The page header shows the information that is specified in the journal batch. You can add or delete lines on the **Lines of FA transfer journal** page as you require.

7. Select **Close**. Information about the asset transfer will be kept in the history.
8. Select **Print** to set the print options and print an invoice for the asset transfer.

## Transfer assets between companies

You can create individual transfer transactions to transfer assets to another company. If the companies are in separate databases, transfer transactions are created in the company that you're transferring the asset from, and receipt transactions are created in the company that that you're transferring the asset to.

### Adjust the value model settings to transfer an asset

Before you create fixed asset transfers between companies, you must adjust the settings of the value models.

1. Select **Fixed assets (Russia) \> Setup \> Value models**, and create a value model.
2. On the **Map** FastTab, in the **Company accounts ID** field, select the code for the company to transfer the asset to.
3. In the **Value model** field, select the value model number that corresponds to the value model number for the company account that you selected in the previous step.

### Transfer an asset to another company

1. Select **Fixed assets (Russia) \> Common \> Fixed assets**, and select the asset to transfer.
2. On the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Transference**.
3. In the **Date** field, enter the date of the transfer.
4. Optional: In the **Company accounts ID** field, enter the code for the company that is receiving the asset.
5. Optional: In the **Fixed asset** field, change the code for the asset.
6. If you selected a company to transfer the asset to, you can select the fixed asset inventory number that the asset will have in the receiving company after the transfer is completed. The status of this asset should be **Scheduled** or **Written off**.

    After a transference transaction is posted in the fixed assets journal (**Fixed assets (Russia) \> Journals \> FA journal**), the following information is automatically updated on the **Transference to another company** page:

    - On the **Overview** tab, the **Posted** check box is selected if the transference operation was posted for all value models.
    - On the **Value models** tab, the balance cost, book depreciation, and lifetime are updated for value models that the transference operation was posted for.

A record can also be automatically created on the **Transference to another company** page after you close the **Transference to another company** journal (**Fixed assets (Russia) \> Journals \> Transfer journals**). For information about how to create a record in the **Transference to another company** journal, see the [Transfer a group of fixed assets](#transfer-a-group-of-fixed-assets) section.

> [!NOTE]
> After you post a transfer journal, the fixed asset status is set to **Written off**. Additionally, in the receiving company, on the **Receipt from another company** page, the fields on the **Value models** tab are updated for the fixed asset that you specified on the **Transference to another company** page.

### Transfer a group of fixed assets

1. Select **Fixed assets (Russia) \> Journals \> Transfer journals \> Transference to another company**.
2. Select **New** to create a line, and then, in the **Date** field, enter the date of the asset transfer.
3. In the **Company accounts ID** field, enter the account ID of the company that is receiving the assets, if the company is in the same database.

    > [!NOTE]
    > The **Journal number** field is automatically filled in, based on the number sequence that is configured. However, you can manually enter a journal number.

4. Select **Lines**.
5. On the **Lines of FA transfer journal** page, create a line.
6. In the **Source** field, select the inventory number of the fixed asset that is being transferred.

    > [!NOTE]
    > Available assets have a status of **In operation**. The **Account name** field shows the name of the asset that is being transferred. If the receiving company is specified for the journal, the **Destination company** field shows the company name.

7. In the **Destination** field, select the asset number, in the receiving company, that corresponds to the asset that is being transferred.

    > [!NOTE]
    > Available assets have a status of **Scheduled** or **Written off**. The **Account name** field shows the account that the asset is transferred to, based on the value that you select in the **Destination** field.

8. Repeat steps 5 through 7 to create all additional lines that are required, and then close the page.
9. On the **Transference to another company** page, select **Close**. The **Posted** check box is selected, and information about the transfer is shown in the history of the fixed assets or inventory assets that are specified on the journal lines (**Transference to another company** page).
10. Select **Fixed assets (Russia) \> Journals \> FA journal**.
11. Select **Lines**, and enter the transference transactions on the journal lines. This process resembles the process for creating an acquisition transaction.

    > [!NOTE]
    > The date of the transaction on the **Fixed asset** page can't be earlier than the date when the transfer to another company was registered in the asset history. You must use a group transaction to create lines. Lines are automatically created for all fixed assets that have information about transfers to another company in the history.

12. Select **Validate \> Validate** to validate the journal.
13. Select **Post \> Post** to create the voucher and fixed asset transactions.
14. You can see an overview of all voucher and fixed asset transactions by using the inquiries. Go to **Fixed assets (Russia) \> Inquiries \> Transactions** or **Fixed assets (Russia) \> Inquiries \> Voucher transactions**.

### Receive a group of fixed assets from another company

You can register the receipt of several fixed assets or inventory assets at the same time.

1. Select **Fixed assets (Russia) \> Journals \> Transfer journals \> Receipt from another company**, and create a journal.
2. In the **Date** field, enter the date of the transfer of assets from the other company.
3. In the **Company accounts ID** field, enter the account ID of the company that the assets are being received from, if the company is in the same database.

    > [!NOTE]
    > The **Journal number** field is automatically filled in, based on the number sequence that is configured. However, you can manually enter a journal number.

4. Select **Lines**.
5. On the **Lines of FA transfer journal** page, create a line.
6. In the **Source** field, select the inventory number of the asset that is being received from the other company.

    > [!NOTE]
    > If you select an asset number in the **Source** field, and a full correspondence of value models has been set up between the transferring company and the receiving company, information is shown in the fields on the **Value models** tab. Otherwise, you must manually enter or modify the information.

7. In the **Destination** field, select the asset number, in the receiving company, that corresponds to the asset that is being transferred.
8. Repeat steps 5 through 7 to create all additional lines that are required.
9. Select **Create fixed asset**.

    > [!NOTE]
    > This button is available only if an asset number is shown in the **Source** field but no destination is selected. This situation can occur if the recipient isn't specified in the transfer transaction for the transfer of an asset to another company.

10. In the **Create fixed asset** dialog box, select the fixed asset group that the asset belongs to. Enter the inventory number if the field isn't automatically filled in.
11. Select **OK**. An asset record is created, and a destination is shown.

#### Automatically create lines

To automatically create lines on the **Receipt from another company** page, select **Create from FA transference journal**, and then follow these steps.

1. On the **Adding fixed assets from issue journals for another company** page, in the upper pane, select the journal. Then select **Copy journal** to copy all the information from the specified transfer journal to the receipt journal.
2. In the lower pane, select **Copy journal line** to copy individual lines of the transfer journal to the receipt journal.
3. On the **Receipt from another company** page, select **Close**. The information from the receipt is updated in the asset records.
4. Select **Fixed assets (Russia) \> Journals \> FA journal**.
5. Select **Lines**, and enter the receipt transaction on the journal lines. This process resembles the process for creating an acquisition transaction.

    > [!NOTE]
    > The date of the transaction on the **Fixed asset** page can't be earlier than the date when the receipt was registered in the asset history. You must use a group transaction to create lines. Lines are automatically created for all fixed assets that have information about receipts from another company in the history.

6. Select **Validate \> Validate** to validate the journal.
7. Select **Post \> Post** to create the voucher and fixed asset transactions.
8. You can see an overview of all voucher and fixed asset transactions by using the inquiries. Go to **Fixed assets (Russia) \> Inquiries \> Transactions** or **Fixed assets (Russia) \> Inquiries \> Voucher transactions**.

    > [!NOTE]
    > You can view the information about the transfer of assets between companies on the **Receipt from another company** page.

## Reverse fixed asset transfer transactions

By default, when you reverse transactions, the reversal date is equal to the original transaction date. However, you can specify a different reversal date.

1. Go to **Fixed assets (Russia)** > **Fixed assets**, and on the Action Pane, select **Value models**.
2. On the **FA value models** page, on the Action Pane, select **Transactions**.
3. On the **FA transactions** page, select and transaction and on the Action Pane, select **Reverse transaction**.
4. In the **Reverse transactions** dialog box, change the transaction reversal date as needed and then select **OK**. A transaction to reverse the original transaction is created and added to the **FA transactions** page.
5. Select **Voucher**, and on the **Voucher transactions** page, view the transactions in the ledger.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
