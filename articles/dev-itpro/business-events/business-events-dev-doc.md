---
# required metadata

title: Business events developer documentation
description: This documentation walks through the development process and best practice for implementing business events.
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

There are two classes that need to be implemented:
1. The business event. 
2. The business event contract. 

The business event class extends BusinessEventsBase and provides support for constructing, payload building, and sending the business event. The business event contract class extends BusinessEventsContract. It provides the definition of the business event payload and provides for the population of the contract at runtime.

### BusinessEventsBase extension

#### Naming convention  
A \<noun/noun phrase\>\<action phrase\>BusinessEvent pattern should be followed for business event names.  

Examples: VendorInvoicePostedBusinessEvent, CollectionLetterSentBusinessEvent 

The 'noun/noun phrase' portion should comply with existing application area prefix definitions.

#### Implementation
Implementing a BusinessEventsBase extension is straight forward. It consists of extending the BusinessEventsBase class and implementing a static construction method, a private new method, methods to maintain internal state, and the buildContract method.

1.  Extend the BusinessEventsBase class

```
[BusinessEvents(classStr(SalesInvoicePostedBusinessEventContract),
"\@AccountsReceivable:SalesOrderInvoicePostedBusinessEventName","\@AccountsReceivable:SalesOrderInvoicePostedBusinessEventDescription",ModuleAxapta::SalesOrder)]

public final class SalesInvoicePostedBusinessEvent extends BusinessEventsBase
```

Note the BusinessEvents attribute. This provided the business events framework with information on the business event's contract, name, description, and the module it is a part of. Labels must be defined for the name and description arguments.

2.  Implement a static newFrom\<foo\> method. Where foo is a typically a table buffer used to initialize the business event contract.

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

3. Implement a private new method. The new method is only called from the static constructor.

```
private void new()

{

}
```

4. Implement private parm methods to maintain internal state.

```
private CustInvoiceJour parmCustInvoiceJour(CustInvoiceJour \_custInvoiceJour = custInvoiceJour)
{

custInvoiceJour = \_custInvoiceJour;

return custInvoiceJour;

}
```

5. Implement buildContract method.

```
[Wrappable(true), Replaceable(true)]

public BusinessEventsContract buildContract()

{

return
SalesInvoicePostedBusinessEventContract::newFromCustInvoiceJour(custInvoiceJour);

}
```

The buildContract method is attributed with the Wrappable(true) and Replaceable(true) attributes for extensibility. The buildContract method will only be called when a business event is enabled for a company.

Below is the complete implementation of the sales order invoice posted business event.

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

/// Creates a \<c\>SalesInvoicePostedBusinessEvent\</c\> from a
\<c\>CustInvoiceJour\</c\> record.

/// \</summary\>

/// \<param name = "_custInvoiceJour"\> A \<c\>CustInvoiceJour\</c\>
record.\</param\>

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
A business event contract class extends BusinessEventsContract and provides the definition and population of the business event payload. Although there is some variation across business events, the basic structure for the business event contract is consistent.

Implementing a business event contract consist of extending the BusinessEventContract class, defining internal state, implementing an initialization method, providing a static construction method, and the implementation of parm methods for accessing contract state.

1.  Extending BusinessEventContract

```
[DataContract]

public final class SalesInvoicePostedBusinessEventContract extends
BusinessEventsContract
```

2. Add private variables to hold contract state.

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

The class must be attributed with the [DataContract] attribute.

3.  Implement private initialization method.

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

The initialize method is responsible for setting the contract classes private state based on data provided through the static constructor method.

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

The static constructor methods calls a private initialize method to initialize the private class state.

5. Implement parm methods for accessing contract state.

```
[DataMember('InvoiceAccount')]

public CustInvoiceAccount parmInvoiceAccount(CustInvoiceAccount \_invoiceAccount = invoiceAccount)

{

invoiceAccount = \_invoiceAccount;

return invoiceAccount;

}

```

