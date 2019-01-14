---
# required metadata

title: Business events developer documentation
description: This topic walks you through the development process and best practices for implementing business events.
author: Sunil-Garg
manager: AnnBe
ms.date: 01/09/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Business events developer documentation

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

## Implementing a business event

Two classes must be implemented:

- **Business event** – This class extends the **BusinessEventsBase** class. It provides support for constructing, building the payload, and sending the business event.
- **Business event contract** – This class extends the **BusinessEventsContract** class. It defines the payload of the business event and allows for population of the contract at runtime.

### BusinessEventsBase extension

#### Naming convention

The names of business events should follow this pattern: \<noun/noun phrase\>\<action phrase\>BusinessEvent

**Examples**

- VendorInvoicePostedBusinessEvent
- CollectionLetterSentBusinessEvent

The \<noun/noun phrase\> part of the name should comply with existing definitions for application area prefixes.

#### Implementation

The process of implementing a **BusinessEventsBase** extension is straightforward. It involves extending the **BusinessEventsBase** class, and implementing a static constructor method, a private **new** method, methods to maintain internal state, and the **buildContract** method.

1. Extend the **BusinessEventsBase** class.

    ```
    [BusinessEvents(classStr(SalesInvoicePostedBusinessEventContract),
    "\@AccountsReceivable:SalesOrderInvoicePostedBusinessEventName","\@AccountsReceivable:SalesOrderInvoicePostedBusinessEventDescription",ModuleAxapta::SalesOrder)]
    public final class SalesInvoicePostedBusinessEvent extends BusinessEventsBase
    ```

    Note the **BusinessEvents** attribute. This attribute provides the business events framework with information about the business event's contract, name, and description, and also the module that it's part of. Labels must be defined for the name and description arguments.

2. Implement a static **newFrom\<foo\>** method. The \<foo\> part of the method name is typically the table buffer that is used to initialize the business event contract.

    ```
    static public SalesInvoicePostedBusinessEvent
    newFromCustInvoiceJour(CustInvoiceJour \_custInvoiceJour)
    {
        SalesInvoicePostedBusinessEvent businessEvent = new
        SalesInvoicePostedBusinessEvent();
        businessEvent.parmCustInvoiceJour(_custInvoiceJour);
        return businessEvent;
    }
    ```

3. Implement a private **new** method. This method is called only from the static constructor method.

    ```
    private void new()
    {
    }
    ```

4. Implement private **parm** methods to maintain internal state.

    ```
    private CustInvoiceJour parmCustInvoiceJour(CustInvoiceJour \_custInvoiceJour = custInvoiceJour)
    {
        custInvoiceJour = \_custInvoiceJour;
        return custInvoiceJour;
    }
    ```

5. Implement the **buildContract** method.

    ```
    [Wrappable(true), Replaceable(true)]
    public BusinessEventsContract buildContract()
    {
        return
        SalesInvoicePostedBusinessEventContract::newFromCustInvoiceJour(custInvoiceJour);
    }
    ```

    For extensibility, the **buildContract** method must be attributed with the **Wrappable(true)** and **Replaceable(true)** attributes. The **buildContract** method will be called only when a business event is enabled for a company.

Here is the complete implementation of the "Sales order invoice posted" business event.

```
/// \<summary\>
/// Sales order invoice posted business event.
/// \</summary\>
[BusinessEvents(classStr(SalesInvoicePostedBusinessEventContract),
'\@AccountsReceivable:SalesOrderInvoicePostedBusinessEventName',
'\@AccountsReceivable:SalesOrderInvoicePostedBusinessEventDescription',
ModuleAxapta::SalesOrder)]
public final class SalesInvoicePostedBusinessEvent extends BusinessEventsBase
{
    private CustInvoiceJour custInvoiceJour;
    private CustInvoiceJour parmCustInvoiceJour(CustInvoiceJour \_custInvoiceJour =
    custInvoiceJour)
    {
        custInvoiceJour = \_custInvoiceJour;
        return custInvoiceJour;
    }
    /// \<summary\>
    /// Creates a \<c\>SalesInvoicePostedBusinessEvent\</c\> from a \<c\>CustInvoiceJour\</c\> record.
    /// \</summary\>
    /// \<param name = "_custInvoiceJour"\> A \<c\>CustInvoiceJour\</c\> record.\</param\>
    /// \<returns\>A \<c\>SalesInvoicePostedBusinessEvent\</c\>.\</returns\>
    static public SalesInvoicePostedBusinessEvent
    newFromCustInvoiceJour(CustInvoiceJour \_custInvoiceJour)
    {
        SalesInvoicePostedBusinessEvent businessEvent = new
        SalesInvoicePostedBusinessEvent();
        businessEvent.parmCustInvoiceJour(_custInvoiceJour);
        return businessEvent;
    }
    private void new()
    {
    }
    [Wrappable(true), Replaceable(true)]
    public BusinessEventsContract buildContract()
    {
        return SalesInvoicePostedBusinessEventContract::newFromCustInvoiceJour(custInvoiceJour);
    }
}
```

