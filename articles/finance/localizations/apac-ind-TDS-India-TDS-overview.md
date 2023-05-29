---
# required metadata

title: Indian Tax Deducted at Source (TDS) overview
description: This article provides detailed information about Indian Tax Deducted at Source (TDS). The TDS documentation covers the functionality of this capability. 
author: kailiang
ms.date: 03/19/2021
ms.topic: overview
ms.prod: 

ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-03-19
ms.dyn365.ops.version: AX 10.0.17

---

# Indian Tax Deducted at Source (TDS) overview

[!include [banner](../includes/banner.md)]

This article provides detailed information about Indian Tax Deducted at Source (TDS).

The TDS documentation covers the functionality of this capability. It also explains how to do the basic setup for TDS, calculate TDS on transactions, complete the TDS settlement process, record TDS certificate numbers, and generate TDS inquiries, TDS statements, and TDS certificates. The documentation includes the following topics:

- [Basic setup for TDS](apac-ind-TDS-TDS-ledger-accounts-setup.md)
- [Formula designer and threshold limit functionality used for TDS calculation](apac-ind-TDS-Formula-designer.md)
- [Calculation of TDS on invoices, payments, promissory notes, and intercompany transactions](apac-ind-TDS-Calculate-TDS-on-invoices-using-journals.md)
- [Periodic TDS settlement process and settlement of TDS amounts to TDS authority vendors](apac-ind-TDS-Run-the-periodic-TDS-settlement-process.md)
- [Recording and updating TDS certificate numbers and dates](apac-ind-TDS-Record-TDS-concession-certificate-numbers.md)

## Introduction to TDS

Per the Income tax Act, 1961, income tax is deducted at the source by the receiver of the service at the time of advance payment or accounting of credit, whichever occurs first. The person who makes the payment must deduct the tax amount and pay only the net balance to the provider of the service. TDS is applied on services that the government specifies, and the tax is deducted by using the rates that the government specifies for a period. The rate of deduction is based on the status of the entity that receives the payment or provides the service. Statuses include **Individual**, **Hindu Undivided Family** (**HUF**), **Company**, **Firm**, **Association of Persons** (**AOP**), **Body of Individuals** (**BOI**), and **Local authority**.

The following sections list the services that TDS is applied on, as specified by the Government of India.

**Residents**

- Income from salaries (Under section 192)
- Income from interest on securities (Under section 193)
- Income from dividend (Under section 194)
- Income from interest (Under section 194A)
- Income from lotteries or puzzles (Under section 194B)
- Winning from horse races etc. (Under section 194BB)
- Contractors and sub-contractors (Under section 194C)
- Insurance commission (Under section 194D)
- Income from deposit under national saving scheme (Under section 194EE)
- Income from mutual fund or UTI (Under section 194F)
- Commission, Remuneration, Prize etc., on sale or lottery (Under section 194G)
- Payment of Commission or brokerage (Under section 194H)
- Rent (Under section 194I)
- Professional service (Under section 194J)
- Income from Units (Under section 194K)
- Payment of compensation on acquisition of certain immovable property (Under section 194LA)

**Non-residents**

- Payments to Non-resident sportsmen or sports association (Under section 194E)
- Other sums (Under section 195)
- Income in respect of units of non-residents (Under section 196A)

    - Income from foreign currency bonds or shares of Indian Company (Under section 196C)
    - Incomes of foreign institutional investors from securities (Under section 196D)
    - Salary and all other positive incomes under any head on income (Section 192)
    - Interest on securities (Section 193)
    - Interest other than interest on securities (Section 194A)
    - Payments to contractors and sub-contractors (Section 194C)
    - Winnings from Lottery or crossword puzzles (Section 194B)
    - Winnings from horse races (Section 194BB)
    - Insurance Commission covering all payments for procuring Insurance business (Section 194D)
    - Any interest other than interest on securities payable to non-residents not being a company or to a foreign company (Section 195)
    - Payment to non-resident sportsman including athlete or sports association or institution. In case of non-resident sportsman, payments in respect of advertisements as well as articles on any game/sports in India in newspapers, magazines, and so. is included (Section 194E)
    - Payment in respect of deposits under NSS \[National Savings Scheme\] (Section 194EE)
    - Payment on account of repurchase of Units by Mutual Fund or UTI (Section 194F)
    - Payment for Commission or brokerage (Section 194H)
    - Payment of rent (Section 194I)
    - Payment of fees for professional or technical services (Section 194J)
    - Commission to Stockiest, distributors, buyers and sellers of Lottery tickets including remuneration or prize on such tickets (Section 194G)
    - Income from Units purchased in foreign currency or long-term capital gain arising from the transfer of such Units purchased in foreign currency (Section 196B)
    - Payment of any income to non-residents in respect of interest or dividend on bonds and shares (Section 196C)

TDS is calculated on purchases, sales, sales returns, credit notes, fixed asset acquisitions, prepayments, advance payments, promissory notes, works tax, and intercompany transactions.

> [!NOTE]
> In the current Indian tax scenario, TDS isn't calculated on sales transactions. However, the system includes a provision to calculate TDS recoverable on sales transactions, especially for intercompany transactions.

The calculation of TDS always considers the threshold and the exception threshold that are defined for the TDS component.

The periodic TDS settlement process must be run, and the TDS payments must be settled to TDS authority vendors.

The certificate numbers and dates for TDS certificates that are received from vendors or customers can be recorded and updated. Additionally, Form 26Q and Form 27Q quarterly statements, and the Form 16A certificate for TDS, can be generated in Finance.

## Setting up and working with TDS

Here is an overview of the process for setting up and working with TDS:

1. **TDS setup:**

    - Parameter setup:

        - In General ledger parameters, activate parameters that are related to TDS.
        - In General ledger parameters, set up the number sequence for withholding tax payments.
        - Set up parameters in Accounts payable and Accounts receivable.

    - Basic setup:

        - Set up TDS registration numbers for a company, customers, and vendors.
        - Set up TDS component groups.
        - Set up TDS components, attach TDS component groups to them, and define the threshold and exception threshold for them.
        - Set up TDS authorities.
        - Set up TDS settlement periods.
        - Set up TDS tax codes, and attach TDS components to them.
        - Set up TDS tax groups, and attach TDS tax codes to them.
        - In the formula designer, define a formula to calculate TDS for a TDS group.
        - Record TDS concession certificate numbers.

    - Ledger accounts and company setup:

        - Set up TDS payable and receivable ledger accounts.
        - Set up a Tax Deduction and Collection Account Number (TAN) and a deductor type category for the company.

    - Other setup:

        - Set up a payment schedule that includes TDS allocation.
        - Set up a payment fee type for payments to the TDS authority.
        - Set up information about TDS groups, permanent account numbers (PANs), and TANs for vendors and customers.

2. **Calculation of TDS in transactions:**

    - Invoices and payments
    - Promissory notes
    - Advance payments
    - Prepayments

3. **TDS settlement:**

    - Periodic TDS settlement process
    - Settlement of TDS payments to TDS authority vendors and generation of TDS challan

4. **TDS inquiries, statements, and certificate:**

    - Record and update TDS certificate numbers and dates.
    - Generate a TDS inquiry and a posted TDS inquiry.
    - Generate Form 27A, Form 26Q, and Form 27Q TDS and e-TDS quarterly statements.
    - Generate a Form 16A TDS certificate.
