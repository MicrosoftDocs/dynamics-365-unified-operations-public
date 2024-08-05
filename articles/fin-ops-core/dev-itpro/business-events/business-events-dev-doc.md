---
title: Business events developer documentation
description: Learn about the development process and best practices for implementing business events through understanding intent, fidelity, and adding custom endpoint types.
author: jaredha
ms.author: kamanick
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/19/2024
ms.reviewer: johnmichalak
ms.search.region: Global for most topics. Set Country/Region name for localizations
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Business events developer documentation

[!include[banner](../includes/banner.md)]

This article walks you through the development process and best practices for implementing business events.

## What is a business event, and what isn't a business event?

This question comes up every time that we start to think about use cases where business events can help. Is the creation of a vendor a business event? Is confirmation of a purchase order a business event? Is it a business event if you capture the event at the table level? Or should business events be captured only at the business logic level in a business process? These questions aren't just valid, but they are also a key article of discussion when a solution is planned and architected for integration. The following guidelines can help with this thought process and decision making.

## Intent

The intent behind capturing a business event must be clearly understood. In other words, what is the reason for capturing the business event, and how it will be used by the recipient?

If your intent is to capture a business event so that you can take a business action outside finance and operations apps in response to a business event that occurs in the finance and operations apps, you have a good use case for business events. The business action that is taken in response to the business event can be to notify users about the business event and/or to call into another business application to take a business action, such as creation of a sales order. It's important that you look at the business action generically and not base the need for a business event on the type of business action that will be taken.

If your intent is to transfer data to a recipient and, in effect, realize a data export scenario, you don't have a good use case for business events. In fact, the use of business events for data transfer scenarios is a misuse of the business events framework. Such scenarios must continue to use data export mechanisms that are already available in data management.

## Fidelity

When the intent is clear, and a legitimate need for a business event is established, the next step is to evaluate the approach that must be used to capture the business event. This section summarizes the approach that must be evaluated.

Regardless of the approach that is used, the fidelity of business events is significant, because it helps guarantee that the following aspects are taken care of. Therefore, it must influence the design choice for implementing the business event. However, the design choice that you make to implement a business event must not influence the concept of business events. In other words, the chosen design must not be used as a decision-making tool, to determine whether an event is a business event. The intent must be used to make those decisions.

- **Durable business events** – No false business events should be sent to the recipient. If a purchase order confirmation business event is sent out, the recipient expects and must trust that the purchase order was really confirmed. The design choice must help guarantee this transactional nature. Therefore, you must not make a design choice that violates the recipient's expectations.
- **Targeted** – Business events must be designed to optimize the consumption story for the recipient. In other words, you should make it as easy as possible for the recipient to consume business events. Therefore, business events must be as specific as possible and must be targeted to specific use cases. They must not be generic, so that the consumer has to determine what the business event is for by trying to understand the payload. The design choice must allow for preservation of targeted business events.
- **Noiseless** – The design should include very little effort to filter out noise. To make business events very specific, avoid writing filtering logic to filter out conditions that don't match the expected business event. The chosen approach must help guarantee that the business event is implemented in code at a sufficiently specific point so that no filtering of noise is required. Any attempt to filter noise by adding logic can affect performance and might also become complicated in specific use cases.

The following table compares capture at the business and table levels.

| Capture at the business logic level | Capture at the table level |
|-------------------------------------|----------------------------|
| Capture at this level helps guarantee durability because it occurs in the transaction. | Capture at this level helps guarantee durability because it occurs in the transaction. |
| Capture at this level allows for targeted business events. | Because events are captured at a lower level, it's difficult to provide targeted business events. |
| It's easy to remain noiseless. | It's difficult to remain noiseless unless additional effort is made to implement sound logic that filters out noise. |
| Capture at this level provides additional context for the business process, and can significantly improve the durability and quality of the payload. | Because events are captured at a lower level, business process context is probably lost. |

> [!NOTE]
> In general, if you implement business events at the table level, you might face other challenges, in addition to the challenges that are described in the preceding table. For example, if the business logic is run via a stored procedure that updates data in the underlying table, the business event might not even be generated, because it was implemented in the table insert method in X++. You might encounter additional challenges in specific use cases. Therefore, we don't recommend that you implement business events at the table level.

## Implement a business event

