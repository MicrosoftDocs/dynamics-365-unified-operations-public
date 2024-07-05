---
title: Sync the tax setup from the Tax Calculation feature to Dynamics 365 Finance
description: Learn how to sync tax setup master data from the Tax Calculation feature to Microsoft Dynamics 365 Finance, including an overview on sales tax codes.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 02/09/2024
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2021-04-01
ms.search.form: TaxIntegration, TaxServiceParameters
ms.dyn365.ops.version: 10.0.21
---

# Sync the tax setup from the Tax Calculation Service to Dynamics 365 Finance

[!include [banner](../../includes/banner.md)]

This article explains how to sync tax setup master data from the Tax Calculation feature to Microsoft Dynamics 365 Finance.

After you complete the required setup steps in [Get started with Tax Calculation](global-get-started-with-tax-calculation-service.md), the following tax setup data is automatically synced from the Tax Calculation feature to Finance.

## Sales tax code

| Tax Calculation feature           | Finance                             |
| --------------------------------- | ----------------------------------- |
| Tax code                          | Sales tax code                      |
| Description                       | Name                                |
| User input                        | Settlement period                   |
| User input                        | Ledger posting group                |
| User input                        | Sales tax currency                  |
| A negative tax rate is configured | Allow negative sales tax percentage |

## Tax value

| Tax Calculation feature | Finance                   |
| ----------------------- | ------------------------- |
| From transaction date   | From date                 |
| To transaction date     | To date                   |
| Minimum amount          | Minimum limit             |
| Maximum amount          | Maximum limit             |
| Tax rate                | Value                     |
| Non-deductible rate     | Non-deductible percentage |

## Tax limits

| Tax Calculation feature | Finance           |
| ----------------------- | ----------------- |
| From transaction date   | From date         |
| To transaction date     | To date           |
| Minimum tax amount      | Minimum sales tax |
| Maximum tax amount      | Maximum sales tax |

## Sales tax group

| Tax Calculation feature                         | Finance                                    |
| ----------------------------------------------- | ------------------------------------------ |
| Tax group                                       | Sales tax group                            |
| Tax codes under this tax group                  | Sales tax codes under this sales tax group |
| The tax code is marked as **Is Exempt**         | Exempt                                     |
| The tax code is marked as **Is Exempt**         | Exempt code                                |
| The tax code is marked as **Is Reverse Charge** | Reverse charge                             |
| The tax code is marked as **Is Use Tax**        | Use tax                                    |

## Item sales tax group

| Tax Calculation feature             | Finance                                         |
| ----------------------------------- | ----------------------------------------------- |
| Item tax group                      | Item sales tax group                            |
| Tax codes under this item tax group | Sales tax codes under this item sales tax group |

After the synchronization is completed, continue to maintain the remaining parameters in Finance for posting and reporting purposes.

> [!NOTE]
> Synchronization of the tax setup from Finance to the Tax Calculation feature isn't supported. For an existing Finance environment, first create the tax setup in the Tax Calculation feature. Then sync the setup data back to the Finance environment.
