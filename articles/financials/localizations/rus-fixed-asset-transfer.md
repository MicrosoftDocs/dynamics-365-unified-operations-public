---
# required metadata

title: Transfer fixed assets (Russia)
description: This topic explains how to transfer a fixed asset in Microsoft Dynamics 365 for Finance and Operations in Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 12/18/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Transfer fixed assets (Russia)

[!include [banner](../includes/banner.md)]

You can transfer fixed assets from one location or person who is in charge to another location or person who is in charge. You can also transfer fixed assets between companies.

## Transfer multiple assets by using the Fixed asset transfer journal

Follow these steps to transfer a fixed asset or a group of fixed assets from one location or person in charge to another location or person in charge.

1. Select **Fixed assets (Russia) \> Journals \> Transfer journals \> FA transfer**.
2. Select **New**, and enter the required details.
3. Select **Lines** to open the **Transfer journal lines creation** dialog box.
4. Select **Filter** to select the required criteria in the **Assets** dialog box.
5. Select **OK** to transfer the details to the **Transfer journal lines creation** dialog box.
6. Select **OK** to open the **Lines of FA transfer journal** page.

    > [!NOTE]
    > In the journal, records are created for all assets or inventory assets that have values in the **Location** and **Previous person in charge** fields. The page header shows the information that is specified in the journal batch. You can add or delete lines on the **Lines of FA transfer journal** page as you require.

7. Select **Close**. Information about the asset transfer will be kept in history.
8. Select **Print** to set the print options and print an invoice for the asset transfer.

## Transfer assets between companies

You can create individual transfer transactions to transfer assets to another company. If the companies have separate databases, transfer transactions are created in the company that you're transferring the asset from, and receipt transactions are created in the company that that you're transferring the asset to.

### Adjust the value model settings to transfer an asset

Before you create fixed asset transfers between companies, you must adjust the settings of the value models.

1. Select **Fixed assets (Russia) \> Setup \> Value models**, and create a value model.
2. On the **Map** FastTab, in the **Company accounts ID** field, select the code for the company to transfer the asset to.
3. In the **Value model** field, select the value model number that corresponds to the current account for the company.

### Transfer an asset to another company

1. Select **Fixed assets (Russia) \> Common \> Fixed assets**, and select the asset to transfer.
2. On the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Transference**.
4. In the **Date** field, enter the date of the transfer.
5. In the **Company accounts ID** field, enter the code for the company that is receiving the asset, if this step is required.
6. In the **Fixed asset** field, change the code for the asset, if a change is required.

    > [!NOTE]
    > After you specify the company that is receiving the asset, you can select the inventory number that corresponds to the asset after the transfer. The possible statuses of the assets are **Scheduled** and **Written off**. Assets that have a status of **Written off** can be returned after a transfer only if you selected a company in the **Company** field.

    After a transfer transaction in the fixed assets journal is posted, the **Posted** field on the **Transference to another company** page is updated. The ledger accounts of the receiving company are also updated to acknowledge the transaction.

7. Select **Transfer journal** to show the transfer journal that is used to transfer the asset, if the journal was created and closed. If the journal wasn't created, you can manually enter the document number and date.

    When a transfer transaction in the fixed assets journal is posted, information is shown on the **Value models** tab of the **Transference to another company** page. This information can't be changed. The number of lines on the **Value models** tab must equal the number of models that the transaction was posted for.

    The value model, balance cost, and book depreciation for the asset that was transferred are shown, together with the period that the asset was used in before the transfer.

8. Select **Fixed assets (Russia) \> Journals \> Transfer journals \> Transference to another company**.
9. Select **Lines**.
10. Enter the transfer transaction on the lines of the journal.

    > [!NOTE]
    > The date of the transaction in the fixed assets journal can't be earlier than the date when the transfer was registered in the asset history.

11. Select **Close** to post the journal. If the transaction included all value models, the status of the asset is **Written off**.

    > [!NOTE]
    > On the **Receipt from another company** page, the fields in the grid and on the **Value models** tab are updated for the asset record. When you transfer an asset to another company, the material asset types in the records for the asset that is being transferred and accepted aren't automatically verified. You must verify that information in the **Type** field on the **General** tab of the **Fixed assets** page.

### Transfer groups of fixed assets

