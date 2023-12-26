---
title: Keyboard shortcuts for extensible controls
description: This article outlines the recommended method for implementing keyboard shortcuts for extensible controls.
author: jasongre
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.assetid: C0E2E0F9-19C1-4CE0-A81C-1ACFA841F6AB
---

# Keyboard shortcuts for extensible controls

[!include [banner](../includes/banner.md)]

Keyboard shortcuts are an important consideration when you create any extensible control. This article provides information that will help you choose keyboard shortcuts for your extensible controls. It also outlines the recommended method for implementing keyboard shortcuts for extensible controls.

## Overview
For accessibility, it's essential that keyboard-only users be able to use controls. Therefore, keyboard shortcuts are an important consideration when you create any extensible control. This article provides information that will help you choose key combinations to use as keyboard shortcuts. It highlights the shortcuts that are currently used by finance and operations apps and supported browsers, shortcuts that are planned for implementation, and shortcuts that one or more browsers don't allow to be overridden. This article also outlines the recommended way to implement keyboard shortcuts for extensible controls.

## Choosing a key combination
When you're trying to choose a key combination to use as a keyboard shortcut, it's important that you be aware of other existing shortcuts. In this way, you help guarantee that your shortcut won't overlap an existing shortcut. If you try to collide with an existing shortcut, one of the following outcomes might occur:

- The new keyboard shortcut might not work, because a browser doesn't allow that key combination to be overridden, or a framework-provided shortcut takes precedence over the new shortcut.
- The new keyboard shortcut might remove expected keyboard functionality, because users expect specific key combinations to perform specific functions in a browser. Alternatively, you might override framework-provided shortcuts or other control shortcuts, so that keyboard-only users can't use them.

Because of these potential issues, we recommend that you adhere to this guidance when you choose a key combination:

- **Don't** choose any key combination that is currently used by finance and operations apps, or that is planned for future implementation.
- **Do** pick key combinations that will work in all supported browsers.
- **Do** be careful when you override shortcuts that are used by a supported browser. You should not suppress shortcuts for important or frequently used browser functionality.
- **Do** use longer key combinations (three keys) for control-specific behavior. Shorter combinations should be reserved for user-defined keyboard shortcuts.
- **Don't** choose any key combination that involves Ctrl+Alt, because this combination maps to Alt+Gr for some Eastern European languages and will conflict with other shortcuts.

### Keyboard shortcut links
Here are links to the keyboard shortcuts that are documented for finance and operations apps and supported browsers:

- <a href="../../fin-ops/get-started/shortcut-keys.md">Keyboard shortcuts</a>
- <a href="https://support.microsoft.com/help/13805">Microsoft Edge</a>
- <a href="https://support.google.com/chrome/answer/157179">Google Chrome</a>
- <a href="https://support.microsoft.com/help/15357/windows-internet-explorer-11-keyboard-shortcuts">Internet Explorer 11</a>
- <a href="https://support.apple.com/kb/PH21483">Apple Safari</a>

### Planned keyboard shortcuts 
In addition to the keyboard shortcuts that are currently used, there are several shortcuts that are planned for future implementation. To avoid conflicts with framework-provided shortcuts, you should not choose the following key combinations for extensible controls.
<table>
<tbody>
<tr>
<th>Shortcut</th>
<th>Functionality</th>
</tr>
<tr>
<td>F3</td>
<td>Move to the nearest QuickFilter.</td>
</tr>
<tr>
<td>Alt+F3</td>
<td>Add a filter that is based on the value of the current control (Filter by value).</td>
</tr>
<tr>
<td>Alt+Shift+F3</td>
<td>Clear all user-defined filters.</td>
</tr>
<tr>
<td>F6</td>
<td>Move to the nearest toolbar.</td>
</tr>
<tr>
<td>Shift+F7</td>
<td>Move to the toast message.</td>
</tr>
</tbody>
</table>

### Browser/operating system keyboard shortcuts to avoid

#### Keyboard shortcuts that correspond to important functionality
The following table provides a short, non-exhaustive list of keyboard shortcuts that correspond to important functionality in a browser or operating system. You should not choose the key combinations in this table.
<table>
<tbody>
<tr>
<th>Shortcut</th>
<th>Functionality</th>
</tr>
</tbody>
<tbody>
<tr>
<td>Ctrl+A</td>
<td>Select all the text in the current field, or select all content on the page.</td>
</tr>
<tr>
<td>Ctrl+C</td>
<td>Copy.</td>
</tr>
<tr>
<td>Ctrl+V</td>
<td>Paste.</td>
</tr>
<tr>
<td>Ctrl+X</td>
<td>Cut.</td>
</tr>
<tr>
<td>F5</td>
<td>Refresh the page.</td>
</tr>
<tr>
<td>Ctrl+F5</td>
<td>Refresh the page, and ignore cached content.</td>
</tr>
<tr>
<td>Shift+F10</td>
<td>Simulate a right-click.</td>
</tr>
<tr>
<td>Tab / Shift+Tab</td>
<td>Move to the next/previous control.</td>
</tr>
<tr>
<td>Ctrl+Tab / Ctrl+Shift+Tab</td>
<td>Move to the next/previous browser tab.</td>
</tr>
<tr>
<td>Alt+Tab / Alt+Shift+Tab</td>
<td>Move to the next/previous application.</td>
</tr>
<tr>
<td>Alt+Right arrow / Alt + Left arrow</td>
<td>Go to the next/previous page in the browser history.</td>
</tr>
</tbody>
</table>