The process for implementing a business event and sending it is fairly straightforward.

1. Build the contract.
2. Build the event.
3. Add code to send the event. 

Two classes must be implemented:

- **Business event** – This class extends the **BusinessEventsBase** class. It supports constructing the business event, building the payload, and sending the business event.
- **Business event contract** – This class extends the **BusinessEventsContract** class. It defines the payload of the business event and allows for population of the contract at runtime.

### BusinessEventsBase extension

#### Naming convention

The names of business events should follow the pattern \<noun or noun phrase\>\<past tense action\>BusinessEvent. The \<noun or noun phrase\> part of the name should comply with existing definitions for application area prefixes.

**Examples**

- VendorInvoicePostedBusinessEvent
- CollectionLetterSentBusinessEvent

#### Implementation

The process of implementing an extension of the **BusinessEventsBase** class is straightforward. It involves extending the **BusinessEventsBase** class, and implementing a static constructor method, a private **new** method, methods to maintain internal state, and the **buildContract** method.

1. Implement a static **newFrom\<my\_buffer\>** method. The \<my\_buffer\> part of the method name is typically the table buffer that is used to initialize the business event contract.

    ```xpp
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

    ```xpp
    [BusinessEvents(classStr(SalesInvoicePostedBusinessEventContract),
    'AccountsReceivable:SalesOrderInvoicePostedBusinessEventName','AccountsReceivable:SalesOrderInvoicePostedBusinessEventDescription',ModuleAxapta::SalesOrder)]
    public class SalesInvoicePostedBusinessEvent extends BusinessEventsBase
    ```

    Note the **BusinessEvents** attribute. This attribute provides the business events framework with information about the business event's contract, name, and description. It also provides the module that the business event is part of. Labels must be defined for the name and description arguments. However, these labels should be referenced without the at symbol (@) to avoid storing localized data.

3. Implement a private **new** method. This method is called only from the static constructor method.

    ```xpp
    private void new()
    {
    }
    ```

4. Implement private **parm** methods to maintain internal state.

    ```xpp
    private CustInvoiceJour parmCustInvoiceJour(CustInvoiceJour _custInvoiceJour = custInvoiceJour)
    {
        custInvoiceJour = _custInvoiceJour;
        return custInvoiceJour;
    }
    ```

5. Implement the **buildContract** method. Note that you need an **EventContract** stub for this step.

    ```xpp
    [Wrappable(false), Replaceable(false)]
    public BusinessEventsContract buildContract()
    {
        return
        SalesInvoicePostedBusinessEventContract::newFromCustInvoiceJour(custInvoiceJour);
    }
    ```

    The **buildContract** method is called only when a business event is enabled for a company.

Here is the complete implementation of the "Sales order invoice posted" business event.

```xpp
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
    [Wrappable(false), Replaceable(false)]
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

    ```xpp
    [DataContract]
    public final class SalesInvoicePostedBusinessEventContract extends
    BusinessEventsContract
    ```

    The class must have the **DataContract** attribute.

2. Add private variables to hold the contract state.

    ```xpp
    private CustInvoiceAccount invoiceAccount;
    private CustInvoiceId invoiceId;
    private SalesIdBase salesId;
    private TransDate invoiceDate;
    private DueDate invoiceDueDate;
    private AmountMST invoiceAmount;
    private TaxAmount invoiceTaxAmount;
    private LegalEntityDataAreaId legalEntity;
    ```

