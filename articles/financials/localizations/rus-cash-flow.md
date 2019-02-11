---
# required metadata

title: Cash flow management (Russia)
description: This topic walks you through an example of setting up and using cash flow management in Microsoft Dynamics 365 for Finance and Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 02/11/2019
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
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Cash flow management (Russia)
[!include [banner](../includes/banner.md)]


**Note:** The data set that is used in this document is for demo purposes only. The codes that you use for ledger accounts, value-added tax (VAT), rates, and so on, should comply with the rules that are accepted in your company.

In a centralized payments organization, there are many legal entities for operations, and each operating legal entity manages its own invoices payable information. Payments for all the operating legal entities are generated from a single legal entity, which might be called the Treasury legal entity (company).

The Treasury company is responsible for monitoring the flow of cash/liquidity movement across companies and cash positions, and for preventing corporate cash shortage in good time.

The key goals of the Treasury company are as follows:

- Obtain an accurate liquidity/cash flow forecast and perform an analysis for the
medium-term/short-term horizon.

- Manage payments daily by using payment schedule journals.

- Control the company’s cash position (shortage and surplus).

- Maintain the company’s cash flows through centralized control.

This document provides a step-by-step example that illustrates the settings and user activities for cash flow management in Microsoft Dynamics 365 for Finance and Operations.

In this example, Contoso Retail RUS (RURT) is a subsidiary of an industrial holding company and does business as an operating legal entity. Contoso Entertainment Systems Russia (RUMF) is an internal bank of an industrial holding company and handles all payments.

The following table shows the stages of payment that a treasurer deals with during payment processing.

<table> 
<tr>
<td>Business scenario</td>
<td>Payment cause</td>
<td>:Payment stage</td>
</tr>
<tr>
<td>The company requests and confirms delivery of goods (that is, a purchase order that has a delivery schedule is confirmed). A treasurer includes information about the expected payments (inflow or outflow) in the cash flow forecast – payment schedule journal (payment plan).
The new entity is an expansion of cash flow forecast transactions and purchase order/sales order payment schedule lines.
</td>
<td>
<ul>
  <li>Purchase order</li>
  <li>Sales order</li>
  <li>Free text invoice</li>
  </ul></td>
<td>Planned payment</td>
</tr>
<tr>
<td>Note: This new entity and the associated functionality are available only if the Payment request license configuration key is enabled.
The company receives the payment request from a seller (prepayment request, invoice, and so on). The manager creates a payment request, which should be approved by the manager lead and a treasurer. The treasurer includes information about the expected and approved payments (inflow or outflow) in the cash flow forecast.
The new entity is an expansion of vendor transactions and customer transactions.
</td>
<td><ul>
  <li>Vendor invoice</li>
  <li>Prepayment invoicer</li>
  <li>Planned payment for confirmed purchase order</li>
  <li>Customer return invoice</li>
  </ul></td>
<td>Payment request</td>
</tr>
<tr>
<td>A treasurer generates and confirms the payment schedule journal (payment register). In this way, the company defines the list of payments that should be performed by the bank/cash account.</td>
<td>Payment schedule journal (of the Payment register type)</td>
<td>Payment order</td>
</tr>
<tr>
<td>The company receives the statement from a bank. This statement includes the authorized transactions (completed payments).</td>
<td>Bank statement</td>
<td>Completed payment</td>
</tr>
</table>

| Business scenario                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Payment cause                                                                                            | Payment stage     |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|-------------------|
| The company requests and confirms delivery of goods (that is, a purchase order that has a delivery schedule is confirmed). A treasurer includes information about the expected payments (inflow or outflow) in the cash flow forecast – payment schedule journal (payment plan). The new entity is an expansion of cash flow forecast transactions and purchase order/sales order payment schedule lines.                                                                                                                                                        | Purchase order Sales order Free text invoice                                                             | Planned payment   |
| **Note:** This new entity and the associated functionality are available only if the **Payment request** license configuration key is enabled. The company receives the payment request from a seller (prepayment request, invoice, and so on). The manager creates a payment request, which should be approved by the manager lead and a treasurer. The treasurer includes information about the expected and approved payments (inflow or outflow) in the cash flow forecast. The new entity is an expansion of vendor transactions and customer transactions. | Vendor invoice Prepayment invoice Planned payment for a confirmed purchase order Customer return invoice | Payment request   |
| A treasurer generates and confirms the payment schedule journal (payment register). In this way, the company defines the list of payments that should be performed by the bank/cash account.                                                                                                                                                                                                                                                                                                                                                                     | Payment schedule journal (of the **Payment register** type)                                              | Payment order     |
| The company receives the statement from a bank. This statement includes the authorized transactions (completed payments).                                                                                                                                                                                                                                                                                                                                                                                                                                        | Bank statement                                                                                           | Completed payment |

After you complete the example that is provided in this document, you will be
able to complete the following tasks:

Configure cash flow management parameters to support the new functionality.

Perform a planned payment processing. Forecast transactions of incoming and
outgoing payments are automatically created and updated based on purchase
orders, sales orders and free text invoices.

(Only if the **Payment request** license configuration key is enabled) Perform
payment request processing (including creation, update, and approval), based on
indebtedness to vendors, customers, and workers, and prepayment requirements
from vendors.

Perform payment schedule journal processing for mid-term liquidity planning
(payment plan) and daily payment management (payment register). Analyze cash
deficit and surplus through payment schedule sheet balancing (the simulation
function).

