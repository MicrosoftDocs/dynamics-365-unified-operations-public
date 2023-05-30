---
# required metadata

title: Configure the number of decimal places in leave and absence
description: This topic describes how to configure the number of decimal places in Microsoft Dynamics 365 Human Resources leave and absence.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 5/23/2023
ms.custom:

---

# Configure the number of decimal places in leave and absence


[!INCLUDE [PEAP](../includes/peap-2.md)]

You can set the number of decimal places in the leave and absence module from a minimum of 2 to a maximum of 6 decimals.

## Prerequisites
1.	Go to **Feature management**, select the **Decimals for rounding precision in leave and absence module** feature is selected.

>[!Note] 
>This feature can't be turned off after it has been turned on.

2.	After this feature is selected, the **Number of decimals** option will be available on the **Leave and absence parameters** page.
3.	The **Number of decimals** fields have values starting from 2 to a maximum of six. The default value is 2. This can be changed and set only once per legal entity.
4.	The number of decimal places in the leave and absence module should be based on the need of your organization. Select the value after carefully considering your organization’s need. 

>[!Iimportant:]
>The number of decimal places can't be changed once the value is set, saved and the page is refreshed. 

5.	Based on the value of the number of decimals selected, the value would be displayed. 
For example, if the organization selected 5 in the **Number of decimals** field:
a.	If the leave balance is 24.123456, the leave balance displays 24.12345.
b.	If the leave balance is 24.12, the leave balance displays 24.12000.
c.	If the leave balance is 24, the leave balance displays 24.00000.

>[!Note:] 
>Power BI reports displays two decimal places regardless of the option selected. 


