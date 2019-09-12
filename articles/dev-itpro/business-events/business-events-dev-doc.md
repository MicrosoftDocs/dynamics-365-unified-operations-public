---
# required metadata

title: Business events developer documentation
description: This topic walks you through the development process and best practices for implementing business events.
author: Sunil-Garg
manager: AnnBe
ms.date: 06/28/2019
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

This topic walks you through the development process and best practices for implementing business events.

## What is a business event and what is not a business event?
This question comes up every time we start to think about use cases where
business events can help. Is creation of a vendor a business event? Or is
confirming a purchase order a business event? Is it a business event if you
capture the event at the table level? Or should business events only be captured
at the business logic level in a business process? These are not only valid
questions, but also a key topic of discussion when planning and architecting a
solution for integration. The following guidelines can be used to help with this
thought process and decision making.

Intent
------

The intent behind capturing the business event must be clearly understood. In
other words, what is the reason for capturing the business event and how it is
going to be used by the recipient.

If the intent for capturing a business event is to take a business action
outside of the application in response to the business event happening, then this is a valid intent to capture the business
event. The business action that is taken in response to the business event can
be to notify users about the business event and/or to call into another
business application to take a business action like, creating a sales order. It is important to look at the business action generically and not
base the need for a business event on the type of business action that will be
taken.

If the intent of capturing the business event is to transfer data to the
recipient and in effect, realizing a data export scenario, then this will not be
a good use case for using business events. In fact, the use of business events
for data transfer use cases will be a misuse of the business events framework.
Such scenarios must continue to use data export mechanisms already available in
data management.

Fidelity
--------

When the intent is clear and a legitimate need for a business event is
established, the next step is to evaluate the approach that must be taken to
capture the business event. The following section summarizes the approach that
must be evaluated.

Regardless of which approach is taken, the fidelity of business events is
significant to ensure the following aspects are taken care of and as a result, must
influence the design choice for implementing the business event. However, the
design choice that you take to implement a business event must not influence the
concept of business events--the chosen design must not be used
as a decision-making tool to determine if it is a business event. The
intent discussed previously must be used for such decisions.

-   **Durable business events** - There should be no false business events sent
    to the recipient. If a purchase order confirmation business event was sent
    out, then the recipient must trust that the purchase order was indeed
    confirmed. The design choice must ensure this transactional nature and hence
    must not take a design choice that would violate this expectation.

-   **Targeted** - Business events must be designed to optimize the consumption
    story for the recipient. In other words, make it as easy as possible
    for the recipient to consume business events. Hence, business events must be
    as specific as possible and targeted to a specific use case. Business
    events must not be generic thereby, leaving the consumer to determine what
    the business event was for by trying to understand the payload. The design
    choice made must allow for this to be preserved.

-   **Noiseless** - There should be very little effort in the design to filter out
    the noise. To make business events very specific, avoid writing
    filtering logic to filter out conditions that do not match the expected
    business event. The chosen approach must be such that the point at which the
    business event is implemented in code is specific enough to avoid the need
    for any filtering of noise. Any attempt to filter the noise by adding logic
    can not only be taxing on performance but, it may also get complicated based
    on specific use cases.

| **Capturing at business logic level**                                                                                    | **Capturing at table level**                                                                                         |
|--------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Ensures durability by being in the transaction                                                                           | Ensures durability by being in the transaction.                                                                      |
| Allows for targeted business events.                                                                                     | Difficult to enable targeted business events due to the lower level capturing of events.                             |
| Makes it easy to remain noiseless.                                                                                       | Difficult to remain noiseless unless additional effort is taken to put sound logic in place to filter out the noise. |
| Provides additional context of the business process, which can significantly improve the durability and the quality of payload. | Business process context is most likely lost due to the lower level capturing of events.                             |


> [!NOTE]
> In general, implementing business events at the table level may pose additional challenges than what is described above. For example, if the business logic is executed via a stored procedure that updates data in the underlying table, then it is possible that the business event will not even get generated because it was implemented in the table insert method in X++. You could potentially encounter additional challenges based on specific use cases. As a result, it is not recommended that you implement business events at the table level.