Generate payments, based on an approved payment register (a type of payment
schedule journal).

Configure parameters to support cash flow management
====================================================

Task overview
-------------

Configure the license configuration.

Configure the organization hierarchy for centralized payments (optional).

Create the payment priority and specify the payment priority for a party.

Create an approval workflow for payment requests and an approval workflow for
payment schedule journals.

Create the payment request type.

Configure the cash flow management parameters.

Specify the payment request type for the terms of payment.

Define the ledger account as a remittance en route account.

Specify the minimum cash balance for a payment account (bank account or cash
account).

Specify payment order requisites on a purchase agreement and sales agreement.

License configuration
---------------------

Click **System administration** \> **Setup** \> **License configuration**.

Under **Country/Regional specific features \>Russia**, select the **Cash flow
management** check box.

If the organization is planning to use payment requests, select the **Payment
requests** check box.

![A screenshot of a social media post Description automatically generated](media/d32e6c4fa740cfd58eeca53a8f6a38d5.jpg)

Close the page.

Organization hierarchy for centralized payments (optional)
----------------------------------------------------------

Click **Organization administration** \> **Organizations** \> **Organization
hierarchies**.

Make sure that the selection in the Hierarchy table is changed to **Centralized
Payments**.

![A screenshot of a cell phone Description automatically generated](media/9af19b1d8b67b09b67b424904c613f13.jpg)

Click **View**.

In the **Hierarchy designer** form, create a new hierarchy, where **RUMF** is
the legal entity of the payment and **RURT** is the operating legal entity.

![A screenshot of a cell phone Description automatically generated](media/4523db94196e8ca17370468a355fe8df.jpg)

Publish the new hierarchy.

Payment priority
----------------

Click **Cash and bank management** \> **Setup** \> **Cash flow management** \>
**Payment priority**.

![A screenshot of a cell phone Description automatically generated](media/7fe5d6a76dbae175398fd8549fd68d9f.jpg)

Click **New** to create a new record.

On the **Manage priority** FastTab, use the **Up** and **Down** buttons to
arrange the priority list.

Click **Accounts payable** \> **Vendors** \> **All vendors**.

In the **Vendors** page, select the vendor.

Click **Edit**. Then, in the **Payment priority** field, specify a priority code
for the associated party. This operation can also be completed in the **Party**
and **Customer** forms.

![A screenshot of a cell phone Description automatically generated](media/2cae42b78db6e38b62a4e2bc40987d8c.jpg)

Cash flow management workflow
-----------------------------

Click **Cash and bank management** \> **Setup** \> **Cash and bank management
workflows**.

Click **New** to create a new record.

Select the required workflow type: **Workflow type for payment requests
approval** or **Payment schedule journal approval workflow**.

![A screenshot of a social media post Description automatically generated](media/d1d01da6a9cc990459218566b0558cf3.jpg)

Set the new workflow by using the new workflow elements: **Approve the payment
request** or **Approve payment schedule journal**.

![A screenshot of a cell phone Description automatically generated](media/75cf1ae83b31d8796c1b4a3f09edf8dd.jpg)

Activate the new workflow.

Payment request type
--------------------

**Note:** The **Payment request type** form is available only if the **Payment
request** license configuration key is enabled.

1.  Click **Cash and bank management** \> **Setup** \> **Cash flow management**
    \> **Payment request type**.

![A screenshot of a cell phone Description automatically generated](media/2861a5e9d472fb1c073042ff29e294c5.jpg)

1.  Click **New** to create a new record.

2.  Specify the **Payment priority**. If a payment priority is not specified for
    a payment request type, the lowest payment priority will be used for payment
    requests of that type. The payment priority for a payment request will be a
    maximum between the payment priority of the party and the payment priority
    of the payment request type.

3.  Specify the cash flow direction: **Cash inflow** or **Cash outflow**.

4.  Specify the workflow that is associated with payment request approval, if
    the approval procedure should be applied to payment requests of this type.

Cash flow management parameters
-------------------------------

**Note:** This setup should be completed for a Treasury company.

Click **Cash and bank management** \> **Setup** \> **Cash and bank management
parameters**. Click on the **Cash flow management** tab,

On the **Financial dimensions** fast tab, specify the dimension set. This step
enables an organization to determine which dimensions in the account structures
that are associated with the chart of accounts (of legal entities in a
centralized payment hierarchy) are available for cash flow management
processing. This means that, for example, combinations of departments that have
cost centers can be used for liquidity/cash flow forecast analysis.

On the **Default exchange rate type for forecast** fast tab, specify the default
exchange rate type for forecasts. This value is used in payment plans when the
currency of a payment source differs from the payment currency.

>   **Note:** The following parameters are available only if the **Payment
>   request** license configuration key is enabled.

On the **Payment requests fast tab**, specify payment request types for
**Indebtedness to vendor**, **Vendor prepayment**, **Indebtedness to customer**,
**Indebtedness to worker**. These payment request types will be used during
automatic payment request creation.

On the **Payments** fast tab, specify the vendor payment journal and customer
payment journal that are used to post payments that are generated by the payment
register.

On the **Payment request re-approval** fast tab, in the **Amount to pay change**
field, specify the system behavior if the amount to pay for a payment request is
changed. You can specify that the system should always initialize a payment
request re-approval through workflow, that the system should initialize a
payment request re-approval only if the amount to pay has increased, or that
re-approval is never required.

