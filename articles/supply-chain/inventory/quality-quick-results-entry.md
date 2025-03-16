---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Quick results entry

 **Quick result entry** offers an efficient way to enter test results on a quality order. Data for all tests is consolidated on one page, with defaulted quantities based on the quality order quantity and  details about minimum, maximum and target values for each test on the Quality order.

## Using Quick result entry

When entering results for quality order tests, the standard quality order page can be used. This option is accessible from the results ribbon on the quality order line. Alternatively, the Quick results page can be used. This page is opened from a menu item in the ribbon on the quality order header. It is indicates from a field on the quality order line, whether test results have already been entered for the appropriate test line.

In the ribbon of the Quick results entry page you have the following five options

- **New** and **Delete** - Options to separate the test results entered for different quantities. For example, if the quality order quantity is 5, using the **New** action, a total of five lines can be entered for that test so that a different test result can be entered for each quantity. The sum of the quantities for each test must still equal the total quantity of the quality order.  
-  **Validate** - Performs the required validation for the selected line. This action also determines if the line is a pass or a fail. 
- **Skip** - 
- 
- **Reset test result** - Eliminates the test result value for the line. This action also deselects the checkbox on the test line that indicates is test results exist given no other lines for that test have test results entered. 
- **Split** - Provides the ability to split an existing line into multiple lines. When you open the dialog you have two options
    - **Single line split** - Split the selected line into two lines where the sum of the quantities matches the total quantity on the selected line. For example, if the line quantity was 8 and a Split quantity of 3 is entered, the result will be two lines, one with quantity of 3 and one with a quantity of 5. Different test results can then be entered for both lines.
    - **Multi lines split** - This can be used to quickly create rows with the same test quantity. The Result quantity per line needs to be entered. The system then will determine the total number of results lines based on the result quantity per line. For example, if the current line has a quantity of 8 and the result quantity per line entered is 2, the system will automatically create 4 lines where there was one, each with a quantity of 2. If the number is not even, the system will do as many rows as possible with the residual in the last row. For example, if the current line has a quantity of 8 and the Result quantity per line entered is 3, the system will create 3 result lines, two lines with the quantity of 3 and the 3rd line with the residual quantity of 2 for a total quantity of 8. [!NOTE] If the item is a catch weight item (CW), you must enter the catch weight quantity  instead of the standard quantity.