Parm methods should be attributed using the [DataMember('\<name\>')] attribute. The name provided on the attribute (e.g. 'InvoiceAccount') will be the name visible to data contract consumers.

   > [!Note]
   > **RecIds** should not be part of a business event payload. Use the alternate key (AK) instead.
   >
   > **Enum values** must be converted to their symbol value for publishing. Use the enum2Symbol method to convert from the enum's value to the symbol string. For example:

```
status = enum2Symbol(enumNum(CustVendDisputeStatus), \_custDispute.Status);
```

In some cases population of the data contract's internal state will require additional retrieval methods to be implemented. This should be implemented as private methods and called from the initialize method.

Below is the complete implementation of the sales order invoice posted business event contract.

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

/// Creates a \<c\>SalesInvoicePostedBusinessEventContract\</c\> from a
\<c\>CustInvoiceJour\</c\> record.

/// \</summary\>

/// \<param name = "_custInvoiceJour"\>A \<c\>CustInvoiceJour\</c\>
record.\</param\>

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

Application code must be modified to send the business event at the appropriate point. Often it is possible to do this a common point within a framework. Documents that extend SourceDocument have a common point for creation and sending of a business event. See [Source document framework support](https://msdyneng.visualstudio.com/FinOps/_wiki/wikis/FinOps.wiki?wikiVersion=GBwikiMaster&pagePath=%2FHome%2FD365%20Finance%20and%20Operations%2FAuthoring%20business%20events#Source-document-framework-support).

Other frameworks also provide common points for the sending of business events. For example the CustVendVoucher class hierarchy has a post method that is leveraged for sending business events related to the posting of customer or vendor vouchers. Overriding base class implementation provides specialization of the business event send logic. See CustVoucher.createBusinessEvent or
VendVoucher.createBusinessEvent as examples.

The sending of a business event is tied to the commit of the underlying transaction. If the underlying transaction is aborted, the business event will not be sent. This allows applications to "send" the business event a the point where the payload information is available.

Whether a business event is published to a consumer is determine by the business events framework. As a general rule, applications should always "send" a business event without regard to whether the business event is enabled or not. If there is significant additional logic required or the logic for sending a business event has a performance impact an application can check if a particular business event is enabled before executing business logic associated with the sending of the business events. This is done through the BusinessEventsConfigurationReader::isBusinessEventEnabled method.

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

The source document framework supports the sending of business events automatically as part of the transition from an in-process state to a completed state for the document. In order for documents extending the source document framework to leverage this capability, they need to implement an extension to the SourceDocumentStateInProcess.getBusinessEvent method to create and return the correct BusinessEventsBase extension type.

## Extending a business event payload

There may be additional information that you wish to publish as part of the payload of a business event. Sending this additional information can be accomplished by following these steps to extend the business event's standard payload.

### Example scenario

Extend the CustFreeTextInvoicePostedBusinessEventContract to include a customer classification. This is a custom classification that is industry based.

#### Step 1: Create an extended business event contract

Create a new contract that is composed of the standard business event contract plus any additional information to be included in the payload.

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

#### Step 2: Initialize method

Create an initialize() method that initializes the value of the private contract.

```
private void initialize(CustFreeTextInvoicePostedBusinessEventContract
\_custFreeTextInvoicePostedBusinessEventContract)

{

custFreeTextInvoicePostedBusinessEventContract =
\_custFreeTextInvoicePostedBusinessEventContract;

}

```

#### Step 3: static NewFrom method

Create a static newFrom method that takes the standard contract as an argument and calls the initialize() method.

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

Copy the parm methods from the standard data contract and modify each method to get and set values in the your class' standard contract instance.

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

#### Step 5: Add parms methods for additional payload data**

```
[DataMember('CustomerClassification')]

public CustomerClassification parmCustomerClassification(CustomerClassification
\_customerClassification = customerClassification)

{

customerClassification = \_customerClassification;

return customerClassification;

}
```

Below is the complete implementation of the extended business contract.

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

#### Step 6: Wrap the buildContract() method.

Provide a build contract implementation that calls 'next' to load the standard business event contract and populates any payload extensions. Below is the complete class.

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
The payload of a business event payload can be easily extended by implementing a business event contract that supplements the standard business event contract and an extension class that uses chain-of-command (CoC) to wrap the implementation of the buildContract() method.

