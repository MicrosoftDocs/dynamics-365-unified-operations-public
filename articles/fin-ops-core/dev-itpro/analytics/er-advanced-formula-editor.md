---
title: Electronic reporting advanced formula editor
description: Learn about how the advanced formula editor can be used to configure expressions in Electronic reporting (ER) model mapping and format components.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 03/12/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-04-01
ms.search.form: ERSolutionTable, ERExpressionDesignerFormula
ms.dyn365.ops.version: AX 10.0.9
---

# Electronic reporting advanced formula editor

[!include [banner](../includes/banner.md)]

In addition to the [Electronic reporting](general-electronic-reporting.md) [formula editor](general-electronic-reporting-formula-designer.md), you can use the advanced Electronic reporting formula editor to improve the experience of configuring Electronic reporting (ER) expressions. The advanced editor is browser-based and powered by the [Monaco editor](https://microsoft.github.io/monaco-editor). This article describes the most commonly used advanced editor features:

- [Code autoformatting](#code-autoformatting)
- [IntelliSense](#intellisense)
- [Code completion](#code-completion)
- [Code navigation](#code-navigation)
- [Code structuring](#code-structuring)
- [Find and replace](#find-and-replace)
- [Data pasting](#data-sources-and-functions-pasting)
- [Syntax colorization](#syntax-colorization)

## Activate the advanced formula editor

Complete the following steps to start using the advanced formula editor in your instance of Microsoft Dynamics 365 Finance.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
2. On **Configurations**, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
3. In **User parameters**, in the **Execution tracing** section, set the **Enable advanced formula editor** parameter to **Yes**.

:::image type="content" source="./media/ER-AdvEditor-Activate.png" alt-text="Screenshot of the User parameters dialog box with the Enable advanced formula editor parameter highlighted.":::

> [!NOTE]
> This parameter is user specific and company specific.

Starting in Microsoft Dynamics 365 Finance version 10.0.19, you can control which ER formula editor is offered by default. Complete the following steps to enable the advanced formula editor for all users and companies of the current Finance instance.

1. Open the **Feature management** workspace.
2. Find and select the feature **Set the ER advanced formula editor as the default one for all users** in the list, and then select **Enable now**.
3. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
4. On **Configurations**, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
5. In **User parameters**, find the **Disable advanced formula editor** parameter and verify that it's set to **No**.

:::image type="content" source="./media/ER-AdvEditor-Activate2.png" alt-text="Screenshot of the User parameters dialog box with the Disable advanced formula editor parameter highlighted.":::

> [!NOTE]
> The values of the parameters **Enable advanced formula editor** and **Disable advanced formula editor** are kept separate for each user. The **User parameters** dialog box displays these parameters depending on the status of the **Set the ER advanced formula editor as the default one for all users** feature.

## Code autoformatting

When you write a complex expression that consists of multiple rows of code, the editor automatically indents a new line based on the indentation of the previous row. You can select lines and change their indentation by typing **Tab** or **Shift+Tab**.

:::image type="content" source="./media/ER-AdvEditor-Indentation.gif" alt-text="Screenshot of the ER formula editor showing selecting lines and changing the indentation.":::

Autoformatting helps you keep the entire expression well formatted, which makes further maintenance easier and simplifies understanding of the configured logic.

## IntelliSense

The editor provides word completion to help you write expressions faster and avoid typos. When you start adding new text, the editor automatically offers a list of functions supported in ER functions that contain the characters you entered. You can also trigger IntelliSense in any place of a configured expression by typing **Ctrl+Space**.

:::image type="content" source="./media/ER-AdvEditor-Intelisense.gif" alt-text="Screenshot of the ER formula editor showing triggering IntelliSense.":::

## Code completion

The editor automatically provides code completion by:

- Inserting a closing bracket when you enter an opening bracket, and keeping the cursor inside the brackets.
- Inserting the second quotation mark when you enter the first one, and keeping the cursor inside the quotations.
- Inserting the second double quotation mark when you enter the first one, and keeping the cursor inside the quotations.

:::image type="content" source="./media/ER-AdvEditor-CodeCompletion.gif" alt-text="Screenshot of the ER formula editor showing automatic code completion.":::

When you point to a typed bracket, the editor automatically highlights the second bracket of this pair to show the construct that they support.

## Code navigation

You can find required symbols or lines in your expression by using the **Go to** command from the command palette or the context menu.

For example, to jump to line **8**, use one of the following methods:

- Press **Ctrl+G**, enter the value **8**, and then press **Enter**.

  -or-

- Press **F1**, type **G**, select **Go to line**, enter the value **8**, and then press **Enter**.

:::image type="content" source="./media/ER-AdvEditor-Goto.gif" alt-text="Screenshot of the ER formula editor showing how to locate parts of an expression using the command palette.":::

## Code structuring

The code for some functions, such as [IF](er-functions-logical-if.md) or [CASE](er-functions-logical-case.md), is automatically structured. You can expand and collapse any or all of the folding regions of this code to reduce the editable part of an expression so you can focus on only the piece of code that requires your attention. Use the toggle fold and unfold commands for that task.

For example, to fold all regions, use one of the following methods:

- Press **Ctrl+K**

  -or-

- Press **F1**, press **FO**, select **Fold all**, and then press **Enter**.

To unfold all regions, use one of the following methods:

- Press **Ctrl+J**

  -or-
  
- Press **F1**, type **UN**, select **Unfold all**, and then press **Enter**.

:::image type="content" source="./media/ER-AdvEditor-ToggleFold.gif" alt-text="Screenshot of the ER formula editor showing code being unfolded.":::

## Find and replace

To find occurrences of certain text, select the text in your expression, and do the following steps:

- Press **Ctrl+F** and then press **F3** to find the next occurrence of the selected text, or press **Shift+F3** to find the previous occurrence.

  -or-
  
- Press **F1**, type **F**, and then select the required option to find the selected text.

To replace occurrences of certain text, select the text in your expression, and do the following steps:

- Press **Ctrl+H**. Enter the alternative text and select the replacement option to replace either the selected text or all occurrences of this text in the current expression.

  -or-
  
- Press **F1**, type **R**, and then select the required option to replace the selected text. Enter the alternative text and select the replacement option to replace either the selected text or all occurrences of this text in the current expression.

To change all occurrences of certain text, select the text in your expression, and do the following steps:

- Press **Ctrl+F2** and then enter the alternative text.

  -or-
  
- Press **F1**, type **C**, and then select the required option to change the selected text. Enter the alternative text.

:::image type="content" source="./media/ER-AdvEditor-Find.gif" alt-text="Screenshot of the ER formula editor showing find and replace functionality.":::

## Data sources and functions pasting

Select **Add data source** to paste a data source from the **Data source** left panel into the current expression. Select **Add function** to paste a function from the **Functions** right panel into the current expression. If you use the ER formula editor, the selected function or data source is always added to the end of the configured expression. When you use the advanced ER formula editor, you can add the selected function or data source to any part of the configured expression. Use the cursor to specify where you want to paste the data.

:::image type="content" source="./media/ER-AdvEditor-PasteValue.gif" alt-text="Screenshot of the ER formula editor showing adding a data source and pasting a function.":::

## Syntax colorization

Currently, the editor uses different colors to highlight the following parts of expressions:

- The text in double brackets that can represent a label ID of a text constant.

:::image type="content" source="./media/ER-AdvEditor-SyntaxColorization.png" alt-text="Screenshot of the ER formula editor showing syntax colorization.":::

## Limitations

The editor currently supports the following web browsers:

- Chrome
- Edge
- Firefox
- Opera
- Safari

## Additional resources

- [Electronic reporting (ER) overview](general-electronic-reporting.md)
- [Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)
- [Monaco editor](https://microsoft.github.io/monaco-editor)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
