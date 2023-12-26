---
title: Troubleshoot Dynamics 365 Payment Connector for Adyen
description: This article provides troubleshooting guidance for common issues related to the Microsoft Dynamics 365 Payment Connector for Adyen.
author: Reza-Assadi
ms.date: 02/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.industry: Retail
---

# Troubleshoot Dynamics 365 Payment Connector for Adyen

[!include [banner](../includes/banner.md)]

This article provides troubleshooting guidance for common issues related to the Microsoft Dynamics 365 Payment Connector for Adyen. For an overview of the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md).

## POS payment terminals

### General issues

For all general issues, you should always consult the Store Commerce app or IIS Hardware Station event logs first. You can find these logs found under the following nodes in the Microsoft Windows event log:

- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-ModernPOS
- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-Hardware Station

### Failing payment transactions

When payment transactions aren't successfully processed through the Adyen payment terminal, the corresponding error messages in the Dynamics 365 POS will contain a PSP reference number(PSP is the reference ID provided by Adyen used to uniquely identify each transaction). Provide this reference number when you contact Adyen support for help with specific transactions.

### The EFT terminal ID isn't set

<table>
<tbody>
<tr>
<td><strong>Title</strong></td>
<td>EFT Terminal ID is not set</td>
</tr>
<tr>
<td><strong>Symptom</strong></td>
<td>Payment authorization calls fail, and a hardware error occurs. An error message in the event log indicates that the <strong>EFT Terminal ID</strong> value isn't set.</td>
</tr>
<tr>
<td><strong>Root cause</strong></td>
<td>This issue can occur when the <strong>EFT POS Register Number</strong> field isn't set on the register or the IIS Hardware Station. It can also occur if the value is set but isn't correctly synced to the POS terminal. Finally, it can also occur when the value is cached.</td>
</tr>
<td><strong>Fix</strong></td>
<td>Follow the instructions in <a href="adyen-connector-setup.md#set-up-a-dynamics-365-register">Set up a Dynamics 365 register</a>. Then run the <strong>1070</strong> and <strong>1090</strong> distribution schedules. If the issue isn't resolved, consider reactivating the Store Commerce app, because the value of the <strong>EFT POS Register Number</strong> field might be cached and might need to be reset.</td>
</tr>
</tbody>
</table>

### The Store Commerce app or IIS Hardware Station configuration isn't updated

<table>
<tbody>
<tr>
<td><strong>Title</strong></td>
<td>Config is not updated</td>
</tr>
<tr>
<td><strong>Symptom</strong></td>
<td>Store Commerce app error: "Sign in Error. The initialization data couldn't be loaded."</td>
</tr>
<tr>
<td><strong>Root cause</strong></td>
<td>This issue can occur when the POS is redeployed but the dllhost.config file hasn't been updated.</td>
</tr>
<td><strong>Fix</strong></td>
<td>Follow the instructions in <a href="adyen-connector-setup.md#update-the-store-commerce-app-or-iis-hardware-station-configuration">Update the Store Commerce app or IIS Hardware Station configuration</a>. Then end the dllhost.exe task on the <strong>Details</strong> tab in Task Manager, and reopen Store Commerce app. If you're using an IIS Hardware Station, reset IIS.</td>
</tr>
</tbody>
</table>

### Invoicing sales orders failed due to stale authorization

| Title | Capture failed due to stale authorization |
|---|---|
| Symptom | Invoicing sales orders fails with "Exception has been thrown by the target of an invocation. System.ArgumentNullException: Value cannot be null." The underlying error in the logs is "The following error occurred during the capture call - Dynamics 365 Payment Connector for Adyen: Error code Decline message Capture failed due to stale authorization." |
| Root cause | This error happens when an authorization older than the **Authorization stale period (days)** is sent to the payment connector for capture. |
| Fix | Ensure the value of **Number of days before expired** in **Accounts receivable parameters, Credit Card** is set to **1 less day** than the value set in merchant properties for all channels and then retry invoicing. The recommended value for **Authorization stale period (days)** is 14 in Adyen merchant properties and 13 in Accounts receivables parameters. |

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md)

[Dynamics 365 Payment Connector for Adyen FAQ](adyen-connector-faq.md)

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