![A screenshot of a cell phone Description automatically generated](media/59f7a1c755b04b0bc8f1c3788ea8413d.jpg)

Click the **Number sequences** tab.

Specify the number sequence code for payment requests.

Specify the number sequence code for payment schedule journals.

Terms of payment
----------------

**Note:** This setup is available only if the **Payment request** license
configuration key is enabled.

Click **Accounts payable** \> Payment **Setup** \> **Terms of payment**.

Click **Edit**. Specify the payment request types for payments and prepayments
if specific payment request types should be used in these scenarios.

![A screenshot of a social media post Description automatically generated](media/d34309f31bbe633919a9bf52a2060d44.jpg)

Payment schedules
-----------------

Click **Accounts payable** \> Payment **setup** \> **Payment schedules**.

Create a new payment schedule and set the allocation method to **Specified**.

On the **Payment lines** FastTab, create new payment lines. Select the
**Prepayment** check box if a payment request on prepayment should be created
for a line.

![A screenshot of a cell phone Description automatically generated](media/c2722634f04947e342d9497293527751.jpg)

Remittance en route account
---------------------------

**Note:** This setup should be completed for a Treasury company.

Click **Cash and bank management \> Cash flow forecasting \> Cash flow forecast
setup.**

On the **General** tab, on the **Liquidity accounts** fast tab, click **Add** to
create a new record.

Select the **Remittance en route** check box.

![A screenshot of a cell phone Description automatically generated](media/24b648ceed8d8f0ab0f37886bcc3fa10.jpg)

Bank accounts
-------------

**Note:** This setup should be completed for a Treasury company.

Click **Cash and bank management** \> **Bank accounts** \> **Bank accounts**.

Select the record and click **Edit**.

Specify the minimum cash balance. If the estimated balance amount of the bank
account is less than the minimum cash balance that you specify, the payment
schedule sheet will overwrite the estimated balance for that date.

![A screenshot of a cell phone Description automatically generated](media/d45380446e2eddbd14a9b50eef118afb.jpg)

Cash accounts
-------------

**Note:** This setup should be completed for a Treasury company.

Click **Cash and bank management** \> **Bank accounts** \> **Cash accounts**.

Select the record and click **Edit**.

Specify the minimum cash balance. If the estimated balance amount of the cash
account is less than the minimum cash balance that you specify, the payment
schedule sheet will overwrite the estimated balance for that date.

![A screenshot of a cell phone Description automatically generated](media/9aa2738f794f63584a4a401e2bc45c15.jpg)

Payment order requisites
------------------------

Click **Accounts payable** \> **Purchase orders** \> **Purchase agreements**.

Select a purchase agreement that has a method of payment that is associated with
a payment order in Russian rubles (RUB).

On the **Action Pane**, on the **Purchase agreement** tab, in the **Setup**
group, click **Payment order**.

Click Edit and specify payment order requisites. Payment order requisites of a
payment request or a payment journal line that is associated with this purchase
agreement will be initialized from the purchase agreement.

![A screenshot of a social media post Description automatically generated](media/e04c312344895be732001bffa9a84823.jpg)

The same setup is valid for payment order requisites on sales agreements.

Planned payment processing
==========================

Task overview
-------------

Create a purchase order. Specify the terms of payments, payment schedule, method
of payment, cash discount, and financial dimensions on the purchase order
header.

Create purchase order lines. Specify the sales tax group, item sales tax group,
and financial dimensions. Distribute an amount if you need to.

Generate and review planned payments.

Generate an invoice on part of the purchase order.

Review planned payments.

Generate planned payments for a sales order and a free text invoice.

Generate planned payments by using a periodic operation in the Treasury company.

Planned payments on purchase orders
-----------------------------------

**Note:** This step should be completed in a subsidiary company.

Click **Accounts payable** \> **Purchase orders** \> **All purchase orders**.

Create a new purchase order, and specify the terms of payments, payment
schedule, method of payment, cash discount, and financial dimensions on the
purchase order header.

Create purchase order lines, and specify the sales tax group, item sales tax
group, and financial dimensions. Distribute the amount of a line if you need to.

On the **Action Pane**, on the **Invoice** tab, in the **Bill** group, click
**Planned payments**.

Review the planned payments that have been created, based on the due dates,
financial dimension values, sales tax group, and item sales tax group.

![](media/5779f866de7976fcc6b3e0ac59852cf3.png)

A planned payment contains details about future payments: the amount, method of
payment, payment account, payment priority, and cash discount amount.

The due date is calculated based on the confirmed delivery date or delivery date
if the first date is not specified.

If a user posts an invoice, planned payments will be recalculated. If a purchase
order is fully invoiced, the purchase order will not have any planned payments.

If the **Payment request** license configuration key is enabled, a planned
payment is created based on the financial dimensions from the purchase order
lines; otherwise, the planned payment is based on the financial dimensions from
the purchase order header.

Planned payments will be generated for a purchase order if a payment schedule is
calculated, or if a user clicks the **Planned payments** button.

Planned payments on sales orders
--------------------------------

**Note:** This step should be completed in a subsidiary company.

Click **Accounts receivable** \> **Orders** \> **All sales orders**.

Create a new sales order, and specify the terms of payments, payment schedule,
method of payment, cash discount, and financial dimensions on the sales order
header.

