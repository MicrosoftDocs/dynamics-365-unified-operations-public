---
# required metadata

title: Set up taxes, tax regions, tax codes, and tax groups
description: This article describes the configuration of tax data and employer tax regions, including how to create tax regions, and then set up tax codes and tax groups.
author: twheeloc
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PayrollTaxCode, PayrollTaxGroup, PayrollWorkerTaxCode, PayrollWorkerTaxRegion
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 222684
ms.assetid: 5fc7b03b-0a18-4dd5-a717-85e40fbbf357
ms.search.region: USA
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up taxes, tax regions, tax codes, and tax groups

[!include [banner](../../includes/banner.md)]

This article describes the configuration of tax data and employer tax regions. It also explains how to create tax regions, and then set up tax codes and tax groups.

Payroll taxes are set up in two parts. The first part, which is described in this article, covers the settings that are used throughout the organization, such as the states where you have a nexus or the rates for unemployment taxes. The second part, which is described in [Set up payroll for workers](noam-usa-worker-position-payroll-tasks.md), covers the additional tax information that must be provided for each worker. For more information about payroll taxes, see [Tax codes, tax groups, and posting definitions FAQ](noam-usa-tax-codes-tax-groups-definitions.md) and [Payroll data updates FAQ](noam-usa-payroll-data-updates.md).

## Prerequisites

The primary address for the legal entity must be in the United States.

## Set up tax data

To set up tax data, you must update the tax data to make tax codes and system-defined tax groups available. Click **Payroll** &gt; **Setup** &gt; **Taxes** &gt; **Update tax data**.

The first time that you run the **Update tax data** process, the full set of supported payroll taxes is loaded, and system-defined tax groups are automatically created. The supported taxes and system-defined tax groups are then updated every time that you run the **Update tax data** process.

Each system-defined tax group contains tax codes of a particular type. For example, all tax codes for school districts are included in the SCHL tax group, and all tax codes for state income tax are included in the SIT tax group. If these system-defined tax groups meet your organization's requirements, you don't have to create additional tax groups.

## Set up employer tax regions for nexus

Multiple factors determines whether a legal entity must pay and withhold taxes in a state. One of the most important factors is whether the legal entity has a *nexus*, or a significant business presence, in that state. In Microsoft Dynamics AX, every state or territory where a legal entity has a nexus is defined as an employer tax region. Every legal entity must have at least one employer tax region. Legal entities that have a nexus in more than one state have multiple employer tax regions. These employer tax regions are used together with multiple-state taxation and reciprocity rules to determine when and where taxes are withheld and paid.

> [!IMPORTANT]
> The question of whether a legal entity has a nexus in a particular state can be complex and difficult to answer. Typically, your legal advisors will make the determination.

## Create tax regions

*Tax regions* are geographic areas where a specific set of payroll taxes applies. Generally, tax regions correspond to the cities or towns where your workers reside or work. A *worker tax region* is a tax region that has been assigned to a specific worker. A *default tax region* is a worker tax region that is used to generate earnings for a specific position that the worker holds.

Before you begin, it's helpful if you determine the county, state, and ZIP/postal code for each city that you identify as a tax region.

To save time when you create tax regions, you can enter any part of the location information. For example, you can enter only the state or only the ZIP/postal code. If more than one tax region matches the location information that you entered, the **Multiple tax regions** page opens. You can then select the correct region in the list of cities that appears on that page.

> [!TIP]
> In the **Name or description** field, include the name of the state as the first part of the tax region name. Tax regions in the same state will then be sorted together.

For information about how to assign tax regions to workers, see [Set up payroll for workers](noam-usa-worker-position-payroll-tasks.md).

## Set up tax codes

You don't have to create tax codes. The codes for all payroll taxes that Dynamics AX supports are provided for you. However, you must provide information about how your organization uses each tax code.

You can create as many versions of the data for each tax code as you require. However, only one version can be active for a legal entity at any time. The **Tax codes** page always shows the version that is currently active for the selected legal entity.

Tax codes are automatically assigned to workers, based on their worker tax regions, position, and legal entity. You can then set up the worker tax code for each worker's individual tax situation. For information about how to set up worker tax codes, see [Set up payroll for workers](noam-usa-worker-position-payroll-tasks.md).

> [!IMPORTANT]
> Dynamics AX doesn't support the following taxes:
>
> - **Employer head taxes** – Taxes that aren't based on a payment, but that are calculated based on the number of employees who are paid over a specific period.
> - **Employer percentage of payroll taxes** – Taxes that aren't based on a payment, but that are calculated based on the amount that is paid to employees over a specific period.
> - **RRTA taxes** – The employee portion of the railroad retirement (RRTA) tax.
> - **Employer RRTA taxes** – The employer portion of the RRTA tax.
> - **Employer RUIA taxes** – Railroad unemployment (RUIA) taxes that are paid by the employer.
> - **SUTA surcharges** – Although base state unemployment (SUTA) taxes are supported, individual surcharges aren't calculated independently. You must increase the defined base SUTA rate to cover the calculation of any SUTA surcharges. Then, when you file, you must manually list the amounts.
> - **Ohio JEDD taxes** – A type of local tax in the state of Ohio that is managed by the Joint Economic Development Districts (JEDD).

