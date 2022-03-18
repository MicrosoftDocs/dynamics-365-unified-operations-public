---
title: Maintain vendor certification
description: This topic describes the steps that vendors can use to  maintain their certifications using the Vendor collaboration workspace. 
author: v-kiarnd
ms.date: 04/27/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: roschloma
ms.search.region: Global
ms.author: roschlom
ms.search.validFrom: 2021-02-09
ms.dyn365.ops.version: 10.0.18
---

# Maintain vendor certification

[!include [banner](../includes/banner.md)]

This topic describes the steps that your vendors can use to  maintain their certifications using the **Vendor collaboration workspace**. Examples of certifications might include a Woman Business Enterprise (WBE) or a Leadership in Energy and Environment Design (LEED) company. Vendors will need to enter certification information in the **Vendor information** workspace. From there, vendors will select **More details**, and then select **Certifications**.

## Turn on the vendor certification feature

Before you can use this feature, it must be turned on in your system. Administrators can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. In the **Feature management** workspace, the feature is listed in the following way:

- **Module** - *Accounts payable*
- **Feature name** - *Enable vendor collaboration certification management*

## Add a new certification

To add a new certification, select the **Add** button that is located above the **Certification** grid in the **Vendor information** workspace. Enter the following information:

- Certification number
- Certification type
- Certifying organization
- Certification date
- Liability amount, if applicable
- Effective date
- Expiration date
- Comments, optional

If there are documents related to the specific certification, you can attach them by selecting the **Document** button.

Certifications that are entered by your vendors on this page will be assigned a source of “Vendor”. You can enter certificate information on your vendor's behalf under vendor bank accounts. The information will display here and the source will display as **Customer**.

Vendors can edit or delete their certifications as needed.

## Vendor collaboration generated certification records

After certification information has been added by a vendor, the information will be visible on the **Vendor collaboration generated certifications** page. To open the page, go to **Accounts payable > Inquiries > Vendor reports > Vendor collaboration generated certifications**. By default, all new or modified certification records are visible. An Accounts payable clerk can view the changes and validate the information through their confirmation process to validate. When the information has been confirmed, the certification record listed on the page can be selected and marked as reviewed. Marking the record as reviewed will remove it from the default list.

All certification changes are visible on the **Vendor collaboration generated certifications** page. If a change isn't displayed on the page, you can view it by adjusting the filters for the vendor account, effective date range, or choosing whether to include information for certification changes that have been reviewed.

