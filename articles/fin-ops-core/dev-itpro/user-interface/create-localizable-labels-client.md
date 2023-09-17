---
title: Create localizable labels
description: This article explains how to create localizable labels for client components and HTML/JavaScript controls.
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
ms.assetid: 73615d1b-9088-496e-989e-d8996f30e76b
---

# Create localizable labels

[!include [banner](../includes/banner.md)]

This article explains how to create localizable labels for client components and HTML/JavaScript controls.

This article details the process for creating **localizable** labels for client components and HTML/JavaScript controls. This process uses the existing localization tools and process for labels to bring localization support to client components and HTML/JavaScript controls. The following process relies on the label resource controller that can serialize label files into their JavaScript equivalents so that the labels can be used by the client components and HTML/JavaScript controls. The label resource controller is deployed automatically. It is an MVC service that is located at the /Resources/Labels endpoint.

## 1. Create a label file
Use the developer tools to create a new label file for your control's area, or use an existing label file for your control's area. A control's area is determined by the owning team.

-   For extensible controls, your goal should be to create one label file for each HTM resource file. If multiple HTM resources share the same set of labels, only one label file should be required for the set of HTM resource files.
-   For client controls and components, in general, controls that share a lot of the same functionality (for example, the Input controls: StringEdit, ComboBox, CheckBox, and so on) should also share the same label file.

*Don't use a label file that also contains labels that are only used in X++.* The whole label file is serialized when it’s loaded by the client, so be sure to keep the labels that aren't required by the client components/controls in a separate label file.

## 2. Add label strings to the label file
Use the developer tools to add label strings to the label file. **Example for extensible controls:**

-   **Label file name:** ClockControl
-   **Label ID:** Seconds
-   **Label string:** seconds

## 3. Request the label file as a JavaScript file by using Resource manager
Use the script loading tag to load the JavaScript file. The loading tag should reference the label file from /Resources/Labels, because the label resource controller is located there. **Note:** For extensible controls, the controller automatically appends the label file name to the beginning of the label identifier in JavaScript.

```javascript
<script src="/Resources/Labels/ClockControl.js"></script>
```

The JavaScript file that is returned will contain code that resembles the following example.

```javascript
Globalize.addCultureInfo("en-us", {
    messages: {
        ClockControl_Seconds: "seconds"
    }
});
```

The culture information is injected automatically, based on the current user's culture. No action is required on the part of the control to set, modify, or read the user's culture. The preceding code adds each of your label strings to the jQuery Globalize label storage. You can then reference your labels throughout your HTML and JavaScript. The JavaScript code in the script file is run the moment that the file is loaded by the browser. Therefore, your labels are immediately ready for use. Be sure to add the label script loading tag **after** any other script loading tags in your HTML. The script loading tags are processed in order, from top to bottom. By loading the label script last, you help guarantee that no other scripts cause conflicts or override the labels that are set in the script label file.

## 4. Use localizable labels in HTML and JavaScript
The following framework application programming interface (API) can be used in HTML (inside **data-dyn-bind**) or in JavaScript to access the labels. **HTML**

```javascript
<!-- Example of using a localizable label with a Label Control. Supply the label to the "Text" property on the control -->
<div data-dyn-role="Label" data-dyn-bind="Text: $dyn.label('ClockControl_Seconds')"></div>
<!-- Example of using a localizable label with a basic HTML element. Supply the label to the "text" binding handler for the element -->
<div data-dyn-bind="text: $dyn.label('ClockControl_Seconds')"></div>
```

**JavaScript**

```javascript
/* Example of using a localizable label in JavaScript. */
var string mylabel = $dyn.label('ClockControl_Seconds');
```

You can also pass the label ID via a variable in HTML or JavaScript. **HTML**

```javascript
<div data-dyn-bind="text: $dyn.label($data.SecondsLabel)"></div>
```

**JavaScript**

```javascript
var string mylabel = $dyn.label(self.SecondsLabel);
```

The **$dyn.label** API will find the appropriately named label and return the string that can be used to display text to the user. This API will automatically select the label, based on the current user's culture.

## Troubleshooting
If you have correctly created a label file, and the label has been deployed, you should be able to load the JavaScript version of the label file directly from the browser. You can access the JavaScript label file by navigating to the home page in the client and appending the following path to the URL: **/Resources/Labels/MyLabelFile.js**, where **MyLabelFile** is the name of the label file without the language suffix. For a deployed label file that is named MyLabelFile.en-us, follow these steps:

1. Navigate to the home page, and sign in. (On one-box deployments, the URL of the home page is `https://usncax1aos.cloud.onebox.dynamics.com/en/`.)
2. Make sure that the desired language has been set by going to **Options** &gt; **Language and Region**. (You don't have to change the language if it's already set to the language that you want.) Now that the user's language has been set in the current session, the label resource controller will know what language to use when the label file is loaded.
3. To load the JavaScript version of the label file, navigate to the label file by adding <strong>Resources/Labels/MyLabelFile.js</strong> to the URL. (On one-box deployments, the whole URL is `https://usncax1aos.cloud.onebox.dynamics.com/en/Resources/Labels/MyLabelFile.js`.)
4. The corresponding label file will be JSON-serialized, and the browser will either show the text on the current tab or prompt you to download the .js file. If you download the file, you can then open it locally to inspect it.

If the browser doesn't find the file, you might have mistyped the name of the label, or you might not have deployed the label correctly. There is never a physical .js file for the label in the web folder /Resources/Labels. The .js file is dynamically generated by the label resource controller.

### Microsoft Visual Studio form previewer

The form previewer isn't currently configured to load labels via the label resource controller. The form previewer will load only labels that are defined directly in the .js file for the code behind (located at /Resources/Scripts). Until the form previewer is updated so that it can load .js files from the label resource controller, make sure that you also define the labels in the .js file for the code behind of the control. The dependency on these labels will be removed in a future update.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
