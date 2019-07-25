---
# required metadata
title: Fixed assets overview 
description: This topic provides information about the Fixed assets module for Russia.
author: v-oloski
manager: AnnBe
ms.date: 07/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2019-01-04
ms.dyn365.ops.version: 10.0.1

---

# Fixed assets overview

[!include [banner](../includes/banner.md)]

The **Fixed assets (Russia)** module provides the automated accounting of fixed assets and intangible assets. The module also includes working clothes, special rigging, and fixed assets that are not considered valuable from the time they are put into operation and posted to the appropriate accounts until they are disposed of.  
Russian Federation legislation contains differences in the requirements for fixed asset accounting, depending on whether an account is used for accounting or tax purposes. Therefore, to meet the requirements of the Russian law, at least two accounting models, financial and tax accounting, should be used for fixed asset accounting records. As a rule, there can be an unlimited number of value models. In addition, you can add models for internal business accounts and for accounts based on international standards of accounting.

All fixed and intangible asset transactions can be calculated simultaneously, according to unlimited value models for a single company. You can define the currency, posting profile, and financial dimension codes for each value model.

A depreciating asset is divided into depreciation groups within a value model. This allows for a flexible setup of depreciation accrual for various fixed asset subgroups within the value models. Depreciation groups are used to organize accounting and tax accounting.

Fixed asset transactions can be allocated to various dimension codes in the same way that they are allocated throughout your accounting system. Cost centers, department, and expense codes for profit tax can be used as dimension codes.

In addition to providing accounting for fixed assets, the Fixed assets (Russia) module has other functionalities. These include:

