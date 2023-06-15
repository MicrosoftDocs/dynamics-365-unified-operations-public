---
title: Control checklist
description: This article categorizes and describes all the release criteria for controls.
author: josaw1
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9e67e62c-1ced-45bd-8591-941e9afb0ab1
---

# Control checklist

[!include [banner](../includes/banner.md)]

This article categorizes and describes all the release criteria for controls.

## Introduction

Typically, when you author a new control, the primary focus is on scenario functionality and technical implementation. However, before a control can be considered ready for shipment, it should conform to a set of best practice, quality, and development release criteria, as outlined in this article.

## Control criteria checklist
This checklist assumes that you're familiar with the basics of control development. The following items highlight important implementation requirements that should be met by all controls.

### Basic usage ready

A control must meet these requirements to be considered a functionally compatible and complete control.

#### Classes

These naming conventions are best practices but aren't functional requirements of a control:

-   The Runtime class is named **\[Name of control\]Control**.
-   The Design-time class is named **Build\[Name of control\]Control**.
-   Any control-specific Component classes are named **\[Name of control\]\[Name of component\]Component**.
-   Any generic Component classes are named **Build\[Name of component\]Component**.

#### Resources

These naming conventions are best practices but aren't functional requirements of a control:

-   The HTML Resource is named **\[Name of control\]HTM**, and the physical file is named **\[Name of control\].htm**.
-   The JavaScript Resource is named **\[Name of control\]JS**, and the physical file is named **\[Name of control\].js**.

#### X++ Runtime

These items apply to the "Runtime" X++ class.

-   FormControlAttribute is supplied with the build class name.
-   The FormControlAttribute is supplied with the template ID.
-   FormControlAttribute is supplied with the resource bundle path.
-   The **FormTemplateControl** class is extended (directly or through inheritance).
-   A FormProperty exists for each change-tracked property (that is, each property that must be read in the client JavaScript).
-   The **New** method initializes each FormProperty instance.
-   The **setTemplateId** and **setResourceBundleName** inherited methods are called with the same values that are supplied in the FormControlAttribute.
-   The **ApplyBuild** method is used to interpret any design-time properties, and to apply design-time properties to the run-time properties as appropriate for the control.
-   A Property getter/setter method exists for each FormProperty.
-   A FormPropertyAttribute is supplied on each FormProperty's getter/setter method.
-   **Anytype** is used as the argument type for FormProperties that have **FormPropertyKind::BindableValue**.
-   All FormProperties are specified as **ReadOnly** to the JS class, via the third argument to the FormPropertyAttribute.
    -   This argument affects only the read/write behavior that is seen by JavaScript, not by X++.
    -   We don't recommend that you allow JavaScript to write directly to properties, because every property state change should be validated. We recommend that you use FormCommands for this purpose, instead of writeable properties.
-   FormCommands that allow the state of FormProperties to be changed must validate that the control is in a valid state to allow for the property change.
    -   Controls that are disabled, read-only, invisible, and so on, should prevent inappropriate state changes.

#### X++ Design time

These items apply to the "Design/Build" X++ class:

-   The FormDesignControlAttribute is supplied with the control common name, **\[Name of control\]**, without “Control” appended at the end.
    -   The name that is supplied here will appear in Microsoft Visual Studio when the control is added to a form.
-   A backing field exists for each design-time property.
-   A Property getter/setter exists for each design-time property.
-   A FormDesignPropertyAttribute is supplied to each design-time property.
-   No code outside of the Design property getters/setters should exist in this class. (In other words, there should be no **new()** methods, and so on.)

#### HTML

These items apply to the .htm file, which is also referred to as the resource bundle:

-   External resources, such as scripts, style sheets, and other HTM files, are loaded by using HTML standard &lt;script&gt; and &lt;link&gt; tags.
-   All external resource loading tags are placed above the outermost HTML element in the file, so that they are loaded and processed first.
-   The template ID is supplied via the **id** attribute on the outermost HTML element.
-   The visibility of the outermost HTML element is bound to the **Visible** property.
-   The sizing of the outermost HTML element is bound to the sizing binding handler.
-   Binding handlers are used to programmatically modify HTML. (APIs such as getElementById in the JavaScript constructor aren't used.)

#### JavaScript

-   The whole JavaScript code is wrapped in an anonymous function.
-   Localizable strings are stored in the Globalize culture info object.
-   Localizable strings are also stored in a label file, according to the instructions in [Create localizable labels](create-localizable-labels-client.md).
-   Default values are provided for all properties that aren't initialized inside the constructor.
-   The JavaScript constructor is added to the control JavaScript namespace.
-   A reference to **this** is stored in an object that is named **self**, and **self** is used instead of **this** throughout the constructor.
-   The base JavaScript control behaviors are inherited.
-   Default values are applied by using a framework utility function.
-   Client-side properties are defined in the scope of the constructor and are added to **self**.
-   Observable and computed properties are used only for UI-bound behaviors.
-   A prototype exists and contains all static methods that are specific to the control.
-   Binding handlers that are specific to the control are stored in the control’s namespace (not in the global control namespace).
-   The control doesn't use or load external plug-ins (Microsoft ActiveX, Flash, Java, and so on).

### Interactivity

#### CSS/LESS

-   Prefix all class names with the template ID to prevent conflicts with other controls.
-   Don't use class names that are defined on other controls, because those classes can change.

#### Layout and resizing

-   The control uses the Sizing API for its outermost element. This requirement helps guarantee that the framework can correctly size and arrange the outermost element of the control.
-   For advanced layout scenarios for elements that are contained in the control, use [CSS Flexible Boxes](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes), which are supported by the HTML standard.

#### Browser support

-   The control correctly renders and supports all intended user interaction patterns on all supported browsers:
    -   Microsoft Edge/Internet Explorer 11
    -   The latest version Chrome
    -   The latest version of iPad/MacOS Safari

#### Tab sequence

-   Make sure that the control meets the W3C standards for tab sequence.

### Globalization

#### Right-to-left languages

-   Full RTL support will arrive after RTW.

#### Localizable labels

-   The control uses a label file for UI text that is used only on the client side (not used in X++). For instructions about how to create and use these labels, see [Create localizable labels](create-localizable-labels-client.md).

### Task Recorder compatibility

-   Basic recording support
    -   For any control that accepts user input, or that a user can interact with, input/actions must be recordable by Task Recorder. For Task Recorder to record the input, the control must use the SysTaskRecorder X++ API to specify the properties that should be recorded.
-   Basic task guide support
    -   For any control that can be recorded by using Task Recorder, the control should have task guide support. This support includes verifying that the task guide pop-up prompt points to the correct UI elements of the control, based on the input/action that was recorded.
    -   In addition, validate that, when the task guide is locked (“on-rails”), the user can interact with the expected parts of the control. For example, for a combo box control, the user should be able to open the drop-down box to select a value, in addition to typing the value directly.
-   Advanced recording support
    -   Support for Cut, Copy, Paste, and Validate can be evaluated on a per-control basis. There are JavaScript and X++ methods that controls can implement to enable these features.

#### Threat modeling the control

-   Vulnerabilities in the logical control (X++/C++) that are related to serialization/deserialization of data types, and command/property execution, should be reviewed and fixed.
    -   Serialization threats are related to the way that the control parses or interprets data types.
        -   Any serializer for data types (except the built-in X++ Data Contracts and primitive type serialization) must be reviewed.
        -   Any parser must be reviewed to verify that it doesn't allow for arbitrary code execution or other exploitation.
        -   Any data access queries that are executed by the control (or by any helper classes that the control uses) must be evaluated and reviewed.
    -   Command/property execution threats are related to the way that the logical control handles an action that the control determines to be invalid.
        -   Example of a command threat: A click command is executed when the control is in a disabled state. You must make sure that the click command is handled appropriately, based on the control state.
        -   Example of a property thread: A property change is executed when the control is ready-only. You must make sure that the property change is handled appropriately, based on the control state.
    -   You must review the use of any .NET libraries to make sure that the .NET library is also secure.
-   Vulnerabilities that are related to the client-side parts of the control (HTML, JavaScript, CSS, third-party libraries) should follow general secure web development principles. Specific examples include XSS vulnerabilities.
    -   Any control that renders user data as HTML/JavaScript/CSS exposes an XSS vulnerability that must have mitigations identified.
    -   Any control that renders external content in an iFrame exposes an XSS vulnerability that must have mitigations identified.
    -   Any control that makes calls to third-party services must have mitigations identified and requires direct review by the client team.
    -   Any control that handles authentication must have mitigations identified.

## Control criteria details
This section explores the control criteria in more detail.

### Basic usage ready

####  X++ Runtime

-   **FormControlAttribute** Each control must supply the FormControlAttribute to the class declaration. The attribute must specify the build/design-time class that accompanies the control. The attribute must also specify the HTML template ID and the physical HTML file name (the resource bundle name).
-   **FormTemplateControl** Each control must extend FormTemplateControl to participate in the control lifecycle.
-   **FormProperty** Each control must declare FormProperties for every statically defined property that must participate in the change tracking system. For properties that are used only on the server side, no FormProperty is required.
-   **New** Each control must implement the **New** method in order for its properties to participate in the change tracking system that propagates value changes between the client and server parts of the control. Inside the **New** method, each FormProperty
-   **ApplyBuild** Each control must implement the **ApplyBuild** method in order for the control to be initialized based on the values that are set on it at design time. This method is primarily used to copy or transform design-time values into their Runtime equivalents. However, not all design-time properties must have Runtime equivalents, and not all Runtime properties must source their initial values from design-time properties.
-   **Property getter/setter** Each control must implement property getters/setters for every FormProperty that is used by the control. These methods should be parm methods. Therefore, the names should begin with “parm” for methods that are getters/setters, “get” for methods that are only getters, and “set” for methods that are only setters. At a minimum, a FormPropertyAttribute must be supplied to each method, together with a FormPropertyKind and the name of the property as it should be made accessible to the HTML and JavaScript in the client.

#### HTML

-   **Template ID** Each control must provide an HTML **id** attribute on the outermost HTML element of the control’s markup. In order for the control to be loaded at run time, this ID must match the ID that is supplied to the FormControlAttribute.
-   **Scripts and style sheets** Each control must use HTML standard &lt;script&gt; and &lt;link&gt; tags to consume other JavaScript or CSS files. These tags should be placed at the beginning of the HTML file for the control, before the HTML definition element for the control. If the files that must be loaded have dependencies, make sure that the order of the &lt;script&gt; or &lt;link&gt; loading tags is appropriate. Tags that appear first are loaded first. To load JavaScript or CSS from AOT Resources, use a site root–relative path (/Resource/Scripts or /Resources/Styles).
-   **Data binding** Each control can participate in the HTML binding framework through use of the **data-dyn-bind** attribute on HTML elements that are contained in the control. The binding attribute enables HTML element properties to be bound to observable or computed properties that are located in the current data context.

#### JavaScript

-   **Script encapsulation** Each control must wrap all its JavaScript in an anonymous function. This requirement helps prevent the framework’s global JavaScript namespace from being populated with control-specific logic.
-   **Localizable strings** Each control must use the Globalization API to store any string messages that are used by the control’s JavaScript. Therefore, the control’s JavaScript should not hard-code any strings that are displayed in the UI. Instead, the JavaScript should reference the string messages that are stored via the Globalization API. To load strings in the globalization object in HTML and JavaScript, you can use the $dyn.label API and pass in the identifier of the label. For more information, see [Create localizable labels](create-localizable-labels-client.md).
-   **Default values** Each control must provide default values for any properties that aren't initialized in the JavaScript. Therefore, any properties for which values are passed in to the JavaScript constructor on initialization (that is, the FormProperties in the X++ Runtime class) must provide a default-value dictionary for these properties.
-   **JavaScript constructor** Each control must implement a constructor in the controls namespace. This constructor is the first line of code that will be executed when the control is loaded in the client. After the constructor is completed, the constructor’s associated object, *this*, is passed in to the HTML as the default data context.
-   **Inheriting base control** Each control’s constructor must “inherit” from the base JavaScript control class. The base JavaScript control class contains behaviors that are required by each control.
-   **Applying default values** Each control must use the provided framework function to apply the default values to the control’s properties.
-   **Adding client-side properties/functions** Each control can add client-side-only properties and functions to the JavaScript class, in addition to the server-side FormProperties and Commands that are passed in to the control constructor. The pattern for adding client-side-only properties/functions is to maintain a local copy of the *this* object and add the functions/properties to the local copy. After the control constructor is completed, all properties, functions, FormProperties, and Commands that have been added will be available in the HTML as the default data context.
-   **Adding observable and computed properties** Each control can add client-side-only properties that participate in the observability patterns of the client. An observable property is initialized by using the $dyn.observable(\[initial value\]) function. A computed property is initialized by using the $dyn.computed(\[function(){}\]) function. Controls should use observable/computed properties sparingly, because these property can significantly harm performance if they are used incorrectly.
-   **Control JavaScript prototype** Each control must implement a JavaScript prototype that extends the base control prototype. The prototype should contain any “static” JavaScript methods (methods that require no references to local variables) that are used by the control.

### Interactivity

#### Layout and resizing

-   To enable the form developer to determine the control layout and size, set the width and height that are specified by the form developer on the control by using the $dyn.layout.sizing API, as shown in the following code. This is standard code that should be applied to all HTML control templates.

    ```xml
    <div id="MyControl" data-dyn-bind="
    sizing: $dyn.layout.sizing($data)>
    </div>
    ```

#### Task Recorder recording support

Controls must use the SysTaskRecorder X++ API to indicate which actions on the control are “recordable.”

-   For controls that enable values to be set via properties, **SysTaskRecorder::addPropertyUserAction** should be called when the value is being set in X++. This method call tells Task Recorder to record the setting of the property.
-   A similar method exists for commands (**SysTaskRecorder::addCommandUserAction**).

For more information, see [Control the text that Task Recorder generates for a control](task-recorder-control-text.md).

#### Task Recorder playback support

-   Task Recorder uses the control’s properties and commands to play back the control. The control must make sure that the commands and properties that it instructs Task Recorder to record can also be executed by Task Recorder when the control is played back. Task Recorder will rely on the interactable names for the properties and commands. The interactable name for a method is the name that is specified in the FormPropertyAttribute or the FormCommandAttribute.

#### Task guide support

The task guide will ask the JavaScript part of the control for the DOM element that the task guide should point to. All controls inherit basic task guide support, where the default DOM element is the outermost element of the control.

-   A control can provide finer-grained details about where the task guide should point by implementing the getTaskGuideParams function in the JavaScript prototype for the control. This function accepts an argument (which is frequently named **options**), and this argument has a property that is named **target**. This **target** property accepts the jQuery element that the task guide should point to.
-   In addition, the argument will contain information about the action that was originally recorded for the control, such as the property/command name and any arguments. The control can react to the various properties/commands that it supports by supplying the target with the DOM element that corresponds to the property/command that the user recorded.
-   For some advanced scenarios, the target can also be supplied with an observable. The control can then update this observable with various DOM elements, based on events that the control exposes. This can be done by initializing the target with the observable (which contains a DOM element), and then observing an event and updating the DOM element via code in the event handler.

#### Task Recorder copy/paste/validate support

For controls that need to support either Copy, Paste, or Validate (mainly for advanced X++ testing purposes), the SysTaskRecorder API exposes static methods that enable the control to inform Task Recorder when a value has been copied, pasted, or validated.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
