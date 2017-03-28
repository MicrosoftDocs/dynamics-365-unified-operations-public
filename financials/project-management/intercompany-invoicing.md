---
# required metadata

title: Intercompany invoicing
description: This article provides information and examples about intercompany invoicing for projects in Microsoft Dynamics 365 for Operations.
author: twheeloc
manager: AnnBe
ms.date: 2016-06-22 23 - 53 - 53
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 94153
ms.assetid: 33e98da7-01c1-4369-923d-aa1c8326cb80
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Intercompany invoicing

This article provides information and examples about intercompany invoicing for projects in Microsoft Dynamics 365 for Operations.

Your organization might have multiple divisions, subsidiaries, and other legal entities that transfer products and services to each other for projects. The legal entity that provides the service or product is called the *lending legal entity*, and the legal entity that receives the service or product is called the *borrowing legal entity*. 

The following illustration shows a typical scenario where two legal entities, SI FR (the borrowing legal entity) and SI USA (the lending legal entity) share resources to deliver a project for customer A. For this scenario, SI FR is contracted to deliver the work to customer A. 

[![Intercompany invoicing example](./media/interco.invoicing-01.jpg)](./media/interco.invoicing-01.jpg) 

The goal is to make cost control, revenue recognition, taxes, and transfer price for intercompany project transactions more flexible and powerful. In addition, the following capabilities are provided:

-   Create customer invoices against a project in a borrowing legal entity by using intercompany timesheets, expenses, and vendor invoices in a lending legal entity.
-   Support tax calculations and indirect costs.
-   Defer revenue recognition in a lending legal entity and when a borrowing legal entity should recognize the cost.
-   Accrue work in process (WIP) revenue in the lending legal entity.
-   Set transfer prices that can be based on various pricing models. Here are some examples:
    -   **Quantity** – The amount that you enter in the **Pricing** field is the actual cost per quantity or unit.
    -   **Charges amount** – The price/cost per transaction plus the charges amount that you enter in the **Pricing** field.
    -   **Charges percentage** – The transfer price is the price/cost per transaction multiplied by the charges percentage that you enter in the **Pricing** field.
    -   **Percentage of sales price** – The percentage of the sales price that is transferred to the lending legal entity.
    -   **Amount below sales price** – The amount that the borrowing legal entity holds back from the sales prices before transfer to the lending legal entity.
    -   **Contribution ratio** – The number that you enter in the **Pricing** field is the contribution ratio, which is expressed as a percentage of the sales price.

## Example 1: Set up parameters for intercompany invoicing
In this example, USSI is a lending legal entity, and its resources are reporting time against the borrowing legal entity, FRSI, which owns the contract with the end customer. Hours and expenses that USSI employees report can be included in the project invoice that FRSI generates. In addition, there is a third source of transactions that can originate from the lending legal entity (USSI in this example) when it provides shared vendors services to subsidiaries (such as FRSI) and then passes on those costs to projects within those subsidiaries. All matching invoice documents and tax calculations are completed by Dynamics 365 for Operations. 

For this example, FRSI must be a customer in the USSI legal entity, and USSI must be a vendor in the FRSI legal entity. You can then set up an intercompany relationship between the two legal entities. The following procedure shows how to set up the parameters so that both legal entities can participate in intercompany invoicing.

1.  Set up FRSI as a customer in the USSI legal entity, and set up USSI as a vendor in the FRSI legal entity. There are three entry points for the steps that are required for this task.
    | Step | Entry point                                                                       | Description   |
    |------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | A    | In USSI, click **Accounts receivable** &gt; **Customers** &gt; **All customers**. | Create a new customer record for FRSI, and select the customer group.                                                                                                                                                                                                                           |
    | B    | In FRSI, click **Accounts payable** &gt; **Vendors** &gt; **All vendors**.        | Create a new vendor record for USSI, and select the vendor group.                                                                                                                                                                                                                               |
    | C    | In FRSI, open the vendor record that you just created.                            | On the Action Pane, on the **General** tab, in the **Set up** group, click **Intercompany**. On the **Intercompany** page, on the **Trading relationship** tab, set the **Active** slider to **Yes**. In the **Customer company** field, select the customer record that you created in step A. |

