---
title: Fixed assets overview
description: Learn about the Fixed assets module for Russia, including outlines on setting up and working with NVFAs, working clothes, and special rigging.
author: evgenypopov
ms.author: evgenypopov
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 07/10/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-01-04
ms.dyn365.ops.version: 10.0.1
---

# Fixed assets overview

[!include [banner](../../includes/banner.md)]

The **Fixed assets (Russia)** module provides automated accounting of fixed assets, intangible assets, and also working clothes, special rigging, and fixed assets that aren't considered valuable, from the time when they are put into operation and posted to the appropriate accounts until they are disposed of.

The requirements for fixed asset accounting in Russian Federation legislation vary, depending on whether an account is used for accounting purposes or tax purposes. Therefore, to meet the requirements of Russian Federation law, at least two accounting models, financial and tax accounting, should be used for fixed asset accounting records. As a rule, there can be an unlimited number of value models. In addition, you can add models for internal business accounts and for accounts that are based on international standards of accounting.

All transactions for fixed assets and intangible assets can be calculated simultaneously, based on unlimited value models for a single company. For each value model, you can define the currency, posting profile, and financial dimension codes.

A depreciating asset is divided into depreciation groups in a value model. Therefore, the setup of depreciation accrual for various fixed asset subgroups in the value models is flexible. Depreciation groups are used to organize accounting and tax accounting.

Fixed asset transactions can be allocated to various dimension codes, in the same way that they are allocated throughout your accounting system. Cost centers, departments, and expense codes for profit tax can be used as dimension codes.

In addition to providing accounting for fixed assets, the **Fixed assets (Russia)** module has other functionality. Here are some examples:

