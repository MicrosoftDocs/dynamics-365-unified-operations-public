---
title: Translate financial dimension names and values
description: Learn how to translate financial dimension names, dimension values, and main account names into different languages.
author: anaborges02
ms.author: aolson
ms.topic: article
ms.date: 03/26/2026
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form: DimensionDetails, DimensionValueDetails, SysTranslationDetail
ms.dyn365.ops.version: 8.1
---

# Translate financial dimension names and values

[!include [banner](../includes/banner.md)]

If your organization operates in multiple languages, you can translate financial dimension names, dimension value descriptions, and main account names so that users see them in their preferred language.

Use the **Text translation** page to translate the following text into various languages:

- **Dimension name** from **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimensions** > **Translations**.
- **Financial dimension value description** from **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimensions**. Select custom financial dimension > **Dimension values** > **Translations**.
- **Main account name** from **General ledger** > **Chart of accounts** > **Accounts** > **Main accounts** > **Name translations**.

When you enter your financial dimension name and financial dimension value description, enter those values in the system language. You can see the system language in the Default language code shown on the **Text translation** page.

> [!IMPORTANT]
> Translated text is only used when the user language is different from the system language. The system is designed this way to increase performance.

If you don't enter the values in the system language, you might not get the expected results. To fix the problem, change the financial dimension name and financial dimension value description to the system language. The translated text isn't necessary for the system language.

## How translation lookup works

The system uses the following logic to determine which name or description to display for a financial dimension, dimension value, or main account:

1. **If the user's language matches the system language**, the system displays the default value from the main record. No translation lookup is performed.
1. **If the user's language differs from the system language**, the system looks for a translation record that matches the user's language.
   - If a translation exists for the user's language, the system displays the translated text.
   - If no translation exists for the user's language, the system falls back to the default value from the main record.

The system doesn't attempt to find translations in any other languages. There's no fallback chain - the only options are the user's specific language translation or the default value.

This translation logic applies consistently to all entities that you can use as financial dimension values, including main accounts, items, and custom financial dimensions, as well as the financial dimension name itself.

## Best practices for translations

- Enter all default names and descriptions in the system language. This approach ensures that users whose language matches the system language see the correct values.
- Create translation records for every language that users in your organization need. If a translation is missing, the user sees the default value instead.
- If a user reports seeing the wrong language for dimension names or values, verify that a translation record exists for their language and that their user language settings are correct.

## Example

The system language is set to "es" (Spanish).
You create a new financial dimension and enter the dimension name in English, not Spanish: "Ownership."

- You can define the name in a non-system language, but it's not recommended.
You create two translations for the "Ownership" dimension name:
- "es" (Spanish) = Propiedad
- "de" (German) = Besitz

User 1 has a user language of "de." When they see the dimension name, it displays as "Besitz."

User 2 has a user language of "es." When they see the dimension name, it displays as "Ownership." The dimension name of "Ownership" is shown because the user language is the same as the system language. As a result, the system doesn't look for any translations.

User 3 has a user language of "fr" (French). No French translation exists, so the system falls back to the default value "Ownership." To fix this, create a French translation for the dimension name.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
