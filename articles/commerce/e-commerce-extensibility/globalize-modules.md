---
# required metadata

title: Globalize modules using CultureInfoFormatter
description: This topic describes how to globalize modules using CultureInfoFormatter.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
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
# Globalize modules using CultureInfoFormatter

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to globalize modules using CultureInfoFormatter.

## Overview

Globalizing an online site should not only include string localization but also number, date, and currency formatting for the various languages and regions your website serves.

The Dynamics 365 Commerce online SDK provides a **CultureInfoFormatter** class to help meet common globalization requirements to format numbers, currency, and date/time.

## Access CultureInfoFormatter in a module view file
An instance of CultureInfoFormatter constructed with the locale derived from the `RenderingContext` is
passed along in the props object to a modules view file. To access this, use the following syntax.

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

## Construct an instance of CultureInfoFormatter

The constructor of CultureInfoFormatter takes in one argument, lang-locale.

The lang-locale argument must be a valid [BCP-47](https://tools.ietf.org/html/bcp47) language tag. A default value of 'en-US' will be used if no language tag is specified. Language tags are not case-sensitive but the locale is generally capitalized by convention.

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

## CultureInfoFormatter formatting functions

CultureInfoFormatter provides the following formatting functions.
- Currency formatting
- Date formatting
- Time formatting
- Number formatting

### Currency Formatting

To format currency in accordance with a certain locale use the `formatCurrency()` method.

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
The currency code argument is optional, but if it is provided it must be in the [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) format. If the currency code is not provided, the formatter will use the locale to determine the best currency code to use.

#### Examples

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

To format a date in accordance with a certain locale, use `formatDate()` as in the following example.

```ts
/**
 * Returns a localized formatted version of a date
 *
 * @param date Date object representing the date that will be localized and formatted
 * @param options An optional argument that controls the formatting.
 */
formatDate(date: Date, options?: IDateFormatOptions): string;
```
The options argument is optional and enables you to control the localization and formatting. For more information on the available date formatting properties, see [IDateFormatOptions](#IDateFormatOptions).

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

To format a time in accordance with a certain locale, use `formatTime()` as in the following example.

```ts
/**
 * Returns a localized formatted version of a time
 *
 * @param time Date object representing the time that will be localized and formatted
 * @param options An optional argument that controls the formatting
 */
formatTime(time: Date, options?: ITimeFormatOptions): string;
```
The options argument is optional and enables you to control the localization and formatting. For more information on the available time formatting properties, see [ITimeFormatOptions](#ITimeFormatOptions).

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

To format a number in accordance with a certain locale use `formatNumber()` as in the following example.

```ts
/**
 * Returns a localized formatted version of a number
 *
 * @param value The number that will be localized and formatted
 * @param options An optional argument that controls the formatting.
 */
formatNumber(value: number, options?: INumberFormatOptions): string;
```
The options argument is an optional argument that allows one to control the localization and formatting. For more information on the available number formatting properties, see [INumberFormatOptions](#INumberFormatOptions).

#### Number formatting examples

```ts
import {CultureInfoFormatter} from '@msdyn365-commerce/core';


let cultureInfoFormatter = new CultureInfoFormatter('en-US');
cultureInfoFormatter.formatNumber(123456789);
// expected output:  "123,456,789"
cultureInfoFormatter.formatNumber(1234567.89);
// expected output:  "1,234,567.89"

// German langauge uses comma as decimal separator and period for thousands
cultureInfoFormatter = new CultureInfoFormatter('de-DE');
cultureInfoFormatter.formatNumber(1234567.89);
// expected output:  "1.234.567,89"

const options: INumberFormatOptions = <INumberFormatOptions>{};
options.style = 'percent';
(cultureInfoFormatter.formatNumber(0.7842, options);
// expected output:  "78,42 %"


// Setting the language to Arabic formats numbers using Arabic numerals
cultureInfoFormatter = new CultureInfoFormatter('ar-EG');
cultureInfoFormatter.formatNumber(1234567.89);
// expected output:  "١٬٢٣٤٬٥٦٧٫٨٩" 
```

## Formatting options

The following section covers the formatting options and property details for ITimeFormatOptions, IDateFormatOptions, and INumberFormatOptions. 

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

| Name | Type | Allowed Values | Description |
| ----------- | ----------- |----------- | ----------- |
| localeMatcher | enum | 'best fit' or 'lookup' | Allows one to set the algorithm used to match and find the locale. The "lookup" matcher follows the lookup algorithm specified in BCP 47. The "best fit" matcher lets the runtime provide a locale that's at least, but possibly more, suited for the request than the result of the lookup algorithm |
| formatMatcher | enum | 'basic' or 'best-fit' | The format matching algorithm to use when. The default is 'best fit' |
| hourCycle | enum | 'h11', 'h12', 'h23' or 'h24' | The hour cycle to use | 
| timeZone | string | Timezone names as defined by [IANA time zone database](https://www.iana.org/time-zones) | Sets the timezone to use. The default is the runtime's default timezone. If environment lacks native Intl support and Intl is polyfilled, this option will not be supported (since Intl polyfill does not support timezones). |
| hour12 | boolean | 'true' or 'false' | Whether or not to use 12 hour time, as opposed to 24 hour time. This option overrides the hourCycle property and its default value is dependant on locale. |
| hour | enum | 'numeric' or '2-digit' | Controls the representation of the hour. '2-digit' forces hours to be displayed with two digits. |  
| minute | enum | 'numeric' or '2-digit' | Controls the representation of the minute. '2-digit' forces minutes to be displayed with two digits. |  
| second | enum | 'numeric' or '2-digit' | Controls the representation of the second. '2-digit' forces seconds to be displayed with two digits. |  
| timeZoneName | enum | 'short' or 'long' | Controls the representation of the time-zone name. The 'short' value is the three character abbreviation for the time-zone, and 'long' is the full time-zone name. | 

### IDateFormatOptions

```ts
interface IDateFormatOptions extends ITimeFormatOptions {
    weekday?: 'narrow' | 'short' | 'long';
    year: 'numeric' | '2-digit';
    month?: 'numeric' | '2-digit' | 'narrow' | 'short' | 'long';
    day?: 'numeric' | '2-digit';
}
```
[!NOTE] 
All options provided in ITimeFormatOptions can be used in IDateFormatOptions. This is because time is a subcomponent of date.

#### Property details

| Name | Type | Allowed Values | Description |
| ----------- | ----------- |----------- | ----------- |
| weekday | enum | 'narrow', 'short', or 'long' | Controls representation of the day. The 'narrow' value is the 1-2 character representation of the day, 'short is the 3 character representation, and 'long' is the full name. |
| year | enum | 'numeric' or '2-digit' | Controls the representation of the year. '2-digit' will display the two most significant digits of the year (2018 -> 18), and 'numeric' will display the entire year |
| month | enum | 'numeric', '2-digit', 'narrow', 'short', or 'long' | Controls the representation of the month. The 'numeric' value is the numeric representation of the month (April -> 4), '2-digit' is the two digit numeric representation (April -> 04), 'narrow is the two character representation of the month (April -> AP), 'short' is the three character representation of the month (April -> Apr), and 'long' is the full month name (April -> April) |
| day | enum | 'numeric' or '2-digit' | Controls the representation of the day. '2-digit' forces days to be displayed with two digits. | 

The default value for each date/time component property is undefined, but if all component properties are undefined, then year, month, and day are assumed to be "numeric."

###  INumberFormatOptions 

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

| Name | Type | Allowed Values | Description |
| ----------- | ----------- |----------- | ----------- |
| localeMatcher | enum | 'best fit' or 'lookup' | Allows one to set the algorithm used to match and find the locale. The "lookup" matcher follows the lookup algorithm specified in BCP 47. The "best fit" matcher lets the runtime provide a locale that's at least, but possibly more, suited for the request than the result of the lookup algorithm. |
| style | enum | 'decimal', 'percent', or 'currency' | The formatting style to use. Possible values are 'decimal' for plain number formatting, 'currency' for currency formatting, and 'percent' for percent formatting; the default is 'decimal'. |
| currency | string | 3 character [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) currency codes | The currency to use in currency formatting. There is no default value. If style is set to 'currency', the currency property must be provided. |
| minimumIntegerDigits | number | Any integer value between 1-21 | The minimum number of integer digits to use. The default is 1. |
| minimumFractionDigits | number | Any integer value between 0-20  | The minimum number of fraction digits to use. The default for number and percent formatting is 0, and the default for currency formatting is provided by [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) standards.  |
| maximumFractionDigits | number | Any integer value between 0-20 | The maximum number of fraction digits to use. |
| minimumSignificantDigits | number | Any integer value between 1-21  | The minimum number of significant digits to use. The default is 1.  |
| maximumSignificantDigits | number | Any integer value between 1-21  | The maximum number of significant digits to use. The default is 21.  |
