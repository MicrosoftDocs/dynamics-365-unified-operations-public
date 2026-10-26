---
title: Manage customer and prospect records for rental (preview)
description: Learn how to manage customer and prospect records for rental, including rental terms, job sites, insurance certificates, and charge exemptions.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage customer and prospect records for rental (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Customer and prospect records in rental management extend the standard Dynamics 365 customer record with rental-specific information. This information includes rental rate and discount terms, job site assignments, insurance certificates, lien notice tracking, and rental history inquiries.

## View rental inquiries on the customer record

The customer record provides several rental-specific inquiries that help you quickly find information when you're on the phone with a customer.

To access these inquiries, open a customer record. On the **Fleet item management** tab of the Action Pane, in the **Rental** group, select one of the following options:

- **Rental contract history** – All historical rental contracts for this customer. Open any contract to access its invoice inquiry and see all rental invoices.
- **Rental quotation history** – All quotations created for this customer.
- **Swap history** – Records of fleet item swaps associated with this customer's contracts.

In the same group, select **Rental/lease contract** or **Rental quotation** to open the customer's rental contracts or quotations, where you can also create a new one.

## Manage job sites on the customer record

A job site represents a physical location where fleet items are delivered and used, such as a construction project or a data center build. The customer record displays job sites on a dedicated **Job sites** FastTab, directly below the standard address FastTab. This view gives you a quick view of all locations where the customer has active or past rental activity.

From the customer record, you can:

- View all job sites linked to this customer.
- Create a new job site by using the same form available in the rental cart.
- Select a job site to view its full details, including the job site manager and notes.

### Job sites shared by multiple customers

A job site can be linked to more than one customer. This setup is common on large projects where several subcontractors work at the same location. When you open a job site record, you can link more customers to that job site.

Each customer's link to the job site keeps its own contact and its own delivery notes. This feature is essential on shared sites: it ensures that you deliver fleet items to the correct contact for each customer, together with that customer's delivery instructions—for example, *deliver at gate D*. Even though a demolition company and a general contractor share the same job site, each customer's deliveries go to the right person and the right spot on site.

### Create and expire job sites

You can create job sites from several places:

- During the rental cart process when you create a quotation or contract.
- Directly on the contract form.
- From the **Job sites** FastTab on the customer record.
- At **Rental management (Preview)** > **Setup** > **Job sites**.
- On a fleet item movement, by selecting **Create job site** next to **From** or **To** when **From type** or **To type** is *Job site*.

When you create a job site, the system also creates a corresponding job site fleet location, and tracks fleet items delivered there at the job site.

When a job site is no longer active—for example, a completed construction project—you can expire it. Set the **Expired** toggle on the job site record to expire an individual job site, or run the **Job site expiration** batch job to expire several at once. In the job dialog, enter a date, and optionally a customer account to limit the run. A job site is expired when all of its rental documents ended before that date. Job sites that were never used on a document are reported instead of expired. Expiring inactive job sites keeps the job site list manageable. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md).

Learn more about adding job sites during the sales process in [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md).

## Customer rental terms, insurance certificates, and lien notices

A rental business that rents to a job site carries two commercial exposures: whether the customer holds valid insurance, and whether it preserves its lien rights on that site.

### Set rental terms on the customer record

Rental management adds rental terms to the **Setup** FastTab on the customer record. Go to **Accounts receivable** > **Customers** > **All customers**.

- **Rental rate group** and **Rental discount group** – The groups that rate and discount lookup and dynamic pricing use to resolve a price for this customer. Learn more in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).
- **Fixed rate** – When you set this option to *Yes*, every rate reduction on this customer's documents is held for review, regardless of the rate override limits that you configured. You can still enter a lower rate; the document goes on hold instead.
- **PO number required** – Makes the customer purchase order number mandatory on a contract, but only when the template's main line carries a fee, and makes the **Customer requisition** mandatory on sales orders that are invoiced to the customer.
- **Notice to owner exempt** – Suppresses the notice to owner automation for this customer.
- **Accounts receivable posting profile** – The profile that overrides the default for this customer.

### Register insurance certificates

Register certificates at **Rental management (Preview)** > **Setup** > **Insurance**. Select **New** to open the **Create insurance** dialog, which creates the header and its four coverage rows in one transaction.

The header carries the name, the customer or vendor account, a financial dimension, the registration type—rental/lease or vendor coverage—and the status. It also carries an **Insurance ID**, which defaults from the number sequence in rental parameters unless you enter one.