Create sales order lines, and specify the sales tax group, item sales tax group,
and financial dimensions.

On the **Action Pane**, on the **Invoice** tab, in the **Bill** group, click
**Planned payments**.

Review the planned payments that have been created, based on the due dates,
dimension values, sales tax group, and item sales tax group.

A planned payment contains details about future payments: the value, method of
payment, payment account, payment priority, and cash discount amount.

If the **Payment request** license configuration key is enabled, a planned
payment is created based on the financial dimensions from the sales order lines;
otherwise, the planned payment is based on the financial dimensions from the
sales order header.

Planned payments will be generated for a sales order if a payment schedule is
calculated, or if a user clicks the **Planned payments** button.

Planned payments on free text invoices
--------------------------------------

**Note:** This step should be completed in a subsidiary company.

Click **Accounts receivable** \> **Invoices** \> **All free text invoices**.

Create a new free text invoice, and specify the terms of payments, payment
schedule, method of payment, cash discount, and financial dimensions on the free
text invoice header.

Create free text invoice lines, and specify the sales tax group, item sales tax
group, and financial dimensions. Distribute the amount of a line you need to.

On the **Action Pane**, on the **Invoice** tab, in the **Details** group, click
**Planned payments**.

Review the planned payments that have been created, based on the due dates,
dimension values, sales tax group, and item sales tax group.

A planned payment contains details about future payments: the value, method of
payment, payment account, payment priority, and cash discount amount.

If the **Payment request** license configuration key is enabled, a planned
payment is created based on the financial dimensions from the free text invoice
lines; otherwise, the planned payment is based on the financial dimensions from
the free text invoice header.

Planned payments will be generated for a free text invoice if a payment schedule
is calculated, or if a user clicks the **Planned payments** button.

Periodic creation of planned payments
-------------------------------------

**Note:** This step should be completed for a Treasury company.

Click **Cash and bank management** \> **Periodic** tasks\> **Cash flow
management** \> **Calculate planned payments**.

On the **General** tab, specify the following parameters:

In the **From date** field, specify the start of the date range for the planned
payment sources.

In the **To date** field, specify the end of the date range for the planned
payment sources.

Select a planned payment source.

Select legal entities. A Treasury company can include all legal entities that
belong to the current centralized payment hierarchy.

Select the **Recalculate all** check box if all planned payments should be
recalculated. If you do not select this check box, only new planned payment will
be created.

![A screenshot of a cell phone Description automatically generated](media/46ffba99d902fad6003c133da3badb3e.jpg)

Payment request processing
==========================

Task overview
-------------

**Note:** This scenario is available only if the **Payment request** license
configuration key is enabled.

Create a manual payment request.

Confirm a manual payment request.

Cancel a payment request.

Create a new payment request as a copy of an existing payment request.

Create a purchase order. Specify the terms of payments, payment schedule (mark a
line as a prepayment if you need to), method of payment, cash discount, and
financial dimensions on the purchase order header.

Create purchase order lines. Specify the sales tax group, item sales tax group,
and financial dimensions. Distribute an amount if you need to.

Generate and review the payment request for prepayment if a payment schedule
line is marked as a prepayment in a payment schedule of this purchase order.

Post an invoice for the purchase order.

Generate and review the payment request for accounts payable.

Generate payment requests for a sales order and a free text invoice if a return
has been registered.

Generate payment requests by using the periodic operation in the Treasury
company.

Update the payment request if an amount of the request origin (vendor/customer
open transaction) has been changed. Payment request can be updated from the
**Payment request** form or by using a periodic operation.

Split the payment request.

Create a manual payment request
-------------------------------

Click **Cash and bank management** \> **Cash flow management** \> **All payment
requests**.

Create new payment request. In the **Create payment request** form, specify the
payment request type, currency of the payment request, account type (vendor,
customer, or worker), account and invoice account, agreement registration
number, payment currency, due date, and method of payment.

>   The payment request type defines the cash flow direction and an application
>   of a particular workflow.

>   The method of payment defines the payment account type and payment account.

>   The payment request priority is defined by properties of the payment account
>   type and party.

>   The centralized payment hierarchy defines the Treasury company. A payment
>   request company is a company where a payment request is created.

![A screenshot of a cell phone Description automatically generated](media/7321ed3e6eabe8cb4e078e2c08207ecf.jpg)

Click **OK**.

In the **Header** view, on the **General** FastTab, specify the required payment
request parameters. You can change the payment date, payment currency, payment
priority, and other parameters if you need to.

![A screenshot of a cell phone Description automatically generated](media/7addfeff1eb83c09e08b498ef7bb43c8.jpg)

O the **Payment** FastTab, specify the required payment request parameters. You
can change the posting profile, payment account type, payment account, and other
parameters if you need to.

On the **Payment order** FastTab, specify the required payment order requisites.
By default, these requisites are initialized from a purchase agreement or sales
agreement. This FastTab is available if the method of payment is associated with
a *Payment order in RUB*.

![](media/5efcb2ef190e535a4a25cda07ada4c0f.png)

On the **History** FastTab, review details about the payment request processing.
You can change the payment request initiator if you need to.

On the **Financial dimensions** FastTab, specify the financial dimensions of the
payment request.

Switch to the **Lines** view

Click **Add line** to create a new record.

Specify the dimension values, sales tax group, item sales tax group, and
original amount. By default, the **Amount to pay** field is set to **Original
amount**.

