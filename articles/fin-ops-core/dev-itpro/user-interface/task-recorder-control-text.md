---
title: Control the text that Task Recorder generates for a control
description: This article describes how Task recorder determines what instruction label to generate for controls.
author: jasongre
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9b75a1e3-cc76-4a2f-ae30-7e5a485b30b1
---

# Control the text that Task Recorder generates for a control

[!include [banner](../includes/banner.md)]

This article describes how Task recorder determines what instruction label to generate for controls. It then explains how you can make sure that these labels are meaningful for the user.

Every control must have useful and meaningful instruction labels, so that the task guide, Microsoft Word document, and Help content meet Content Publishing standards for readability. We must first define two terms:

-   **Control label** – The value that comes from the label property on the control.
-   **Instruction label** – The label that a control instructs Task recorder to use when it's describing how to use that control (for example, “Click OK” or “In the First name field, enter ‘John’”).

When a control logs an event to Task recorder, three methods can be used to determine the instruction label that is shown to the user:

-   As part of logging the Task recorder event, the control might specify an exact instruction label ID to use. As a best practice, here is how label IDs should be named: \[client control type name\]\_\[property or command name\] For manual specification of an instruction label ID, see the code example later in this article (**OptionalInstructionLabelIDOverride**).
-   If the control doesn't explicitly specify an instruction label ID, Task recorder looks in the SysTaskRecorderLabel file to try to find an existing instruction label ID that fits the following naming syntax: \[client control type name\]\_\[property or command name\] If an instruction label ID of this type is found, Task recorder uses it.
-   If a label can't be determined by using the preceding methods, Task recorder falls back to a more general-purpose instruction label. The general purpose instruction labels are in the SysTaskRecorder label file. There is one general-purpose instruction label for commands and another for properties.
    -   Here is the general purpose instruction label for commands:
        -   **Label ID:** CommandUserAction
        -   **Label string:** %2 the %1
    -   Here is the general purpose instruction label for properties:
        -   **Label ID:** PropertySetValue
        -   **Label string:** In the %1 field, enter %2

When Task recorder has determined which instruction label to use (via one of the preceding three methods), it strFormats the label by using the following arguments:

-   **%1** – This argument is the control label. Task recorder gets the control label by inspecting the label on the intractable. However, a control can override this label and provide its own label. See the code example later in this article (**OptionalControlLabelOverride**).
-   **%2** –  This argument is either the value (for properties) or the command name (for commands). This value will be the value that the control sent to Task recorder as part of logging the event. However, the raw data value can be ugly or meaningless to an end user. Therefore, a control can also provide a more user-friendly version of the value that Task recorder can display instead of the raw data value. See the code example later in this article (**OptionalValueLabelOverride**).
-   **%3**–**%5** – These are command arguments and are used rarely. However, grids use them to record the row number, for example.

## Case study
Let's use the Checkbox control as a case study for improvement. Currently, an instruction label isn't specified for the Checkbox via either method 1 or method 2 (see the previous section of this article). Therefore, the general-purpose property instruction label is used instead. If someone records selecting the Checkbox for a field that is named **Show infolog on failure**, the Task recorder output currently looks like this:


> In the Show infolog on failure field, enter True.

However, typical end users might not know what it means to set a Checkbox to **True**. Therefore, a suggested improvement is for the Checkbox to produce a label that looks like this:

> Check Show infolog on failure.

To make this improvement, someone must add a new label ID. That user must then use the label ID when the event is logged to Task recorder by using method 1:

-   **Label ID:** Checkbox\_Value
-   **Label string:** "%2 %1."

This change produces output that looks like this:

> True Show infolog on failure.

This isn't quite what we want to see. Therefore, in addition, when the Checkbox logs the property change event to Task recorder, it should pass in a specific *value label* that says either “Check” or “Uncheck.” If the control explicitly specifies a value label, Task recorder will use that value label instead of the raw data value that was recorded (**True** or **False**, in this case). See the code example later in this article (**OptionalValueLabelOverride**). After the user creates the new label and specifies the value label when the event is logged to Task recorder, the control will have suitable text output:

> Check Show infolog on failure.

Finally, the Checkbox should have a second instruction label for “example value” usage of the Checkbox. “Example value” represents a special way that Task recorder displays an instruction label to the user. The author of the task recording can specify whether the task guide should instruct users to enter the same values that were entered when the guide was recorded, or whether the task guide should instruct users to enter their own values that are specific to their business requirements. Example value instruction labels have the following label ID syntax: \[client control type name\]\_\[property name\]\_Example For the Checkbox example, the value label would look like this:

-   **Label ID:** Checkbox\_Value\_Example
-   **Label string:** “Check or uncheck the %1 field.”

The following code example shows how property change events are logged to Task recorder by an X++ control. Similar application programming interfaces (APIs) exist for C++ kernel controls. Command events have a similar API.

```xpp
[FormPropertyAttribute(FormPropertyKind::Value, #MyPropertyName)]
    public str value(str_value = valueProperty.parmValue())
    {
        if(!prmIsDefault(_value))
        {
            using (var scope = SysTaskRecorder::addPropertyUserAction(#MyPropertyName, this, _value, [OptionalInstructionLabelIDOverride], [OptionalValueLabelOverride], [OptionalControlLabelOverride]))
            {
                // Property set logic goes here
                valueProperty.setValueOrBinding(_value);
            }
        }
    }
```




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