Each coverage row records one insurance type—liability, automobile liability, workers compensation, or physical damage—with the **Policy number**, **Insurance company name**, **Insurance agent name**, and the effective and expiration dates. The limit fields depend on the coverage: **Each occurrence limit**, an aggregate **Amount**, and **Currency** on **Liability**, **Limit** on **Automobile liability** and **Workers compensation**, and **Deductible amount** and **Maximum coverage limit** on **Physical damage**.

Two settings decide what a row covers. **Blanket** applies the coverage across the fleet rather than to a single fleet item: a valid blanket *Physical damage* row covers every fleet item that the customer rents, so no *Fire-Theft-Vandalism Waiver* charge is added for them. Scope narrows a row to one fleet item model, one serial number, or one location, and a contract line reads it to determine whether the fleet item on the line is covered.

A certificate is *Open*, *Expiry logged*, or *Expired*. The **Insurance expiry check** periodic job monitors expiry. It looks ahead by the number of days that you enter, and sets open certificates whose physical damage coverage expires inside that window to *Expiry logged*. It also writes a row to the insurance expiry log, so that a coordinator can request updated proof of insurance. Expiry doesn't block renting, so verify the certificate before you ship to a customer whose insurance has lapsed. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md).

### Track notice to owner filings

The notice to owner register at **Rental management (Preview)** > **Setup** > **Notice to owner** tracks lien notice filings, with one filing for each combination of customer and job site.

The system creates filings automatically. When you add a fleet item to a contract that includes a job site, the system links the customer to the job site and opens a filing for that pairing if it doesn't already have one. A second contract for the same customer at the same site reuses the existing filing, and the reference follows the contract through to the sales order that invoicing creates. Quotations and contracts without a job site aren't processed.

Two switches suppress the automation. Set **Notice to owner exempt** to *Yes* on the customer record or on a fleet item model, and the system clears the reference. One exempt model on an active line item clears the filing for the whole contract.

The system fills in the ship and start dates automatically. The first time an outbound fleet item movement ships for a fleet item on a contract line that carries the filing, the system sets both dates. **Ship date** is set to the movement's estimated delivery date, and **Start date** is set to the contract's **Invoice from** date. The system sets these dates only while **Start date** is empty, so later deliveries to the same site don't overwrite them. You can change both dates on the register. Because **Ship date** comes from the estimated delivery date, not the actual delivery, check it against the delivery record before you calculate a filing deadline from it.

Everything else is manual. You maintain **Filing number**, **Filing date**, and **Notice to owner filing status** (*Required*, *Filing company*, *Confirmed on file*, *Early return*, or *Canceled*) on the register. Use the page as a tracking register.

## Set up charge exemptions

Some customers might be exempt from certain miscellaneous charges based on their contract terms or business relationship.

To set up a charge exemption, follow these steps:

1. Open the customer record, and then, on the Action Pane, select the **Fleet item management** tab.
1. Select **Miscellaneous charge exemptions**.
1. Add a line for each rental template line that the customer is exempt from. An exemption is the combination of a customer account and a rental template line, so you exempt the charge as it's defined on one template line rather than a charge type in general.
1. Select **Save**.

When you create quotations and contracts for this customer, the system doesn't add charges from the exempted template lines. The system applies the exemption again when the contract is closed and the final charges are proposed.

## Link rental templates to customers

Linking rental templates to a customer makes frequently used templates easier to find. When you open the **Rental template** lookup for that customer, the linked templates appear in the initial list. You can still select any template, including one that's linked to another customer.

To select a template that isn't in the initial list, follow these steps:

1. Open the **Rental template** lookup on the quotation or contract.
1. Switch the lookup to show all templates, and select the template that you want.
1. Save the quotation or contract. For a customer document, the system automatically creates the customer-template link if it doesn't already exist. The template then appears in the initial list the next time you select a template for that customer.

Customer links are a selection convenience, not a restriction on which templates customers or prospects can use.

You can also maintain the links at **Rental management (Preview)** > **Setup** > **Rental template customer assignments**, or from the customer record, on the **Fleet item management** tab, in the **Rental** group. Each line pairs a **Customer account** with a **Rental template**.

## Work with prospect records

Prospect records are the prospects at **Sales and marketing** > **Relationships** > **Prospects** > **All prospects**, and a rental document carries either a customer account or a prospect, never both. You use prospect records for potential customers who don't yet have a full customer account. On the prospect record, you can:

- Manage job sites on the **Job sites** tab.
- Start a new **Rental quotation** or **Rental contract** directly from the prospect context.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
- [Invoice rental contracts](invoice-rental-contracts.md)
- [Set up rental templates](set-up-rental-templates.md)