![A screenshot of a cell phone Description automatically generated](media/2a4ad70cf983ecc4272d636c254f66e1.jpg)

Create more new lines if you need to.

Save the record.

On the **Action Pane**, on the **General** tab, in the **Bill** group, click
**Cash discount**.

Create a new record and specify the cash discount date and cash discount amount.

![A screenshot of a cell phone Description automatically generated](media/7110045c069c0ebdf57c51118615f314.jpg)

Create more lines if you need to and close the window

If all data are filled in and workflow approval can start, on the **Action
Pane**, on the **Payment request** tab, in the **Generate** group, click
**Confirmation**

Click **Workflow \> Submit** button

![A screenshot of a cell phone Description automatically generated](media/2eadc484fab51fa1edd3add98b404913.jpg)

The status of a payment request is updated automatically. The following table
describes all payment request statuses.

| PR status | System event                                                                                                                                                                   |
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Opened    | A user creates a manual payment request.                                                                                                                                       |
| Confirmed | A user confirms a manual payment request, or the system creates a payment request that is based on a source (vendor invoice, customer invoice, or prepayment planned payment). |
| Scheduled | A payment schedule journal of the **Payment plan** type (including a payment request) is posted.                                                                               |
| Accepted  | A payment schedule journal of the **Payment register** type (including a payment request) is posted.                                                                           |
| Completed | A payment journal (including a payment request) is posted.                                                                                                                     |
| Canceled  | A user cancels a payment request.                                                                                                                                              |

Cancel a payment request
------------------------

Click **Cash and bank management** \> **Cash flow management** \> **All payment
requests**.

Select a payment request.

On the **Action Pane**, on the **Payment request** tab, in the **Maintain**
group, click **Cancel**.

![](media/f05f559742476a1ad5c4a45b03ea81de.png)

Click **OK**.

![](media/dd79cb7c29e53c5c35eb66ec38f9c730.png)

This operation is available only if the status of a payment request is
**Opened**, **Confirmed**, or **Scheduled**.

Put a payment request on hold
-----------------------------

Click **Cash and bank management** \> **Cash flow management** \> **All payment
requests**.

Select a payment request.

On the **Action Pane**, on the **Payment request** tab, in the **Maintain**
group, click **On hold**.

Select the **On hold** check box, and specify a reason code.

![A screenshot of a cell phone Description automatically generated](media/c652a787615fda7176861d1420a0c950.jpg)

Click **OK**.

To remove the hold from a payment request, on the **Action Pane**, on the
**Payment request** tab, in the **Maintain** group, click **On hold**, and clear
the **On hold** check box.

This operation is available only if the status of a payment request is
**Opened**, **Confirmed**, or **Scheduled**.

A payment request that is on hold will be not be included in payment schedule
journals.

Split a payment request
-----------------------

Click **Cash and bank management** \> **Cash flow management** \> **All payment
requests**.

Select a payment request.

On the **Action Pane**, on the **Payment request** tab, in the **Generate**
group, click **Split request**.

Specify the amount to pay and the payment date for the new payment request.

![A screenshot of a cell phone Description automatically generated](media/c253497f19d1bf84b3fbe561d1cac8f4.jpg)

Click **OK**.

This operation is available only if the following conditions are met:

The status of the payment request is **Confirmed** or **Scheduled**.

The payment request is not included in an unposted payment schedule journal.

The workflow status is not **Submitted**.

The system will create a new payment request by copying all the main requisites
from the original payment request. The amount and amount to pay of the original
payment request will be reduced. The status of the new payment request will be
**Confirmed** if the status of the original payment is **Scheduled** but the new
payment request is out of range for the associated payment schedule journal.

Copy a payment request
----------------------

Click **Cash and bank management** \> **Cash flow management** \> **All payment
requests**.

Select a payment request.

On the **Action Pane**, on the **Payment request** tab, in the **New** group,
click **Copy**.

Specify the due date for the new payment request.

![A screenshot of a cell phone Description automatically generated](media/24b9388794e4f3962f29c49a9d476fb5.jpg)

Click **OK**.

Select a previously created payment request.

On the **Action Pane**, on the **Payment request** tab, in the **New** group,
click **Edit**.

Change the payment request parameters if you need to.

Click **OK**.

Create a payment request for a vendor invoice
---------------------------------------------

Click **Accounts payable** \> **Purchase orders** \> **All purchase orders**.

Create a new purchase order, and specify the terms of payments, payment
schedules, method of payment, cash discount, and financial dimensions on the
purchase order header.

Create purchase order lines, and specify the sales tax group, item sales tax
group, and financial dimensions. Distribute the amount of a line.

Generate and post an invoice.

On the **Action Pane**, on the **Purchase** tab, in the **Generate** group,
click **Payment requests**.

![A screenshot of a cell phone Description automatically generated](media/67fe7f0631de847a9cdfc7fa6a1b6fdf.jpg)

On the **Action Pane**, on the **Purchase** tab, in the **Journals** group,
click **Payment requests**.

Review the payment requests that have been created.

![A screenshot of a social media post Description automatically generated](media/1821f350b0f60c9d603066dd3ec0541e.jpg)

In the **Vendors** page, on the **Vendor** tab, in the **Transactions** group,
click **Transactions**.

Select the vendor transaction.

Click **Inquiry** \> **Payment requests**.

