# Controlling secure access of customer data using Customer Lockbox with Dynamics 365 Finance and Operations applications

[This article is pre-release documentation and is subject to change.]

Most operations, support, and troubleshooting performed by Microsoft personnel (including sub-processors) don't require access to customer data.

With Power Platform Customer Lockbox, we provide an interface for the customers to review and approve (or reject) data access requests in the rare occasion when data access to customer data is needed. It's used in cases where a Microsoft engineer needs to access customer data, whether in response to a customer-initiated support ticket or a problem identified by Microsoft.

This article covers how to enable Customer Lockbox and how lockbox requests are initiated, tracked, and stored for later reviews and audits.

> [!IMPORTANT]
>
> - Customer Lockbox is provided through the Power Platform. It applies to Finance and Operations environments where Power Platform Integration is enabled (see also: [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md)), for all environment specific resources (SQL DBs and Storage Account).
> - Customer Lockbox is available in preview at no cost. When this feature becomes generally available, there will be a cost associated with environments protected with Customer Lockbox.
> - Preview features aren’t meant for production use and may have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.
> - This feature is being gradually rolled out across regions and might not be available yet in your region.

## Summary

You can enable Customer Lockbox for your data sources within your tenant. For the duration of the preview, enabling Customer Lockbox will apply to all environments in the respective tenant. Global administrators and Power Platform administrators can enable the lockbox policy.
Once enabled you can also use Lockbox for the Dynamics 365 Finance and Operations applications within your tenant.

To enable Customer lockbox for your Finance and Operations applications

1. [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md)
1. [Enable and operate Customer Lockbox on the Power Platform](/power-platform/admin/about-lockbox)

### Customer lockbox support in Finance and Operation Environment Add-Ins

A number of Add-Ins may be available in LCS for each Finance and Operations environment once the Power Platform integration has been enabled. Add-Ins that have some limitations for Customer Lockbox are mentioned in the following table (if an Add-In is not in this list, then it supports Customer Lockbox).

|Add In  |Status  |
|--------|--------|
|Tax Calculation|.???.|
|Electronic Invoicing|.???.|
|||

### Customer Lockbox support across Finance and Operations Offers / Applications

Not all applications among Finance and Operations support Customer Lockbox in the preview to the full extent yet. Find more details for individual applications below:

|Offer|Application Status|
|-----|------------------|
|Dynamics 365 Supply Chain Management|Finance and Operations environment provisioned under Dynamics 365 Supply Chain Management offering supports Customer Lockbox for all environment specific resources.|
|Dynamics 365 Human Resources|.???.|
|Dynamics 365 Finance|Finance and Operations environment provisioned under Dynamics 365 Finance offering supports Customer Lockbox for all environment specific resources.<br/>.???.<br/>If you use [Regular Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) to compliment your Dynamics 365 Finance environment then please note that data managed under RCS environment, currently doesn’t support Customer Lockbox. Customer Lockbox support for RCS will be enabled in late 2023.|
|||