1. Select **Fixed assets (Russia) \> Journals \> Transfer journals \> Transference to another company**.
2. On the **Overview** tab, press **Ctrl+N** to create a line, and then, in the **Date** field, enter the date of the asset transfer.
3. In the **Company accounts ID** field, enter the account ID for the company that is receiving the assets, if the company is in the same database.

    > [!NOTE]
    > The **Journal number** field is filled in automatically, based on the number sequence that is configured. However, you can manually enter a journal number.

4. Select **Lines**.
5. On the **Lines of FA transfer journal** page, create a line.
6. In the **Source** field, select the inventory number of the fixed asset that is being transferred.

    > [!NOTE]
    > Available assets have a status of **In operation**. The **Account name** field shows the name of the asset that is being transferred. If the receiving company is specified for the journal, the **Destination company** field shows the company name.

7. In the **Destination** field, select the asset number that corresponds to the asset that is being transferred, in the receiving company.

    > [!NOTE]
    > Available assets have a status of **Scheduled** or **Written off**. The **Account name** field shows the account that the asset is transferred to, based on the value that you select in the **Destination** field.

8. Repeat steps 5 through 7 to create all additional lines that are required, and then close the page.
9. On the **Transference to another company** page, select **Close**. The **Posted** check box is selected, and information about the transfer is shown in the history of the fixed assets or inventory assets that are specified on the journal lines.
10. Select **Fixed assets (Russia) \> Journals \> FA journal**.
11. Select **Lines**, and enter the transfer transactions on the journal lines. This process resembles the process for creating an acquisition transaction.

    > [!NOTE]
    > The date of the transaction on the **Fixed asset** page can't be earlier than the date when the transfer to another company was registered in the asset history. You must use a group transaction to create lines. Lines are automatically created for all fixed assets that have information about transfers to another company in the history.

12. Select **Validate \> Validate** to validate the journal.
13. Select **Post \> Post** to create the transactions in the ledger and in fixed assets.

### Receive a group of fixed assets from another company

You can register the receipt of several fixed assets or inventory assets at the same time.

1. Select **Fixed assets (Russia) \> Journals \> Transfer journals \> Receipt from another company**, and create a journal.
2. In the **Date** field, enter the date of the transfer of the assets from the other company.
3. In the **Company accounts ID** field, enter the account ID for the company that is receiving the assets, if the company is in the same database.

    > [!NOTE]
    > The **Journal number** field is filled in automatically, based on the number sequence that is configured. However, you can manually enter a journal number.

4. Select **Lines**.
5. On the **Lines of FA transfer journal** page, create the lines.
6. In the **Source** field, select the inventory number of the asset that is being received from the other company.

    > [!NOTE]
    > If you select an asset number in the **Source** field, and a full correspondence of value models has been set up between the transferring company and the receiving company, information is shown in the fields on the **Value models** tab. Otherwise, you must manually enter or modify the information.

7. Select **Create fixed asset**.

    > [!NOTE]
    > This button is available only if an asset number is shown in the **Source** field, but no destination is selected. This situation can occur if the recipient isn't specified in the transfer transaction for the transfer of an asset to another company.

8. In the **Create fixed asset** dialog box, select the FA group that the asset belongs to. An inventory number is automatically assigned to the fixed asset or inventory asset.
9. Select **OK**. An asset record is created, and a destination is shown.
10. On the **Lines of FA transfer journal** page, select **Create from FA transference journal** to automatically create lines on the **Receipt from another company** page.
11. On the **Adding fixed assets from issue journals for another company** page, in the upper pane, select the journal. Then select **Copy journal** to copy all the information from the specified transfer journal to the receipt journal.
12. In the lower pane, select **Copy journal line** to copy individual lines of the transfer journal to the receipt journal.
13. On the **Receipt from another company** page, select **Close**. The information from the receipt is updated in the asset records.
14. Select **Fixed assets (Russia) \> Journals \> FA journal**.
15. Select **Lines**, and enter the receipt transaction on the journal lines. This process resembles the process for creating an acquisition transaction.

    > [!NOTE]
    > The date of the transaction on the **Fixed asset** page can't be earlier than the date when the receipt was registered in the asset history. You must use a group transaction to create lines. Lines are automatically created for all fixed assets that have information about receipts from another company in the history.

16. Select **Validate \> Validate** to validate the journal.
17. Select **Post \> Post** to create the transactions in the ledger and in fixed assets.

    > [!NOTE]
    > You can view the information about the transfer of assets between companies on the **Receipt from another company** page.
