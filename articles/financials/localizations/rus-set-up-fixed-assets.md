---
# required metadata

title: Set up fixed assets (Russia)
description:
author: ShylaThompson
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up fixed assets (Russia)

[!include [banner](../includes/banner.md)]

## Set up fixed asset value models 

You define a value model so that you can create fixed asset transactions in the general ledger for accounting functions, such as tax and business transactions. You can also create sub-models and depreciation groups for each value model.

Use this procedure to set up value models for fixed assets.

1.  Click **Fixed assets** \> **Setup** \> **Value models**.

2.  Press CTRL+N to create a new value model.

3.  In the **Value model** field, enter the code for the value model. In the **Name** field, enter the name of the value model.

4.  In the **Currency** field, select the currency code for the fixed asset value model.

5.  In the **Round-off** field, enter the value that is used to round amounts.

6.  In the **Posting profile** field, select the posting profile that is used for the fixed asset transactions.

7.  In the **Posting profile (Shortage)** field, select the posting profile that is used to write off fixed assets.

8.  In the **Posting layer** field, select a posting layer for value model transactions, from the following options:
    
      - **Current** − The value model is used for all general business transactions and corrections.
    
      - **Operations** – The value model is used for unique business transactions and corrections that are part of the periodic financial reporting for internal purposes.
    
      - **Tax** − The value model is used for tax accounting purposes.
       
        > [!NOTE]
        > A separate posting profile must be configured for the tax value model, because the value of the fixed asset tax account is based on off-balance accounts.</P>

9.  Click the **FA value submodels** FastTab to create sub-models or derived models for the value model.

10. In the **Value model** field, select a derived model for the value model.

11. In the **Transaction type** field, select the type of transaction that the derived model is associated with.

12. Click **Depreciation groups** to define depreciation groups for the value model. 

## Set up fixed asset posting profiles 

You can set up posting profiles for fixed assets. Posting profiles define the ledger accounts that are used in the value model for each fixed asset transaction.

1.  Click **Fixed assets** \> **Setup** \> **Fixed asset posting profiles**.

2.  On the **Overview** tab, press CTRL+N to create a new fixed asset posting profile.

3.  In the **Posting profile** field, enter the name of the posting profile.

4.  In the **Description** field, enter the description of the posting profile.

5.  On the left pane, in the **Select** field, select any one of the following options:
    
      - **Depreciation** – Calculation of depreciation of a fixed asset.
    
      - **Depreciation revaluation** – Revaluation of depreciation calculated for a fixed asset.
    
      - **Major repairs** – Conducting major repairs for a fixed asset.
    
      - **Putting into operation** – Putting a fixed asset into operation.
    
      - **Cost revaluation** – Revaluate the cost of a fixed asset.
    
      - **Leaving (sale)** – Disposal sale of the fixed asset.
    
      - **Leaving (dismantlement)** – Disassembly of a fixed asset.
    
      - **Partial take-down** – Partial disposal of a fixed asset.
    
      - **Currency cost revaluate** – Revaluation of a fixed asset based on currency cost.
    
      - **Currency depreciation revaluate** – Revaluation of depreciation calculated for a fixed asset in currency.
    
      - **Others** – Other fixed asset transactions.

6.  On the **Ledger accounts** tab, in the **Groupings** field, select the grouping used for the posting profile from the following options:
    
      - **Table** – Select this option to retrieve fixed asset data (value) from the table.
    
      - **Group** – Select this option to retrieve a defined depreciation group from the fixed asset group.
    
      - **All** – Select this option for all fixed asset transactions.
    
      - **Accounting** – Select this option to retrieve a defined value model.

7.  In the **Account/Group number** field, select the value model, group, or fixed asset object that the posting profile will be used for.

8.  In the **Ledger account** and **Offset account** fields, select the account number (debit) and the offset account (credit) for the transactions.

9.  Click **Options** and then click **Leaving (sale)** or **Leaving (dismantlement)** to open the **Sales** form or the **Dismantlement** form.

10. Press CTRL+N to create a new line.

11. In the **Valid for** field, select the grouping that will be used for the posting profile from the following options:
    
      - **Table** – Select this option to retrieve fixed asset data (value) from the table.
    
      - **Group** – Select this option to retrieve a defined depreciation group from the fixed asset group.
    
      - **All** – Select this option to for all fixed asset transactions.
    
      - **Accounting** – Select this option to retrieve a defined value model.

12. In the **FA relation** field, select the value model, group, or fixed asset object that will be used for the posting profile.

13. In the **Post value** field, select the amount to post to the specified account.

14. In the **Sale value type** field, select the type of amount that will be posted from the following options:
    
      - **All** – Any amount
    
      - **Loss** – The amount of loss
    
      - **Gain** – The amount of gain

15. In the **Ledger account** and **Offset account** fields, select the account numbers of the ledger account (debit) and the offset account (credit) for the transactions.

16. Select the **Storno** check box if you have to create a rental repayment transaction as a reversal transaction.

17. Press CTRL+S or close the forms.

## Set up fixed asset parameters 

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Parameters**.

2.  In the **Base value model** and **Tax value model** fields, select the value models for accounting and tax business functions, respectively.

3.  In the **Minimal depreciation** field, enter the minimum depreciation amount when depreciating a fixed asset with the **Reducing remainder** method.

4.  Select the **Allow multiple putting into operation** check box to enter multiple acquisitions.
    
    > [!NOTE]
    > If this check box is selected, you can register multiple acquisition transactions for a fixed asset. This allows you to register changes in the cost of the asset over time.

5.  Select the **Require reasons for asset changes** check box if a reason must be entered to explain changes in depreciation.

6.  Select the appropriate reason codes and move them from the **Not required** list to the **Required** list.

