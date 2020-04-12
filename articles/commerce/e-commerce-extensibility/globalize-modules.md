---
# required metadata

title: Globalize modules by using the CultureInfoFormatter class
description: This topic describes how to globalize modules by using the CultureInfoFormatter class.
author: samjarawan
manager: annbe
ms.date: 10/24/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Globalize modules by using the CultureInfoFormatter class

[!include [banner](../includes/banner.md)]

This topic describes how to globalize modules by using the **CultureInfoFormatter** class.

## Overview

Globalization of an online site should include not only string localization, but also number, date, and currency formatting for the various languages and regions that your website serves.

The Microsoft Dynamics 365 Commerce Online Software Development Kit (SDK) provides a **CultureInfoFormatter** class that helps meet typical globalization requirements for the format of numbers, currencies as well as dates and times.

## Access the CultureInfoFormatter class in a module view file

An instance of the **CultureInfoFormatter** class is automatically created and can be accessed in the module view through the **this.props.context** object.  The following examples shows how to use the **CultureInfoFormatter** methods to format currency.

```ts
public render(): JSX.Element | null {
    ...
    // this.props.context.cultureFormatter contains an initialized formatter
    // with locale of 'en-US' in this example
    const intlFormatter = this.props.context.cultureFormatter
    intlFormatter.formatCurrency(34.12);
    // expected output: $ 34.12
}
```

## Construct an instance of the CultureInfoFormatter class

The constructor of the **CultureInfoFormatter** class takes one argument, **lang-locale**.