2.  Click **Project management and accounting** &gt; **Setup** &gt; **Project management accounting parameters**, and then click the **Intercompany** tab. The way that you set up the parameters depends on whether you're the borrowing legal entity or the lending legal entity.
    -   If you're the borrowing legal entity, select the procurement category that should be used to match the vendor invoices, which are automatically generated.
    -   If you're the lending legal entity, for each borrowing entity, select a default project category for each transaction type. Project categories are used for tax configuration when the invoiced category in intercompany transactions exists only in the borrowing legal entity. You can choose to accrue revenue for intercompany transactions. This accrual is done when the transactions are posted, and it's then reversed when the intercompany invoice is posted.

3.  Click **Project management and accounting** &gt; **Setup** &gt; **Prices** &gt; **Transfer price**.
4.  Select a currency, transaction type, and transfer price model. The currency that is used on the invoice is the currency that is configured in the customer record for the borrowing legal entity in the lending legal entity. The currency is used to match entries in the transfer price table.
5.  Click **General ledger** &gt; **Posting setup** &gt; **Intercompany accounting**, and set up a relationship for USSI and FRSI.

## Example 2: Create and post an intercompany timesheet
USSI, the lending legal entity, must create and post the timesheet for a project from FRSI, the borrowing legal entity. There are two entry points for the steps that are required for this task.

| Step | Entry point                                                                       | Description                                                                                                                                                                                       |
|------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| A    | **Project management and accounting** &gt; **Timesheets** &gt; **All timesheets** | Create a new timesheet. On the timesheet line, in the **Legal entity** field, select **FRSI**. In the **Project ID** field, select the project in FRSI. Enter the hours for each day of the week. |
| B    | **Timesheet** page                                                                | After the workflow runs, post the timesheet, and make a note of the voucher number.                                                                                                               |

## Example 3: Create and post an intercompany vendor invoice
USSI, the lending legal entity, must create and post the intercompany vendor invoice for a project from FRSI, the borrowing legal entity. This vendor invoice represents the outsourced labor and expense that were performed by vendors that are paid by USSI. There are two entry points for the steps that are required for this task.

| Step | Entry point                                                                                      | Description                                                                                                                                                                                                                                                                          |
|------|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| A    | **Accounts payable** &gt; **Invoices** &gt; **Open vendor invoices** &gt; **New vendor invoice** | Create a new vendor invoice, and enter the services that were procured on behalf of FRSI's project.                                                                                                                                                                                  |
| B    | The **Vendor invoice** page                                                                      | Enter lines that represent the outsourced services on behalf of FRSI. On the **Line details** FastTab, on the **Project** tab for the invoice line, in the **Project company** field, enter **FRSI**. Enter the project and corresponding information. Then post the vendor invoice. |

## Example 4: Create and post the intercompany invoice
USSI, the lending legal entity, must create and post the intercompany invoice. There are two entry points for the steps that are required for this task.

| Step | Entry point                                                                                             | Description                                                                                                                                      |
|------|---------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| A    | **Project management and accounting** &gt; **Project invoices** &gt; **Intercompany customer invoice**  | Click **New** to open the **Create intercompany invoice** page.                                                                                  |
| B    | **Project management and accounting** &gt; **Project invoices** &gt; **Intercompany customer invoices** | On the **Create intercompany invoice** page, enter the legal entity, specify the transaction that should be included, and then click **Search**. |
| C    | **Project management and accounting** &gt; **Project invoices** &gt; **Intercompany customer invoices** | Select the transactions to invoice, or click **Select all** to invoice all the transactions in the list, and then click **OK**.                  |
| D    | The **Intercompany invoice** page                                                                       | The intercompany customer invoice proposal is shown.                                                                                             |
| E    | The **Intercompany invoice** page                                                                       | Click **Post**.                                                                                                                                  |

## Example 5: Post the vendor invoice and invoice the customer
When the lending legal entity, USSI, posts the intercompany customer invoice, a matching pending vendor invoice is created in the borrowing legal entity, FRSI. After this vendor invoice is posted, FRSI also invoices the project customer for the hours that USSI entered. There are three entry points for the steps that are required for this task.

| Step | Entry point                                                                                        | Description                                                                                                             |
|------|----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| A    | **Accounts payable** &gt; **Invoices** &gt; **Pending vendor invoices**                            | Review the invoice to verify that the timesheet values are included, and then post the vendor invoice.                  |
| B    | **Project management and accounting** &gt; **Project invoices** &gt; **Project invoice proposals** | Create a new project invoice for the project, and verify that the hour transactions that were posted appear.            |
| C    | The **Project invoice** page                                                                       | Select the project invoice, and then click **View details** to review the cost and sales amount. Then post the invoice. |



