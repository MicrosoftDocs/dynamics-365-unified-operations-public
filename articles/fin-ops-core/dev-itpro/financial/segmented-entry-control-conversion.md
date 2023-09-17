---
# required metadata

title: Migrate Segmented Entry controls
description: This article describes migration scenarios for the Segmented Entry control.
author: RyanCCarlson2
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 82e953d0-878e-4a3f-a91b-7375017a2810
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Migrate Segmented Entry controls

[!include [banner](../includes/banner.md)]

This tutorial walks you through two migration scenarios for the Segmented Entry control -  a simple scenario (for the SMAServiceOrderTable form) and a complex scenario (for the LedgerJournalTransDaily form).

## Simple migration scenario – SMAServiceOrderTable form

1.  Search for the **SMAServiceOrderTable** form in Application Explorer.
2.  Add the form to the current project.
3.  Open the form in the form design view and the code editor view.
4.  In the form design view, find the Segmented Entry control (SEC), either by manually walking the control tree or by searching for “SegmentedEntry” in the search bar below the **File** tab.
5.  Select the SEC, and verify the following information:
    -   The type for the control, as specified in parenthesis next to the control, is **SegmentedEntryControl**.
    -   The **Controller class** property is set to **DimensionDynamicAccountController**. This property indicates the type of controller that this instance of the SEC will use. The type of controller, in turn, determines the behavior of the control.

6.  Switch to the code editor view, and search for all occurrences of “TODO: (Code Upgrade) \[Segmented entry control\]” in the form source code.
7.  In the search results, ignore the first result, which points to the controller variable declaration. You must fix this TODO last, after you've removed all references to the controller variable.
8.  Go through each of the remaining TODO comments, as described in the following subsections.

### LedgerDimension data field

(**Form** &gt; **Data sources** &gt; **SMAServiceOrderLine** &gt; **Fields** &gt; **LedgerDimension** &gt; **Methods**)

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    ExpenseCost_LedgerDimension.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

### ExpenseCost\_LedgerDimension control

(Search for "ExpenseCost\_LedgerDimension" in the search bar below the **Form** tab.)

#### Step 1

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    ExpenseCost_LedgerDimension.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't performing any additional processing, you can delete it.

#### Step 2

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void loadSegments()
{
    super();
    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimDynamicAccountController.loadSegments();
}
```

##### Dynamics AX for Operations

Because this method only calls the **loadSegments()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 3

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Fix controller usage, if any, in this method based on the migration guidance */
public void lookup()
{
    switch (smaServiceOrderLine.OffsetAccountTypeExpense)
    {
        case LedgerJournalACType::Bank:
            BankAccountTable::lookupBankAccount(this);
            break;
        case LedgerJournalACType::Cust:
            CustTable::lookupCustomer(this);
            break;
        case LedgerJournalACType::FixedAssets:
            AssetTable::lookupAccountNum(this);
            break;
        case LedgerJournalACType::Project:
            ProjTable::lookupProjId(this, smaServiceOrderLine);
            break;
        case LedgerJournalACType::Vend:
            VendTable::lookupVendor(this);
            break;
        default:
            super();
            break;
    }
}
```

##### Dynamics AX for Operations

This method implements a custom lookup for the control. Therefore, leave the method as it is. Just remove the TODO. To hook up custom lookups, you must override the SEC’s **checkUseCustomLookup** method. Here is an example.

```xpp
public boolean checkUseCustomLookup(int _accountTypeEnumValue, int _secondaryAccountTypeEnumValue)
{
    boolean ret;
    switch(_accountTypeEnumValue)
    {
        case LedgerJournalACType::Bank:
        case LedgerJournalACType::Cust:
        case LedgerJournalACType::FixedAssets:
        case LedgerJournalACType::Project:
        case LedgerJournalACType::Vend:
            ret = true;
            break;
        default:
            ret = false;
    }
    return ret;
}
```

Additionally, make sure that the **closeSelectRecord** method on the custom lookup form is overridden. For an example, see the **CustTableLookup** form.

#### Step 4

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void segmentValueChanged(SegmentValueChangedEventArgs _e)
{
    super(_e);
    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimDynamicAccountController.segmentValueChanged(_e);
}
```

##### Dynamics AX for Operations

Because this method only calls the **segmentValueChanged()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 5

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public boolean validate()
{
    boolean isValid;
    isValid = super();
    /* TODO: (Code Upgrade) [Segmented entry control] This statement can be removed if there is no custom logic */
    // isValid = dimDynamicAccountController.validate() && isValid;
    return isValid;
}
```

##### Dynamics AX for Operations

Because this method only calls the **validate()** method on the control and doesn't perform any additional processing, you can delete it.

### Controller variable declarations

##### Dynamics AX 2012

