---
# required metadata

title: Manage features in Human Resources
description: This article describes the Feature management feature and how you can use it.
author: twheeloc
ms.date: 01/15/2025
ms.topic: article
# optional metadata

ms.search.form: FeatureManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Manage features in Human Resources

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The **Feature management** workspace provides a list of features delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them. For more information about Feature management, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

For more information about new features in Human Resources, see [What's new in Human Resources](hr-admin-whats-new.md) and [Dynamics 365 and Power Platform Release Plan](/dynamics365/release-plans/?panel=products1#pivot=products).

All new features remain in preview for at least 30 days, and typically 30-60 days. Major features are generally available in October and April of each year following the preview period. As soon as you see new capabilities in the **Feature management** workspace, you can turn them on. Some features may be on by default.

Once a feature is generally available, it may be turned on or off in production environments. The **Feature management** workspace indicates when a preview feature will become mandatory. This date is usually on October 1 or April 1 to align with the semiannual release plans. You can't turn off mandatory features. Until it becomes mandatory, you can turn a feature on and off in all environments.

## Enable or disable preview features

To access preview features, you must first enable them in your environment. Enabling or disabling preview features is environment-specific.

> [!IMPORTANT]
> Preview features are only available in **Sandbox** environments. When you turn on a preview feature, you enable it for all users in your organization who are in that environment. When you turn off the preview feature, you disable it and make it inaccessible to your users. Preview features have limited support in Human Resources. They might use fewer privacy and security measures, and they aren't included in the Human Resources service level agreement (SLA). You should not use preview features to process personal data (that is, any information that could identify you), or to process other data that is subject to legal or regulatory compliance requirements.

1. In Human Resources, select **System administration**.
2. Select the **Feature management** tile.
3. To enable a preview feature, select it from the list, and then select **Enable**. To disable a preview feature, select it from the list, and then select **Disable**.

## Enable or disable Benefits management

To enable Benefits management, use the same procedure in [Enable or disable preview features](hr-admin-manage-features.md?enable-or-disable-preview-features).

> [!IMPORTANT]
> You can't disable Benefits management in a **Production** environment after you enable it. 

For more information about Benefits management configuration and use, see [Benefits management overview](hr-benefits-management-overview.md).

Benefits management replaces functionality in the **Benefits** workspace. When you enable the Benefits management preview feature, you can no longer access the following forms in the **Benefits** workspace:

- **Benefits**
- **Benefit elements**
- **Contribution calculation rates**
- **Benefit enrollment results**
- **Benefit expiration and extension results**
- **Benefit eligibility policy rule types**
- **Benefit eligibility policies**
- **Eligibility events**

You can view the information in these pages in read-only mode. If you want to edit the information, you must first disable Benefits management (applicable to **Sandbox** environments only).

## Enable or disable Leave and absence

To enable Leave and absence, use the same procedure in [Enable or disable preview features](hr-admin-manage-features.md?enable-or-disable-preview-features).

> [!IMPORTANT]
> You can’t disable the **Multiple leave types** feature in Leave and absence after you enable it. This applies to both **Sandbox** and **Production** environments.

For more information about preview features in Leave and absence, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

## Send us feedback

We want to hear from you about your experience with preview features. We encourage you to regularly post your feedback on the following sites as you use these or any other features:

- [Community](https://community.dynamics.com/enterprise/f/759?pi53869=0&category=Talent) – This site is a great resource where users can discuss use cases, ask questions, and get community help.
- Let us know about features that you want to see in the product, or let us know about any changes you think we should make to existing features. Suggest product ideas on [Human Resources ideas](https://powerusers.microsoft.com/t5/Ideas-for-Human-Resources/idb-p/HumanResources).
    
Don't include personal data (any information that could identify you) in your feedback or product review submissions. Collected information might be analyzed further and isn't used to answer requests under applicable privacy laws. Personal data that is collected separately under these programs is subject to the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

## See also

- [What's new in Human Resources](hr-admin-whats-new.md)
- [Dynamics 365 and Power Platform Release Plan](/dynamics365/release-plans/?panel=products1#pivot=products)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
