---
# required metadata

title: US Payroll overview
description: Payroll provides full gross-to-net processing for employees in the United States.
author: twheeloc
ms.date: 05/05/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: PayrollWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["248434"]
ms.collection: get-started
ms.assetid: 33dae9aa-f673-4195-9b63-7cb41534c502
ms.search.region: USA
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# US Payroll overview

[!include [banner](../../includes/banner.md)]

US payroll provides gross-to-net processing for employees in the United States. With Payroll you can set up, enter, and maintain all payroll records and transactions. The comprehensive earnings and pay statement process covers federal, state, and local taxes, flexible deduction and benefits processing, and support for garnishments and tax levies. US payroll provides full reporting and inquires for W2 processing, and 940 and 941 reporting. It also lets you view current and historical payroll information for individual employees or for groups of employees.

> [!NOTE]
> Tax updates are being retired for the US payroll feature in Microsoft Dynamics 365 Finance starting July 31, 2024. Tax updates were originally scheduled to be removed as of October 2021, however this was extended to July 2024. For more information, see [Support date extended for tax updates](https://cloudblogs.microsoft.com/dynamics365/it/2020/10/02/support-date-extended-for-tax-updates-in-us-payroll-feature-in-dynamics-365-finance).

## Payroll setup

Basic setup for US payroll involves setting pay cycles and pay periods, calculation frequencies, and setting work schedules. The pay cycle frequency determines how often a pay cycle is run. Pay periods and pay dates are defined as part of the pay cycle. You use the payroll calculation frequency to select the specific pay periods when you want certain earnings or other payroll entities to be processed.

Configuring US payroll also includes setting up earning codes and creating earning code groups, and entering information for tax withholding, benefit accrual, and setting beginning balances.

### Frequencies and cycles

- [Set up pay cycles and pay periods](noam-usa-pay-cycle-pay-period-tasks-sample.md)
- [Set up payroll calculation frequencies](noam-usa-payroll-calculation-frequencies-tasks.md)
- [Set up work schedules and leave](noam-usa-work-schedule-leave-tasks.md)

### Codes

- [Set up earning codes and earning code groups](noam-usa-earning-code-group-tasks.md)

## Taxes

Payroll taxes are set up in two parts. One part covers the settings that are used throughout your organizations, such as the states where you have a connection or the rates for unemployment taxes. The second part includes additional tax information that is provided for each worker.

- [Set up taxes, tax regions, tax codes, and tax groups](noam-usa-tax-information-tasks.md)
- [Tax codes, tax groups, and posting definitions FAQ](noam-usa-tax-codes-tax-groups-definitions.md)

### Find and install tax updates

For information about tax updates, refer to the [Microsoft Dynamics 365 HCM](https://community.dynamics.com/ax/b/axhcmnewslearningshighlights) blog. The blog includes posts that announce the availability of tax updates for Dynamics 365 Human Resources, as well as tax updates for other versions.

## Benefits

Topics related to benefits describe how to set up current and future benefits that workers and their dependents and beneficiaries can receive, and how to maintain payroll information for benefits. Examples of benefits include medical insurance, retirement investments, workers' compensation plans, and parking benefits.

- [Set up benefit accrual plans](noam-usa-benefit-accrual-plan-tasks.md)
- [Set up benefits](noam-usa-benefit-set-up-tasks.md)

## Garnishments, tax levies, and premium earnings

Premium earnings, garnishments, and tax levies won't be used by all employees. If your organization needs to pay premium earnings or garnish an employee's pay, US payroll includes a framework that can help ensure that the impact of these transactions is handled correctly.

- [Set up garnishments and tax levies](noam-usa-garnishment-tax-levy-set-up-tasks.md)
- [Enroll workers in garnishments or tax levies](noam-usa-garnishment-tax-levy-enrollment-tasks.md)
- [Garnishments, tax levies, and administrative fees FAQ](noam-usa-garnishment-tax-levy-administrative-fees.md)
- [Set up premium earnings](noam-usa-premium-earning-setup-tasks.md)

## Payroll processing tasks

Running a payroll includes generating earnings and then issuing worker payments. When those tasks have been completed, you'll post the payroll transactions and then generate vendor invoices, which result in payments being made to employees.

- [Generate earnings for workers](noam-usa-generate-earnings.md)
- [Issue worker payments](noam-usa-issue-worker-payments.md)
- [Post payroll distributions and generate vendor invoices](noam-usa-post-payroll-generate-vendor-invoices.md)
- [Pay statements and payment generation FAQ](noam-usa-pay-statements-payment-generation-process.md)

Several tasks must be completed after you generate pay statements for your employees. These include releasing earnings for payment processing, and at times, holding earnings from payment processing and changing information on earnings statements.

- [Process existing payroll payments](noam-usa-existing-payroll-payments.md)
- [Process existing earnings](noam-usa-existing-earnings.md)
- [Generate and work with pay statement](noam-usa-pay-statements.md)

## Maintenance and reporting

Maintaining your payroll data involves adjusting the carry-forward balances for accrued benefits, removing a worker from enrollment in a benefit accrual plan, or updating rates for a new plan year. It might also be necessary to change benefits for a worker that has a qualifying life event.

- [Payroll data updates FAQ](noam-usa-payroll-data-updates.md)

Standard payroll reports are provided to help you with payroll processing and government reporting. Use these standard reports to create pay statements and W-2 forms that you can issue to your workers, validate payroll taxes and benefit amounts, and complete federal and state regulatory reports.

- [Standard payroll reports](noam-usa-generate-payroll-reports.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

