---
# required metadata

title: Configure the number of decimal places in Leave and absence
description: This article describes how to set the number of decimal places that are shown in the Leave and absence module in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: how-to
ms.date: 6/25/2026
ms.custom:

---

# Configure the number of decimal places in Leave and absence

You can set the number of decimal places that display in the **Leave and absence** module to a minimum of two and a maximum of six.

## Set the number of decimal places

1. Go to **Feature management**, and select the **Decimals for rounding precision in leave and absence module** feature.

    > [!NOTE]
    > You can't turn off this feature after you turn it on.

    After you turn on the feature, the **Number of decimals** field becomes available on the **Leave and absence parameters** page. The minimum value of this field is **2**, and the maximum value is **6**. The default value is **2**. You can change and set the value only once per legal entity.

1. On the **Leave and absence parameters** page, in the **Number of decimals** field, select a value.

    The number of decimal places that display in the **Leave and absence** module should reflect the needs of your organization. Therefore, select the **Number of decimals** value only after you carefully consider your organization's needs.

    > [!IMPORTANT]
    > You can't change the number of decimal places after you set and save the value, and refresh the page.

Numerical values in the **Leave and absence** module now reflect the **Number of decimals** value that you selected for your organization. For example, if you select **5** in the **Number of decimals** field, the following behavior occurs:

- A leave balance of 24.123456 displays as **24.12345**.
- A leave balance of 24.12 displays as **24.12000**.
- A leave balance of 24 displays as **24.00000**.

> [!NOTE]
> Microsoft Power BI reports show two decimal places, regardless of the value that you select in the **Number of decimals** field.