## Implementing a business event

Implementing a business event and sending it is a fairly straightforward process:
1. Build the contract.
2. Build the event.
3. Add code to send the event. 

Two classes must be implemented:

- **Business event** – This class extends the **BusinessEventsBase** class. It provides support for constructing the business event, building the payload, and sending the business event.
- **Business event contract** – This class extends the **BusinessEventsContract** class. It defines the payload of the business event and allows for population of the contract at runtime. 

### BusinessEventsBase extension

#### Naming convention

The names of business events should follow this pattern: <noun/noun phrase><past tense action>BusinessEvent

**Examples**

- VendorInvoicePostedBusinessEvent
- CollectionLetterSentBusinessEvent

The <noun/noun phrase> part of the name should comply with existing definitions for application area prefixes.

#### Implementation

The process of implementing a **BusinessEventsBase** extension is straightforward. It involves extending the **BusinessEventsBase** class, and implementing a static constructor method, a private **new** method, methods to maintain internal state, and the **buildContract** method.

1. Implement a static **newFrom<my_buffer>** method. The <my_buffer> part of the method name is typically the table buffer that is used to initialize the business event contract.

    ```
    static public SalesInvoicePostedBusinessEvent
    newFromCustInvoiceJour(CustInvoiceJour _custInvoiceJour)
    {
        SalesInvoicePostedBusinessEvent businessEvent = new
        SalesInvoicePostedBusinessEvent();
        businessEvent.parmCustInvoiceJour(_custInvoiceJour);
        return businessEvent;
    }
    ```

2. Extend the **BusinessEventsBase** class.

    ```
    [BusinessEvents(classStr(SalesInvoicePostedBusinessEventContract),
    "AccountsReceivable:SalesOrderInvoicePostedBusinessEventName","AccountsReceivable:SalesOrderInvoicePostedBusinessEventDescription",ModuleAxapta::SalesOrder)]
    public class SalesInvoicePostedBusinessEvent extends BusinessEventsBase
    ```

    Note the **BusinessEvents** attribute. This attribute provides the business events framework with information about the business event's contract, name, and description, and also the module that it's part of. Labels must be defined for the name and description arguments, but should be referenced without the '@' symbol to avoid storing localized data.

3. Implement a private **new** method. This method is called only from the static constructor method.

    ```
    private void new()
    {
    }
    ```

4. Implement private **parm** methods to maintain internal state.

    ```
    private CustInvoiceJour parmCustInvoiceJour(CustInvoiceJour _custInvoiceJour = custInvoiceJour)
    {
        custInvoiceJour = _custInvoiceJour;
        return custInvoiceJour;
    }
    ```