- Provide detailed information about the company's fixed assets.
- Print the following regulatory forms about fixed asset operations, and create the printed form registry:

    - Acceptance report (\#FA-1 and \#FA-1a)
    - Transference statement (\#FA-1 and \#FA-1a)
    - Statement about fixed asset object acceptance – transference (\#FA-1 and \#FA-1a)
    - Internal transfer slip (\#FA-2)
    - Acceptance-handover statement (\#FA-3)
    - Statement about writing -off (\#FA-4 and \#FA-4a)
    - Inventory card (\#FA-6)
    - Equipment acceptance statement (\#FA-14)

- Maintain a tax accounting for profit tax purposes. As part of this maintenance, you can create deferrals to write off loss in the tax accounting.
- Maintain the accounting of not valuable fixed assets (NVFAs), working clothes, and special rigging.
- Maintain various periodic tasks. These tasks include creating bar codes from fixed asset inventory numbers, initializing depreciation bonuses, and changing the depreciation method.
- Maintain fixed asset operations by using the fixed asset journal (for example, Put into operation, Depreciation, and Writing off).
- Maintain fixed asset operations by using periodic journals (Counting, Revaluation, and Writing off).
- Maintain fixed asset budgeting. 
- Calculate and create tax declarations on assessed tax, transport tax, and land tax.
- Generate various reports.

## Settings

Set up the **Fixed assets** module to help guarantee accurate calculation of accounting transaction values and to simplify the process of working with fixed assets. For more information about how to set up the **Fixed assets** module, see the following topics:

- [Set up fixed assets (Russia)](rus-set-up-fixed-assets.md) – This article explains how to set up fixed assets for Russia. It includes information about how to set up fixed asset value models, posting profiles, fixed asset groups, and fixed asset parameters.
- [Set up depreciation (Russia)](rus-depreciation-setup.md) – This article explains how to set up depreciation for Russian fixed assets. It includes information about how to set up depreciation methods, analysis codes for fixed asset depreciation, and depreciation groups, and how to update the depreciation method for tax accounting.
- [Depreciation methods (Russia)](rus-depreciation-methods.md) – This article describes the various methods that can be used for fixed asset depreciation for Russia and the implementation of those methods in the application. The process of calculating monthly depreciation can be done in several ways. In accounting and tax accounting, there are a linear and non-linear depreciation calculation methods.
- [Depreciation bonuses (Russia)](rus-bonus-depreciation.md) – This article explains how to set up and calculate depreciation bonuses. A depreciation bonus is an additional depreciation amount that is assessed during the first year for some asset types that are operational. You can calculate a depreciation bonus by reducing the value of an asset through means other than the usual rate of depreciation. You can apply depreciation bonus amounts during the accounting period, after the asset is put into operation, or after major repairs. Depreciation bonuses are always calculated and applied before other types of depreciation.
- [Set up fixed asset locations and numbering (Russia)](rus-fixed-assets-locations-numbering.md) – This article explains how to set up locations and numbering for fixed assets. Locations are defined for fixed assets and used to calculate depreciation accrual. Depending on the fixed asset location, the depreciation amount that is calculated is allocated either to the production cost of the product or to a ledger account.

## Working with fixed assets

- [Fixed assets](../../fixed-assets/fixed-assets.md) – Before you create transactions for any fixed or intangible asset, you must register the asset record and provide basic information about it. This article includes a description of the **Fixed asset** page, which is used for registration and provides an overview of fixed asset accounts.
- [Register fixed assets acquisitions (Russia)](rus-register-acquisition.md) – You can register a fixed asset acquisition by using either a vendor invoice journal or a purchase order. Typically, a vendor invoice journal is used if inventory movement of the fixed asset doesn't have to be tracked (for example, if a fixed asset is bought and put into operation during the same period). A purchase order might be used if several identical fixed assets are bought, or if inventory movement of the fixed asset must be tracked. This article explains how to register a fixed asset acquisition by using an invoice journal and a purchase order. It also explains how to reverse a fixed asset acquisition transaction.
- [Acquiring fixed assets and putting them into operation (Russia)](rus-fixed-asset-acquisition.md) – The following depreciated property assets can be acquired and put into operation:

    - Purchased assets
    - Assets that are obtained as a deposit in charter capital
    - Assets that are obtained under a gift agreement (that is, assets that are obtained without compensation)
    - Assets that are obtained in exchange for other property
    - Unaccounted fixed assets that are discovered during inventory
    - Leased fixed assets and funds that are redeemed from a lessor

    For scenarios that involve all these assets, a credit account is used. A credit account provides several options for creating the correction transactions in the ledger. To specify an account, manually create a transaction in the fixed asset journal. Alternatively, on the **Posting profiles** page (**Fixed assets (Russia)** \> **Setup** \> **Posting profiles**), configure the posting profiles for transactions for various types of fixed assets.

    The cost of a fixed asset that was acquired might differ from the purchase cost. For example, the cost might be increased by the addition of miscellaneous charges per acquisition, such as charges for testing and commissioning work.

    This article explains how to acquire a fixed asset (that is, put it into operation), create standard printing forms, assemble a fixed asset, and reverse acquisition transactions.

- [Calculate depreciation (Russia)](rus-depreciation-calculation.md) – This article explains how to calculate fixed asset depreciation. It includes information about how to calculate and reverse depreciation by using the tax non-linear group depreciation method.
- [Partial fixed asset disassembly (liquidation) (Russia)](rus-fixed-assets-disassembly.md) – In accordance with Russian Federation law (PBU 6/01), partial disassembly (liquidation) of fixed asset objects can cause the original value of the asset to change. The components that are removed for disassembly can be accounted for as spare parts. The inventory that remains after the disposal of an asset is posted at its actual cost price. This price is based on the current market value of the inventory on the date of posting to accounting.

    This article includes information about how to configure transaction profiles and create a partial fixed asset disassembly transaction. It also provides information about the various methods for calculating prices.

- [Sell, dispose, and write-off assets (Russia)](rus-sell-dispose-write-off-fixed-assets.md) – You can dispose of fixed assets for any of the following reasons:

    - The assets are sold to other legal entities or private individuals.
    - The assets are transferred and used as a deposit in joint activities or as charter capital.
    - The assets are donated or used as another type of non-compensated transfer.
    - The assets are liquidated because of an accident or natural disaster.
    - The assets are exchanged through an exchange agreement.

    There are three ways to create a disposal transaction: leaving (sale), leaving (dismantlement), and fixed asset write-off. This article explains how to dispose of a fixed asset, set up the automatic creation of a deferrals account, create a sales order for a fixed asset, and create a free text invoice for a fixed asset.

- [Create a fixed asset lease and a return from lease transaction (Russia)](rus-fixed-asset-leasing.md) – This article explains how to lease a fixed asset and register the return of a leased fixed asset.
- [Maintain fixed assets](rus-maintain-fixed-assets.md) – This article includes a description of major repairs. If a fixed asset is inactive for more than three months, or if refurbishment of the asset is done for more than 12 months, the calculation of depreciation is suspended. It's resumed only when the fixed asset is put back into operation. For example, a fixed asset might become inactive in the case of capital improvements. **Capital improvements** is a special asset category that includes capital renovations, improvements, technical updates, additional construction, and the acquisition of additional equipment for a fixed asset. When you update capital improvements, calculated depreciation isn't revalued. However, the depreciated cost and service life of the fixed asset are changed.
- [Fixed asset counting (Russia)](rus-fixed-assets-counting.md) – The procedure for counting fixed assets is regulated by legislative acts and is one of the procedures that help control the safety of a company's property. Essentially, in fixed asset counting, the actual presence of values (money, equipment, buildings, and obligations) is compared with accounting data.
- [Fixed asset currency revaluation](rus-fixed-asset-currency-revaluation.md) – Foreign representatives have the right to keep an account of fixed assets in the foreign currency. Fixed asset accounting, such as business accounting and tax accounting, can be done in different currencies. If a fixed asset value model is entered in a foreign currency, the accounting currency is specified in the asset record. Fixed asset transaction amounts are specified in both the accounting currency and the original company currency at the exchange rate that applied on the transaction date. When the currency exchange rate is changed, a revaluation is calculated, and profit or loss exchange rate adjustment transactions are created both for the **Fixed asset** module and for ledger transactions.
- [Revaluate fixed asset cost and depreciation (Russia)](rus-fixed-assets-revaluation.md) – An organization can independently change the cost of a fixed asset one time per year, at the end of the reporting year (usually on December 31). Revaluation of fixed assets can also occur because of a decision of the state. As a rule, the revaluation of fixed asset cost is accompanied by a revaluation of depreciation. This article includes a description of two methods that can be used to change the cost of fixed assets: indexing and direct recalculation (or direct evaluation).
- [Create and post budget journals for fixed asset acquisitions (Russia)](rus-post-budget-fixed-asset-acquisition.md) – You can create financial plans and current budgets in the **Fixed assets (Russia)** module by using budget models. A budget model represents a collection of planned turnovers for specific accounts and periods. This article explains how to set up budget models and create the fixed asset budget journal.

## Setting up and working with NVFAs, working clothes, and special rigging

- [Not valuable fixed assets (NVFAs) accounting for Russia](rus-not-valuable-assets.md) – Low-value, high-wear items that are used in the workplace can be tracked and accounted for as a special type of fixed assets. These assets are known as not valuable fixed assets (NVFAs). NVFAs are items that cost less than the specified cost limit. The full cost of NVFAs should be written off for depreciation in the first month of use. During the process of purchasing fixed assets, the system divides fixed assets and NVFAs by price, based on the value of the **Max cost of the NVFA** parameter.

    This article includes descriptions of the settings for fixed asset parameters, fixed asset groups, identification of fixed asset groups, inventory dimensions, items, and officials for NVFAs.

- [Working clothes/Special riggings accounting for Russia](rus-working-clothes-instruments-accounting.md) – An organization must account for and create a record for each working clothes item or special rigging asset that is issued to an employee. You can create queries to show all the assets that are on hand for employees, and you can print the **Working clothes issue sheet (No. MB-7)**. You can cancel the working clothes or special rigging issue, or return it to inventory, and you can calculate the net book value and residual wearing period.

    Working clothes and special rigging assets are regulated by their useful life cycle. This period starts when the item is written off from a warehouse and issued to an employee. It ends after the stipulated period of use. The useful life of each item is specified in months. All the data that is related to an item is linked. This information includes the identity of the employee, the useful life of the item, the date when the item is issued to the employee, and the end date that is calculated based on the rating of the item. When the end of the useful life approaches, the item is written off, so that it's no longer assigned to the employee.

    During their life cycle, the cost of these types of assets must be amortized. If the life cycle is longer than the legally defined rate of twelve months, the linear method of depreciation is used. If it's less than twelve months, the cost is written off when the item is issued to the employee. The **Working clothes** and **Special rigging** pages are like the **Fixed assets** page that accounts for all working clothes items and special rigging assets that are issued.

- [Printing forms](printing-forms-fixed-assets.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
