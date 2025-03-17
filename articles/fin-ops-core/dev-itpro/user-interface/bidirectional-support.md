---
title: Right-to-left language support and bidirectional text
description: Learn about right-to-left language support and bidirectional text, including an example of right-to-left language support with Microsoft Word.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: f0d7680c-bf07-44e7-83d8-381e4471f45e
ms.custom: 
  - bap-template
  - evergreen
---

# Right-to-left language support and bidirectional text

[!include [banner](../includes/banner.md)]

In the area of right-to-left (RTL) language support, one consideration is the combination of RTL text and left-to-right (LTR) text in the same string. This article discusses the issue of bidirectional text and how it's handled.

## A great example of right-to-left language support: Microsoft Word

In the area of right-to-left (RTL) language support, one consideration is the combination of RTL text and left-to-right (LTR) text in the same string. One example of a program that implements this functionality correctly is Microsoft Word. If you're trying to understand the correct behavior of mixed language presentation, you can use Word for validation. The problem is that most software just implements the Unicode standard to display bidirectional data, without evaluating how that data is actually used. Additionally, there's no attempt to provide the interactive experience that the user actually requires. 

To understand how Word “gets it right” and provides a great experience, you can inspect the XML of a Word document. There, you will see that Word tracks (and stores together with the run of characters) the keyboard that is used to enter each character, and that it treats each character as a member of the language that is associated with the keyboard. Therefore, the character is given the behavioral aspects of that language.

Keeping track of character orientation in a financial program that might record billions of transactions and multi-billions of characters would produce significant transnational and spatial overhead if we stored contextual information for each character. Therefore, this behavior would be considered only for special conditions.

## Bidirectional text
To support Arabic and Hebrew, both of which are RTL languages, there is an RTL orientation for the controls in each form, so that an RTL reader can interact with the form in a natural reading manner. For the most part, RTL orientation of the controls works as expected and provides RTL users with the experience that they expect. Finance and operations apps and modern browsers support RTL orientation, and the apps conform to that functionality. However, in some cases, extensible controls (custom controls) require special code to orient their elements correctly. 

A point of reference in this article is the Win32 CEdit control, which is used primarily for standard text entry (account name, description, user name, and so on, in Microsoft Dynamics AX 2012). The behavior of the HTML Input control mimics the functionality of the CEdit control. Therefore, the same behavior applies to finance and operations apps. 

The CEdit control is a Win32 control that is governed by the rules for bidirectional text management that are defined by the Unicode standard. Bidirectional text occurs when the control hosts both RTL text (such as Arabic or Hebrew) and LTR text within the same string of characters. 

When you evaluate the examples in this article, remember that, regardless of the orientation of the form (RTL or LTR), the actual text that is presented is never reversed or “mirrored.” English text is always read LTR and Arabic/Hebrew text is always read RTL. When LTR and RTL text are combined, the reader must jump to the beginning of the run of characters in a given orientation. For example, when a mixed string is read from right to left, the individual words might be read like this: 

**–––––&gt;  &lt;–––––  –––––&gt;  &lt;–––––** 

**English  Arabic  English  Arabic**