There might be other taxes that Dynamics AX doesn't support. To verify whether a tax is supported, see the tax codes that are delivered with the system, or contact product support. Because legislative changes can also change the taxes that are supported, changes are noted in the release documentation for each tax update. The following information is built into the tax code and can't be changed.

| Field                               | Description |
|-------------------------------------|-------------|
| Tax code Description Country/region | The description is printed on pay statements and other reports. If this description should not be printed, enter a different description in the **Report description** field on the **General** tab. |
| Lock pay statement                  | If this option is selected, tax lines that are related to this tax code can't be modified on pay statements. |
| Employer tax                        | If this option is selected, the tax is an employer tax that is paid by the employer. If this option is cleared, the tax applies to the employee and is withheld from the employee's gross pay. |

If a tax code is used by more than one legal entity in your organization, you must set up the tax code for each legal entity.

> [!NOTE]
> For many tax codes, the fields on the **General** tab are blank. We recommend that you review all settings, even the settings on the **Accounting** tab, to verify that a tax code has been set up for a legal entity. On the **General** tab, specify the following information.

| Field              | Description |
|--------------------|-------------|
| Report description | Optional: To overwrite the description of the tax code that appears on reports, such as printed pay statements, enter the new description here. To use the default description, leave this field blank. |
| Account ID         | Enter the account number that the legal entity has with the taxing authority. State income taxes always have an account ID. If the taxing authority hasn't specified an account ID, leave this field blank. |
| Wage base          | Enter the value that is specified by the taxing authority. If the taxing authority doesn't specify a wage base, leave this field blank. |
| Rate               | Enter the rate that the legal entity pays. For example, if the rate is 2.5 percent, enter **0.025**. Unemployment taxes always have a specified rate. For other taxes, if the taxing authority hasn't specified a rate, leave this field blank. **IMPORTANT:**  Although base state unemployment taxes are supported, individual surcharges aren't calculated independently. You must increase the defined base SUTA rate to cover the calculation of any SUTA surcharges. Then, when you file, you must manually list the amounts. |

On the **Accounting** tab, specify the following information.

| Field                        | Description |
|------------------------------|-------------|
| Vendor                       | To automatically create invoices for the calculated tax amounts, enter the agency that the tax is paid to. If you prefer to create tax invoices manually, leave this field blank. |
| Project category             | If the tax code is used for employer tax transactions that are posted to a project instead of the general ledger, select a project category. If a tax code must be posted to a project, you must specify a project category on the tax code line before you can generate a pay statement. **NOTE:**  This field is never used for taxes that are paid by the worker. |
| Default financial dimensions | Define the default financial dimensions for the main account. When you select a financial dimension value, the **Where the %1 dimension is used** field group shows where the dimension is used in account structures and advanced rule structures. |
| Main account                 | Enter the main account that this tax will be posted to. For employer taxes, employer tax transaction costs are posted to the main account. For employee taxes, the withholding liability is posted to the main account. This account is used for all transactions that are related to this tax code and legal entity. |

## Optional: Set up tax groups

You can use tax groups to help sort and select payroll taxes. You can also use them to update the accounting data for all the tax codes in a tax group at the same time.

When you set up Payroll, a set of system-defined tax groups is automatically created the first time that you run the **Update tax data** process. System-defined tax groups are then updated every time that you run that process. Each system-defined tax group contains tax codes of a particular type. For example, all tax codes for school districts are included in the SCHL tax group, and all tax codes for state income tax are included in the SIT tax group. If these system-defined tax groups meet your organization's requirements, you don't have to create additional tax groups.

However, if several tax codes share the same accounting data, you might want to put these tax codes in a single tax group. Then, if the vendor changes, you can use the tax group to change the vendor for all the tax codes in the group at the same time. This approach can save time and reduce the risk of errors.

In most cases, when you create a list of tax codes to include in each tax group, you will include all the tax codes that share the same accounting information in a single tax group. Additionally, if a set of tax codes shares the same posting requirements, you can include them in a single tax group that you enable for posting definitions. A tax code can be included in multiple tax groups, provided that only one of the tax groups is enabled for posting definitions. For more information, see [Tax codes, tax groups, and posting definitions FAQ](noam-usa-tax-codes-tax-groups-definitions.md).

> [!TIP]
> You can set up the transaction posting definitions so that some tax codes in the group use a different posting definition than the rest of the tax codes in the group. For more information, see [Tax codes, tax groups, and posting definitions FAQ](noam-usa-tax-codes-tax-groups-definitions.md).

After you create tax groups that are enabled for posting definitions, you can assign those tax groups to transaction posting definitions. For more information, see [Posting definitions in the public sector](../../../../finance/public-sector/posting-definitions-public-sector.md).

## Next step

The next step is to set up benefits and mandatory deductions. For more information, see [Set up benefits](noam-usa-benefit-set-up-tasks.md).

## Additional resources

[Set up payroll for workers](noam-usa-worker-position-payroll-tasks.md)

[Posting definitions in the public sector](../../../../finance/public-sector/posting-definitions-public-sector.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