Finally, go back to the first TODO, for the controller variable declaration.

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
/* 'dimDynamicAccountController' controller object is used with 'ExpenseCost_LedgerDimension' segmented entry controls.*/
DimensionDynamicAccountController dimDynamicAccountController;
```

##### Dynamics AX for Operations

The **dimDynamicAccountController** variable is no longer used on the form. Therefore, you can now delete it.

## Complex migration scenario – LedgerJournalTransDaily form
1.  Search for the **LedgerJournalTransDaily** form in Application Explorer.
2.  Add the form to the current project.
3.  Open the form in the form design view and the code editor view.
4.  In the form design view, find the SEC, either by manually walking the control tree or by searching for “SegmentedEntry” in the search bar below the **File** tab.
5.  Select the SEC, and verify the following information:
    -   The type for the control, as specified in parenthesis next to the control, is **SegmentedEntryControl**.
    -   The **Controller class** property is set to **DimensionDynamicAccountController**. This property indicates the type of controller that this instance of the SEC will use. The type of controller, in turn, determines the behavior of the control.

6.  Switch to the code editor view, and search for all occurrences of “TODO: (Code Upgrade) \[Segmented entry control\]” in the form source code.
7.  In the search results, the first three results are for the controller variable declarations. Look at the comments that accompany the TODOs, and make a note of the mapping that shows which SEC instance uses which controller instance. You will need this mapping when you replace method calls on the controller with method calls on the control. Here is what the controller-to-control mapping looks like:
    1.  dimAccountController
        1.  LedgerJournalTrans\_AccountNum
        2.  LedgerJournalTrans\_AccountNum1
        3.  Group4\_AccountNum

    2.  dimOffsetAccountController
        1.  GridOffsetAccount
        2.  LedgerJournalTrans\_OffsetAccount1
        3.  Group4\_OffsetAccount

    3.  dimPaymentFeeAccountController
        1.  CustPaymJournalFee\_CustAccount

    You will fix these three TODO comments at the end, after you've removed all references to the controller variables.
8.  Go through each of the remaining TODO comments, as described in the following subsections.

### LedgerDimension data field

(**Form** &gt; **Data sources** &gt; **LedgerJournalTrans** &gt; **Fields** &gt; **LedgerDimension** &gt; **Methods**)

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
// </GEEPL>
public void jumpRef()
{
    LedgerJournalTrans_AccountNum.jumpRef();
    LedgerJournalTrans_AccountNum1.jumpRef();
    Group4_AccountNum.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

### OffsetLedgerDimension data field

(**Form** &gt; **Data sources** &gt; **LedgerJournalTrans** &gt; **Fields** &gt; **OffsetLedgerDimension** &gt; **Methods**)

##### Dynamics AX 2012

The **OffsetLedgerDimension** field’s **jumpRef()** method:

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    GridOffsetAccount.jumpRef();
    LedgerJournalTrans_OffsetAccount1.jumpRef();
    Group4_OffsetAccount.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

### LedgerJournalTrans\_AccountNum control

(Search for "LedgerJournalTrans\_AccountNum" in the search bar below the **Form** tab.)

#### Step 1

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    LedgerJournalTrans_AccountNum.jumpRef();
    LedgerJournalTrans_AccountNum1.jumpRef();
    Group4_AccountNum.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 2

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void loadSegments()
{
    super();
    LedgerJournalTrans_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_AccountNum1.parmJournalName(ledgerJournalTable.JournalName);
    Group4_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum1.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    Group4_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_AccountNum1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimAccountController.loadSegments();
    currentMainAccountId = dimAccountController.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
}
```

##### Dynamics AX for Operations

1.  Update the **initLedger()** method.

    ```xpp
    void initLedger()
    {
        TransDate   dateFrom   = dateNull();
        TransDate   dateTo     = systemDateGet();
        if (element.args().dataset() == tableNum(LedgerJournalTable))
        {
            ledgerJournalTable = element.args().record();
            journalNum         = ledgerJournalTable.JournalNum;
            LedgerJournalTrans_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
            LedgerJournalTrans_AccountNum1.parmJournalName(ledgerJournalTable.JournalName);
            Group4_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
    . . .
    ```

2.  Update the code in the **LedgerJournalTrans** data source’s **active()** method. **Note:** The **getValue()** method should be called only if the account type is set to **Ledger**. Otherwise, a call to this method will cause an invalid function call.

    ```xpp
    . . .
    LedgerJournalTrans_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum1.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    Group4_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_AccountNum1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);
    if (ledgerJournalTrans.AccountType == LedgerJournalACType::Ledger)
    {
        currentMainAccountId = LedgerJournalTrans_AccountNum.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentMainAccountId = 0;
    }
    return ret;
    ```

3.  Add the following code to the **modified()** method of the **LedgerJournalTrans** data source’s **CurrencyCode** field.

    ```xpp
    LedgerJournalTrans_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    ```

4.  Add the following code to the **modified()** method of the **LedgerJournalTrans** data source’s **Company** field.

    ```xpp
    LedgerJournalTrans_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum1.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    Group4_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    ```

5.  Add the following code to the **modified()** method of the **LedgerJournalTrans** data source’s **TransDate** field.

    ```xpp
    LedgerJournalTrans_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_AccountNum1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);
    ```

6.  Delete the **loadSegments()** method.

#### Step 3

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Fix controller usage, if any, in this method based on the migration guidance */
public void lookup()
{
    // Polish sale disposal may require to filter asset that are not
    // marked for sale. lookupAccountNum method needs the ledgerJournalTrans_Asset.TransType
    // value to filter appropriately the assets. Thus, ledgerJournalTrans_Asset is
    // passed to accountNumLookup metho jumpRef d.
    // <GEEPL>
    if (!ledgerJournalEngine.accountNumLookup(ledgerJournalTrans_AccountNum,
        ledgerJournalTrans,
        ledgerJournalTrans.OffsetAccountType,
        ledgerJournalTrans.parmOffsetAccount(),
        ledgerJournalTrans_Asset))
    {
        super();
    }
    // </GEEPL>
}
```

##### Dynamics AX for Operations

This method implements a custom lookup for the control. Therefore, leave the method as it is. Just remove the TODO. To hook up custom lookups, you must override the SEC’s **checkUseCustomLookup** method. Additionally, make sure that the **closeSelectRecord** method on the custom lookup form is overridden. For an example, see the **CustTableLookup** form.

#### Step 4

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void segmentValueChanged(SegmentValueChangedEventArgs _e)
{
    // <GIN>
    if (TaxWithholdParameters_IN::checkTaxParameters()
        && ledgerJournalTrans.TaxWithholdCode_IN != '')
    {
        if (Box::okCancel("@GLS222698",
            DialogButton::Cancel) == DialogButton::Cancel)
        {
            return;
        }
    }
    // </GIN>
    super(_e);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimAccountController.segmentValueChanged(_e);
    currentMainAccountId = ledgerJournalEngine.onPrimaryAccountSegmentChanged(dimAccountController, currentMainAccountId, ledgerJournalTrans);
}
```