### BusinessEventsContract extension

A business event contract class extends the **BusinessEventsContract** class. It defines and populates the payload of the business event. Although there is some variation across business events, the basic structure of the business event contract is consistent.

The process of implementing a business event contract involves extending the **BusinessEventContract** class, defining internal state, implementing an initialization method, providing a static constructor method, and implementing **parm** methods to access the contract state.

1. Extend the **BusinessEventContract** class.

    ```
    [DataContract]
    public final class SalesInvoicePostedBusinessEventContract extends
    BusinessEventsContract
    ```

    The class must be attributed with the **DataContract** attribute.

2. Add private variables to hold the contract state.

    ```
    private CustInvoiceAccount invoiceAccount;
    private CustInvoiceId invoiceId;
    private SalesIdBase salesId;
    private TransDate invoiceDate;
    private DueDate invoiceDueDate;
    private AmountMST invoiceAmount;
    private TaxAmount invoiceTaxAmount;
    private LegalEntityDataAreaId legalEntity;
    ```

3. Implement a private initialization method.

    ```
    private void initialize(CustInvoiceJour \_custInvoiceJour)
    {
        invoiceAccount = \_custInvoiceJour.InvoiceAccount;
        invoiceId = \_custInvoiceJour.InvoiceId;
        salesId = \_custInvoiceJour.SalesId;
        invoiceDate = \_custInvoiceJour.InvoiceDate;
        invoiceDueDate = \_custInvoiceJour.DueDate;
        invoiceAmount = \_custInvoiceJour.InvoiceAmountMST;
        invoiceTaxAmount = \_custInvoiceJour.SumTaxMST;
        legalEntity = \_custInvoiceJour.DataAreaId;
    }
    ```

    The **initialize** method is responsible for setting the business event contract class's private state, based on data that is provided through the static constructor method.

4. Provide a static constructor method.

    ```
    public static SalesInvoicePostedBusinessEventContract
    newFromCustInvoiceJour(CustInvoiceJour \_custInvoiceJour)
    {
        var contract = new SalesInvoicePostedBusinessEventContract();
        contract.initialize(_custInvoiceJour);
        return contract;
    }
    ```

    The static constructor method calls a private **initialize** method to initialize the private class state.

5. Implement **parm** methods to access the contract state.

    ```
    [DataMember('InvoiceAccount')]
    public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount \_invoiceAccount = invoiceAccount)
    {
        invoiceAccount = \_invoiceAccount;
        return invoiceAccount;
    }
    ```

    The **parm** methods should be attributed with the **DataMember('\<name\>')** attribute. The name that you provide on the attribute (for example **'InvoiceAccount'**) will be visible to data contract consumers.

> [!NOTE]
> - **RecId** values should not be part of a business event payload. Use the alternate key (AK) instead.
> - Enumeration (enum) values must be converted to their symbol value for publishing. Use the **enum2Symbol** method to convert an enum's value to the symbol string. Here is an example:
>
>    ```
>    status = enum2Symbol(enumNum(CustVendDisputeStatus), \_custDispute.Status);
>    ```

In some cases, population of the data contract's internal state will require that you implement additional retrieval methods. These retrieval methods should be implemented as private methods, and they should be called from the **initialize** method.

Here is the complete implementation of the "Sales order invoice posted" business event contract.

