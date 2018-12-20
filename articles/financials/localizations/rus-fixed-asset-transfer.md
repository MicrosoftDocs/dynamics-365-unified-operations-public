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

You may transfer fixed assets from one location (person in cahrge) to another location (person in charge) or transfer fixed assets between companies. 

## Transfer multiple assets using the Fixed asset transfer journal 

Use these steps to transfer a fixed asset of fixed asset group from one location and/or person in charge to another location and/or person in charge.

1.  Click **Fixed assets (Russia) > Journals > Transfer journals > FA transfer**.
2.  Click **New** then enter the required details.
3.  Click **Lines** to open the **Transfer lines creation** page.
4.  Click **Select** to select the required criteria on the **Assets** page.
5.  Click **OK** to transfer the details to the **Transfer lines creation** page.
6.  Click **OK** to open the **Lines of FA transfer journal** page.
    
    > [!NOTE]
    > Records are created in the journal for all assets or inventory assets that have entries in the **Location** and **Previous person in charge** fields. The form header shows the information specified in the journal batch. Where applicable, you can add or delete lines on the **Overview**> tab.</P>

7.  Click **Close**. Information about the asset transfer will be kept in history.
8.  Click **Print** to set the print options and print an invoice for the asset transfer.


## Transfer assets between companies 

You can create individual transfer transactions to transfer assets to another company. If the companies have separate databases, transfer transactions are created in the company that you are transferring an asset from, and receipt transactions are created in the company that that you are transferring the asset to.

## Adjust the value model settings to transfer an asset

Before you create fixed assets transfers between companies, you must adjust the settings of the value models.

1.  Click **Fixed assets (Russia) > Setup > Value models** and create a new value model.
2.  On the **Map** FastTab, in the **Company accounts ID** field, select the company code that the asset will be transferred to.
3.  In the **Value model** field, select the value model number that corresponds to the current account for the company.

## Transfer an asset to another company

1.  Click **Fixed assets (Russia) > Common > Fixed assets** and select the asset to be transferred.
2.  Click **History** \> **Transference**.
4.  In the **Date** field, enter the date of the transfer.
5.  In the **Company accounts ID** field enter the code for the company receiving the asset, if necessary.
6.  In the **Fixed asset** field, modify the code for the asset, if necessary.
    
    > [!NOTE]
    > After you select the company that is receiving the asset, you can select the inventory number that corresponds to the asset after the transfer. The statuses of the assets are **Scheduled** and **Written off**. Assets with a **Written off** status can be returned after transfer only if you have selected a company in the **Company** field.

7.  The **Posted** field in the **Transference to another company** page is updated after a transfer transaction in the fixed assets journal is posted. The ledger accounts of the receiving company are updated to acknowledge the transaction.
    
8. Click **Transfer journal** button to display the transfer journal used to transfer the asset, if the journal was created and closed. If the journal was not created, you can enter the document number and date manually.
    
 9. Information on the **Value models** tab is displayed when posting a transfer transaction in the fixed assets journal. This information cannot be modified. The number of lines displayed on the **Value models** tab must be equal to the number of models that the transaction was posted for.
    
 10. The value model, balance cost, and book depreciation for the asset that was transferred are displayed, along with the period that the asset was used prior to the transfer.

11.  Click **Fixed assets (Russia) > Journals > Transfer journals > Transfer to another company**.
12.  Click **Lines**. Enter the transfer transaction in the lines of the journal.
    
    > [!NOTE]
    > The date of the transaction in the fixed assets journal cannot be earlier than the date that the transfer was registered in the asset history.

13. Click **Close** button to post the journal. If the transaction included all value models, the status of the asset is **Written off**.     
    > [!NOTE]
    > In the **Receipt from another company** page, the fields on the list page and **Value models** tabs are updated for the asset record. When you transfer an asset to another company, the material asset types in the records for the asset being transferred and accepted is not verified automatically. You must verify that information in the **Type** field on the **General** tab of the **Fixed assets** page.