Review the associated payment requests.

On the **General** tab, in the **Related information** group, click **Request
origin**.

Verify the vendor transaction that is a source for the payment request.

![A screenshot of a social media post Description automatically generated](media/e828196d99b2a94d8d4297d449365214.jpg)

Payment requisites (method of payment, due date, vendor bank account, and so on)
on an open vendor transaction cannot be changed if a payment request exists for
it. Instead, you should modify payment requisites in the payment request. The
payment requisites will then be synchronized in the open vendor transaction
automatically.

Create a payment request for a prepayment to a vendor
-----------------------------------------------------

Click **Accounts payable** \> **Purchase orders** \> **All purchase orders**.

Create a new purchase order, and specify the terms of payments, payment
schedules, method of payment, cash discount, and financial dimensions on the
purchase order header.

>   One or more payment schedules lines should be marked as prepayments.

Create purchase order lines, and specify the sales tax group, item sales tax
group, and financial dimensions. Distribute the amount of a line.

Confirm the purchase order.

Calculate planned payments by using the periodic operation; or, on the purchase
order, on the **Action Pane**, on the **Invoice** tab, in the **Bill** group,
click **Planned payments**. Close the page.

On the **Action Pane**, on the **Purchase** tab, in the **Generate** group,
click **Payment requests**.

On the **Action Pane**, on the **Purchase** tab, in the **Journals** group,
click **Payment requests**.

Review the payment requests that have been created.

In the **Payment request** form, on the **Action Pane**, on the **General** tab,
in the **Related information** group, click **Request origin**.

Verify that the purchase order is a source for the payment request.

Create a payment request for a customer invoice return
------------------------------------------------------

Click **Accounts receivable** \> **Orders** \> **All sales orders**.

Create a new return sales order, and specify the terms of payments, method of
payment, and financial dimensions on the sales order header.

Create sales order lines, and specify the sales tax group, item sales tax group,
and financial dimensions.

Generate and post an invoice.

On the **Action Pane**, on the **Sell** tab, in the **Generate** group, click
**Payment requests**.

Click **Close**.

On the **Action Pane**, on the **Sell** tab, in the **Journals** group, click
**Payment requests**.

Review the payment requests that have been created.

In the **Customers** form, click the **General** FastTab.

On the **Action Pane**, on the **Customer** tab, in the **Transactions** group,
click **Transactions**.

Select the last customer transaction.

Click **Inquiry** \> **Payment requests**.

Review the associated payment requests.

In the **Payment request** form, on the **Action Pane**, on the **General** tab,
in the **Related information** group, click **Request origin**.

Verify that the customer transaction is a source for the payment request.

>   Payment requisites (method of payment, due date, customer bank account, and
>   so on) on an open customer transaction cannot be changed if a payment
>   request exists for it. Instead, you should modify payment requisites in the
>   payment request. The payment requisites will then be synchronized in the
>   open customer transaction automatically.

Click **Accounts receivable** \> **Common** \> **Free text invoices** \> **All
free text invoices**.

Create a new return free text invoice, and specify the terms of payments, method
of payment, and financial dimensions on free text invoice header.

Create free text invoice lines, and specify the sales tax group, item sales tax
group, and financial dimensions.

Generate and post an invoice.

On the **Action Pane**, on the **Invoice** tab, in the **Details** group, click
**Payment requests**.

Click **Close**.

On the **Action Pane**, on the **Invoice** tab, in the **Related information**
group, click **Payment requests**.

Review the payment requests that have been created.

In the **Customers** form, click the **General** FastTab.

On the **Action Pane**, on the **Customer** tab, in the **Transactions** group,
click **Transactions**.

Select the last customer transaction.

Click **Inquiry** \> **Payment requests**.

Review the associated payment requests.

In the **Payment request** form, on the **Action Pane**, on the **General** tab,
in the **Related information** group, click **Request origin**.

Verify that the customer transaction is a source for the payment request.

Periodic creation of payment requests
-------------------------------------

**Note:** This step should be completed for a Treasury company.

Click **Cash and bank management** \> **Periodic** \> **Cash flow management**
\> **Create payment requests**.

On the **General** tab, specify the following parameters:

In the **From date** field, specify the start of the date range for the payment
request sources.

In the **To date** field, specify the end of the date range for the payment
request sources.

Select the sources of the payment request: **Vendor invoice**, **Customer
invoice**, or **Planned payment**.

Select legal entities. A Treasury company can include all legal entities that
belong to the current centralized payment hierarchy.

In the **Number of batch threads** field, enter the number of parallel tasks for
payment request creation.

![](media/e2815a1339e6ded7f73209276700e259.png)

Update a payment request
------------------------

Click **Cash and bank management** \> **Cash flow management** \> **All payment
requests**.

Select a payment request for which the **Outdated** check box is selected.

![A screenshot of a cell phone Description automatically generated](media/6d28fe2279d9af067bf1276fd7a2336d.jpg)

>   The system selects this check box automatically if the original source of a
>   payment request has been changed through settlement or unsettlement. A
>   selected check box indicates that the amount to pay of the payment request
>   is not equal to the amount of the vendor/customer open transaction.

On the **Action Pane**, on the **Payment request** tab, in the **Generate**
group, click **Request update**.

This operation is available only if the following conditions are met:

The status of the payment request is **Confirmed** or **Scheduled**.