```
/// \<summary\>
/// The data contract for a \<c\>SalesInvoicePostedBusinessEvent\</c\>.
/// \</summary\>
[DataContract]
public final class SalesInvoicePostedBusinessEventContract extends
BusinessEventsContract
{
    private CustInvoiceAccount invoiceAccount;
    private CustInvoiceId invoiceId;
    private SalesIdBase salesId;
    private TransDate invoiceDate;
    private DueDate invoiceDueDate;
    private AmountMST invoiceAmount;
    private TaxAmount invoiceTaxAmount;
    private LegalEntityDataAreaId legalEntity;
    /// \<summary\>
    /// Creates a \<c\>SalesInvoicePostedBusinessEventContract\</c\> from a \<c\>CustInvoiceJour\</c\> record.
    /// \</summary\>
    /// \<param name = "_custInvoiceJour"\>A \<c\>CustInvoiceJour\</c\> record.\</param\>
    /// \<returns\>A \<c\>SalesInvoicePostedBusinessEventContract\</c\>.\</returns\>
    public static SalesInvoicePostedBusinessEventContract
    newFromCustInvoiceJour(CustInvoiceJour \_custInvoiceJour)
    {
        var contract = new SalesInvoicePostedBusinessEventContract();
        contract.initialize(_custInvoiceJour);
        return contract;
    }
    private void initialize(CustInvoiceJour \_custInvoiceJour)
    {
        invoiceAccount = \_custInvoiceJour.InvoiceAccount;
        invoiceId = \_custInvoiceJour.InvoiceId;
        salesId = \_custInvoiceJour.SalesId;
        invoiceDate = \_custInvoiceJour.InvoiceDate;
        invoiceDueDate = \_custInvoiceJour.DueDate;
        invoiceAmount = \_custInvoiceJour.InvoiceAmountMST;
        invoiceTaxAmount = \_custInvoiceJour.SumTaxMST;
        legalEntity = \_custInvoiceJour.DataAreaId;
    }
    private void new()
    {
    }
    [DataMember('InvoiceAccount')]
    public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount \_invoiceAccount
    = invoiceAccount)
    {
        invoiceAccount = \_invoiceAccount;
        return invoiceAccount;
    }
    [DataMember('InvoiceId')]
    public CustInvoiceId parmInvoiceId(CustInvoiceId \_invoiceId = invoiceId)
    {
    invoiceId = \_invoiceId;
    return invoiceId;
    }
    [DataMember('SalesOrderId')]
    public SalesIdBase parmSaleOrderId(SalesIdBase \_salesId = salesId)
    {
        salesId = \_salesId;
        return salesId;
    }
    [DataMember('InvoiceDate')]
    public TransDate parmInvoiceDate(TransDate \_invoiceDate = invoiceDate)
    {
        invoiceDate = \_invoiceDate;
        return invoiceDate;
    }
    [DataMember('InvoiceDueDate')]
    public DueDate parmInvoiceDueDate(DueDate \_invoiceDueDate = invoiceDueDate)
    {
        invoiceDueDate = \_invoiceDueDate;
        return invoiceDueDate;
    }
    [DataMember('InvoiceAmountInAccountingCurrency')]
    public AmountMST parmInvoiceAmount(AmountMST \_invoiceAmount = invoiceAmount)
    {
        invoiceAmount = \_invoiceAmount;
        return invoiceAmount;
    }
    [DataMember('InvoiceTaxAmount')]
    public TaxAmount parmInvoiceTaxAmount(TaxAmount \_invoiceTaxAmount =
    invoiceTaxAmount)
    {
        invoiceTaxAmount = \_invoiceTaxAmount;
        return invoiceTaxAmount;
    }
    [DataMember('LegalEntity')]
    public LegalEntityDataAreaId parmLegalEntity(LegalEntityDataAreaId \_legalEntity
    = legalEntity)
    {
        legalEntity = \_legalEntity;
        return legalEntity;
    }
}
```

## Sending a business event