5. Implement the **buildContract** method. Note that you'll need an EventContract stub for this step.

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
/// <summary>
/// Sales order invoice posted business event.
/// </summary>
[BusinessEvents(classStr(SalesInvoicePostedBusinessEventContract),
'AccountsReceivable:SalesOrderInvoicePostedBusinessEventName',
'AccountsReceivable:SalesOrderInvoicePostedBusinessEventDescription',
ModuleAxapta::SalesOrder)]
public class SalesInvoicePostedBusinessEvent extends BusinessEventsBase
{
    private CustInvoiceJour custInvoiceJour;
    private CustInvoiceJour parmCustInvoiceJour(CustInvoiceJour _custInvoiceJour =
    custInvoiceJour)
    {
        custInvoiceJour = _custInvoiceJour;
        return custInvoiceJour;
    }
    /// <summary\>
    /// Creates a SalesInvoicePostedBusinessEvent from a CustInvoiceJour record.
    /// <summary>
    /// param name = "_custInvoiceJour"> CustInvoiceJour record <param>
    /// <returns>A SalesInvoicePostedBusinessEvent </returns>
    static public SalesInvoicePostedBusinessEvent
    newFromCustInvoiceJour(CustInvoiceJour _custInvoiceJour)
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

The process of implementing a business event contract involves extending the **BusinessEventContract** class, defining internal state, implementing an initialization method, implementing a static constructor method, and implementing **parm** methods to access the contract state.

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
    private void initialize(CustInvoiceJour _custInvoiceJour)
    {
        invoiceAccount = _custInvoiceJour.InvoiceAccount;
        invoiceId = _custInvoiceJour.InvoiceId;
        salesId = _custInvoiceJour.SalesId;
        invoiceDate = _custInvoiceJour.InvoiceDate;
        invoiceDueDate = _custInvoiceJour.DueDate;
        invoiceAmount = _custInvoiceJour.InvoiceAmountMST;
        invoiceTaxAmount = _custInvoiceJour.SumTaxMST;
        legalEntity = _custInvoiceJour.DataAreaId;
    }
    ```

    The **initialize** method is responsible for setting the business event contract class's private state, based on data that is provided through the static constructor method.

4. Implement a static constructor method.

    ```
    public static SalesInvoicePostedBusinessEventContract
    newFromCustInvoiceJour(CustInvoiceJour _custInvoiceJour)
    {
        var contract = new SalesInvoicePostedBusinessEventContract();
        contract.initialize(_custInvoiceJour);
        return contract;
    }
    ```

    The static constructor method calls a private **initialize** method to initialize the private class state.

5. Implement **parm** methods to access the contract state.

    ```
    [DataMember('InvoiceAccount'), BusinessEventsDataMember("@AccountsReceivable:InvoiceAccount")]
    public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount _invoiceAccount = invoiceAccount)
    {
        invoiceAccount = _invoiceAccount;
        return invoiceAccount;
    }
    ```

    The **parm** methods should be attributed with the **DataMember('<name>')** and **BusinessEventsDataMember('<description>')** attributes. The name that you provide on the attribute (for example **'InvoiceAccount'**) will be visible to data contract consumers. The description provided in the BusinessEventsDataMember will be visible in the Business Events catalog UI when describing this contract's data members.

> [!NOTE]
> - **RecId** values should not be part of a business event payload. Use the alternate key (AK) instead.
> - Enumeration (enum) values must be converted to their symbol value before they can be published. Use the **enum2Symbol** method to convert an enum's value to the symbol string. Here is an example:
>
>    ```
>    status = enum2Symbol(enumNum(CustVendDisputeStatus), _custDispute.Status);
>    ```

In some cases, population of the data contract's internal state will require that you implement additional retrieval methods. These retrieval methods should be implemented as private methods, and they should be called from the **initialize** method.

Here is the complete implementation of the "Sales order invoice posted" business event contract.

```
/// <summary>
/// The data contract for a SalesInvoicePostedBusinessEvent
/// </summary>
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
    /// <summary>
    /// Creates a SalesInvoicePostedBusinessEventContract from a CustInvoiceJour record.
    /// </summary>
    /// <param name = "_custInvoiceJour"> CustInvoiceJour record</param>
    /// <returns>A SalesInvoicePostedBusinessEventContract </returns>
    public static SalesInvoicePostedBusinessEventContract
    newFromCustInvoiceJour(CustInvoiceJour _custInvoiceJour)
    {
        var contract = new SalesInvoicePostedBusinessEventContract();
        contract.initialize(_custInvoiceJour);
        return contract;
    }
    private void initialize(CustInvoiceJour _custInvoiceJour)
    {
        invoiceAccount = _custInvoiceJour.InvoiceAccount;
        invoiceId = _custInvoiceJour.InvoiceId;
        salesId = _custInvoiceJour.SalesId;
        invoiceDate = _custInvoiceJour.InvoiceDate;
        invoiceDueDate = _custInvoiceJour.DueDate;
        invoiceAmount = _custInvoiceJour.InvoiceAmountMST;
        invoiceTaxAmount = _custInvoiceJour.SumTaxMST;
        legalEntity = _custInvoiceJour.DataAreaId;
    }
    private void new()
    {
    }
    [DataMember('InvoiceAccount'), BusinessEventsDataMember("@AccountsReceivable:InvoiceAccount")]
    public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount _invoiceAccount
    = invoiceAccount)
    {
        invoiceAccount = _invoiceAccount;
        return invoiceAccount;
    }
    [DataMember('InvoiceId'), BusinessEventsDataMember("@AccountsReceivable:BusinessEventInvoiceId")]
    public CustInvoiceId parmInvoiceId(CustInvoiceId _invoiceId = invoiceId)
    {
    invoiceId = _invoiceId;
    return invoiceId;
    }
    [DataMember('SalesOrderId'), BusinessEventsDataMember("@AccountsReceivable:SalesOrderId")]
    public SalesIdBase parmSaleOrderId(SalesIdBase _salesId = salesId)
    {
        salesId = _salesId;
        return salesId;
    }
    [DataMember('InvoiceDate'), BusinessEventsDataMember("@AccountsReceivable:BusinessEventInvoiceDate")]
    public TransDate parmInvoiceDate(TransDate _invoiceDate = invoiceDate)
    {
        invoiceDate = _invoiceDate;
        return invoiceDate;
    }
    [DataMember('InvoiceDueDate'), BusinessEventsDataMember("@AccountsReceivable:InvoiceDueDate")]
    public DueDate parmInvoiceDueDate(DueDate _invoiceDueDate = invoiceDueDate)
    {
        invoiceDueDate = _invoiceDueDate;
        return invoiceDueDate;
    }
    [DataMember('InvoiceAmountInAccountingCurrency'), BusinessEventsDataMember("@AccountsReceivable:InvoiceAmountInAccountingCurrency")]
    public AmountMST parmInvoiceAmount(AmountMST _invoiceAmount = invoiceAmount)
    {
        invoiceAmount = _invoiceAmount;
        return invoiceAmount;
    }
    [DataMember('InvoiceTaxAmount'), BusinessEventsDataMember("@AccountsReceivable:InvoiceTaxAmount")]
    public TaxAmount parmInvoiceTaxAmount(TaxAmount _invoiceTaxAmount =
    invoiceTaxAmount)
    {
        invoiceTaxAmount = _invoiceTaxAmount;
        return invoiceTaxAmount;
    }
    [DataMember('LegalEntity'), BusinessEventsDataMember("@AccountsReceivable:LegalEntity")]
    public LegalEntityDataAreaId parmLegalEntity(LegalEntityDataAreaId _legalEntity
    = legalEntity)
    {
        legalEntity = _legalEntity;
        return legalEntity;
    }
}
```

## Sending a business event

You must modify application code so that it sends the business event at the appropriate point. Often, you can use a common point within a framework. Documents that extend **SourceDocument** have a common point for creating and sending a business event. For more information, see the section on source document framework support below.

Other frameworks also provide common points for sending business events. For example, the **CustVendVoucher** class hierarchy in AOT has a **post** method that is used to send business events that are related to posting customer or vendor vouchers. Overrides of the base class implementation provide specialization of the logic for sending business events. For an example, see **CustVoucher.createBusinessEvent** or **VendVoucher.createBusinessEvent** in AOT.

The sending of a business event is linked to the commit of the underlying transaction. If the underlying transaction is aborted, the business event won't be sent. Therefore, applications can send the business event at the point where the payload information is available.

The business events framework determines whether a business event is published to a consumer. As a general rule, applications should always send a business event, regardless of whether the business event is enabled. If significant additional logic is required, or if the logic for sending a business event has a performance impact, an application can check whether a specific business event is enabled before it runs business logic that is associated with sending business events. This check is done through the **BusinessEventsConfigurationReader::isBusinessEventEnabled** method.

```
if (BusinessEventsConfigurationReader::isBusinessEventEnabled(classStr(CollectionStatusUpdatedBusinessEvent)))
{
    while select dispute
    where dispute.Status == CustVendDisputeStatus::PromiseToPay
    && dispute.FollowUpDate _currentDate
    exists join custTrans
    where custTrans.RecId == dispute.CustTrans
    && !custTrans.Closed
    exists join _tmpCustAging
    where _tmpCustAging.AccountNum == custTrans.AccountNum
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

This example shows how to extend the **CustFreeTextInvoicePostedBusinessEventContract** class so that it includes a customer classification. This customer classification is an industry-based custom classification.

#### Step 1: Create an extended business event contract

Create a contract that consists of the standard business event contract plus any additional information that must be included in the payload.

    ```
    [DataContract]
    public class CustFreeTextInvoicePostedBusinessEventExtendedContract
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
    _custFreeTextInvoicePostedBusinessEventContract)
    {
        custFreeTextInvoicePostedBusinessEventContract =
        _custFreeTextInvoicePostedBusinessEventContract;
    }
    ```

#### Step 3: Create a static newFrom method

Create a static **newFrom** method that takes the standard contract as an argument and calls the **initialize** method.

    ```
    public static CustFreeTextInvoicePostedBusinessEventExtendedContract
    newFromCustFreeTextInvoicePostedBusinessEventContract(CustFreeTextInvoicePostedBusinessEventContract
    _custFreeTextInvoicePostedBusinessEventContract)
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
public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount _invoiceAccount
= custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAccount())
{
    return
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAccount(_invoiceAccount);
}
[DataMember('InvoiceId')]
public CustInvoiceId parmInvoiceId(CustInvoiceId _invoiceId =
custFreeTextInvoicePostedBusinessEventContract.parmInvoiceId())
{
    return custFreeTextInvoicePostedBusinessEventContract.parmInvoiceId(_invoiceId);
}
```

#### Step 5: Add parms methods for additional payload data

```
[DataMember('CustomerClassification')]
public CustomerClassification parmCustomerClassification(CustomerClassification
_customerClassification = customerClassification)
{
    customerClassification = _customerClassification;
    return customerClassification;
}
```

Here is the complete implementation of the extended business contract.

```
[DataContract]
public class CustFreeTextInvoicePostedBusinessEventExtendedContract
extends BusinessEventsContract
{
    // standard contract
    private CustFreeTextInvoicePostedBusinessEventContract
    custFreeTextInvoicePostedBusinessEventContract;
    // contract extensions
    private str customerClassification;
    public static CustFreeTextInvoicePostedBusinessEventExtendedContract
    newFromCustFreeTextInvoicePostedBusinessEventContract(CustFreeTextInvoicePostedBusinessEventContract
    _custFreeTextInvoicePostedBusinessEventContract)
    {
        var contract = new CustFreeTextInvoicePostedBusinessEventExtendedContract();
        contract.initialize(_custFreeTextInvoicePostedBusinessEventContract);
        return contract;
    }
    private void initialize(CustFreeTextInvoicePostedBusinessEventContract
    _custFreeTextInvoicePostedBusinessEventContract)
    {
        custFreeTextInvoicePostedBusinessEventContract =
        _custFreeTextInvoicePostedBusinessEventContract;
    }
    private void new()
    {
    }
    [DataMember('InvoiceAccount')]
    public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount _invoiceAccount
    = custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAccount())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAccount(_invoiceAccount);
    }
    [DataMember('InvoiceId')]
    public CustInvoiceId parmInvoiceId(CustInvoiceId _invoiceId =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceId())
    {
        return custFreeTextInvoicePostedBusinessEventContract.parmInvoiceId(_invoiceId);
    }
    [DataMember('InvoiceDate')]
    public TransDate parmInvoiceDate(TransDate _invoiceDate =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceDate())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceDate(_invoiceDate);
    }
    [DataMember('InvoiceDueDate')]
    public DueDate parmInvoiceDueDate(DueDate _invoiceDueDate =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceDueDate())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceDueDate(_invoiceDueDate);
    }
    [DataMember('InvoiceAmountInAccountingCurrency')]
    public AmountMST parmInvoiceAmount(AmountMST _invoiceAmount =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAmount())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceAmount(_invoiceAmount);
    }
    [DataMember('InvoiceTaxAmount')]
    public TaxAmount parmInvoiceTaxAmount(TaxAmount _invoiceTaxAmount =
    custFreeTextInvoicePostedBusinessEventContract.parmInvoiceTaxAmount())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmInvoiceTaxAmount(_invoiceTaxAmount);
    }
    [DataMember('LegalEntity')]
    public LegalEntityDataAreaId parmLegalEntity(LegalEntityDataAreaId _legalEntity
    = custFreeTextInvoicePostedBusinessEventContract.parmLegalEntity())
    {
        return
        custFreeTextInvoicePostedBusinessEventContract.parmLegalEntity(_legalEntity);
    }
    // contract extensions
    [DataMember('CustomerClassification')]
    public CustomerClassification parmCustomerClassification(CustomerClassification
    _customerClassification = customerClassification)
    {
        customerClassification = _customerClassification;
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

## Extending filters to have custom fields (if supported by the middleware)

Some middleware systems allow for filtering of the events. For example, Azure Service Bus has a property bag that can be populated with key-value pairs. These key-value pairs can be used for filtering events when reading from the Azure Service Bus Queue or Topic. Additionally, Azure Event Grid has filterable message properties like Subject, Event Type, and ID. To support these different properties for the different systems, the Business Events framework uses a concept called PayloadContext, which can be extended to include custom fields for filtering by the different eventing systems.

### Payload context

The Business Events framework supports a concept of *payload context*, which provides a means for decorating messages sent by the framework with context about the payload. In some scenarios, additional context may be required when sending messages to endpoints, so the framework has hookpoints where the context can be overwritten and the adapters can be customized.

### Adding a custom payload context

A custom payload context must extend from the class BusinessEventsCommitLogPayloadContext.

```
class CustomCommitLogPayloadContext extends
BusinessEventsCommitLogPayloadContext

{

private utcdatetime eventTime;

public utcdatetime parmEventTime(utcdatetime \_eventTime = eventTime)

{

eventTime = \_eventTime;

return eventTime;

}

}  
```

### Constructing the custom payload context

A Chain of Command (CoC) extension will need to be written for the BusinessEventsSender.buildPayloadContext method to construct the new payload context type.

```
[ExtensionOf(classStr(BusinessEventsSender))]

public final class CustomPayloadContextBusinessEventsSender_Extension

{

protected BusinessEventsCommitLogPayloadContext
buildPayloadContext(BusinessEventsCommitLogEntry \_commitLogEntry)

{

BusinessEventsCommitLogPayloadContext payloadContext = next
buildPayloadContext(_commitLogEntry);

CustomCommitLogPayloadContext customPayloadContext = new
CustomCommitLogPayloadContext();

customPayloadContext.initFromBusinessEventsCommitLogEntry(_commitLogEntry);

customPayloadContext.parmEventTime(_commitLogEntry.parmEventTime());

return customPayloadContext;

}

}  
```

### Consuming the custom payload context from an adapter

Adapters that consume payload context are written in such a way that they expose CoC methods to allow consuming new payload contexts. The following example explores what this looks like for the Service Bus adapter, which has a generic property bag that can be filtered on by the consumers of the Service Bus.

The BusinessEventsServiceBusAdapter has the CoC method called addProperties.

```
[ExtensionOf(classStr(BusinessEventsServiceBusAdapter))]

public final class CustomBusinessEventsServiceBusAdapter_Extension

{

protected void addProperties(BrokeredMessage \_message,
BusinessEventsEndpointPayloadContext \_context)

{

if (_context is CustomCommitLogPayloadContext)

{

CustomCommitLogPayloadContext customPayloadContext = \_context as
CustomCommitLogPayloadContext;

var propertyBag = \_message.Properties;

propertyBag.Add('EventId', customPayloadContext.parmEventId());

propertyBag.Add('BusinessEventId', customPayloadContext.parmBusinessEventId());

*// Convert the enum to string to be able to serialize the property.*

propertyBag.Add('BusinessEventCategory', enum2Symbol(enumNum(ModuleAxapta),
customPayloadContext.parmBusinessEventCategory()));

propertyBag.Add('LegalEntity', customPayloadContext.parmLegalEntity());

propertyBag.Add('EventTime', customPayloadContext.parmEventTime());

}

}

}  
```

## Adding a custom endpoint type
The Business Events framework supports adding new endpoint types in addition to the ones that ship out of the box. An example of how to do this is describe with the below.

### Add new endpoint type

Each endpoint type is represented by the enum BusinessEventsEndpointType. Adding a new endpoint starts by extending this enum, as shown in the following section.

![Business event endpoint](../media/customendpoint1.png)

### Add new endpoint table to the hierarchy

All endpoint data is stored in a hierarchy table, the root of which is BusinessEventsEndpoint. A new endpoint table must extend this root table by setting the Support Inheritance property = Yes, and the Extends property = “BusinessEventsEndpoint” (or any other endpoint in the BusinessEventsEndpoint hierarchy).

![Business event endpoint](../media/customendpoint2.png)

The new table will then hold the definition of the custom fields needed to initialize and communicate with this endpoint in code. To avoid the possibility of conflict, field names should be qualified to the specific endpoint where they belong. For example, two endpoints can have the concept of a “URL” field, but to distinguish them, their names should be specific to the custom endpoint like “CustomURL”.

![Business event endpoint](../media/customendpoint3.png)

### Add new EndpointAdapter class that implements IBusinessEventsEndpoint

The new endpoint adapter class must implement the IBusinessEventsEndpoint interface as well as be decorated with the BusinessEventsEndpointAttribute attribute.

```

[BusinessEventsEndpoint(BusinessEventsEndpointType::CustomEndpoint)]

public class CustomEndpointAdapter implements IBusinessEventsEndpoint

{  
```

The initialize method should be implemented to check the type of the BusinessEventsEndpoint buffer that is passed in, and initialize when it is of the correct type for this new adapter, as shown below.

```

if (!(_endpoint is CustomBusinessEventsEndpoint))

{

BusinessEventsEndpointManager::logUnknownEndpointRecord(tableStr(CustomBusinessEventsEndpoint),
\_endpoint.RecId);

}

CustomBusinessEventsEndpoint customBusinessEventsEndpoint = \_endpoint as
CustomBusinessEventsEndpoint;

customField = customBusinessEventsEndpoint.CustomField;

if (!customField)

{

throw warning(strFmt("\@BusinessEvents:MissingAdapterConstructorParameter",
classStr(CustomEndpointAdapter), varStr(customField)));

}

```

### Extend the EndpointConfiguration form

Add a new group control under FormDesign/BusinessEventsEndpointConfigurationGroup/EndpointFieldsGroup/ to hold
your custom field input.

![Business event endpoint](../media/customendpoint4.png)

The custom field input should be bound to the new table and field created in the previous step. Create a class extension to extend the getConcreteType and showOtherFields methods of BusinessEventsEndpointConfiguration form, as shown below.

![Business event endpoint](../media/customendpoint5.png)

```

[ExtensionOf(formStr(BusinessEventsEndpointConfiguration))]

final public class CustomBusinessEventsEndpointConfiguration_Extension

{

public TableName getConcreteTableType(BusinessEventsEndpointType \_endpointType)

{

TableName tableName = next getConcreteTableType(_endpointType);

if (_endpointType == BusinessEventsEndpointType::CustomEndpoint)

{

tableName = tableStr(CustomBusinessEventsEndpoint);

}

return tableName;

}

public void showOtherFields()

{

next showOtherFields();

BusinessEventsEndpointType selection =
any2Enum(EndpointTypeSelection.selection());

if (selection == BusinessEventsEndpointType::CustomEndpoint)

{

this.control(this.controlId(formControlStr(BusinessEventsEndpointConfiguration,
CustomFields))).visible(true);

}

}

}

```
