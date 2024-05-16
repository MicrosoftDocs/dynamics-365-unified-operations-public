---
title: View independent software vendor license status
description: Learn about how to view the status of an independent software vendor in finance and operations apps, including additional resources.
author: Peakerbl
ms.author: johnmichalak
ms.topic: article
ms.date: 04/20/2021
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.17
---

# View independent software vendor license status

[!include [banner](../includes/banner.md)]


This article explains how you can view the status of independent software vendor (ISV) licenses for finance and operations apps, such as Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Commerce.

License codes and configuration keys are part of the ISV licensing model for finance and operations apps.

> [!NOTE]
> Configuration keys that are provided by Microsoft aren't part of the licensing model for finance and operations apps. The keys are only used to enable and disable functionality.

When an ISV license key and code are installed, the corresponding configuration key will be available and enabled on the **License configuration** page.

## View ISV license status
Each ISV solution that is tied to a license runs only when a valid license code exists in the customer's environment. Therefore, if an ISV ties their solution to a license, but the customer doesn't have a valid license code, the solution doesn't run. To prevent the loss of functionality, it's important to track the expiration dates, if applicable, for license codes. To view the expiration dates, go to **System administration** > **Setup** > **License configuration**, and select the **License codes** tab.

To avoid downtime, review the expiration dates of the license keys, and if applicable, obtain and import new license keys before moving to a new version.
The **License codes** tab shows the expired license codes. The corresponding configuration key won't appear in the **Configuration keys** tab.


## Additional resources
For more information about the ISV licensing feature, see [Independent software vendor (ISV) licensing](../dev-tools/isv-licensing.md).

For more information about how to import ISV licenses into an on-premises deployment, see [Independent software vendor (ISV) licensing (on-premises)](../dev-tools/isv-licensing-on-prem.md).

For more information about the configuration keys report, see [License codes and configuration keys report](license-codes-configuration-keys-report.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

