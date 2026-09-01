---
title: Manage database storage in Dynamics 365 Commerce
description: Learn about supported options for reducing database storage in Dynamics 365 Commerce by compressing, archiving, or purging data and configuring retention.
author: zhfk930129
ms.author: fangzhan
ms.topic: overview
ms.date: 09/01/2026
ms.reviewer: mirao
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2026-09-02
ms.custom:
  - bap-template
---

# Manage database storage in Dynamics 365 Commerce

[!INCLUDE [banner](includes/banner.md)]

This article summarizes the supported options for reducing the database storage used by Microsoft Dynamics 365 Commerce. It covers the Commerce headquarters database and Commerce Scale Unit (CSU) channel databases. Use the linked articles for setup instructions and the complete prerequisites for each option.

## Before you begin

Before you archive or delete data, complete the following steps:

1. Identify the database and data category that account for the storage growth.
1. Confirm your organization's legal, tax, audit, return, and refund retention requirements.
1. Test the operation in a sandbox environment before you use it in production.
1. Schedule resource-intensive jobs outside peak business hours and monitor the first runs.

> [!IMPORTANT]
> You can't recover purged and deleted data. Some archived payment data can't easily be restored and might no longer support linked refunds. Review the warnings in the detailed feature documentation before you run a job.

## Choose a storage management option

The following table summarizes the supported options:

| Goal | Database or data | Option | Availability or prerequisite |
| ---- | ---------------- | ------ | ---------------------------- |
| Reduce the size of stored payment tokens | Commerce headquarters, `RetailTransactionPaymentTrans` | [Compress payment tokens](dev-itpro/archive-cc-data.md#further-storage-management-with-token-compression) | Commerce headquarters version 10.0.25 or later and POS version 9.35 or later. Starting in Commerce headquarters version 10.0.49, you can run compression independently of the **Archive credit card transaction data** job. |
| Archive or delete old payment tokens in `RetailTransactionPaymentTrans` | Commerce headquarters, `RetailTransactionPaymentTrans` | [Archive credit card transaction data](dev-itpro/archive-cc-data.md) | Commerce headquarters version 10.0.17 or later. The same job supports both archiving and deleting payment tokens in `RetailTransactionPaymentTrans`, based on a parameter. |
| Archive or delete old payment tokens in `CreditCardAuthTrans` | Commerce headquarters, `CreditCardAuthTrans` | Archive credit card authorization data | Commerce headquarters version 10.0.23 or later. The same job supports both archiving and deleting payment tokens in `CreditCardAuthTrans`, based on a parameter. |
| Retain posted Commerce transactions in long-term storage | Commerce headquarters, Commerce transaction tables | [Archive Commerce transactions](archive-transactions.md) | Generally available in Commerce version 10.0.47. |
| Permanently delete old Commerce transactions | Commerce headquarters, Commerce transaction tables | [Purge Commerce transactions](purge-transactions.md) | Available in Commerce version 10.0.42 and enabled by default in version 10.0.47. |
| Retain eligible sales orders in long-term storage | Commerce headquarters, sales order data | [Archive Supply Chain Management sales order data](../fin-ops-core/dev-itpro/sysadmin/archive-so.md?context=/dynamics365/context/commerce) | Sales orders must be fully invoiced and can't be part of an intercompany order chain. |
| Automatically remove aged transactions and carts | CSU channel database | [DB maintenance agent](#db-maintenance-agent) (preview) | Rollout starts in August 2026 and gradually expands to all CSUs. Cleanup follows the retention settings in the POS and online store functionality profiles. |

## Manage Commerce headquarters storage

### Payment tokens

Credit card tokens can make the `RetailTransactionPaymentTrans` and `CreditCardAuthTrans` tables grow significantly. A separate batch job manages the tokens in each table. Commerce provides archival, deletion, and compression options for managing payment token data.

#### Archive payment tokens

Archival exports payment token data to Azure Blob Storage through document management, and then deletes that data from the database.

> [!IMPORTANT]
> Set the minimum age so that transactions remain available throughout your linked-refund period. If you archive the data that's required for a linked refund, you must process the refund as a standalone refund.

##### Archive payment tokens from the RetailTransactionPaymentTrans table

The **Archive credit card transaction data** job exports aged payment tokens from the `RetailTransactionPaymentTrans` table to Azure Blob Storage, and then deletes that token data from the table. The job archives the `PaymentAuthorization`, `PaymentCaptureToken`, `PaymentCardToken`, and `SigCapData` fields. Use the **Minimum transaction age in days** parameter to control which data the job processes. For more information, see [Archive credit card transaction data](dev-itpro/archive-cc-data.md).

##### Archive payment tokens from the CreditCardAuthTrans table

The **Archive credit card authorization data** job exports aged payment tokens from the `CreditCardAuthTrans` table to Azure Blob Storage, and then deletes that token data from the table. The job archives the `CardTokenRequest` and `CardTokenResult` fields.

#### Delete payment tokens

If your organization doesn't have to retain payment token data, each job can permanently delete the data instead of archiving it. You can't recover deleted data.

##### Delete payment tokens from the RetailTransactionPaymentTrans table

The **Archive credit card transaction data** job has a **Delete data without archiving** option. If you enable this option, the payment token fields are permanently deleted instead of being archived. The job deletes the `PaymentAuthorization`, `PaymentCaptureToken`, `PaymentCardToken`, and `SigCapData` fields. For more information, see [Archive credit card transaction data](dev-itpro/archive-cc-data.md).

##### Delete payment tokens from the CreditCardAuthTrans table

The **Archive credit card authorization data** job has a **Prevent uploading into blob storage** option. If you enable this option, the payment token fields are permanently deleted instead of being archived. The job deletes the `CardTokenRequest` and `CardTokenResult` fields.

#### Compress payment tokens

The **Compress payment tokens** feature compresses stored payment tokens. Therefore, it reduces the storage that the tokens use while it keeps the tokens in place. To use this feature, enable it in the **Feature management** workspace. Starting in Commerce version 10.0.49, you can compress payment tokens independently of the **Archive credit card transaction data** job. For more information, see [Further storage management with token compression](dev-itpro/archive-cc-data.md#further-storage-management-with-token-compression).

### Commerce transactions

Select archive or purge operations based on whether your organization needs to retain historical transaction data.

- **Archive Commerce transactions** uses Dataverse long-term retention to archive posted transactions. The archive process supports the Commerce transaction tables listed in [Archive Commerce transactions](archive-transactions.md#tables-archived-by-the-retail-long-term-retention-job).
- **Purge Commerce transactions** permanently deletes transactions for the selected period, regardless of posting status. A purge can cover a maximum of six months at a time, and its start and end dates must be before the previous calendar year. Only users who have the **Information technology officer** role can run the job. For the complete table list and restrictions, see [Purge Commerce transactions](purge-transactions.md#tables-purged-by-the-purge-commerce-sales-transactions-job).

### Sales orders

If sales order data contributes to database growth, use the Dynamics 365 Supply Chain Management archive framework to move eligible sales orders to Dataverse long-term retention. The orders must be fully invoiced and can't be part of an intercompany order chain. For setup and scheduling instructions, see [Archive Supply Chain Management sales order data](../fin-ops-core/dev-itpro/sysadmin/archive-so.md?context=/dynamics365/context/commerce).

### Monitor table storage changes

To monitor the effect of storage-management features on the Commerce headquarters database, use the [table-level storage consumption view for finance and operations environments](/power-platform/admin/finance-operations-storage-capacity#table-level-drill-down-view-into-storage-consumption-details-for-finance-and-operations-environments) in the Power Platform admin center.

On the **Finance and Operations** capacity page, select the value in the **Finance and operations database usage** column for the environment. The **Finance and operations database usage** pane provides a near real-time snapshot of storage consumption by table. Select **View as chart** to track the storage trend for a specific table over time, or select **Export to CSV** to analyze the table-level details outside the admin center.

Record a baseline before you enable a feature or run a job, and then review the affected tables after each initial run. For example, monitor `RetailTransactionPaymentTrans` and `CreditCardAuthTrans` after payment-token compression, archival, or deletion, and monitor the Commerce transaction tables after an archive or purge job.

## Manage CSU channel database storage

### Configure transaction and cart retention

Commerce headquarters has separate functionality profiles for POS and online stores. Configure the applicable retention values based on your business requirements:

- **POS functionality profile**: Go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS profiles** > **Functionality profiles**, and configure **Days transactions exist**.
- **Online store functionality profile**: Go to **Retail and Commerce** > **Channel setup** > **Online store setup** > **Functionality profiles**, and configure **Days transactions exist** and **Days carts exist**.

Set **Days transactions exist** to the same value as, or close to, your return-policy period. For example, if the standard return period is 30 days, use 30 or 31 days. If your organization allows exceptions, use a value that also covers those exceptions. For more information, see [Commerce Data Exchange best practices](dev-itpro/CDX-Best-Practices.md#valuable-configurations). Set **Days carts exist** to the number of days that your organization must retain inactive carts.

### DB maintenance agent

> [!IMPORTANT]
> The DB maintenance agent is available as a public preview starting in August 2026. Microsoft is gradually rolling it out to all CSUs. So, availability can differ among CSUs during the rollout. The preview functionality is subject to change.

The DB maintenance agent applies the functionality-profile settings as follows:

| Channel | Setting | Data cleaned up |
| ------- | ------- | --------------- |
| POS | **Days transactions exist** | POS carts and transactions |
| Online store | **Days transactions exist** | Online store transactions |
| Online store | **Days carts exist** | Online store carts |

## Recommended actions

Select the actions that meet your organization's data-retention and storage requirements:

- Define the required retention period for each data category, including return and linked-refund periods.
- Use non-destructive compression where it's supported and appropriate.
- Archive data that must remain available for historical or compliance purposes.
- Delete or purge data only after you confirm that it no longer has any business, legal, or regulatory value.
- Configure transaction and cart retention to limit future CSU channel database growth.
- Schedule recurring jobs where the feature supports recurrence.
- Use the Power Platform admin center table-level view to monitor Commerce headquarters storage before and after you apply a storage management feature.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