## English and Arabic/Hebrew text together: Bidirectional issues
The visual presentation (glyphs) of English, Arabic, and Hebrew characters on the corresponding keyboards clearly differ. However, those three keyboards also share some symbols. These symbols include numerals, and formatting characters such as parentheses, brackets, and underscores. According to the Unicode bidirectional algorithm, when these characters are used in a bidirectional string, their RTL/LTR orientation depends on **the context of the characters that surround them**. From the [Unicode standard](https://www.unicode.org/versions/Unicode5.1.0/): 

> [!NOTE]
> You can find the Unicode display algorithm at <https://www.unicode.org/reports/tr9/>. (Section 3.3.4 of the algorithm describes how to position neutrals.)

-   Characters that have a weak bidirectional type determine their directionality according to their proximity to other characters that have strong directionality.
-   Characters that have a neutral bidirectional type determine their directionality from either the surrounding strong text or the embedding level.

The following table describes the bidirectional character types.

|Category|Type|Description|General scope|
|---|---|---|---|
|Strong|L|Left-to-Right|LRM, most alphabetic, syllabic, Han ideographs, non-European or non-Arabic digits, …|
|Strong|LRE|Left-to-Right Embedding|LRE|
|Strong|LRO|Left-to-Right Override|LRO|
|Strong|R|Right-to-Left|RLM, Hebrew alphabet, and related punctuation|
|Strong|AL|Right-to-Left Arabic|Arabic, Thaana, and Syriac alphabets, most punctuation specific to those scripts, …|
|Strong|RLE|Right-to-Left Embedding|RLE|
|Strong|RLO|Right-to-Left Override|RLO|
|Weak|PDF|Pop Directional Format|PDF|
|Weak|EN|European Number|European digits, Eastern Arabic-Indic digits, …|
|Weak|ES|European Number Separator|Plus sign, minus sign|
|Weak|ET|European Number Terminator|Degree sign, currency symbols, …|
|Weak|AN|Arabic Number|Arabic-Indic digits, Arabic decimal and thousands separators, …|
|Weak|CS|Common Number Separator|Colon, comma, full stop (period), Non-breaking space, …|
|Weak|NSM|Nonspacing Mark|Characters marked Mn (Nonspacing_Mark) and Me (Enclosing_Mark) in the Unicode Character Database|
|Weak|BN|Boundary Neutral|Default ignorables, non-characters, and control characters, other than those that are explicitly given other types|
|Neutral|B|Paragraph Separator|Paragraph separator, appropriate Newline Functions, higher-level protocol paragraph determination|
|Neutral|S|Segment Separator|Tab|
|Neutral|WS|Whitespace|Space, figure space, line separator, form feed, General Punctuation spaces, …|
|Neutral|ON|Other Neutrals|All other characters, including OBJECT REPLACEMENT CHARACTER|



The fundamental problem with the Unicode standard for bidirectional text is that it fails to capture the user’s intent. Therefore, the algorithm will move characters around within the same string, and put them in a location that the user didn't specify or doesn't want. This issue is troublesome for accounting and financial systems, because the data that users enter into the system might not match the corresponding source documents. 

As we mentioned, Arabic, English, and Hebrew keyboards share some of the same characters. However, in some cases, those characters are positioned differently, depending on the keyboard that was used to type them, and/or the context of the surrounding characters and the orientation of the input control. These language-neutral characters include commas, periods, parentheses, hyphens, and underscore characters. 

In some cases, the rules for displaying the same characters varies between languages. Additionally, those rules can change, depending on the kind of data that is displayed. For more information about this issue, see the "Issue: The hyphen used together with numbers: Language-specific behavior" section, later in this article. 

Some people expect that characters that are entered in RTL mode will appear the same when the form is viewed in LTR mode. In other words, the expectation is that a customer can have some users who use Hebrew and others who use English on the same installation or in the same company.

## Issue: The underscore character used together with numbers

**Description:** 123\_456 appears as 456\_123, although the user wants it to appear as 123\_456. 

**Example:** The user wants to enter an item number (such as 123\_456) or a journal name (such as BA\_Chk\_Rev) that includes underscore characters for grouping purposes. 

There is a difference between the Unicode standard and what our users want to see in a financial program. Even Word presents 123\_456 as 456\_123 for both Arabic and Hebrew. This behavior occurs because the underscore character is a grouping mechanism. It splits the number into groups of numbers that can be read from right to left. 

Numbers are read from left to right in Arabic and Hebrew. “Item” numbers, regardless of the combination (RTL\_LTR\_RTL, LTR\_RTL\_LTR, Neutral\_RTL, and so), should appear exactly the same in a paragraph of any direction or alignment. This issue isn't easy to resolve for plain text programs. All the customer knows is that the physical item number is (from left to right) 123\_456, and that the string should appear as 123\_456 in every language, so that the number that users see always matches what they know the physical number is.

**Control behavior:** None of the off-the-shelf controls provide the desired behavior. Word fails too.

| WPF RichTxt | Win32 CEdit | Win32 RichTxt | Word |
|-------------|-------------|---------------|------|
| No          | No          | No            | No   |

**Workarounds:**

-   When you're using an English keyboard, use a different delimiter. For example, enter **123.456** or **123/456**.
-   When you're using a Hebrew keyboard, use a different delimiter. For example, enter **123.456**. The slash character (/) on a Hebrew keyboard produces a period (.).

**Recommendation:** None of the off-the-shelf controls provide the requested behavior. One alternative is to identify fields that must allow for this directional formatting and flag those fields as LTR for data input (right-aligned for display purposes). The program can't automatically determine that a field must have this behavior. Therefore, if we expose an RTL/LTR flag, a customizer can modify targeted fields for the desired behavior. Although this approach enables this specific scenario, it's important to understand that, if you extend the scenario by using characters in a combination of RTL and LTR languages, you will introduce other issues. Another alternative is to educate users about the fundamental behavior when underscore characters and numbers are used together. When underscore characters and numbers are required, users can then use a workaround to obtain the desired display behavior. 

> [!NOTE]
> The underscore character doesn't present an issue when you combine English and RTL languages (pattern: RTL\_LTR\_RTL). Therefore, if you force a control to LTR when the input includes numbers/text/underscore characters, the behavior won't be as expected. Users will have to manually reposition the cursor after each use of an underscore when they type RTL text. However, the behavior will be as expected for the use of numbers/text/underscore characters. 

**Hebrew:** קשגכ\_english\_יקנקרק 

**Arabic:** شقلاهؤ\_english\_شقشلاهؤ

## Issue: The hyphen used together with numbers: Language-specific behavior

**Description:** LTR is expected for Hebrew, whereas RTL is expected for Arabic. 

**Example:** Item names that include numbers Arabic and Hebrew treat the hyphen differently when it's used together with numbers. An Arabic keyboard treats the hyphen as an RTL character, whereas a Hebrew keyboard treats it as an LTR character. Therefore, similar typed strings should be presented differently, depending upon the keyboard that was used. Some readers will be familiar with this example from a meeting of interested parties: 1-2-3-a-b-c 

**Arabic:** The desired behavior is correct in Dynamics AX 2012. 1-2-3-ش-لال-ؤ 

**Hebrew:** The desired behavior is incorrect in Dynamics AX 2012. 1-2-3-ש-נ-ב 

The Unicode standard doesn’t provide for language-specific or keyboard-specific behavior. Instead, it supplies fundamental bidirectional behavior and treats the hyphen as an RTL character. Therefore, it presents the Arabic string correctly but the Hebrew string incorrectly. 

**Control behavior:** The WPF RichTxt control produces the correct/desired behavior for each language.

| WPF RichTxt | Win32 CEdit | Win32 RichTxt | Word |
|-------------|-------------|---------------|------|
| Yes         | No          | No            | Yes  |

**Workarounds for the Hebrew user:**

-   Don't type hyphens between the numbers. For example, if you type 1 2 3-A-B-C on a Hebrew keyboard, it appears in RTL as C-B-A-3 2 1. You should assume that the ABC order is correct for Hebrew, which is an RTL language. The English ABC text is reversed here for demonstrative purposes.
-   Use a different delimiter between the numbers. For example, the slash character (/)  on a Hebrew keyboard produces a period (.).

**Recommendation:** This pattern is an issue for Hebrew users who want to use numbers or hyphens in item names. Therefore, a global solution might not be appropriate, because there are exceptions. Phone numbers, Social Security numbers, and other source document identification numbers are always read LTR. 

The WPF RichTxt control provides the desired behavior according to the strict guidance. However, it isn't clear that this behavior is always the desired behavior. That is, phone numbers, US Social Security numbers, and so on, should always be read and appear in LTR order, regardless of the language orientation. The alternative is to identify fields that must enable this behavior. The program can't automatically determine that a field must have this behavior. Therefore, you might have to use a descriptive property on the control, so that users can specify “Structured Formatting.” If none of these approaches can be achieved, you must educate Hebrew users about the fundamental behavior when hyphens are used together with numbers. Users can then use one of the preceding workarounds to get the desired display behavior, by omitting the hyphens between numbers. 

**Hebrew example:** (Desired and correct Operations for both Arabic and the Hebrew example in Hebrew) 

**Pattern:** First (עברית) hyphen second (English) hyphen third (שלום) hyphen forth (Hello) 

**Correct:** עברית-English-שלום-Hello 

**Pattern:**

1.  First (English letter) hyphen second (Hebrew letter) hyphen
2.  First (Hebrew letter) hyphen second (English letter) hyphen

A RTL form appears as desired:

1.  ש-**-a**
2.  **-a**ש-

**Exception for phone numbers:** Often, Arabic users don't have to use hyphens in phone numbers, because international phone numbers rarely use hyphens to separate digits. Any fundamental changes in the behavior of hyphens (for example, if you introduce use of the WPF RichTxt control) will cause phone numbers to appear incorrectly for Arabic users. 

Phone numbers are always read LTR and often include hyphens. Phone numbers sometimes appear correctly, when they are shown in a grid through a display method that presents the string as LTR.

Currently, the input of phone numbers by using numbers and hyphens produces the correct display, such as 701-225-2188. 

There is an issue with phone numbers if you try to use a US pattern that includes parentheses. 

**Arabic/Hebrew/English (desired):** (701)225-2188 

**Arabic (actual):** )701(225-2188 

**Hebrew (actual):** )701(225-2188 

**Recommendation:** Expose an RTL flag for controls or an extended data type for phone numbers. A customizer can force the control into LTR mode. This approach will let users enter values in the order that they want.

## Issue: LTR text combined with neutral characters in RTL input

**Description:** English text is combined with parentheses or other neutral characters. 

**Example:** A company name together with the company abbreviation, such as "Dynamics (DAT)" 

In a typical example, the company name is followed by the company abbreviation, which is enclosed in parentheses. In this case, "Dynamics (DAT)" is shown as "(Dynamics(DAT". This behavior occurs because the closing parenthesis isn't surrounded by two English characters. Therefore, the parenthesis is treated as an RTL character. It's changed to the RTL closing parenthesis and moved to the end of the string (in RTL orientation). 

**Control behavior:** None of the controls provide the desired behavior.

| WPF RichTxt | Win32 CEdit | Win32 RichTxt | Word |
|-------------|-------------|---------------|------|
| No          | No          | No            | Yes  |

The WPF RichTxt control has a flag that tries to format text according the first character in the string. Although the algorithm **should** fix this issue, it doesn't. 

**Workarounds:** Don't use weak or neutral characters for grouping when you use English. For example, use "Dynamics DAT". 

**Recommendation:** None of the controls provide the desired behavior. You must educate users about the fundamental behavior when weak or neutral characters are used together with English text. Don't use weak or neutral characters unless English characters appear on each side.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
