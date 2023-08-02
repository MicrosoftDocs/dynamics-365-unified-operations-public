---
# required metadata

title: Configure the number of decimal places in Leave and absence
description: This topic describes how to set the number of decimal places that are shown in the Leave and absence module in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 5/23/2023
ms.custom:

---

# Configure the number of decimal places in Leave and absence

[!INCLUDE [PEAP](../includes/peap-2.md)]

You can set the number of decimal places that are shown in the **Leave and absence** module to a minimum of two and a maximum of six.

## Set the number of decimal places

1. Go to **Feature management**, and select the **Decimals for rounding precision in leave and absence module** feature.

    > [!NOTE]
    > This feature can't be turned off after it's turned on.

    After the feature is turned on, the **Number of decimals** field becomes available on the **Leave and absence parameters** page. The minimum value of this field is **2**, and the maximum value is **6**. The default value is **2**. The value can be changed and set only once per legal entity.

2. On the **Leave and absence parameters** page, in the **Number of decimals** field, select a value.

    The number of decimal places that are shown in the **Leave and absence** module should reflect the needs of your organization. Therefore, select the **Number of decimals** value only after you carefully consider your organization's needs.

    > [!IMPORTANT]
    > The number of decimal places can't be changed after the value is set and saved, and the page is refreshed.

Numerical values in the **Leave and absence** module now reflect the **Number of decimals** value that you selected for your organization. For example, if you selected **5** in the **Number of decimals** field, the following behavior occurs:

- A leave balance of 24.123456 is shown as **24.12345**.
- A leave balance of 24.12 is shown as **24.12000**.
- A leave balance of 24 is shown as **24.00000**.

> [!NOTE]
> Microsoft Power BI reports show two decimal places, regardless of the value that you select in the **Number of decimals** field.