3. Implement a protected initialization method.

    ```xpp
    protected void initialize(CustInvoiceJour _custInvoiceJour)
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

    The **initialize** method is responsible for setting the private state of the business event contract class, based on data that is provided through the static constructor method. It should be protected so that a [Chain of Command (CoC)](../extensibility/method-wrapping-coc.md) class extension can be used to extend the contract class.

4. Implement a static constructor method.

    ```xpp
    public static SalesInvoicePostedBusinessEventContract
    newFromCustInvoiceJour(CustInvoiceJour _custInvoiceJour)
    {
        var contract = new SalesInvoicePostedBusinessEventContract();
        contract.initialize(_custInvoiceJour);
        return contract;
    }
    ```

    The static constructor method calls the **initialize** method to initialize the private class state.

5. Implement **parm** methods to access the contract state.

    ```xpp
    [DataMember('InvoiceAccount'), BusinessEventsDataMember("@AccountsReceivable:InvoiceAccount")]
    public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount _invoiceAccount = invoiceAccount)
    {
        invoiceAccount = _invoiceAccount;
        return invoiceAccount;
    }
    ```

    The **parm** methods should have the **DataMember('\<name\>')** and **BusinessEventsDataMember('\<description\>')** attributes. The name that you provide on the **DataMember** attribute (for example, **'InvoiceAccount'**) will be visible to data contract consumers. The description that you provide in the **BusinessEventsDataMember** attribute will be visible in the Business Events catalog user interface (UI) and used to describe this contract's data members.

> [!NOTE]
> - **RecId** values should not be part of a business event's payload. Use the alternate key (AK) instead.
> - Enumeration (enum) values must be converted to their symbol value before they can be published. Use the **enum2Symbol** method to convert an enum's value to the symbol string. Here is an example:
>
>    ```xpp
>    status = enum2Symbol(enumNum(CustVendDisputeStatus), _custDispute.Status);
>    ```

In some cases, population of the data contract's internal state requires that you implement additional retrieval methods. These retrieval methods should be implemented as private methods, and they should be called from the **initialize** method.

Here is the complete implementation of the "Sales order invoice posted" business event contract.

```xpp
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
    protected void initialize(CustInvoiceJour _custInvoiceJour)
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