##### Dynamics AX for Operations

1.  Override the **onSegmentChanged()** method on the control, and add the following code to it.

    ```xpp
    /// <summary>
    /// Event handler for the segment changed event.
    /// </summary>
    /// <param name = "_segment">The segment that has been changed.</param>
    public void onSegmentChanged(DimensionControlSegment _segment)
    {
        super(_segment);

        // <GIN>
        if (TaxWithholdParameters_IN::checkTaxParameters()
            && ledgerJournalTrans.TaxWithholdCode_IN != '')
        {
            if (Box::okCancel("@GLS222698",
                DialogButton::Cancel) == DialogButton::Cancel)
            {
                return;
            }
        }

        // </GIN>
        if (_segment.parmName() == mainAccountDimAttrName)
        {
            previousMainAccountId = currentMainAccountId;
        }
        currentMainAccountId = ledgerJournalEngine.onPrimaryAccountSegmentChanged(LedgerJournalTrans_AccountNum, currentMainAccountId, ledgerJournalTrans);
    }
    ```

2.  Delete the **segmentValueChanged()** method. **Note:** The preceding code for the **onSegmentChanged()** method will not compile, because the **onPrimaryAccountSegmentChanged()** method expects a controller object, but this code passes an instance of the SEC. To call methods on the control instance, you must change the method’s signature and its implementation accordingly. This method is used by more than 50 callers. Therefore, you would also have to update all those calls. Alternatively, you can add a new method that follows this guidance.

#### Step 5

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public boolean validate()
{
    boolean isValid;
    isValid = super();

    /* TODO: (Code Upgrade) [Segmented entry control] This statement can be removed if there is no custom logic */
    // isValid = dimAccountController.validate() && isValid;
    return isValid;
}
```

##### Dynamics AX for Operations

Because this method only calls the **validate()** method on the control and doesn't perform any additional processing, you can delete it.

### GridOffsetAccount control

(Search for "GridOffsetAccount" in the search bar below the **Form** tab.)

#### Step 1

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
void gotFocus()
{
    super();
    if (ledgerJournalTable.FixedOffsetAccount)
    {
        gridOffsetAccount.allowEdit(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger);
    }
    else if (!gridOffsetAccount.allowEdit())
    {
        gridOffsetAccount.allowEdit(true);
    }
}
```

##### Dynamics AX for Operations

1.  Add the following code to the **initLedger()** method, after the code that updates the ledgerJournalTable buffer.

    ```xpp
    . . .
    if (element.args().dataset() == tableNum(LedgerJournalTable))
    {
        ledgerJournalTable = element.args().record();
        journalNum         = ledgerJournalTable.JournalNum;
        LedgerJournalTrans_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
        LedgerJournalTrans_AccountNum1.parmJournalName(ledgerJournalTable.JournalName);
        Group4_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
        if (ledgerJournalTable.FixedOffsetAccount)
        {               
            gridOffsetAccount.allowEdit(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger);
        }
        else if (!gridOffsetAccount.allowEdit())
        {
            gridOffsetAccount.allowEdit(true);
        }
    . . .
    ```

2.  Delete the **gotFocus()** method.