The payment request is not included in an unposted payment schedule journal.

The workflow status is not **Submitted**.

The **Request update** operation will change the **Amount to pay** value on
payment request lines and in the cash discount details.

Re-approval of payment requests can be required and is controlled by the
**Amount to pay change** parameter in the **Cash and bank management
parameters** form.

Periodic update of payment requests
-----------------------------------

**Note:** This step should be completed for a Treasury company.

Click **Cash and bank management** \> **Periodic** tasks\> **Cash flow
management** \> **Update payment requests**.

On the **General** tab, specify the following parameters:

In the **From date** field, specify the start of the date range for the payment
requests.

In the **To date** field, specify the end of the date range for the payment
requests.

Specify the sources of the payment request.

Specify legal entities. A Treasury company can include all legal entities that
belong to the current centralized payment hierarchy.

![A screenshot of a cell phone Description automatically generated](media/519dd80e71ea01741aa1ed17ede06abe.jpg)

Payment schedule journal processing
===================================

Task overview
-------------

Set up a payment schedule journal.

Create a new payment schedule journal.

Payment schedule journal processing: Generate and process the payment schedule
sheet.

Generate payments.

Set up a payment schedule journal
---------------------------------

Click **Cash and bank management** \> **Setup** \> **Cash flow management** \>
**Payment schedule journal names**.

![A screenshot of a cell phone Description automatically generated](media/a121802689f1fe4a467c550498a9d771.jpg)

Click **New** to create a new record. Specify a name and description for the
journal.

Select the journal type:

**Payment plan** – This journal type is intended for payment forecasts in a
medium-term/short-term horizon.

**Payment register** – This journal type is intended for payment statement
generation.

On the **General** FastTab, specify the following parameters:

Select the **Payment on cash discount date** check box if a date of payment in
the payment schedule should be used as a cash discount date.

Select the **Overdue payments** check box (only for a payment plan) if the
payment schedule should include outstanding payments.

Select the **Active** check box if this journal should use the workflow
procedure.

Specify the **Workflow ID** that should be applied.

Click the **Dimensions** FastTab. This section defines how the lines of the
payment schedule journal will be aggregated. The analytic report of the payment
schedule journal will also use these dimensions.

![](media/e320294d044dd4ac05ad26d1ca45d297.jpg)

>   Use the button to select an aggregation parameter.

Click the **Legal entities** FastTab. This section defines the legal entities
that are used for payment schedule journal generation.

>   Use the button to select a legal entity.

On the **Journal data sources** FastTab, click **Add line** to create a new
record.

Specify the data source and source direction for the payment schedule journal.
The following table lists the possible sources.

| Source type (direction)                | Description                                                                                     |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| Bank account balance                   | The current balance of bank accounts.                                                           |
| Cash account balance                   | The current balance of cash accounts.                                                           |
| Remittance en route balance            | The current balance of general ledger (GL) accounts that are marked as **Remittance en route**. |
| Open payment journals (inflow/outflow) | Payments that are included in open payment journals.                                            |
| Open slip journals (inflow/outflow)    | Payments that are included in open cash slip journals.                                          |
| Planned payment (inflow/outflow)       | Planned payments.                                                                               |
| Payment request (inflow/outflow)       | Payment requests.                                                                               |
| Accounts payable (inflow/outflow)      | Open vendor transactions without a link to a payment request.                                   |
| Accounts receivable (inflow/outflow)   | Open customer transactions without a link to a payment request.                                 |

Create lines that have the required journal data sources.

On the **Payment accounts** FastTab, select the **Include transactions with no
specified bank account** check box if the payment schedule journal should
include planned payments and payment requests that do not have a payment account
specified.

![A screenshot of a cell phone Description automatically generated](media/402450ab359aec1fb5616f0f8c8bc15b.jpg)

Click **Add line** to create a new record.

Specify the payment account type and account number. The payment schedule
journal will include only sources that are associated with the specified payment
accounts.

On the **Cash balance control** FastTab, click **Add line** to create a new
record.

Specify the currency and minimum cash balance. If the estimated balance amount
of the cash account is less than the minimum cash balance that you specify, the
payment schedule sheet will overwrite the estimated balance for that date.

![A screenshot of a cell phone Description automatically generated](media/0f28b3c26c4fdb45576b101a3dbd82fe.jpg)

Payment plan processing
-----------------------

Click **Cash and bank management** \> **Cash flow management** \> **Payment
schedule journal**.

In the **Name** field, select a payment schedule journal of the **Payment plan**
type.

![](media/d8ba3e0c8e492088c871c8978a42b24c.jpg)

Use the **From date** and **To date** fields to specify an effective date range.

Change the payment schedule journal attributes on the **General**,
**Dimensions**, **Legal entities**, **Journal data sources**, **Payment
accounts**, and **Cash balance control** tabs, if you need to.

Click **Calculate**.

Click **Lines** to validate the payment schedule journal lines.

![A screenshot of a cell phone Description automatically generated](media/5faff99f085d408170e8ebf6737af301.jpg)

Click **Edit beginning balance** to change the beginning balance of this
journal.

For lines that have **Payment request** as the data source, click **Payment
request lines** button to review the payment request lines that are included on
the current journal line.

**Close** the page

In the **Payment schedule journal**, click **Payment schedule** to review the
payment schedule sheet. If a cash shortage or surplus is detected and should be
prevented, you can make changes.

