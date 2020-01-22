---
# required metadata

title: Electronic reporting (ER) advanced formula editor
description: This topic describes how the advanced formula editor can be used to configure expressions in Electronic reporting (ER) model mapping and format components.
author: NickSelin
manager: AnnBe
ms.date: 01/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERExpressionDesignerFormula
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: AX 10.0.9

---

# Electronic reporting (ER) advanced formula editor

[!include [banner](../includes/banner.md)]

In addition to the regular [Electronic reporting](general-electronic-reporting.md) (ER) [formula editor](general-electronic-reporting-formula-designer.md), you can use the advanced ER formula editor to improve the experience of configuring ER expressions. It is a browser-based editor that is powered by the [Monaco editor](https://microsoft.github.io/monaco-editor) and offers many great
features. The mostly used ones are described in this topic.

- [Code autoformatting](#Autoformatting)
- [IntelliSense](#IntelliSense)
- [Code completion](#CodeCompletion)
- [Code navigation](#CodeNavigation)
- [Code structuring](#CodeStructuring)
- [Find and replace](#FindAndReplace)
- [Data pasting](#DataPasting)
- [Syntax colorization](#SyntaxColorization)

## <a name="ActivateAdvEditor">Activate advanced formula editor</a>

Complete the following steps to start using the advanced formula editor in your instance of Microsoft Dynamics 365 Finance.

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
3.  In the **User parameters** dialog box, in the **Execution tracing** section, set the **Enable advanced formula editor** parameter to **Yes**.

[![ER configurations page](./media/ER-AdvEditor-Activate.png)](./media/ER-AdvEditor-Activate.png)

> [!NOTE]
> Be aware that this parameter is user and company specific.

## <a name="Autoformatting">Code autoformatting</a>

When you write a complex expression that consists of multiple rows of code, the indentation of a new entered line will be automatically done based on the indentation of the previous row. You can select lines and changes their indentation by typing **Tab** or **Shift** + **Tab**.

[![ER formula editor](./media/ER-AdvEditor-Indentation.gif)](./media/ER-AdvEditor-Indentation.gif)

This allows you to keep the entire expression well formatted to make further maintenance easier and to simplify understanding of the configured logic.

## <a name="IntelliSense">IntelliSense</a>

The editor automatically provides word completion to help you write expression faster and to avoid typos. Whenever you start adding a new text, the editor automatically offers the list of supported in ER functions the name of which contains your typed characters . You can also trigger IntelliSense in any place of a configured expression by typing **Ctrl + Space**.

[![ER formula editor](./media/ER-AdvEditor-Intelisense.gif)](./media/ER-AdvEditor-Intelisense.gif)

## <a name="CodeCompletion">Code completion</a>

The editor automatically provides code completion:

- It inserts a closing bracket when an opening one is entered keeping the cursor inside entered brackets.
- It inserts the second quotation symbol when the first one is entered keeping the cursor inside entered quotations.
- It inserts the second double quotation symbol when the first one is entered keeping the cursor inside entered quotations.

[![ER formula editor](./media/ER-AdvEditor-CodeCompletion.gif)](./media/ER-AdvEditor-CodeCompletion.gif)

When you point to the typed bracket, the second bracket of this pair is automatically highlighted to show the construct that they embrace.

## <a name="CodeNavigation">Code navigation</a>

You can locate required symbols or lines in your expression by typing **Go to** command either using the command palette or context menu.

For example, to jump to the line **8**, just do the following:

- Either type **Ctrl** + **G**, enter the value **8** and type **Enter**.
- Or type **F1**, type **G**, select the option **Go to line**, enter the value **8** and type **Enter**.

[![ER formula editor](./media/ER-AdvEditor-Goto.gif)](./media/ER-AdvEditor-Goto.gif)

## <a name="CodeStructuring">Code structuring</a>

The code of some functions such as [IF](er-functions-logical-if.md) or [CASE](er-functions-logical-case.md) is automatically structured. You can expand and collapse any of or all folding regions of such code to reduce the editable part of an expression and to concentrate on the only piece of code that
requires your attention. The toggle fold / unfold commands can be used for that.

For example, to fold all regions do the following:

- Either type **Ctrl** + **K**.
-  Or type **F1**, type **FO**, select **Fold all** option and type **Enter**.

To unfold all regions, do the following:

- Either type **Ctrl** + **J**.
- Or type **F1**, type **UN**, select **Unfold all** option and type **Enter**.

[![ER formula editor](./media/ER-AdvEditor-ToggleFold.gif)](./media/ER-AdvEditor-ToggleFold.gif)

## <a name="FindAndReplace">Find and replace</a>

To find occurrences of a certain text, you can select this text in your expression, and do the following:

- Either type **Ctrl** + **F**. Then, type **F3** to find the next occurrence of the selected or type **Shift** + **F3** to find its previous occurrence.
- Or type **F1**, type **F** and select the required option to find the selected text.

To replace occurrences of a certain text, you can select this text in your expression, and do the following:

- Either type **Ctrl** + **H**. Then, enter the alternative text and select the replacement option to replace either the selected text or all occurrences of this text in the current expression.
- Or type **F1**, type **R** and select the required option to replace the selected text. Then, enter the alternative text and select the replacement option to replace either the selected text or all occurrences of this text in the current expression.

To change all occurrences of a certain text, you can select this text in your expression, and do the following:

- Either type **Ctrl** + **F2**. Then, enter the alternative text.
- Or type **F1**, type **C** and select the required option to change the selected text. Then, enter the alternative text.

[![ER formula editor](./media/ER-AdvEditor-Find.gif)](./media/ER-AdvEditor-Find.gif)

## <a name="DataPasting">Data sources and functions pasting</a>

You can select **Add data source** to paste to the current expression a data source that is currently selected on the **Data source** left-hand-side panel. In a like manner, you can select **Add function** to paste to the current expression a function that is currently selected on the **Functions** right-hand-side panel. If you use the regular ER formula editor, a selected function or a selected data source will be always pasted to the end of the configured expression. When you use the advanced ER formula editor, a selected function or a selected data source can be pasted to any place of the configured expression – you need to use the cursor to specify the desired position for data pasting.

[![ER formula editor](./media/ER-AdvEditor-PasteValue.gif)](./media/ER-AdvEditor-PasteValue.gif)

## <a name="SyntaxColorization">Syntax colorization</a>

Currently, different colors are used to highlight the following parts of expressions:

- The **\@** symbol that is used in relative paths to data sources and in references to labels.
- The text in double brackets that can represent either a label Id of a text constant.

[![ER formula editor](./media/ER-AdvEditor-SyntaxColorization.png)](./media/ER-AdvEditor-SyntaxColorization.png)

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Monaco editor](https://microsoft.github.io/monaco-editor)