#### Step 2

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    GridOffsetAccount.jumpRef();
    LedgerJournalTrans_OffsetAccount1.jumpRef();
    Group4_OffsetAccount.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 3

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void loadSegments()
{
    super();
    GridOffsetAccount.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_OffsetAccount1.parmJournalName(ledgerJournalTable.JournalName);
    Group4_OffsetAccount.parmJournalName(ledgerJournalTable.JournalName);
    GridOffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_OffsetAccount1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_OffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    GridOffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    LedgerJournalTrans_OffsetAccount1.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    Group4_OffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    GridOffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_OffsetAccount1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_OffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimOffsetAccountController.loadSegments();
    currentOffsetMainAccountId = dimOffsetAccountController.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));

    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        Group4_OffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
}
```

##### Dynamics AX for Operations

1.  Update the **initLedger()** method. **Note:** The **getValue()** method should be called only if the account type is set to **Ledger**. Otherwise, a call to this method will cause an invalid function call.

    ```xpp
    void initLedger()
    {
        TransDate   dateFrom   = dateNull();
        TransDate   dateTo     = systemDateGet();
        if (element.args().dataset() == tableNum(LedgerJournalTable))
        {
            ledgerJournalTable = element.args().record();
            journalNum         = ledgerJournalTable.JournalNum;
            GridOffsetAccount.parmJournalName(ledgerJournalTable.JournalName);
            LedgerJournalTrans_OffsetAccount1.parmJournalName(ledgerJournalTable.JournalName);
            Group4_OffsetAccount.parmJournalName(ledgerJournalTable.JournalName);
            if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
            {
                currentOffsetMainAccountId = GridOffsetAccount.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
            }
            else
            {
                currentOffsetMainAccountId = 0;
            }

            // Lock the main account segment if "Fixed offset account" is selected in Journal Names
            if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
            {
                GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
            }
    . . .
    ```

2.  Update the code in the **LedgerJournalTrans** data source’s **active()** method. **Note:** The **getValue()** method should be called only if the account type is set to **Ledger**. Otherwise, a call to this method will cause an invalid function call.

    ```xpp
    . . .
    GridOffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_OffsetAccount1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_OffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    GridOffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    LedgerJournalTrans_OffsetAccount1.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    Group4_OffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    GridOffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_OffsetAccount1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_OffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        currentOffsetMainAccountId = GridOffsetAccount.getValue( DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentOffsetMainAccountId = 0;
    }

    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    { 
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
    return ret;
    ```

3.  Add the following code to the **modified()** method of the **LedgerJournalTrans** data source’s **CurrencyCode** field.

    ```xpp
    GridOffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_OffsetAccount1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_OffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    ```

4.  Add the following code to the **modified()** method of the **LedgerJournalTrans** data source’s **OffsetCompany** field.

    ```xpp
    GridOffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    LedgerJournalTrans_OffsetAccount1.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    Group4_OffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    ```

5.  Add the following code to the **modified()** method of the **LedgerJournalTrans** data source’s **TransDate** field.

    ```xpp
    GridOffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_OffsetAccount1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_OffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);
    ```

6.  Add the following code to the **modified()** method of the **LedgerJournalTrans** data source’s **OffsetAccountType** field. **Note:** The **getValue()** method should be called only if the account type is set to **Ledger**. Otherwise, a call to this method cause an invalid function call.

    ```xpp
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        currentOffsetMainAccountId = GridOffsetAccount.getValue( DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentOffsetMainAccountId = 0;
    }

    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
    ```

7.  Delete the **loadSegments()** method.

#### Step 4

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Fix controller usage, if any, in this method based on the migration guidance */
public void lookup()
{
    // Find the current segment index value
    int currentSegmentIndex = dimOffsetAccountController.parmControl().currentSegmentIndex();
    if ((ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger &&
        dimOffsetAccountController.getDimensionAttributeByControlIndex(currentSegmentIndex) != DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount)) ||
        !ledgerJournalEngine.offsetAccountNumLookUp(gridOffsetAccount, ledgerJournalTrans))
    {
        super();
    }
}
```

##### Dynamics AX for Operations

This method implements a custom lookup for the control. Therefore, keep the method, but replace the controller with the control instance. In this case, because the method is overridden on the **GridOffsetAccount** control, even though **dimOffsetAccountController** was used for three different SEC instances (based on the mapping that is shown in the TODOs on controller variable declarations), we must replace the controller with only one SEC instance. Therefore, the code will look like this.

```xpp
public void lookup()
{
    // Find the current segment index value
    int currentSegmentIndex = GridOffsetAccount.getCurrentSegmentIndex();
    if ((ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger && GridOffsetAccount.getDimensionAttributeByControlIndex(currentSegmentIndex) != DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount)) || !ledgerJournalEngine.offsetAccountNumLookUp(gridOffsetAccount, ledgerJournalTrans))
    {
        super();
    }
}
```

To hook up custom lookups, you must override the SEC’s **checkUseCustomLookup** method. Additionally, make sure that the **closeSelectRecord** method on the custom lookup form is overridden. For an example, see the **CustTableLookup** form.

#### Step 5

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void segmentValueChanged(SegmentValueChangedEventArgs _e)
{
    super(_e);
    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimOffsetAccountController.segmentValueChanged(_e);
    currentOffsetMainAccountId = ledgerJournalEngine.onOffsetAccountSegmentChanged(dimOffsetAccountController, currentOffsetMainAccountId, ledgerJournalTrans);
}
```

##### Dynamics AX for Operations

1.  Override the **onSegmentChanged()** method on the control, and add the following code to it.

    ```xpp
    /// <summary>
    /// Event handler for the segment changed event.
    /// </summary>
    /// <param name = "_segment">The segment that was modified.</param>
    public void onSegmentChanged(DimensionControlSegment _segment)
    {
        super(_segment);
        currentOffsetMainAccountId = ledgerJournalEngine.onOffsetAccountSegmentChanged(
        GridOffsetAccount, currentOffsetMainAccountId, ledgerJournalTrans);
    }
    ```

2.  Delete the **segmentValueChanged()** method. **Note:** The preceding code for the **onSegmentChanged()** method will not compile, because the **onOffsetAccountSegmentChanged()** method expects a controller object, but this code passes an instance of the SEC. To call methods on the control instance, you must change the method’s signature and its implementation accordingly. This method is used by more than 50 callers. Therefore, you would also have to update all those calls. Alternatively, you can add a new method that follows this guidance.

#### Step 6

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public boolean validate()
{
    boolean isValid;
    isValid = super();

    /* TODO: (Code Upgrade) [Segmented entry control] This statement can be removed if there is no custom logic */
    // isValid = dimOffsetAccountController.validate() && isValid;
    return isValid;
}
```

##### Dynamics AX for Operations

Because this method only calls the **validate()** method on the control and doesn't perform any additional processing, you can delete it.

### LedgerJournalTrans\_AccountNum1

(Search for "LedgerJournalTrans\_AccountNum1" in the search bar below the **Form** tab.)

#### Step 1

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    LedgerJournalTrans_AccountNum.jumpRef();
    LedgerJournalTrans_AccountNum1.jumpRef();
    Group4_AccountNum.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 2

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void loadSegments()
{
    super();
    LedgerJournalTrans_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_AccountNum1.parmJournalName(ledgerJournalTable.JournalName);
    Group4_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum1.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    Group4_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_AccountNum1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimAccountController.loadSegments();
    currentMainAccountId = dimAccountController.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
}
```

##### Dynamics AX for Operations

The steps for migrating this method are the same as the steps for migrating the **LedgerJournalTrans\_AccountNum.loadSegments()** method. Therefore, no additional steps are required. Delete this method.

#### Step 3

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Fix controller usage, if any, in this method based on the migration guidance */
public void lookup()
{
    if (!ledgerJournalEngine.accountNumLookup(ledgerJournalTrans_AccountNum1, ledgerJournalTrans))
    {
        super();
    }
}
```

##### Dynamics AX for Operations

This method implements a custom lookup for the control. Therefore, leave the method as it is. Just remove the TODO. To hook up custom lookups, you must override the SEC’s **checkUseCustomLookup** method. Additionally, make sure that the **closeSelectRecord** method on the custom lookup is overridden. For an example, see the **CustTableLookup** form.

#### Step 4

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void segmentValueChanged(SegmentValueChangedEventArgs _e)
{
    super(_e);
    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimAccountController.segmentValueChanged(_e);
    currentMainAccountId = ledgerJournalEngine.onPrimaryAccountSegmentChanged(dimAccountController, currentMainAccountId, ledgerJournalTrans);
}
```

##### Dynamics AX for Operations

1.  Override the **onSegmentChanged()** method on the control, and add the following code to it.

    ```xpp
    /// <summary>
    /// The event handler when a segment is modified.
    /// </summary>
    /// <param name = "_segment">The segment that was modified.</param>
    public void onSegmentChanged(DimensionControlSegment _segment)
    {
        super(_segment);
        currentMainAccountId = ledgerJournalEngine.onPrimaryAccountSegmentChanged(
        LedgerJournalTrans_AccountNum1, currentMainAccountId, ledgerJournalTrans);
    }
    ```

2.  Delete the **segmentValueChanged()** method. **Note:** The preceding code for the **onSegmentChanged()** method will not compile, because the **onPrimaryAccountSegmentChanged()** method expects a controller object, but this code passes an instance of the SEC. To call methods on the control instance, you must change the method’s signature and its implementation accordingly. This method is used by more than 50 callers. Therefore, you would also have to update all of those calls. Alternatively, you can add a new method that follows this guidance.

#### Step 5

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public boolean validate()
{
    boolean isValid;
    isValid = super();
    /* TODO: (Code Upgrade) [Segmented entry control] This statement can be removed if there is no custom logic */
    // isValid = dimAccountController.validate() && isValid;
    return isValid;
}
```

##### Dynamics AX for Operations

Because this method only calls the **validate()** method on the control and doesn't perform any additional processing, you can delete it.

### LedgerJournalTrans\_OffsetAccount1

(Search for "LedgerJournalTrans\_OffsetAccount1" in the search bar below the **Form** tab.)

#### Step 1

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    GridOffsetAccount.jumpRef();
    LedgerJournalTrans_OffsetAccount1.jumpRef();
    Group4_OffsetAccount.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 2

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void loadSegments()
{
    super();
    GridOffsetAccount.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_OffsetAccount1.parmJournalName(ledgerJournalTable.JournalName);
    Group4_OffsetAccount.parmJournalName(ledgerJournalTable.JournalName);
    GridOffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_OffsetAccount1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_OffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    GridOffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    LedgerJournalTrans_OffsetAccount1.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    Group4_OffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    GridOffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_OffsetAccount1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_OffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimOffsetAccountController.loadSegments();
    currentOffsetMainAccountId = dimOffsetAccountController.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        Group4_OffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
}
```

##### Dynamics AX for Operations

The migration steps for the **GridOffsetAccount.loadSegments()** method already made most of the changes that are required for this method. However, you must still make the following changes.

1.  Add a line of code to the **LedgerJournalTrans** data source’s **active** method.

    ```xpp
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        currentOffsetMainAccountId = GridOffsetAccount.getValue(
        DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentOffsetMainAccountId = 0;
    }

    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
    ```

2.  Make the same change in the **modified()** method of the **LedgerJournalTrans** data source’s **OffsetAccountType** field.

    ```xpp
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        currentOffsetMainAccountId = GridOffsetAccount.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentOffsetMainAccountId = 0;
    }

    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
    ```

3.  Make the same change in the **initLedger()** method.

    ```xpp
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        currentOffsetMainAccountId = GridOffsetAccount.getValue( DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentOffsetMainAccountId = 0;
    }

    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
    ```

4.  Delete the **loadSegments()** method.

#### Step 3

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Fix controller usage, if any, in this method based on the migration guidance */
public void lookup()
{
    // Find the current segment index value
    int currentSegmentIndex = dimOffsetAccountController.parmControl().currentSegmentIndex();
    if ((ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger &&
        dimOffsetAccountController.getDimensionAttributeByControlIndex(currentSegmentIndex) != DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount)) ||
        !ledgerJournalEngine.offsetAccountNumLookUp(ledgerJournalTrans_OffsetAccount1, ledgerJournalTrans))
    {
        super();
    }
}
```

##### Dynamics AX for Operations

This method implements a custom lookup for the control. Therefore, keep the method, but replace the controller with the control instance. In this case, because the method is overridden on the **LedgerJournalTrans\_OffsetAccount1** control, even though **dimOffsetAccountController** was used for three different SEC instances (based on the mapping that is shown in the TODOs on controller variable declarations), we must replace the controller with only one SEC instance. Therefore, the code will look like this.

```xpp
public void lookup()
{
    // Find the current segment index value
    int currentSegmentIndex = LedgerJournalTrans_OffsetAccount1.getCurrentSegmentIndex();
    if ((ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger && LedgerJournalTrans_OffsetAccount1.getDimensionAttributeByControlIndex(currentSegmentIndex) != DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount)) || !ledgerJournalEngine.offsetAccountNumLookUp(ledgerJournalTrans_OffsetAccount1, ledgerJournalTrans))
    {
        super();
    }
}
```

To hook up custom lookups, you must override the SEC’s **checkUseCustomLookup** method. Additionally, make sure that the **closeSelectRecord** method on the custom lookup form is overridden. For an example, see the **CustTableLookup** form.

#### Step 4

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void segmentValueChanged(SegmentValueChangedEventArgs _e)
{
    super(_e);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimOffsetAccountController.segmentValueChanged(_e);
    currentOffsetMainAccountId = ledgerJournalEngine.onOffsetAccountSegmentChanged(dimOffsetAccountController, currentOffsetMainAccountId, ledgerJournalTrans);
}
```

##### Dynamics AX for Operations

1.  Override the **onSegmentChanged()** method on the control, and add the following code to it.

    ```xpp
    /// <summary>
    /// The event handler when a segment is modified.
    /// </summary>
    /// <param name = "_segment">The segment that was modified.</param>
    public void onSegmentChanged(DimensionControlSegment _segment)
    {
        super(_segment);
        currentOffsetMainAccountId = ledgerJournalEngine.onOffsetAccountSegmentChanged(
        LedgerJournalTrans_OffsetAccount1, currentOffsetMainAccountId, ledgerJournalTrans);
    }
    ```

2.  Delete the **segmentValueChanged()** method. **Note:** The preceding code for the **onSegmentChanged()** method will not compile, because the **onOffsetAccountSegmentChanged()** method expects a controller object, but this code passes an instance of the SEC. To call methods on the control instance, you must change the method’s signature and its implementation accordingly. This method is used by more than 50 callers. Therefore, you would also have to update all those calls. Alternatively, you can add a new method that follows this guidance.

#### Step 5

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public boolean validate()
{
    boolean isValid;
    isValid = super();

    /* TODO: (Code Upgrade) [Segmented entry control] This statement can be removed if there is no custom logic */
    // isValid = dimOffsetAccountController.validate() && isValid;
    return isValid;
}
```

##### Dynamics AX for Operations

Because this method only calls the **validate()** method on the control and doesn't perform any additional processing, you can delete it.

### CustPaymJournalFee\_CustAccount

(Search for "CustPaymJournalFee\_CustAccount" in the search bar below the **Form** tab.)

#### Step 1

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    CustPaymJournalFee_CustAccount.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 2

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void loadSegments()
{
    super();
    CustPaymJournalFee_CustAccount.parmJournalName(ledgerJournalTable.JournalName);
    CustPaymJournalFee_CustAccount.parmCurrency(custVendPaymJournalFee.FeeCurrency);
    CustPaymJournalFee_CustAccount.parmControlDate(ledgerJournalTrans.TransDate);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimPaymentFeeAccountController.loadSegments();
    currentPaymentFeeMainAccountId = dimPaymentFeeAccountController.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
}
```

##### Dynamics AX for Operations

1.  Update the **initLedger()** method.

    ```xpp
    ledgerJournalTable = element.args().record();
    journalNum = ledgerJournalTable.JournalNum;
    LedgerJournalTrans_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_AccountNum1.parmJournalName(ledgerJournalTable.JournalName); Group4_AccountNum.parmJournalName(ledgerJournalTable.JournalName); CustPaymJournalFee_CustAccount.parmJournalName(ledgerJournalTable.JournalName);
    . . .
    ```

2.  Add the following code to the **CustVendPaymJournalFee** data source’s **active()** method. **Note:** The method doesn't exist, so you must override it.

    ```xpp
    CustPaymJournalFee_CustAccount.parmCurrency(custVendPaymJournalFee.FeeCurrency);
    ```

3.  Add the following code to the **modified()** method of the **CustVendPaymJournalFee** data source’s **FeeCurrency** field. **Note:** The method doesn't exist, so you must override it.

    ```xpp
    CustPaymJournalFee_CustAccount.parmCurrency(custVendPaymJournalFee.FeeCurrency);
    ```

4.  Add the following code to the **LedgerJournalTrans** data source’s **active()** method.

    ```xpp
    CustPaymJournalFee_CustAccount.parmControlDate(ledgerJournalTrans.TransDate);
    ```

5.  Add the following code to the **modified()** method of the **LedgerJournalTrans** data source’s **TransDate** field.

    ```xpp
    CustPaymJournalFee_CustAccount.parmControlDate(ledgerJournalTrans.TransDate);
    ```

6.  Delete the **loadSegments()** method.

#### Step 3

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Fix controller usage, if any, in this method based on the migration guidance */
public void lookup()
{
    if (custVendPaymJournalFee.Module == ModuleCustVend::Cust)
    {
        if (custVendPaymJournalFee.LedgerJournalACType == LedgerJournalACType::Cust)
        {
            CustTable::lookupCustomer(this, ledgerJournalTrans.Company);
        }
        else if (custVendPaymJournalFee.LedgerJournalACType == LedgerJournalACType::Ledger)
        {
            super();
        }
    }
    else if (custVendPaymJournalFee.Module == ModuleCustVend::Vend)
    {
        if (custVendPaymJournalFee.LedgerJournalACType == LedgerJournalACType::Vend)
        {
            VendTable::lookupVendor(this, ledgerJournalTrans.Company);
        }
        else if (custVendPaymJournalFee.LedgerJournalACType == LedgerJournalACType::Ledger)
        {
            super();
        }
    }
}
```

##### Dynamics AX for Operations

This method implements a custom lookup for the control. Therefore, leave the method as it is. Just remove the TODO. To hook up custom lookups, you must override the SEC’s **checkUseCustomLookup** method. Here is an example.

```xpp
public boolean checkUseCustomLookup(int _accountTypeEnumValue, int _secondaryAccountTypeEnumValue)
{
    boolean ret;
    switch(_accountTypeEnumValue)
    {
        case LedgerJournalACType::Bank:
        case LedgerJournalACType::Cust:
        case LedgerJournalACType::FixedAssets:
        case LedgerJournalACType::Project:
        case LedgerJournalACType::Vend:
            ret = true;
            break;
        default:
            ret = false;
    }
    return ret;
}
```

Additionally, make sure that the **closeSelectRecord** method on the custom lookup form is overridden. For an example, see the **CustTableLookup** form.

#### Step 4

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void segmentValueChanged(SegmentValueChangedEventArgs _e)
{
    super(_e);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimPaymentFeeAccountController.segmentValueChanged(_e);
    currentPaymentFeeMainAccountId = ledgerJournalEngine.onPrimaryAccountSegmentChanged(dimPaymentFeeAccountController, currentPaymentFeeMainAccountId, ledgerJournalTrans);
}
```

##### Dynamics AX for Operations

1.  Override the **onSegmentChanged()** method on the control, and add the following code to it.

    ```xpp
    /// <summary>
    /// The event handler when a segment is modified.
    /// </summary>
    /// <param name = "_segment">The segment that was modified.</param>
    public void onSegmentChanged(DimensionControlSegment _segment)
    {
        super(_segment);
        currentPaymentFeeMainAccountId = ledgerJournalEngine.onPrimaryAccountSegmentChanged(
        CustPaymJournalFee_CustAccount, currentPaymentFeeMainAccountId, ledgerJournalTrans);
    }
    ```

2.  Delete the **segmentValueChanged()** method. **Note:** The preceding code for the **onSegmentChanged()** method will not compile, because the **onPrimaryAccountSegmentChanged()** method expects a controller object, but this code passes an instance of the SEC. To call methods on the control instance, you must change the method’s signature and its implementation accordingly. This method is used by more than 50 callers. Therefore, you would also have to update all those calls. Alternatively, you can add a new method that can follow this guidance.

#### Step 5

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public boolean validate()
{
    boolean isValid;
    isValid = super();

    /* TODO: (Code Upgrade) [Segmented entry control] This statement can be removed if there is no custom logic */
    // isValid = dimPaymentFeeAccountController.validate() && isValid;
    return isValid;
}
```

##### Dynamics AX for Operations

Because this method only calls the **validate()** method on the control and doesn't perform any additional processing, you can delete it.

### Group4\_AccountNum

(Search for "Group4\_AccountNum" in the search bar below the **Form** tab.)

#### Step 1

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    LedgerJournalTrans_AccountNum.jumpRef();
    LedgerJournalTrans_AccountNum1.jumpRef();
    Group4_AccountNum.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 2

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void loadSegments()
{
    super();
    LedgerJournalTrans_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_AccountNum1.parmJournalName(ledgerJournalTable.JournalName);
    Group4_AccountNum.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_AccountNum.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum1.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    Group4_AccountNum.parmDataAreaId(ledgerJournalTrans.Company ? ledgerJournalTrans.Company : curext());
    LedgerJournalTrans_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_AccountNum1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_AccountNum.parmControlDate(ledgerJournalTrans.TransDate);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimAccountController.loadSegments();
    currentMainAccountId = dimAccountController.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
}
```

##### Dynamics AX for Operations

The steps for migrating this method are the same as the steps for migrating the **LedgerJournalTrans\_AccountNum.loadSegments()** method. Therefore, no additional steps are required. Delete this method.

#### Step 3

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Fix controller usage, if any, in this method based on the migration guidance */
public void lookup()
{
    if (!ledgerJournalEngine.accountNumLookup(group4_AccountNum, ledgerJournalTrans))
    {
        super();
    }
}
```

##### Dynamics AX for Operations

This method implements a custom lookup for the control. Therefore, leave the method as it is. Just remove the TODO. To hook up custom lookups, you must override the SEC’s **checkUseCustomLookup** method. Additionally, make sure that the **closeSelectRecord** method on the custom lookup form is overridden. For an example, see the **CustTableLookup** form.

#### Step 4

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void segmentValueChanged(SegmentValueChangedEventArgs _e)
{
    super(_e);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimAccountController.segmentValueChanged(_e);
    currentMainAccountId = ledgerJournalEngine.onPrimaryAccountSegmentChanged(dimAccountController, currentMainAccountId, ledgerJournalTrans);
}
```

##### Dynamics AX for Operations

1.  Override the **onSegmentChanged()** method on the control, and add the following code to it.

    ```xpp
    /// <summary>
    /// The event handler for the segment change event.
    /// </summary>
    /// <param name = "_segment">The segment that was modified.</param>
    public void onSegmentChanged(DimensionControlSegment _segment)
    {
        super(_segment);
        if (_segment.parmName() == mainAccountDimAttrName)
        {
            previousMainAccountId = currentMainAccountId;
        }
        currentMainAccountId = ledgerJournalEngine.onPrimaryAccountSegmentChanged(Group4_AccountNum, currentMainAccountId, ledgerJournalTrans);
    }
    ```

2.  Delete the **segmentValueChanged()** method. **Note:** The preceding code for the **onSegmentChanged()** method will not compile, because the **onPrimaryAccountSegmentChanged()** method expects a controller object, but this code passes an instance of the SEC. To call methods on the control instance, you must change the method’s signature and its implementation accordingly. This method is used by more than 50 callers. Therefore, you would also have to update all those calls. Alternatively, you can add a new method that follows this guidance.

#### Step 5

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public boolean validate()
{
    boolean isValid;
    isValid = super();

    /* TODO: (Code Upgrade) [Segmented entry control] This statement can be removed if there is no custom logic */
    // isValid = dimAccountController.validate() && isValid;
    return isValid;
}
```

##### Dynamics AX for Operations

Because this method only calls the **validate()** method on the control and doesn't perform any additional processing, you can delete it.

### Group4\_OffsetAccount

(Search for "Group4\_OffsetAccount" in the search bar below the **Form** tab.)

#### Step 1

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
void gotFocus()
{
    super();
    if (ledgerJournalTable.FixedOffsetAccount)
    {
        group4_OffsetAccount.allowEdit(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger);
    }
    else if (!group4_OffsetAccount.allowEdit())
    {
        group4_OffsetAccount.allowEdit(true);
    }
}
```

##### Dynamics AX for Operations

1.  Update the code in the **initLedger()** method, after the code that updates the ledgerJournalTable buffer.

    ```xpp
    . . .
    if (ledgerJournalTable.FixedOffsetAccount)
    {
        gridOffsetAccount.allowEdit(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger); group4_OffsetAccount.allowEdit(ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger);
    }
    else if (!gridOffsetAccount.allowEdit())
    {
        gridOffsetAccount.allowEdit(true);
        group4_OffsetAccount.allowEdit(true);
    }
    . . .
    ```

2.  Delete the **gotFocus()** method.

#### Step 2

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public void jumpRef()
{
    GridOffsetAccount.jumpRef();
    LedgerJournalTrans_OffsetAccount1.jumpRef();
    Group4_OffsetAccount.jumpRef();
}
```

##### Dynamics AX for Operations

Because this method only calls the **jumpRef()** method on the control and doesn't perform any additional processing, you can delete it.

#### Step 3

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void loadSegments()
{
    super();
    GridOffsetAccount.parmJournalName(ledgerJournalTable.JournalName);
    LedgerJournalTrans_OffsetAccount1.parmJournalName(ledgerJournalTable.JournalName);
    Group4_OffsetAccount.parmJournalName(ledgerJournalTable.JournalName);
    GridOffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    LedgerJournalTrans_OffsetAccount1.parmCurrency(ledgerJournalTrans.CurrencyCode);
    Group4_OffsetAccount.parmCurrency(ledgerJournalTrans.CurrencyCode);
    GridOffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    LedgerJournalTrans_OffsetAccount1.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    Group4_OffsetAccount.parmDataAreaId(ledgerJournalTrans.getOffsetCompany());
    GridOffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);
    LedgerJournalTrans_OffsetAccount1.parmControlDate(ledgerJournalTrans.TransDate);
    Group4_OffsetAccount.parmControlDate(ledgerJournalTrans.TransDate);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimOffsetAccountController.loadSegments();
    currentOffsetMainAccountId = dimOffsetAccountController.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));

    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        Group4_OffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
}
```

##### Dynamics AX for Operations

The migration steps for the **GridOffsetAccount.loadSegments()** method already made most of the changes that are required for this method. However, you must still make the following changes.

1.  Update the code in the **LedgerJournalTrans** data source’s **active** method.

    ```xpp
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        currentOffsetMainAccountId = GridOffsetAccount.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentOffsetMainAccountId = 0;
    }

    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        Group4_OffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
    ```

2.  Make the same change in the **modified()** method of the **LedgerJournalTrans** data source’s **OffsetAccountType** field.

    ```xpp
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        currentOffsetMainAccountId = GridOffsetAccount.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentOffsetMainAccountId = 0;
    }
    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        Group4_OffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
    ```

3.  Make the same change in the **initLedger()** method.

    ```xpp
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        currentOffsetMainAccountId = GridOffsetAccount.getValue(DimensionAttribute::getWellKnownDimensionAttribute(DimensionAttributeType::MainAccount));
    }
    else
    {
        currentOffsetMainAccountId = 0;
    }
    // Lock the main account segment if "Fixed offset account" is selected in Journal Names
    if (ledgerJournalTrans.OffsetAccountType == LedgerJournalACType::Ledger)
    {
        GridOffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        LedgerJournalTrans_OffsetAccount1.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
        Group4_OffsetAccount.parmLockMainAccountSegment(ledgerJournalTable.FixedOffsetAccount);
    }
    ```

4.  Delete the **loadSegments()** method.

#### Step 4

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] Fix controller usage, if any, in this method based on the migration guidance */
public void lookup()
{
    if (!ledgerJournalEngine.offsetAccountNumLookUp(group4_OffsetAccount, ledgerJournalTrans))
    {
        super();
    }
}
```