You must modify application code so that it sends the business event at the appropriate point. Often, you can use a common point within a framework. Documents that extend **SourceDocument** have a common point for creating and sending a business event. For more information, see [Source document framework support](https://msdyneng.visualstudio.com/FinOps/_wiki/wikis/FinOps.wiki?wikiVersion=GBwikiMaster&pagePath=%2FHome%2FD365%20Finance%20and%20Operations%2FAuthoring%20business%20events#Source-document-framework-support).

Other frameworks also provide common points for sending business events. For example, the **CustVendVoucher** class hierarchy has a **post** method that is used to send business events that are related to posting customer or vendor vouchers. Overrides of the base class implementation provide specialization of the logic for sending business events. For an example, see **CustVoucher.createBusinessEvent** or **VendVoucher.createBusinessEvent**.

The sending of a business event is linked to the commit of the underlying transaction. If the underlying transaction is aborted, the business event won't be sent. Therefore, applications can "send" the business event at the point where the payload information is available.

The business events framework determines whether a business event is published to a consumer. As a general rule, applications should always "send" a business event, regardless of whether the business event is enabled. If significant additional logic is required, or if the logic for sending a business event has a performance impact, an application can check whether a specific business event is enabled before it runs business logic that is associated with sending business events. This check is done through the **BusinessEventsConfigurationReader::isBusinessEventEnabled** method.

```
if (BusinessEventsConfigurationReader::isBusinessEventEnabled(new
CollectionStatusUpdatedBusinessEvent()))
{
    while select dispute
    where dispute.Status == CustVendDisputeStatus::PromiseToPay
    && dispute.FollowUpDate \< \_currentDate
    exists join custTrans
    where custTrans.RecId == dispute.CustTrans
    && !custTrans.Closed
    exists join \_tmpCustAging
    where \_tmpCustAging.AccountNum == custTrans.AccountNum
    {
        CollectionStatusUpdatedBusinessEvent::newFromCustDispute(dispute).send();
    }
}
```

## Source document framework support

The source document framework supports sending business events automatically as part of the transition from an in-process state to a completed state for the document. To take advantage of this capability, documents that extend the source document framework must implement an extension of the **SourceDocumentStateInProcess.getBusinessEvent** method to create and return the correct **BusinessEventsBase** extension type.

## Extending a business event payload

You might want to publish additional information as part of the payload of a business event. To send this additional information, you must extend the business event's standard payload.

### Example scenario

This example shows how to extend the **CustFreeTextInvoicePostedBusinessEventContract** so that it includes a customer classification. This customer classification is an industry-based custom classification.

#### Step 1: Create an extended business event contract

Create a contract that consists of the standard business event contract plus any additional information that must be included in the payload.

    ```
    [DataContract]
    public final class CustFreeTextInvoicePostedBusinessEventExtendedContract
    extends BusinessEventsContract
    {
        // standard contract
        private CustFreeTextInvoicePostedBusinessEventContract
        custFreeTextInvoicePostedBusinessEventContract;
        // contract extensions
        private str customerClassification;
    }
    ```

#### Step 2: Create an initialize method

Create an **initialize** method that initializes the value of the private contract.

    ```
    private void initialize(CustFreeTextInvoicePostedBusinessEventContract
    \_custFreeTextInvoicePostedBusinessEventContract)
    {
        custFreeTextInvoicePostedBusinessEventContract =
        \_custFreeTextInvoicePostedBusinessEventContract;
    }
    ```

#### Step 3: Create a static newFrom method

Create a static **newFrom** method that takes the standard contract as an argument and calls the **initialize** method.

    ```
    public static CustFreeTextInvoicePostedBusinessEventExtendedContract
    newFromCustFreeTextInvoicePostedBusinessEventContract(CustFreeTextInvoicePostedBusinessEventContract
    \_custFreeTextInvoicePostedBusinessEventContract)
    {
        var contract = new CustFreeTextInvoicePostedBusinessEventExtendedContract();
        contract.initialize(_custFreeTextInvoicePostedBusinessEventContract);
        return contract;
    }
    ```

#### Step 4: Map parm methods

Copy the **parm** methods from the standard data contract, and modify each method so that it gets and sets values in the class's standard contract instance.

```
[DataMember('InvoiceAccount')]
public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount \_invoiceAccount
= custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAccount())
{
    return
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAccount(_invoiceAccount);
}
[DataMember('InvoiceId')]
public CustInvoiceId parmInvoiceId(CustInvoiceId \_invoiceId =
custFreeTextInvoicePostedBusinessEventContract.parmInvoiceId())
{
    return custFreeTextInvoicePostedBusinessEventContract.parmInvoiceId(_invoiceId);
}
```

#### Step 5: Add parms methods for additional payload data

```
[DataMember('CustomerClassification')]
public CustomerClassification parmCustomerClassification(CustomerClassification
\_customerClassification = customerClassification)
{
    customerClassification = \_customerClassification;
    return customerClassification;
}
```

Here is the complete implementation of the extended business contract.

```
[DataContract]
public final class CustFreeTextInvoicePostedBusinessEventExtendedContract
extends BusinessEventsContract
{
    // standard contract
    private CustFreeTextInvoicePostedBusinessEventContract
    custFreeTextInvoicePostedBusinessEventContract;
    // contract extensions
    private str customerClassification;
    public static CustFreeTextInvoicePostedBusinessEventExtendedContract
    newFromCustFreeTextInvoicePostedBusinessEventContract(CustFreeTextInvoicePostedBusinessEventContract
    \_custFreeTextInvoicePostedBusinessEventContract)
    {
        var contract = new CustFreeTextInvoicePostedBusinessEventExtendedContract();
        contract.initialize(_custFreeTextInvoicePostedBusinessEventContract);
        return contract;
    }
    private void initialize(CustFreeTextInvoicePostedBusinessEventContract
    \_custFreeTextInvoicePostedBusinessEventContract)
    {
        custFreeTextInvoicePostedBusinessEventContract =
        \_custFreeTextInvoicePostedBusinessEventContract;
    }
    private void new()
    {
    }
    [DataMember('InvoiceAccount')]
    public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount \_invoiceAccount
    = custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAccount())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAccount(_invoiceAccount);
    }
    [DataMember('InvoiceId')]
    public CustInvoiceId parmInvoiceId(CustInvoiceId \_invoiceId =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceId())
    {
        return custFreeTextInvoicePostedBusinessEventContract.parmInvoiceId(_invoiceId);
    }
    [DataMember('InvoiceDate')]
    public TransDate parmInvoiceDate(TransDate \_invoiceDate =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceDate())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceDate(_invoiceDate);
    }
    [DataMember('InvoiceDueDate')]
    public DueDate parmInvoiceDueDate(DueDate \_invoiceDueDate =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceDueDate())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceDueDate(_invoiceDueDate);
    }
    [DataMember('InvoiceAmountInAccountingCurrency')]
    public AmountMST parmInvoiceAmount(AmountMST \_invoiceAmount =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAmount())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAmount(_invoiceAmount);
    }
    [DataMember('InvoiceTaxAmount')]
    public TaxAmount parmInvoiceTaxAmount(TaxAmount \_invoiceTaxAmount =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceTaxAmount())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceTaxAmount(_invoiceTaxAmount);
    }
    [DataMember('LegalEntity')]
    public LegalEntityDataAreaId parmLegalEntity(LegalEntityDataAreaId \_legalEntity
    = custFreeTextInvoicePostedBusinessEventContract.parmLegalEntity())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmLegalEntity(_legalEntity);
    }
    // contract extensions
    [DataMember('CustomerClassification')]
    public CustomerClassification parmCustomerClassification(CustomerClassification
    \_customerClassification = customerClassification)
    {
        customerClassification = \_customerClassification;
        return customerClassification;
    }
}
```

#### Step 6: Wrap the buildContract method

Provide a build contract implementation that calls **next** to load the standard business event contract and populates any payload extensions. Here is the complete class.

```
[ExtensionOf(classStr(CustFreeTextInvoicePostedBusinessEvent))]
public final class FreeTextInvoicePostedBusinessEventContract_Extension
{
    public BusinessEventsContract buildContract()
    {
        var businessEventContract =
        CustFreeTextInvoicePostedBusinessEventExtendedContract::newFromCustFreeTextInvoicePostedBusinessEventContract(next
        buildContract());
        businessEventContract.parmCustomerClassification(CustomerClassifier::deriveCustomerClassification(businessEventContract.parmInvoiceAccount()));
        return businessEventContract;
    }
}
```

## Summary

You can easily extend the payload of a business event by implementing a business event contract that supplements the standard business event contract, and an extension class that uses Chain of Command (CoC) to wrap the implementation of the **buildContract** method.