You must modify application code so that it sends the business event at the appropriate point. Often, you can use a common point in a framework. Documents that extend **SourceDocument** have a common point for creating and sending a business event. For more information, see the [Source document framework support](#source-document-framework-support) section later in this article.

Other frameworks also provide common points for sending business events. For example, the **CustVendVoucher** class hierarchy in the Application Object Tree (AOT) has a **post** method that is used to send business events that are related to posting customer or vendor vouchers. Overrides of the base class implementation provide specialization of the logic for sending business events. For an example, see **CustVoucher.createBusinessEvent** or **VendVoucher.createBusinessEvent** in the AOT.

The sending of a business event is linked to the commit of the underlying transaction. If the underlying transaction is aborted, the business event won't be sent. Therefore, applications can send the business event at the point where the payload information is available.

The business events framework determines whether a business event is published to a consumer. As a general rule, applications should always send a business event, regardless of whether the business event is enabled. If significant additional logic is required, or if the logic for sending a business event has a performance impact, an application can check whether a specific business event is enabled before it runs business logic that is associated with sending business events. This check is done through the **BusinessEventsConfigurationReader::isBusinessEventEnabled** method.

```xpp
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

#### Step 1: Create an extension class for the business event contract

Create an extension class of the contract class you are extending to add information that must be included in the payload.

```xpp
[ExtensionOf(classStr(CustFreeTextInvoicePostedBusinessEventContract))]
internal final class CustFreeTextInvoicePostedBusinessEventContractMyModel_Extension
{
    // contract extension state
    private str customerClassification;
}
```

#### Step 2: Extend the initialize method through Chain of Command

Create a Chain of Command extension of the **initialize** method that initializes the value of the private contract.

```xpp
protected void initialize(CustInvoiceJour _custInvoiceJour)
{
    next initialize(_custInvoiceJour);
    
    customerClassification = 'StandardCustomer';
}
```
#### Step 3: Add parm methods for additional fields that you want to add to the payload

```xpp
// contract extension data members
[DataMember('MyModelCustomerClassification')]
public str parmMyModelCustomerClassification(str _customerClassification = customerClassification)
{
    customerClassification = _customerClassification;
    return customerClassification;
}
```

Here is the complete implementation of the extended business contract.

Follow the [standard naming guidelines for extensions](../extensibility/naming-guidelines-extensions.md) when creating your class to avoid collisions with your newly added fields.

```xpp
[ExtensionOf(classStr(CustFreeTextInvoicePostedBusinessEventContract))]
internal final class CustFreeTextInvoicePostedBusinessEventContractMyModel_Extension
{
    // contract extension private state
    private str customerClassification;
    protected void initialize(CustInvoiceJour _custInvoiceJour)
    {
        next initialize(_custInvoiceJour);

        customerClassification = 'StandardCustomer';
    }

    // contract extension data members
    [DataMember('MyModelCustomerClassification')]
    public str parmMyModelCustomerClassification(str _customerClassification = customerClassification)
    {
        customerClassification = _customerClassification;
        return customerClassification;
    }
}
```

## Extending filters so that they have custom fields (if the middleware supports this extension)

Some middleware systems allow for filtering of the events. For example, Microsoft Azure Service Bus has a property bag that can be populated with key-value pairs. These key-value pairs can be used to filter events when reading from the Service Bus Queue or Topic. Additionally, Azure Event Grid has filterable message properties such as **Subject**, **Event Type**, and **ID**. To support these various properties for the different systems, the business events framework uses a concept that is named *payload context*. This concept can be extended so that it includes custom fields that the different eventing systems can use for filtering.

### Payload context

The business events framework supports the payload context concept. Payload context provides a way to decorate messages that the framework sends with context about the payload. In some scenarios, additional context might be required when messages are sent to endpoints. Therefore, the framework has hookpoints where the context can be overwritten and the adapters can be customized.

### Step 1: Add a custom payload context

A custom payload context must be extended from the **BusinessEventsCommitLogPayloadContext** class.

```xpp
class CustomCommitLogPayloadContext extends BusinessEventsCommitLogPayloadContext
{
    private utcdatetime eventTime;
    public utcdatetime parmEventTime(utcdatetime _eventTime = eventTime)
    {
        eventTime = _eventTime;
        return eventTime;
    }
}
```

### Step 2: Construct the custom payload context

A Chain of Command (CoC) extension must be written for the **BusinessEventsSender.buildPayloadContext** method, so that it can construct the new payload context type.

```xpp
[ExtensionOf(classStr(BusinessEventsSender))]
public final class CustomPayloadContextBusinessEventsSender_Extension
{
    protected BusinessEventsCommitLogPayloadContext
    buildPayloadContext(BusinessEventsCommitLogEntry _commitLogEntry)
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

### Step 3: Consume the custom payload context from an adapter

Adapters that consume payload context are written in such a way that they expose CoC methods that allow for the consumption of new payload contexts. The following example shows what this step looks like for the Service Bus adapter. This adapter has a generic property bag that Service Bus consumers can filter on.

The **BusinessEventsServiceBusAdapter** class has the CoC method that is named **addProperties**.

```xpp
using Microsoft.ServiceBus.Messaging;

[ExtensionOf(classStr(BusinessEventsServiceBusAdapter))]
public final class CustomBusinessEventsServiceBusAdapter_Extension
{
    protected void addProperties(BrokeredMessage _message, BusinessEventsEndpointPayloadContext _context)
    {
        next addProperties(_message, _context);
        if (_context is CustomCommitLogPayloadContext)
        {
            CustomCommitLogPayloadContext customPayloadContext = _context as CustomCommitLogPayloadContext;
            var propertyBag = _message.Properties;
            propertyBag.Add('EventId', customPayloadContext.parmEventId());
            propertyBag.Add('BusinessEventId', customPayloadContext.parmBusinessEventId());
            // Convert the enum to string to be able to serialize the property.
            propertyBag.Add('BusinessEventCategory', enum2Symbol(enumNum(ModuleAxapta),
            customPayloadContext.parmBusinessEventCategory()));
            propertyBag.Add('LegalEntity', customPayloadContext.parmLegalEntity());
            propertyBag.Add('EventTime', customPayloadContext.parmEventTime());
        }
    }
}
```


The **BusinessEventsEventGridAdapter** class has the CoC method that is named **setContextProperties**. The following example shows what this step looks like for the Event Grid Adapter. The eventGridMessage has a Subject that can be filtered on.

```xpp
using Microsoft.Azure.EventGrid.Models;

[ExtensionOf(classStr(BusinessEventsEventGridAdapter))]
public final class CustomBusinessEventsEventGridAdapter_Extension
{
    protected void setContextProperties(EventGridEvent _eventGridEvent, BusinessEventsEndpointPayloadContext _context)
    {
        next setContextProperties(_eventGridEvent, _context);
        if (_context is CustomCommitLogPayloadContext)
        {
            CustomCommitLogPayloadContext customPayloadContext = _context as CustomCommitLogPayloadContext;

            _eventGridEvent.Subject = _eventGridEvent.Subject + customPayloadContext.parmLegalEntity();
        }
    }
}
```

## Adding a custom endpoint type

The business events framework supports the addition of new endpoint types to the out-of-box endpoint types. This section provides an example that shows how to add new custom endpoint types.

### Step 1: Add a new endpoint type

Each endpoint type is represented by the **BusinessEventsEndpointType** enum. The first step in the process of adding a new endpoint is to extend this enum, as shown in the following illustration.

![Enum extension.](../media/customendpoint1.png)

### Step 2: Add a new endpoint table to the hierarchy

All endpoint data is stored in a hierarchy table. The root of this table is the BusinessEventsEndpoint table. A new endpoint table must extend this root table by setting the **Support Inheritance** property to **Yes** and the **Extends** property to **"BusinessEventsEndpoint"** (or any other endpoint in the BusinessEventsEndpoint hierarchy).

![Table extends BusinessEventsEndpoint.](../media/customendpoint2.png)

The new table then holds the definition of the custom fields that are required to initialize and communicate with the endpoint in code. To help avoid conflict, you should qualify field names to the specific endpoint where they belong. For example, two endpoints can have the concept of a **URL** field. To distinguish the fields, names should be specific to the custom endpoint. For example, name the field for the custom endpoint **CustomURL**.

![New table with custom fields.](../media/customendpoint3.png)

### Step 3: Add a new endpoint adapter class that implements the IBusinessEventsEndpoint interface

The new endpoint adapter class must implement the **IBusinessEventsEndpoint** interface. It must also be decorated with the **BusinessEventsEndpointAttribute** attribute.

```xpp
[BusinessEventsEndpoint(BusinessEventsEndpointType::CustomEndpoint)]
public class CustomEndpointAdapter implements IBusinessEventsEndpoint
{
```

The **initialize** method should be implemented to check the type of the **BusinessEventsEndpoint** buffer that is passed in, and then, if the buffer is of the correct type, initialize it, as shown in the following example.

```xpp
if (!(_endpoint is CustomBusinessEventsEndpoint))
{
    BusinessEventsEndpointManager::logUnknownEndpointRecord(tableStr(CustomBusinessEventsEndpoint),
    _endpoint.RecId);
}
CustomBusinessEventsEndpoint customBusinessEventsEndpoint = _endpoint as CustomBusinessEventsEndpoint;
customField = customBusinessEventsEndpoint.CustomField;
if (!customField)
{
    throw warning(strFmt("\@BusinessEvents:MissingAdapterConstructorParameter",
    classStr(CustomEndpointAdapter), varStr(customField)));
}
```

### Step 4: Extend the EndpointConfiguration form

Add a new group control under FormDesign/BusinessEventsEndpointConfigurationGroup/EndpointFieldsGroup/ to hold your custom field input.

![New group control for custom field input.](../media/customendpoint4.png)

The custom field input should be bound to the new table and field that you created in the previous step. Create a class extension to extend the **getConcreteType** and **showOtherFields** methods of **BusinessEventsEndpointConfiguration** form, as shown in the following example.

![Class extension for data source.](../media/customendpoint5.png)

```xpp
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

## Adding human-readable data fields to the payload

This feature is available in Platform update 30 and later.

The serialization of business events uses FormJsonSerializer to serialize objects in the data contract. FormJsonSerializer can format **UtcDataTime** values in the ISO 8601 date and time format. This format is human-readable when the payload of a business event is viewed. For example, a **UtcDataTime** value can now be formatted as **"2007-12-05T14:30Z"** instead of **"/Date(1196865000000)/"**. In the "/Date(N)" format, N is the number of milliseconds that have passed since January 1, 1970, UTC+0. The ISO format is more often understood by tools that parse JavaScript Object Notation (JSON).

To get the human-readable format, use the extended data type (EDT) that is named **DateTimeIso8601** as the type of the value in the data contract. Alternatively, use an EDT that is derived from the **DateTimeIso8601** EDT.

```xpp
[DataMember("TestIsoEdtUtcDateTime")]
public DateTimeIso8601 testIsoEdtUtcDateTime(DateTimeIso8601 _value = this._testIsoDateTime)
{
    if (!prmIsDefault(_value))
    {
        this._testIsoDateTime = _value;
    }
    return this._testIsoDateTime;
}
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