##### Dynamics AX for Operations

This method implements a custom lookup for the control. Therefore, leave the method as it is. Just remove the TODO. To hook up custom lookups, you must override the SEC’s **checkUseCustomLookup** method. Additionally, make sure that the **closeSelectRecord** method on the custom lookup form is overridden. For an example, see the **CustTableLookup** form.

#### Step 5

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] For custom implementation, code in this method needs to be moved elsewhere based on the migration guidance */
public void segmentValueChanged(SegmentValueChangedEventArgs _e)
{
    super(_e);

    /* TODO: (Code Upgrade) [Segmented entry control] Replace this based on the migration guidance */
    // dimOffsetAccountController.segmentValueChanged(_e);
    currentOffsetMainAccountId = ledgerJournalEngine.onOffsetAccountSegmentChanged(dimOffsetAccountController, currentOffsetMainAccountId, ledgerJournalTrans);
}
```

##### Dynamics AX for Operations

1.  Override the **onSegmentChanged()** method on the control, and add the following code to it.

    ```xpp
    /// <summary>
    /// The event handler for the segment change event.
    /// </summary>
    /// <param name = "_segment">The segment that was modified.</param>
    public void onSegmentChanged(DimensionControlSegment _segment)
    {
        super(_segment);
        currentOffsetMainAccountId = ledgerJournalEngine.onOffsetAccountSegmentChanged(
        Group4_OffsetAccount, currentOffsetMainAccountId, ledgerJournalTrans);
    }
    ```

2.  Delete the **segmentValueChanged()** method. **Note:** The preceding code for the **onSegmentChanged()** method will not compile, because the **onOffsetAccountSegmentChanged()** method expects a controller object, but this code passes an instance of the SEC. To call methods on the control instance, you must change the method’s signature and its implementation accordingly. This method is used by more than 50 callers. Therefore, you would also have to update all those calls. Alternatively, you can add a new method that follows this guidance.

#### Step 6

##### Dynamics AX 2012

```xpp
/* TODO: (Code Upgrade) [Segmented entry control] This method can be removed if there is no custom implementation */
public boolean validate()
{
    boolean isValid;
    isValid = super();

    /* TODO: (Code Upgrade) [Segmented entry control] This statement can be removed if there is no custom logic */
    // isValid = dimOffsetAccountController.validate() && isValid;
    return isValid;
}
```

##### Dynamics AX for Operations

Because this method only calls the **validate()** method on the control and doesn't perform any additional processing, you can delete it.

## Additional resources

[Support for Segmented Entry controls on dialogs](segmented-entry-control-dialog-support.md)

[Design-time metadata for Segmented Entry controls](segmented-entry-control-metadata-specification.md)

[Parm methods for Segmented Entry controls](segmented-entry-control-parm-method-specification.md)

[Migration guidance for Segmented Entry controls](segmented-entry-control-migration-guidance.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
