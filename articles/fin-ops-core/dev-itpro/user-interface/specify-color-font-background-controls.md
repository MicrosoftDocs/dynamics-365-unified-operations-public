---
title: Font and background colors for input, table, and grid controls
description: This article provides information about the new color picker control that lets users select a color.
author: jasongre
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 84e06ee2-be1c-443b-b595-9309eaea84c5
---

# Font and background colors for input, table, and grid controls

[!include [banner](../includes/banner.md)]

This article provides information about the new color picker control that lets users select a color.

Traditionally, color has been considered an ideal way to communicate with a user. For example, the color red is often used to draw the user's attention to information that is important. However, some users can't distinguish certain colors or shades, and some users are blind. Therefore, we don't recommend that you use color alone to communicate information to the user. Instead, you should use color together with a symbol or additional text to convey information to all users.

## Color selection in Dynamics AX 2012
In Microsoft Dynamics AX 2012, color selection had these characteristics:

-   It used the Win32 color picker.
-   It required Win32 application programming interfaces (APIs) for RGB/decimal conversion. (The input control accepted a decimal value for RGB.)

```xpp
Public void lookup()
{
    #DEFINE.COLORVALUE(64)
    Int r,g,b
    container choosencolor;
    Binary customcolors = new Binary(#COLORVALUE);
    CCColor colorvalue;

    Super();

    [r,g,b] = WinAPI::RGBint2Con(this.backgroundColor());

    chosenColor = WinAPI::chooseColor(element.hWnd(),r,g,b, customColors, true);

    If(chosencolor)
    {
        [r, g, b] = chosencolor;
        Colorvalue = WinAPI::RGB2int(r,g,b);
        This.backgroundColor(colorValue);
        employeeWorkPlannerForm.parmAbsensceColor(colorvalue);
        Employeetable.columns(employeeworkplannerform.numberofcolumns());
        Absenscecolorparm = colorvalue;
    }
}
```

## Color selection for input controls
In the current version, the color picker control is a standard control type. The color picker control can be put directly in a form, or it can be used as part of a custom lookup for an integer or string control. The following example shows how to interact with the color picker control in a custom lookup. However, the code is similar if you put the color picker in a form and provide the user with a button to select a color.

-   A color picker control can be hosted in a form or a custom lookup to let the user visually pick a color or specify an RGB value.
-   The return value is a decimal value that can be assigned directly to an input control property. (No run-time RGB conversion is required.)

```xpp
[Control("String")]
class stringControl
{
    /// <summary>
    ///
    /// </summary>

    public void lookup()
    {
        int color = hex2Int(this.valueStr());
        color = ColorSelection::selectColorStringControl(this, color);
        this.text(int2hex(color));
        this.backgroundColor(color);
    }
}

[Control("Integer")]
class integerControl
{
    /// <summary>
    ///
    /// </summary>
    public void lookup()
    {
        int color = this.value();
        color = ColorSelection::selectColor(this, color);
        this.value(color);
        this.backgroundColor(color);
    }
}
```

## Using color in a table control
There is no design-time experience for coloring input controls. In other words, you can’t model an input control so that it's “blue” by default. However, there are run-time capabilities that let you change color values. The following example shows how you can change the way that the cells of a table control are colored.

```xpp
public FormControl editControl(int column, int row)
{
    stringEdit.colorScheme(FormColorScheme::RGB);
    stringEdit.backgroundColor(WinAPI::RGB2int(225,225,125));
    stringEdit.foregroundColor(WinAPI::RGB2int(8,10,200));
}
```

[![Example of a table control that has colored cells.](./media/tablecontrol_withcolor.png)](./media/tablecontrol_withcolor.png)

## Using color in a grid control

```xpp
public void displayOption(Common _record, FormRowDisplayOption _options)
{
    CLIParentTable table;
    table = _record;

    if(!cleared)
    {
        _options.affectedElementsByControl(CliParentTable_AInt.id());
        _options.affectedElementsByControl(CliParentTable_AEnum.id());
        _options.affectedElementsByControl(CliParentTable_AString.id());
        _options.affectedElementsByControl(CliParentTable_EditMethodString.id());

        if(table.AInt<=20)
        {
            _options.backColor(WinAPI::RGB2int(255,165,0));
        }
        else if( table.AInt>20 &&  table.AInt <60)
        {
            _options.backColor(WinAPI::RGB2int(255,255,0));
            _options.fontItalic(true);
            _options.textColor(WinAPI::RGB2int(255,0,127 ));
            _options.fontStrikethrough(true);
        }
        else
        {
            _options.backColor(WinAPI::RGB2int(128,0,128));
                _options.fontUnderline(true);
        }
    }

    super(_record, _options);
}
```

## Static RGB instead of run-time conversion from integer to RGB values
Previously, run-time conversion that used **WinAPI::RGB2Int** was required, because the Win32 color picker returned an RGB value, whereas the background color APIs accepted an integer. This run-time conversion isn't required, because the new color picker returns an integer to match the control's consumption of an integer. Additionally, it’s understood that .NET code often uses RGB values for colors. Therefore, in those cases, run-time conversion of colors isn't required for each use. Instead, you can define static color variables. Here are three examples.

```xpp
Static int GrayColor = 220 + 220 <<#offset8 + 220<<offset16;

Static int GrayColor = 0xdcdcdc

Static int GrayColor = 14474460; // DCDCDC or 220,220,220
```




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