The **lang-locale** argument must be a valid [BCP-47](https://tools.ietf.org/html/bcp47) language tag. A default value, **'en-US'**, is used if no language tag is specified. Language tags aren't case-sensitive. However, by convention, but the locale is usually capitalized.

### Example

```ts
import {CultureInfoFormatter} from '@msdyn365-commerce/core';

// Default constructor will use 'en-US' for locale
let intlFormatter = new CultureInfoFormatter();

// Constructs a new intl formatter using the French language as spoken in France
intlFormatter = new CultureInfoFormatter('fr-FR');

// Constructs a new intl formatter using the English language as spoken in Great Britain
intlFormatter = new CultureInfoFormatter('en-GB');
```

## CultureInfoFormatter class formatting functions

The **CultureInfoFormatter** class provides the following formatting functions:

- Currency formatting
- Date formatting
- Time formatting
- Number formatting

### Currency formatting

To format currency according to the conventions for a specific locale, use the **formatCurrency()** method. Here is an example.

```ts
/**
 * Returns a localized currency formatted version of a price.
 *
 * @param price Either a string or number representing the price that will be localized and formatted
 * @param currencyCode Optional argument. The three letter currency code that will be used for formatting the currency.
 * If the currency code is not provided the locale will be used to determine the best fit currency code.
 */
formatCurrency(price: string | number, currencyCode?: string): string;
```

The **currencyCode** argument is optional. If it's provided, it must be in [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) format. If the **currencyCode** argument isn't provided, the formatter uses the locale to determine the best currency code to use.

#### Currency formatting examples

```ts
import {CultureInfoFormatter} from '@msdyn365-commerce/core';

// Set locale to fr-FR
let cultureInfoFormatter = new CultureInfoFormatter('fr-FR');

// Using a string argument for the price
cultureInfoFormatter.formatCurrency('34.12', 'eur');
// expected output:  "34,12 €"

// Using a number argument for the price and letting the formatter find
// the best currency code to use from the locale given
cultureInfoFormatter.formatCurrency(34.12); 
// expected output: "34,12 €"

cultureInfoFormatter = new CultureInfoFormatter('en-IN');
cultureInfoFormatter.formatCurrency(34.12, 'inr');
// expected output: ₹ 34.12
```

### Date formatting

To format a date according to the conventions for a specific locale, use the **formatDate()** method. Here is an example.

```ts
/**
 * Returns a localized formatted version of a date
 *
 * @param date Date object representing the date that will be localized and formatted
 * @param options An optional argument that controls the formatting.
 */
formatDate(date: Date, options?: IDateFormatOptions): string;
```

The **options** argument is optional. It lets you control the localization and formatting. For more information about date formatting properties, see [IDateFormatOptions](#idateformatoptions).

#### Date formatting examples

```ts
import {CultureInfoFormatter} from '@msdyn365-commerce/core';
const testDate = new Date(2012, 11, 20, 3, 0, 0); // 12/20/2012 (in US format-mm/dd/yyyy)
let cultureInfoFormatter = new CultureInfoFormatter('en-US');

// Basic format with no options
cultureInfoFormatter.formatDate(testDate);
// expected output:  "12/20/2012"

// Set lang-locale to English as spoken in Great Britain
cultureInfoFormatter = new CultureInfoFormatter('en-GB');
cultureInfoFormatter.formatDate(testDate);
// expected output:  "20/12/2012"

// Set lang-locale to German as spoken in Germany
cultureInfoFormatter = new CultureInfoFormatter('de-DE');

let options: IDateFormatOptions = <IDateFormatOptions>{};
options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };

cultureInfoFormatter.formatDate(testDate);
// expected output:  "Donnerstag, 20. Dezember 2012"
```

### Time formatting

To format a time according to the conventions for a specific locale, use the **formatTime()** method. Here is an example.

```ts
/**
 * Returns a localized formatted version of a time
 *
 * @param time Date object representing the time that will be localized and formatted
 * @param options An optional argument that controls the formatting
 */
formatTime(time: Date, options?: ITimeFormatOptions): string;
```

The **options** argument is optional. It lets you control the localization and formatting. For more information about time formatting properties, see [ITimeFormatOptions](#itimeformatoptions).

#### Time formatting examples

```ts
import {CultureInfoFormatter} from '@msdyn365-commerce/core';
const testDate = new Date(2012, 11, 20, 13, 34, 23); // 1:34:23 PM in en-US Format
let cultureInfoFormatter = new CultureInfoFormatter('en-US');
let options: ITimeFormatOptions = <ITimeFormatOptions>{};
options.hour12 = false;
// Format time with 24 hour time
cultureInfoFormatter.formatTime(testDate, options);

cultureInfoFormatter = new CultureInfoFormatter('fr-FR');
options = <ITimeFormatOptions>{};
options.second = 'numeric';
cultureInfoFormatter.formatTime(testDate, options);
// expected output:  "13:34:23"
```

### Number formatting

To format a number according to the conventions for a specific locale, use the **formatNumber()** method. Here is an example.

```ts
/**
 * Returns a localized formatted version of a number
 *
 * @param value The number that will be localized and formatted
 * @param options An optional argument that controls the formatting.
 */
formatNumber(value: number, options?: INumberFormatOptions): string;
```

The **options** argument is optional. It lets you control the localization and formatting. For more information about number formatting properties, see [INumberFormatOptions](#inumberformatoptions).

#### Number formatting examples

```ts
import {CultureInfoFormatter} from '@msdyn365-commerce/core';

let cultureInfoFormatter = new CultureInfoFormatter('en-US');
cultureInfoFormatter.formatNumber(123456789);
// expected output:  "123,456,789"
cultureInfoFormatter.formatNumber(1234567.89);
// expected output:  "1,234,567.89"

// German language uses comma as decimal separator and period for thousands
cultureInfoFormatter = new CultureInfoFormatter('de-DE');
cultureInfoFormatter.formatNumber(1234567.89);
// expected output:  "1.234.567,89"

const options: INumberFormatOptions = <INumberFormatOptions>{};
options.style = 'percent';
(cultureInfoFormatter.formatNumber(0.7842, options);
// expected output:  "78,42 %"

// Setting the language to Arabic formats numbers using Arabic numerals
cultureInfoFormatter = new CultureInfoFormatter('ar-EG');
cultureInfoFormatter.formatNumber(1234567.89);
// expected output:  "١٬٢٣٤٬٥٦٧٫٨٩" 
```

## Formatting options

This section covers the formatting options and property details for **ITimeFormatOptions**, **IDateFormatOptions**, and **INumberFormatOptions** interfaces. 

### ITimeFormatOptions 

```ts
interface ITimeFormatOptions {
    localeMatcher?: 'best fit' | 'lookup';
    formatMatcher?: 'basic' | 'best fit';
    hourCycle?: 'h11' | 'h12' | 'h23' | 'h24';
    timeZone?: string;
    hour12?: boolean;
    hour?: 'numeric' | '2-digit';
    minute?: 'numeric' | '2-digit';
    second?: 'numeric' | '2-digit';
    timeZoneName?: 'short' | 'long';
}
```

#### Property details

| Name | Type | Allowed values | Description |
|------|------|----------------|-------------|
| localeMatcher | enum | 'best fit' or 'lookup' | Specify the algorithm that is used to match and find the locale. The **'lookup'** matcher follows the lookup algorithm that is specified in [BCP-47](https://tools.ietf.org/html/bcp47). The **'best fit'** matcher lets the runtime provide a locale that is at least as well-suited to the request as the result of the lookup algorithm, although it might be better suited than that result. |
| formatMatcher | enum | 'basic' or 'best-fit' | Specify the format matching algorithm that is used, and when it's used. The default value is **'best fit'**. |
| hourCycle | enum | 'h11', 'h12', 'h23', or 'h24' | Specify the hour cycle that is used. | 
| timeZone | string | Time zone names, as defined by the [IANA time zone database](https://www.iana.org/time-zones) | Specify the time zone that is used. The default value is the runtime's default time zone. If the environment lacks native internationalization support and internationalization is polyfilled, this option won't be supported (because internationalization polyfill doesn't support time zones). |
| hour12 | boolean | 'true' or 'false' | Specify whether 12-hour time is used instead of 24-hour time. This option overrides the **hourCycle** property, and its default value depends on the locale. |
| hour | enum | 'numeric' or '2-digit' | Specify the representation of the hour. The **'2-digit'** value forces hours to be shown as two digits. |
| minute | enum | 'numeric' or '2-digit' | Specify the representation of the minute. The **'2-digit'** value forces minutes to be shown as two digits. |
| second | enum | 'numeric' or '2-digit' | Specify the representation of the second. The **'2-digit'** value forces seconds to be shown as two digits. |
| timeZoneName | enum | 'short' or 'long' | Specify the representation of the time zone name. The **'short'** value shows the three-character abbreviation for the time zone. The **'long'** value shows the full name. | 

### IDateFormatOptions

```ts
interface IDateFormatOptions extends ITimeFormatOptions {
    weekday?: 'narrow' | 'short' | 'long';
    year: 'numeric' | '2-digit';
    month?: 'numeric' | '2-digit' | 'narrow' | 'short' | 'long';
    day?: 'numeric' | '2-digit';
}
```

> [!NOTE] 
> All properties provided in **ITimeFormatOptions** interface can be used in **IDateFormatOptions** interface since the time object is a subcomponent of the date object.

#### Property details

| Name | Type | Allowed values | Description |
|------|------|----------------|-------------|
| weekday | enum | 'narrow', 'short', or 'long' | Specify the representation of the day. The **'narrow'** value shows the one-character or two-character representation of the day. The **'short'** value shows the three-character representation. The **'long'** value shows the full name. |
| year | enum | 'numeric' or '2-digit' | Specify the representation of the year. The **'2-digit'** value shows the two most significant digits of the year (for example, the year 2018 is shown as **18**). The **'numeric'** value shows the whole year. |
| month | enum | 'numeric', '2-digit', 'narrow', 'short', or 'long' | Specify the representation of the month. The **'numeric'** value shows the numeric representation of the month (for example, April is shown as **4**). The **'2-digit'** value shows the two-digit numeric representation (for example, April is shown as **04**). The **'narrow'** value shows the two-character representation (for example, April is shown as **AP**). The **'short'** value shows the three-character representation (for example, April is shown as **Apr**). The **'long'** value shows the full name. |
| day | enum | 'numeric' or '2-digit' | Specify the representation of the day. The **'2-digit'** value forces days to be shown as two digits. | 

No default value is defined for each date/time component property. However, if all component properties are undefined, the **'numeric'** value is assumed for the **year**, **month**, and **day** property.

### INumberFormatOptions 

```ts
export interface INumberFormatOptions {
    localeMatcher?: 'best fit' | 'lookup';
    style?: 'decimal' | 'percent' | 'currency';
    currency?: string;
    minimumIntegerDigits?: number;
    minimumFractionDigits?: number;
    maximumFractionDigits?: number;
    minimumSignificantDigits?: number;
    maximumSignificantDigits?: number;
}
```

#### Property details

| Name | Type | Allowed values | Description |
|------|------|----------------|-------------|
| localeMatcher | enum | 'best fit' or 'lookup' | Specify the algorithm that is used to match and find the locale. The **'lookup'** matcher follows the lookup algorithm that is specified in [BCP-47](https://tools.ietf.org/html/bcp47). The **'best fit'** matcher lets the runtime provide a locale that is at least as well-suited to the request as the result of the lookup algorithm, although it might better suited than that result. |
| style | enum | 'decimal', 'percent', or 'currency' | Specify the formatting style that is used. Use the **'decimal'** value for plain number formatting, the **'currency'** value for currency formatting, and the **'percent'** value for percentage formatting. The default value is **'decimal'**. |
| currency | string | Three-character [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) currency codes | Specify the currency that is used in currency formatting. There is no default value. If the **style** property is set to **'currency'**, the **currency** property must be provided. |
| minimumIntegerDigits | number | Any integer value between 1 and 21 | Specify the minimum number of integer digits that is used. The default value is **1**. |
| minimumFractionDigits | number | Any integer value between 0 and 20 | Specify the minimum number of fraction digits that is used. The default value for number and percentage formatting is **0** (zero). The default value for currency formatting is provided by the [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) standard. |
| maximumFractionDigits | number | Any integer value between 0 and 20 | Specify the maximum number of fraction digits that is used. |
| minimumSignificantDigits | number | Any integer value between 1 and 21 | Specify the minimum number of significant digits that is used. The default value is **1**. |
| maximumSignificantDigits | number | Any integer value between 1 and 21 | Specify the maximum number of significant digits that is used. The default value is **21**. |

## Additional resources

[Request properties object](request-properties-object.md)

[App settings](app-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Cookie API overview](cookie-api-overview.md)