7.  Select the **Autonumeration FA** check box to activate automatic numbering.

8.  Select the **Barcode equals FA number** check box to automatically assign bar codes for fixed asset numbers.
    
    > [!NOTE]
    > If this check box is selected, a bar code number that is the same as the fixed asset number will be automatically generated for the fixed asset and displayed on the **Fixed assets** page.

9.  Select the **Barcodes autonumeration** check box to activate automatic numbering of bar codes with a number series.
    
    > [!NOTE]
    > This check box is not activated, if **Barcode equals FA number** check box is selected.

10. In the **Round-off** field, enter the value by which transaction amounts must be rounded for accounting purposes.

11. In the **Posting profile** field, select the default posting profile to be used if no posting profile is specified for the value models.

12. In the **Language** field, select a language for the fixed asset documents.

13. In the **Reservation** field, select **Manual**, **Automatic**, or **Explosion** to specify the type of reservation of items during assembly or disassembly of a fixed asset.

14. Click the **Tax reporting** tab, and then, in the **Sales tax code** field, select values for **Assessed tax**, **Transport tax**, and **Land tax**.

15. In the **Compression** field, select the level of compression from the following options:
    
      - **Tax** – When you create a fixed asset tax journal in the ledger, the detailing of the journal lines is generated according to the tax codes.
    
      - **Total** – When you generate transactions in the fixed asset tax journal in the ledger, the total of the transactions is generated without detailing according to the tax codes.

16. On the **Document** tab in the **Document location** field, select the folder where the fixed asset documents are to be saved.

17. On the **Financial dimensions** tab, select the financial dimension codes for the fixed asset transactions.

18. On the **Document types** tab, select a number series for the various types of fixed asset documents.

19. On the **Number sequence code** tab, select a number series for the various fixed asset references, such as **FA number**, **Bar code**, **FA revaluation**, **FA inventory**, **FA transfer**, **Writing off on lifetime**, and **Assessed tax register journal number**.

20. Press CTRL+S or close the form.

## Set up fixed asset groups 

Fixed asset groups are defined to group fixed assets. By defining fixed asset groups, you accomplish the following goals:

  - Simplify the setup of fixed assets and posting profiles for fixed assets.
  - Simplify the creation of queries and reports.
  - Create a template, so that common information is copied by default into the records of new and similar fixed assets that are acquired by the company.

Use the **FA groups** form to define fixed asset groups for working clothes and special rigging accounting. To each group that you define, you assign an appropriate type that is specified in the **Type of group** field. You can also use the **FA group value models** form to set up value models for the defined fixed asset groups, and specify the duration of the wear or usage period of an asset.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **FA groups**.

2.  Press CTRL+N to create a new fixed asset group.

3.  In the **FA group** field, enter the code for the fixed asset group. In the **Name** field, enter the name of the fixed asset group.

4.  In the **Type of group** field, select **Fixed assets**, **Working clothes**, **Special rigging**, or **NVFA** (not valuable fixed asset) as the type of fixed asset group.

5.  Select the **Autonumeration FA** check box to generate a fixed asset number automatically when you create fixed assets for the group in the **Fixed assets** form.

6.  In the **FA autonumbering sequence** field, select a number series for automatic number generation.

7.  In the **VAT refunding** field, select the start date for refunding value-added tax (VAT) for the fixed assets. Select one of the following options:
    
      - **Acquisition date** – Start refunding VAT from the acquisition date.
    
      - **Depreciation run date** – Start refunding VAT from the date of depreciation.

8.  Select the **Barcodes autonumeration** check box to generate bar codes automatically for the fixed assets in the group.

9.  In the **Barcode autonumeration sequence** field, select a number series for automatic bar code generation.

10. Click **Value models** to open the **FA group value models** form.

11. In the **Value model** field, select a value model for the fixed asset group.

12. In the **Depreciation group** field, select a depreciation group for the fixed asset group.
   
    > [!NOTE]
    > <P>When you create a fixed asset for a specific fixed asset group, the value model and depreciation group that you define in this form are displayed by default in the <STRONG>Value models</STRONG> form and cannot be changed.</P>

13. Select the **Service life by rate** check box to specify the wear or usage period for the asset, based on the lifetime that is specified during the issue process in the **Working clothes/Special rigging/NVFA issue journal** form. If you do not select this check box, the usage period is determined by the depreciation group.
    
    > [!NOTE]
    > <P>The <STRONG>Service life by rate</STRONG> check box is available only when you select <STRONG>Working clothes</STRONG>, <STRONG>Special rigging</STRONG>, or <STRONG>NVFA</STRONG> in the <STRONG>Type of group</STRONG> field in the <STRONG>FA groups</STRONG> form. If you select this check box, the lifetime that is specified in the <STRONG>Issue and usage rates</STRONG> form is updated in the <STRONG>Lifetime</STRONG> field in the <STRONG>Working clothes/Special riggings/NVFA issue journal lines</STRONG> form when you create an issue journal for the asset. The lifetime is updated on the working clothes or special rigging card.</P>

## View the balance of a fixed asset 

You can view the fixed asset balance for a specific date.

1.  Click Click **Fixed assets (Russia)** \> **Setup** \> **Value models**.
2.  Select the value model to view the balance for.
3.  Click **Balance** to open the **FA balances** form.
4.  In the **Transaction date** field, enter the date for the balance sheet. The default date is the current date.
    
    > [!NOTE]
    > The amounts in the <STRONG>FA balances</STRONG> form are displayed in the currency of the fixed asset value model. If the value model currency is different from your default currency, the default currency is also displayed in the form.

5.  Click the **Graphics** tab to view a graphical presentation of the asset's characteristics, such as types of cost, scrap or leaving sales, and profit or loss.
