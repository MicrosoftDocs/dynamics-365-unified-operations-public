---
# required metadata

title: User interface control styles for production floor execution
description: The topic describes how to configure form controls so that the default Production Floor Execution styles are applied to the controls.
author: inkharki
manager: tfehr
ms.date: 02/22/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

audience: Developer
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: inkharki
ms.search.validFrom: 2021-02-22
ms.dyn365.ops.version: Release 10.0.15
---

# User interface control styles for production floor execution

[!include [banner](../includes/banner.md)]

[!include [preview banner](../includes/preview-banner.md)]

The topic describes how to configure form controls so that the default Production Floor Execution styles are applied to the controls.

## Grid

Styles are applied automatically. No specific configuration is required.

## Card view

To apply styles to card view controls:

+ Each card view must be contained in a form group.
+ The group name must start with **CardGroup**, for example, **CardGroupJobsView**.

A card view without controls inside:

![Card without elements](media/pfe-styles-empty-card.png)

A card view with controls inside:

![Card with elements](media/pfe-styles-elements.png)

## Business card

To apply styles to business card controls:

+ Each business card must be contained in a form group.
+ The group name must start with **BusinessCardGroup**, for example, **BusinessCardGroupJobsList**.
+ Set these properties on the business card:

    - **Style**: **list**.
    - **Extended style**: **cardList**.
    - **Multi Select**: **No**.
    - **Show Col Labels**: **No**.

## Radio button

To apply styles to radio buttons:

+ Each radio button must be contained in a form group.
+ The group name must start with **RadioTextBelow** or **RadioTextRight**, depending on where you want the text to appear.
+ Set these properties on the radio button:

    - **Toggle button**: **Check**.
    - **Toggle value**: **On** if radio button should be selected; otherwise, **Off**.

An example with the text below the radio button:

![Radio buttons with text below](media/pfe-styles-radio-text-below.png)

An example with the text to the right of the radio button:

![Radio buttons with text right](media/pfe-styles-radio-text-right.png)

### Internet Explorer

Production Floor Execution styles aren't supported in Internet Explorer. An example of radio buttons in Internet Explorer:

![Radio buttons in Internet Explorer](media/pfe-styles-browser.png)

## Buttons

To apply styles to buttons:

+ Each group of buttons must be contained in a form group. All the buttons in the group will have the same style.
+ There are no requirements on naming the group.
+ Set these properties on the buttons:

    - **Button Display**: **TextWithImageLeft**.
    - **Normal Image**: Can't be blank. For example, use **CoffeeScript**.
    - **Text**: Can't be blank. For example, use **Start Break**.
    - **Width**: **Auto**.
    - **Height**: **Auto**.

### Primary button

To apply styles to a primary button:

+ The button must be contained in a form group.
+ The group name must contain **DefaultButtonGroup** or  **PrimaryButtonGroup**, for example, **DefaultButtonGroup10**.

![Primary button appearance](media/pfe-styles-first.png)

### Secondary button

To apply styles to a secondary button:

+ The button must be contained in a form group.
+ The group must be named **Right panel** or the name must start with **SecondaryButtonGroup**.

![Secondary button appearance](media/pfe-styles-second.png)

### Third-group button

To apply styles to a third-group button:

+ The button must be contained in a form group.
+ The group must be named **Left panel** or the name must start with **ThirdButtonGroup**.

![Third-group button appearance](media/pfe-styles-third.png)

### Fourth-group button

To apply styles to a fourth-group button:

+ The button must be contained in a form group.
+ The group name must start with **FourthButtonGroup**.
+ Set these properties on the button:

    - **Button Display**: **TextOnly**.
    - **Normal Image**: Must be blank.
    - **Text**: Can't be blank. For example, it can be **View** or **Edit**.
    - **Width**: **Auto**.
    - **Height**: **Auto**.

![Fourth-group button appearance](media/pfe-styles-fourth.png)

### Flat button

To apply styles to a flat button:

+ The button must be contained in a form group.
+ The group name must start with **FlatButtonGroup**.
+ Set these properties on the button:

    - **Button Display**: **ImageOnly**.
    - **Normal Image**: Can't be blank. For example, use **CoffeeScript**.
    - **Text**: Must be blank.
    - **Width**: **Auto**.
    - **Height**: **Auto**.

![Flat button appearance](media/pfe-styles-flat-button.png)

## Combo box

A combo box is a combination of three controls, an input control, a button to clear the input control, and a button for search. Requirements for combo boxes:

To apply styles to a combo box:

+ The combo box must be contained in a form group.
+ The group name must start with **Combobox**.
+ Inside the group, the first control must be an **AxFormStringControl** control. This control displays of the current value, and is where the user enters the required value.
+ The second control must be a **CommonButton** control. The name must start with **ClearButton**. This button must contain code using the **enable** property to show or hide the button. For example, to show or hide the **Clear** button when the user is typing information into the input field, you can use the following code:

    ```xpp
    public void textChange()
    {
        super();
        ClearButtonSerial.enabled(this.text()? true : false);
    }
    ```

    You should have one method where the data is set into the input box, and then enable **Clear** button in that method. For example:

    ```xpp
    public void setSerialId(str _serialId)
    {
        JmgTmpJobBundleProdFeedback.InventSerial = _serialId;
        ClearButtonSerial.enabled(_serialId? true : false);

        if (_serialId)
        {
            this.addSerialNumber();
        }
    }
    ```

    Use the following code for the **clicked** method of the **Clear** button:

    ```xpp
    public void clicked()
    {
        element.setSerialId('');
        InventSerialId.setFocus(); // set focus back to the input box
    }
    ```

    Set the value of the input control, **AxFormStringControl**, when the form is initialized by using the **init** method. If value is not blank, then enable the **Clear** button. If the value is blank, disable the **Clear** button.

+ The third control must be a **CommonButton** control. The name must start with **SearchButton**.

The following image shows two combo box controls. The left combo box has an empty text box and the clear button is disabled. The right combo box has text in the text box and the clear button is enabled.

![Combo box appearance](media/pfe-styles-combo.png)

## Dialog

The styles for all these controls keep the same rules when they're included in a dialog form, if the name of the dialog form starts with **JmgProductionFloorExecutionDialog**. 

To apply styles to the **OK** button:

+ The button must be contained in a form group.
+ The group name must start with **OkButtonGroup**.

To apply styles to the **Cancel** button:

+ The button must be contained in a form group.
+ The group name must start with **CancelButtonGroup**.