![A screenshot of a social media post Description automatically generated](media/a9d72ede452af4897feacf3d9e1d7101.jpg)

Select the **Show totals per payment accounts** check box if the payment
schedule sheet should be calculated based on payment accounts.

Select the **Show totals per method of payments** check box if the payment
schedule sheet should be calculated based on methods of payments.

Click the **\<** button to select an aggregation parameter for the payment
schedule sheet.

Click **Show results**.

![A screenshot of a social media post Description automatically generated](media/7d37da18e4fae7ed0464e72852a0b614.jpg)

>   If the minimum cash balance for a currency or a payment account is exceeded,
>   the payment schedule sheet highlights the **Estimated balance** amounts in
>   yellow.

Click on the amount for a journal data source of **Payment request** (if the
**Payment request** license configuration key is enabled) or **Accounts
payable**/**Accounts receivable** (if the **Payment request** license
configuration key is *not* enabled) and press **Show origin** to open the
sources of that amount.

Click on the amount for a journal data source of **Payment request** and press
**Change payment sources**

![A screenshot of a cell phone Description automatically generated](media/ba9d386723621376bba4902747beeb56.jpg)

Select payment sources that should be moved to another date, or that should be
paid by using another method of payment, or payment account.

![A screenshot of a cell phone Description automatically generated](media/c9f27e4e56a0804cb163a4d098c19d83.jpg)

Click **Multiple change**, specify the new payment details in the **Modify
payment attributes** form, and then click **OK**.

![A screenshot of a cell phone Description automatically generated](media/1b73ca97151196d34b939136e3e180d8.jpg)

>   Alternatively, you can specify a new payment date, new method of payment, or
>   payment account requisites for a specific line.

Click **Update payment schedule**. The system updates the payment schedule sheet
and creates uncommitted payment schedule journal lines of payment sources
correction.

![A screenshot of a cell phone Description automatically generated](media/dff390e19d65c93388def67bb09011cf.jpg)

Make additional changes in the payment schedule sheet if you need to.

In the **Payment schedule journal** form, click **Functions** \> **Apply
changes** to apply your changes or **Revert changes** to reject them.

Click **Functions** \> **Delete journal lines** if changes in the journal setup
are required, and calculate the journal.

![A screenshot of a social media post Description automatically generated](media/6f3e695e5a325f7dc60a7629c284591a.jpg)

Click **Validate** to verify the journal. The system will inform you if
canceled, on-hold, or incomplete workflow payment requests are included in this
journal.

If all data is correct and workflow approval of the payment plan can start, on
the **Action Pane**, click **Workflow \> Submit**.

![A screenshot of a cell phone Description automatically generated](media/71941090e6ec2e796adfd82a4c77d972.jpg)

Approvers may see the following actions during approval flow:

![A screenshot of a cell phone Description automatically generated](media/bcee671cf3cfe355875a7ebb13e3490e.jpg)

If the payment plan is approved, click **Confirm**. The status of the payment
requests that are included changes to **Scheduled**.

In the **Payment request** form, on the **Action Pane**, on the **General** tab,
in the **Related information** group, click **Payment schedule journal**.

Review the payment schedule journal that is associated with the payment request.

Payment register processing
---------------------------

Click **Cash and bank management** \> **Cash flow management** \> **Payment
schedule journal**.

In the **Name** field, select a payment schedule journal of the **Payment
register** type.

Use the **From date** and **To date** fields to specify an effective date range.

Change the payment schedule journal attributes on the **General**,
**Dimensions**, **Legal entities**, **Journal data sources**, **Payment
accounts**, and **Cash balance control** tabs, if you need to.

Click **Calculate**.

Click **Lines** to validate the payment schedule journal lines.

Click **Edit beginning balance** to change the beginning balance of this
journal.

For lines that have **Payment request** as the journal data source, click
**Payment request lines** to review the payment request lines that are included
on the current journal line.

Close the form.

Click **Payment schedule** to review the payment register. If a cash shortage or
surplus is detected, you can make changes.

Click **Validate** to verify the journal. The system informs you if canceled or
on-hold payment requests are included in this journal.

If all data is correct and workflow approval of the payment plan can start, on
the **Action Pane**, Workflow \> **Submit**.

If the payment plan is approved, click **Confirm**. The status of the payment
requests that are included changes to **Accepted**.

In the **Payment request** form, on the **Action Pane**, on the **General** tab,
in the **Related information** group, click **Payment schedule journal**.

Review the payment schedule journal that is associated with the payment request.

>   **Note:** The following steps can be completed only if the **Payment
>   request** license configuration key is enabled.

In the Payment schedule journal page, click **Functions** \> **Generate
payments**.

Specify parameters for payment journal generation.

![A screenshot of a cell phone Description automatically generated](media/8480aaafc869761a88a35a7cde0d6375.jpg)

Click **OK**.

Click **Accounts payable** \> **Journals** \> **Payments** \> **Payment
journal** to validate and process the vendor payment journal that is created.

Click **Accounts receivable** \> **Journals** \> **Payments** \> **Payment
journal** to validate and process the customer payment journal that is created.

Standard payment proposal functionality will process open transactions that have
a link to a payment request that has **Accepted** status.

The payment proposal algorithm includes additional changes that are applied when
payment requests are used. The system will take into account the posting
profile, the **Prepayment** parameter, and the payment order requisites that are
filled on payment requests.