- Providing detailed information about the company's fixed assets.
- Printing the following regulatory forms regarding fixed asset (FA) operations and creating the printed form registry:  

    - Acceptance report (#FA-1 and #FA-1a)
    - Transference statement (#FA-1 and #FA-1a)
    - Statement about fixed asset object acceptance – transference (#FA-1 and #FA-1a)
    - Internal transfer slip (#FA-2)
    - Acceptance-handover statement (#FA-3)
    - Statement about writing -off (#FA-4 and #FA-4a)
    - Inventory card (#FA-6)
    - Equipment acceptance statement (#FA-14). 

- Maintaining tax accounting for profit tax purposes, including creating deferrals for writing-off loss in the tax accounting.
- Maintaining the accounting of non-valuable fixed assets, working clothes, and special rigging. 
- Maintaining different periodic tasks such as creating barcodes from FA Inventory numbers, Depreciation bonus initialization, and changing depreciation method.  
- Maintaining fixed asset operations by using the fixed asset journal (Put into operation, Depreciation, writing-off etc.) 
- Maintaining fixed asset operations by using periodic journals (Counting, Revaluation and Writing off)
- Maintaining fixed asset budgeting. 
- Calculating and creating tax declarations on assessed tax, transport tax, and land tax.
- Different reports

## Settings
Set up the Fixed asset module to provide accurate calculations of accounting transaction values and simplified work with Fixed assets. For more information about setting up the Fixed asset module see:

- [Set up fixed assets (Russia)](rus-set-up-fixed-assets.md): This topic explains how to set up fixed assets for Russia and includes description of settings fixed asset value models, posting profiles, fixed asset groups, and fixed asset parameters. 
- [Set up depreciation (Russia)](rus-depreciation-setup.md): This topic explains how to set up depreciation for Russian fixed assets including setting depreciation methods, analysis codes for fixed asset depreciation, depreciation groups, and updating the depreciation method for tax accounting.
- [Depreciation methods (Russia)](rus-depreciation-methods.md): This topic describes the various methods that can be used for fixed asset depreciation for Russia and implementation in the application. The process of calculating monthly depreciation can be done in several ways. In tax accounting and accounting, there are a linear and non-linear depreciation calculation methods.
- [Depreciation bonuses (Russia)](rus-bonus-depreciation.md): The depreciation bonus is an additional depreciation amount that is assessed during the first year for some asset types that are operational. You can calculate a depreciation bonus by reducing the value of an asset through means other than the usual rate of depreciation. You can apply depreciation bonus amounts during the accounting period, after the asset is put into operation, or after major repairs. Depreciation bonuses are always calculated and applied before other types of depreciation. This topic also includes description of setting and calculation of depreciation bonus.
- [Set up fixed asset locations and numbering (Russia)](rus-fixed-assets-locations-numbering.md): This topic includes description of setting locations and fixed asset numeration. Locations are defined for fixed assets and used to calculate depreciation accrual. Depending on the fixed asset location, the calculated depreciation amount is allocated either to the production cost of the product or to a ledger account.

## Working 
- [Fixed assets](../fixed-assets/fixed-assets.md): Before you create transactions for any fixed or intangible asset, you must first register the asset record, and provide the basic information about it. This topic includes a description of the **Fixed asset** page, which is used for registering and overview fixed asset account.
- [Register fixed assets acquisitions (Russia)](rus-register-acquisition.md): You can register a fixed asset acquisition using a vendor invoice journal or a purchase order. Typically, a vendor invoice journal is used if there is no need to track the inventory movement of the fixed asset. For example, a fixed asset is bought and put into operation during the same period. A purchase order might be used if several identical fixed assets are bought or if it is necessary to track the inventory movement of a fixed asset. This topic includes description of registering a fixed asset acquisition using an invoice journal, a purchase order, and reversing a fixed asset acquisition transaction
- [Acquiring fixed assets and putting them into operation (Russia)](rus-fixed-asset-acquisition.md): The following depreciated property assets can be acquired and put into operation:

  - Purchased assets
  - Assets that are obtained as a deposit in charter capital
  - Assets that are obtained under a gift agreement (obtained without compensation)
  - Assets that are obtained in exchange for other property
  - Unaccounted fixed assets that are discovered during inventory
  - Leased fixed assets and funds that are redeemed from a lessor

  For scenarios that involve all of these assets, a credit account is used. A credit account provides several options for creating the correction transactions in the ledger. To specify an account, manually create a transaction in the **Fixed asset** journal. Alternatively, on the **Posting profiles** page (**Fixed assets (Russia)** \> **Setup** \> **Posting profiles**), configure the posting profiles for transactions for various types of fixed assets.

  The cost of an acquired fixed asset might differ from the purchase cost. For example, the cost might be increased by the addition of miscellaneous charges per acquisition, such as charges for testing and commissioning work.
  This topic includes description of acquiring a fixed asset (putting into operation), creating standard printing forms, fixed asset assembling, reversing acquisition transactions.

- [Calculate depreciation (Russia)](rus-depreciation-calculation.md): This topic includes description of fixed asset depreciation calculation, calculation, and reversing depreciation by using the tax non-linear group depreciation method.
- [Partial fixed asset disassembly (liquidation) (Russia)](rus-fixed-assets-disassembly.md): In accordance with Russian Federation law (PBU 6/01), partial disassembly (liquidation) of fixed asset objects can cause the original value of the asset to change. The components that are removed for disassembly can be accounted for as spare parts. The inventory that remains after the disposal of an asset is posted at it's actual cost price. This price is based on the current market value of the inventory on the date of posting to accounting.
This topic includes description of configuration of transaction profiles, creation of a partial fixed asset disassembly transaction, and methods of calculating prices.
- [Sell, dispose, and write-off assets (Russia)](rus-sell-dispose-write-off-fixed-assets.md): You can dispose of a fixed asset for any of the following reasons:

  - Sold to other legal entities or private individuals
  - Transferred and used as a deposit in joint activities or as charter capital
  - Donated or used as another type of non-compensated transfer
  - Liquidated because of an accident or natural disaster
  - Exchanged through an exchange agreement
  
    There are three ways to create a disposal transaction: Leaving (sale), Leaving (dismantlement), and Fixed Assets write-off. This topic includes description of fixed asset disposal, setting the automatic creation of a deferrals account, creating a sales order for a fixed asset, and creating a free text invoice for a fixed asset.

- [Create a fixed asset lease and a return from lease transaction (Russia)](rus-fixed-asset-leasing.md): This topic provides information about leasing a fixed asset and registering the return of a leased fixed asset.
- [Maintain fixed assets](rus-maintain-fixed-assets.md): This topic includes a description of major repair. If a fixed asset is inactive for more than three months, or if refurbishment of the asset is conducted for more than 12 months, the calculation of depreciation is suspended only to resume when the fixed asset is put back into operation. For example, a fixed asset may become inactive in the case of capital improvements. **Capital improvements** is a special asset category that includes capital renovations, improvements, technical updates, additional construction, and the acquisition of additional equipment for a fixed asset. When you update capital improvements, calculated depreciation isn't revalued. However, the depreciated cost and service life of the fixed asset are changed.
- [Fixed asset counting (Russia)](rus-fixed-assets-counting.md): The procedure for counting fixed assets is regulated by legislative acts and is one of the procedures that help control the safety of a company's property. Essentially, in fixed asset counting, the actual presence of values (money, equipment, buildings, and obligations) is compared with accounting data.
- [Fixed asset currency revaluation](rus-fixed-asset-currency-revaluation.md): Foreign representatives have the right to keep an account of the fixed assets in the foreign currency. Fixed asset accounting, such as business accounting and tax accounting, can be executed in different currencies. If a fixed asset value model is entered in a foreign currency, the accounting currency is specified in the asset record. Fixed asset transaction amounts are specified in both the accounting currency and the original company currency at the exchange rate that applied on the transaction date. When the currency exchange rate is changed, a revaluation is calculated, and profit or loss exchange rate adjustment transactions are created both for fixed asset module and ledger transactions.
- [Revaluate fixed asset cost and depreciation (Russia)](rus-fixed-assets-revaluation.md): An organization can independently change the cost of a fixed asset one time per year at the end of the reporting year (usually on 31 December). Revaluation of fixed assets can also occur because of a decision of the state. As a rule, the revaluation of fixed assets cost is accompanied by a revaluation of depreciation. This topic includes a description of two methods, Indexing and Direct recalculation or evaluation, which can be used to change the cost of fixed assets.
- [Create and post budget journals for fixed asset acquisitions (Russia)](rus-post-budget-fixed-asset-acquisition.md): You can create financial plans and current budgets in the **Fixed assets (Russia)** module by using budget models. A budget model represents a collection of planned turnovers for specific accounts and periods. This topic includes description of budget model setting and creation of the FA budget journal.

## Set up and work with not valuable fixed assets (NVFAs), working clothes and special riggings

- [Not valuable fixed assets (NVFAs) accounting for Russia](rus-not-valuable-assets.md): You can track and account for low-value, high-wear items that are used in the workplace as a special type of fixed asset named, not valuable fixed assets (NVFAs). NVFAs are items that cost less than the specified cost limit. The full cost of NVFAs should be written off for depreciation in the first month of use. In the process of Fixed asset purchasing ,the system divides fixed assets and NVFAs by price according to the max cost of the NVFA parameter value. This topic includes a description of the fixed asset parameter settings, FA groups, identification of FA groups, inventory dimensions, items, and officials for NVFA. 
- [Working clothes/Special riggings accounting for Russia](rus-working-clothes-instruments-accounting.md): An organization must account and create a record for each working clothes item or special rigging asset that is issued to an employee. You can create queries to display all of the assets that are on-hand for employees and print the **Working clothes issue sheet (No. MB-7)**. You can cancel or return the working clothes or special rigging issue to the inventory and calculate the net book value and residual wearing period.
Working clothes and special rigging assets are regulated by their useful life cycle. This period starts when the item is written off from a warehouse and issued to an employee. The period ends after the stipulated period of use. The useful lifetime is specified in months for each item. All of the data that pertains to an item is linked. This includes the identity of the employee, the useful life of the item, the date when the item is issued to the employee, and the calculated end date based on the rating of the item. When the end of the useful life approaches, the item is written off, so that it is no longer assigned to the employee.
During their life cycle, the cost of these types of assets must be amortized. If the life cycle is longer than the legally defined rate of twelve months, the linear method of depreciation is used. If it is less than twelve months, the cost is written off when the item is issued to the employee. The **Working clothes** and **Special rigging** pages are like the **Fixed assets** page, which accounts for all issued working clothes and special rigging.
- [Printing forms](printing-forms-fixed-assets.md)