#### Keyboard shortcuts that can't be overridden by some browsers
Some browsers don't allow the following keyboard shortcuts to be overridden. Therefore, you should not choose the following key combinations, because the shortcut won't work in all browsers.
<table>
<tbody>
<tr>
<td>Alt+A</td>
<td>Alt+T</td>
<td>Ctrl+F4</td>
<td>Alt+Tab</td>
</tr>
<tr>
<td>Alt+C</td>
<td>Alt+V</td>
<td>Alt+F5</td>
<td>Alt+Shift+Tab</td>
</tr>
<tr>
<td>Alt+D</td>
<td>Ctrl+W</td>
<td>Alt+F6</td>
<td>Spacebar</td>
</tr>
<tr>
<td>Alt+Shift+D</td>
<td>Ctrl+Shift+W</td>
<td>Alt+Shift+F6</td>
<td>Alt+Shift+Backspace</td>
</tr>
<tr>
<td>Alt+E</td>
<td>Alt+X</td>
<td>F12</td>
<td>Ctrl+Pause/Break</td>
</tr>
<tr>
<td>Alt+F</td>
<td>Ctrl+Shift+0</td>
<td>Ctrl+Esc</td>
<td>Ctrl+Shift+Pause/Break</td>
</tr>
<tr>
<td>Alt+H</td>
<td>Ctrl+Shift+7</td>
<td>Ctrl+Shift+Esc</td>
<td>Ctrl+Page up</td>
</tr>
<tr>
<td>Ctrl+N</td>
<td>F1</td>
<td>Alt+Esc</td>
<td>Ctrl+Page down</td>
</tr>
<tr>
<td>Ctrl+Shift+N</td>
<td>Ctrl+F1</td>
<td>Alt+Shift+Esc</td>
<td>Ctrl+Plus sign (+)</td>
</tr>
<tr>
<td>Ctrl+Shift+Q</td>
<td>Ctrl+Shift+F1</td>
<td>Ctrl+Tab</td>
<td>Shift+Plus sign (+)</td>
</tr>
<tr>
<td>Ctrl+T</td>
<td>Shift+F1</td>
<td>Ctrl+Shift+Tab</td>
<td>Ctrl+Minus sign (–)</td>
</tr>
</tbody>
</table>

## Implementing keyboard shortcuts
We recommend that you use the registration mechanism that is described in this section to implement keyboard shortcuts. There are several benefits to registering a control's shortcuts in this manner:

- You specify only the modifier keys that you want. If any other modifiers are pressed, the shortcut won't run. Therefore, a keyboard shortcut that is defined for Ctrl+Down arrow won't be triggered if Ctrl+Shift+Down arrow is pressed.</li>
- You can reuse code.
- If you return <strong>false</strong> from the handler function, propagation won't stop on the event. If you return <strong>true</strong> (or if you don't specify a return value), propagation will stop.
- Ctrl and Meta modifiers are treated the same. Therefore, you can specify keyboard shortcuts that will work for both iOS and Microsoft Windows. For example, the shortcut Ctrl+G on Windows will be translated to Meta+G on iOS.
- Built-in telemetry for the keyboard shortcuts is used.

### Define a keyboard shortcut

1. Define a Shortcuts object on the control's prototype. Then define the keyboard shortcuts inside the Shortcuts object. These shortcuts should have the following structure. Make sure that the key code that you're trying to use is defined in the $dyn.ui.KeyCodes object.

    ```Text
    Shortcuts: {
        Name: {
            Keys: { modifier1: true, modifier2:true, 
                keyCode: $dyn.ui.KeyCodes.* }, 
            // Only specify the modifiers you need 
            // (between alt, ctrl/meta, shift)
            Handler: function (evt) {
                // Code to handle shortcut.
            },
            // Additional code.
    }
    ```

    If more than one key code should apply to your keyboard shortcut, pass in an array of codes, as shown here.

    ```Text
    Keys: {modifier1:true, 
        keyCode:[$dyn.ui.KeyCodes.*, $dyn.ui.KeyCodes.*, ... ] } 
    // Note: If any of these keyCodes match then the handler is called. I.E. 
    // The keyCodes in the array are OR'd not AND'd
    ```
2. Add the keydown handler by using the following code.

    ```Text
    keydown: function (event) {
        $dyn.util.handleShortcuts(this, event);
    },
    ```

3. Bind the keyDown handler. The keyDown handler is automatically bound for form objects. Other controls must be manually bound to the keyDown handler, as for any regular binding. 

    > [!IMPORTANT]
    > "keyDown" is case sensitive.

    ```Text
    <div data-dyn-bind="keyDown: $data.keydown"></div>;
    ```

### Examples
Here is a Form example.

```Text
Shortcuts: {
    Save: {
        Keys: { ctrl: true, keyCode: $dyn.ui.KeyCodes.letterS },
        Handler: function (evt) {
            var control = evt ? $dyn.context(evt.target) : undefined;
            this.executeShortcuts(true, "SaveRecord", control);
        },
    },
    New: {
        Keys: { alt: true, keyCode: $dyn.ui.KeyCodes.letterN },
        Handler: function (evt) {
            var control = evt ? $dyn.context(evt.target) : undefined;
            this.executeShortcuts(true, "NewRecord", control);
        },
    },
    Delete: {
        Keys: { alt: true, keyCode: $dyn.ui.KeyCodes.deleteKey },
        Handler: function (evt) {
            this.executeShortcuts(false, "DeleteRecord");
        },
    },
    // Additional code
}
```

Here is a Dialogs example that extends the Form control.

```Text
Shortcuts: $dyn.extendPrototype($dyn.controls.Form.prototype.Shortcuts, {
    InvokeDefaultButton: {
        Keys: { keyCode: $dyn.ui.KeyCodes.enter },
        Handler: function (evt) {
            this.executeShortcuts(false, "InvokeDefaultButton");
        }
    },
})
```




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