## Transfer groups of fixed assets

1.  Click **Fixed assets (Russia) > Journals > Transfer journals > Transference to another company**.
2.  On the **Overview** tab, press CTRL+N to create a new line, and then in the **Date** field, enter the date for the asset transfer.
3.  In the **Company accounts ID** field, enter the account ID for the receiving company, if the company shares the same database.
    
    > [!NOTE]
    > The journal number is based on the configured number sequence. However, you can enter it manually.


4.  Click **Lines**.
5.  In the **Lines of FA transfer journal** page create a new line.
6.  In the **Source** field, select the fixed asset inventory number that is being transferred.
    
    > [!NOTE]
    > Available assets have an **In operation** status. The name of the asset being transferred is displayed in the **Account name** field. If the receiving company is specified for the journal, its name is displayed in the **Destination company** field.

7.  In the **Destination** field, select the asset number of the receiving company that corresponds to the asset that is being transferred.
    
    > [!NOTE]
    > Available assets have a **Scheduled** or **Written off** status. The account that the asset is transferred to is displayed in the **Account name** field based on your entry in the **Destination** field.

8.  Create the required number of lines and close the form.
9.  Click **Close** in the **Tranference to another company** page. The **Posted** check box will be selected, and information about the transfer will be displayed in the history of the FA/IAs specified in the journal lines.
10. Post the transfer transaction in the FA journal.

## Receive a group of fixed assets from another company 

You can register the receipt of several fixed assets or inventory assets at the same time. 

1.  Click **Fixed assets (Russia) > Journals > Transfer journals > Receipt from another company** and create a new journal.
2.  In the **Date** field, enter the date of the transfer of the assets from the other company.
3.  In the **Company accounts ID** field, enter the account ID of the company that is receiving the assets, if this company is in the same database.
    > [!NOTE]
    > A journal number is displayed in the **Journal number** field, based on the configured number sequence. You can also enter the journal number manually.

4.  Click **Lines** and create the lines on the **Lines of FA transfer journal** page.
6.  In the **Source** field, select the inventory number of the asset being accepted from the other company.
 
    > [!NOTE]
    > If you have selected an asset number in the **Source** field and a full correspondence of value models has been set up between the transferring and accepting companies, then information in the fields on the **Value models** tab are displayed. Otherwise, you must enter or modify the information manually.

7.  Click **Create fixed asset**.
  
    > [!NOTE]
    > This button is available only if an asset number is displayed in the **Source** field, but no destination is selected. This may occur if the recipient is not specified in the asset transfer transaction to another company.

8.  On the **Create fixed asset** page, select the FA group that the asset belongs to. An inventory number for the fixed asset or inventory asset will be assigned automatically.
9.  Click **OK**. An asset record will be created and a destination will be displayed.
10. On the **Lines of FA transfer journal** page, click **Creating from FA transference journal** to automatically create lines on the **Receipt from another company** page.
11. Select the journal on the upper pane of the **Adding fixed assets from issue journals for another company** page, and then click **Copy journal** to copy all the information from the specified transfer journal into the receipt journal.
12. In the lower pane of the page, click **Copy journal line** to copy individual lines of the transfer journal into the receipt journal.
13. On the **Receipt from another company** page, click **Close**. The information from the receipt will be updated in the asset records.
14. Click **Fixed assets (Russia) > Journals > FA journal**.
15. Click **Lines** and enter the receipt transaction in the journal lines. This process is similar to creating an acquisition transaction.
    
    > [!NOTE]
    > The date of the transaction in the **Fixed asset** form cannot be earlier than the date when the receipt was registered in the asset history. You must use a group transaction to create lines. Lines will be automatically created for all fixed assets for which history information about receipt from another company has been specified.



16. Click **Validate > Validate** to validate the journal.
17. Click **Post > Post** to create the transactions in the ledger and in fixed assets.
    

    > [!NOTE]
    > You can view the information about the transfer of assets between companies on the **Receipt from another company** page.

