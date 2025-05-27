---
title: Calculator feature for mobile app
description: Learn how to use the Calculator feature in the mobile app to input numerical values with enhanced gesture controls.
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

The Calculator feature provides a specialized numerical input interface within the mobile application, designed specifically for entering numerical values in quantity fields and other number-type inputs as configured by the WMS workflow.

> [!NOTE]
> The Calculator appears automatically when you need to input numerical values such as quantities, based on the flow configuration set by your WMS (Warehouse Mobile Service) system.

The Calculator supports the following enhanced gesture controls:

- Long press functionality for negative number input
- Long press access to mathematical operations menu
- Standard numerical input and real-time calculations

> [!IMPORTANT]
> The gesture controls require a press duration of at least 500 ms to activate. Brief taps won't trigger the enhanced functionality.

## <a name="when-calculator-appears"></a>When the Calculator is used

The Calculator interface is automatically activated when the mobile app requires numerical input for specific field types, including:

- **Quantity fields** - When entering item quantities during warehouse operations
- **Number-type inputs** - As defined by your WMS workflow configuration
- **Measurement values** - When precise numerical input is required

The appearance and availability of the Calculator is controlled by your WMS system configuration and will display contextually based on the current workflow step.

## <a name="basic-operations"></a>Basic calculator functionality

The Calculator functions as a specialized numerical input tool with an enhanced interface. Users can input numbers using the numeric keypad and perform mathematical operations when needed to calculate the correct values for quantity fields or other numerical inputs.

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
1. To configure calculation, select your desired operation.

## <a name="usage-examples"></a>Usage examples

### Entering a quantity value

To input a numerical value for a quantity field:

1. When prompted for a quantity input, the Calculator interface will appear automatically.
1. Enter your desired quantity using the numeric keypad.
1. Confirm the entry to proceed with your workflow.

### Calculating a quantity value

To perform a calculation for a quantity field:

1. Enter your first number using the numeric keypad.
1. To access the operations menu, long press the decimal point (.).
1. Select your desired operation (addition, subtraction, multiplication, or division).
1. Enter your second number.
1. Press equals to view the result.
1. Confirm the calculated value to input it into the quantity field.

### Working with negative values

To calculate using negative numbers for quantity adjustments:

1. Enter a positive number (for example, 9).
1. To convert to negative, long press 9.
1. To access the operations menu, long press the decimal point (.).
1. Select your operation and continue the calculation.

## Troubleshooting

This section describes common issues and their solutions.

### Calculator not appearing

**Problem:** The Calculator interface doesn't display when expected.

**Solution:** Verify that your WMS workflow is configured to use numerical input fields for the current step. Contact your system administrator if the Calculator should appear but doesn't.

### Long press gestures not responding

**Problem:** The long press gesture doesn't activate the enhanced functionality.

**Solution:** Ensure you're holding the button for at least 500ms. A brief tap won't activate the gesture control.

### Operations menu not appearing

**Problem:** The mathematical operations menu doesn't display when needed.

**Solution:** Verify that you're long pressing the decimal point (.) button specifically, not another number or function key on the keypad.

### Gesture activates unintentionally

**Problem:** Enhanced functionality triggers during normal use.

**Solution:** Adjust your input technique to use brief taps for standard number entry. Reserve longer presses only when you intend to use the enhanced gesture controls.
 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]