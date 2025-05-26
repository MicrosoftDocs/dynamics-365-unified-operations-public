---
title: Calculator feature for mobile app
description: Learn how to use the Calculator feature in the mobile app to perform mathematical calculations with enhanced gesture controls.
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 05/26/2025
ms.custom: bap-template
ms.reviewer: 
ms.search.form: 
---

# Calculator feature for mobile app

[!include [banner](../includes/banner.md)]

The Calculator feature provides essential mathematical computation capabilities within the mobile application, enabling users to perform calculations without leaving their current workflow.

The Calculator supports the following enhanced gesture controls:

- Long press functionality for negative number input
- Long press access to mathematical operations menu
- Standard numerical input and real-time calculations

> [!IMPORTANT]
> The gesture controls require a press duration of at least 500ms to activate. Brief taps will not trigger the enhanced functionality.

## <a name="basic-operations"></a>Basic calculator functionality

The Calculator functions as a standard computational tool with an enhanced interface. Users can input numbers using the numeric keypad and perform mathematical operations in real-time. 

## <a name="negative-numbers"></a>Negative number input

To enter negative numbers in the Calculator:

1. Enter your desired number using the numeric keypad.
1. **Long press** the number **9** on the keypad.
1. The number toggles to its negative value.
1. Continue with your calculation as normal.

> [!NOTE]
> This gesture works specifically with the number 9 and provides quick access to negative values without requiring a separate negative sign button.

## <a name="operations-menu"></a>Mathematical operations access

The Calculator provides access to four basic mathematical operations through an enhanced gesture control:

1. **Long press** the decimal point (**.**) button on the keypad.
1. A menu appears with the following mathematical operations:
   - **Addition** (+)
   - **Subtraction** (−)
   - **Multiplication** (×)
   - **Division** (÷)
1. Select your desired operation to continue the calculation.

## <a name="usage-examples"></a>Usage examples

### Performing a standard calculation

To perform a basic mathematical operation:

1. Enter your first number using the numeric keypad.
1. Long press the decimal point (.) to access the operations menu.
1. Select your desired operation (addition, subtraction, multiplication, or division).
1. Enter your second number.
1. Press equals to view the result.

### Working with negative values

To calculate using negative numbers:

1. Enter a positive number (for example, 9).
1. Long press the 9 to convert it to negative (-9).
1. Long press the decimal point (.) to access the operations menu.
1. Select your operation and continue the calculation.

## Troubleshooting

This section describes common issues and their solutions.

### Long press gestures not responding

**Problem:** The long press gesture doesn't activate the enhanced functionality.

**Solution:** Ensure you're holding the button for at least 500ms. A brief tap will not activate the gesture control.

### Operations menu not appearing

**Problem:** The mathematical operations menu doesn't display when needed.

**Solution:** Verify that you're long pressing the decimal point (.) button specifically, not another number or function key on the keypad.

### Gesture activates unintentionally

**Problem:** Enhanced functionality triggers during normal use.

**Solution:** Adjust your input technique to use brief taps for standard number entry. Reserve longer presses only when you intend to use the enhanced gesture controls.

## Related information

- [Mobile app user guide](mobile-app-user-guide.md)
- [App configuration settings](app-configuration.md)
- [Troubleshooting mobile app issues](mobile-app-troubleshooting.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]