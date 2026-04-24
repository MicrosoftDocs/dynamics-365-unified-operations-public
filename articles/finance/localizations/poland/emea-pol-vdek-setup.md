---
title: Prepare for JPK-V7 reporting
description: Learn how to set up a VAT declaration with registers (also known as a JPK-V7, VDEK) for Poland in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/12/2026
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
---

# Prepare for JPK-V7 reporting

[!include [banner](../../includes/banner.md)]

This article explains how to set up a VAT declaration with registers (also known as a JPK-V7, VDEK) for Poland in Microsoft Dynamics 365 Finance.

The solution that supports JPK-V7 reporting is based on the [Electronic messaging](../../general-ledger/electronic-messaging.md) functionality. This functionality provides a flexible approach to setting up and supporting reporting processes.

Complete the following tasks to prepare Microsoft Dynamics 365 Finance to report a JPK-V7:

- [Import and set up Electronic reporting (ER) configurations](#configurations-vdek).
- [Set up application-specific parameters](#application-specific-parameters-vdek).
- [Import a package of data entities that includes a predefined electronic message setup](#import-data-entities-vdek).
- [Set up general ledger parameters](#general-ledger-parameters-vdek).
- [Save the executable class parameters for electronic messaging](#executable-class-parameters-vdek).
- [Set up security roles for electronic message processing](#security-roles-vdek).
- [Set up an office code for electronic message processing](#office-code-vdek).
- [Set up a "Sklad pliku" (file composition) for electronic message processing](#sklad-pliku)
- [Set up a "Wariant JPK_VAT" (variant JPK_VAT) for electronic message processing](#wariant-jpk-vat)
- [Set up a "Wersja schematu" (schema version) for electronic message processing](#wersja-schematu)
- [Set up sales tax codes and sales tax reporting codes](#sales-tax-reporting-codes-vdek).

## <a id="configurations-vdek"></a>Import and set up ER configurations

To prepare Finance for JPK-V7 reporting, import the following ER configurations.

| ER configuration name             | Type | Description |
|-----------------------------------|------|-------------|
| Standard Audit File (SAF-T)       | Model | The common ER model for Standard Audit Files. |
| Standard Audit File model mapping | Model mapping | The model mapping that defines data sources for Polish Standard Audit File (JPK) reports. |
| JPK-V7 XML format (PL)           | Format (exporting) | The XML format that provides the file that the Polish Ministry of Finance requires for periodic reporting. |
| JPK-V7 Excel format (PL)         | Format (exporting) | The Excel format for preview information that's reported in XML format. |

Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use the Issue search tool in [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2) to find the KB article by number.

For more information about importing ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

> [!NOTE]
> After you import all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **Standard Audit File model mapping** configuration on the **Configurations** page.
>
> :::image type="content" source="../media/default-mm.jpg" alt-text="Screenshot of Default for model mapping option set to Yes for the Standard audit file model mapping configuration.":::

## <a id="application-specific-parameters-vdek"></a>Set up application-specific parameters

Depending on the tax transaction data, you can define the values of some elements (markers) in the JPK-V7 report for reporting purposes. You need enough transactional data to define values for these elements. Therefore, set up enough sales tax codes, sales tax groups, and item sales tax groups to differentiate tax transactions for all the parameters (elements) that the JPK-V7 report introduces. The JPK-V7 format includes application-specific parameters (fields) that you can use to define values for these elements in the report.

The format includes the following lookup fields for setup.

| Name                          | Description | Impact |
|-------------------------------|-------------|--------|
| ImportSelector                | A designation that's related to input tax on imports of goods, including goods that are taxed in accordance with article 33a of the VAT Act | Use this lookup field to define the value of the **IMP** marker for purchase documents. |
| ProceduralMarkingsSelector    | Designations that are related to the procedures | Use this lookup field to define the values of the following markers for sales documents: **SW**, **EE**, **TP**, **TT-WNT**, **TT_D**, **I_42**, **I_63**, **B_SPV**, and **B_SPV_DOSTAWA**. |
| ServiceDeliverySelector       | An indicator that's related to the delivery and provision of services | Use this lookup field to define the values of all **GTU_\*** markers (from **GTU_1** through **GTU_13**) for sales documents. |
| DeclarationMarkersSelector    | Markers from the declaration part for tax transactions | Use this lookup field to define the **P_65** and **P_67** markers for the declaration part, based on the information in documents. |
| ZakupVAT_MarzaSelector        | The amount of purchases of goods and services from other taxpayers for the direct benefit of tourists, and the amount of second-hand goods, works of art, collectors' items, and antiques that are connected with sales that are taxed based on a margin, in accordance with article 120 of the VAT Act | Use this lookup field to define the **ZakupVAT_Marza** marker for purchase documents. |
| SalesDocumentTypesSelector    | A designation of the type of the sales document | Use this lookup field to define the **FP**, **RO**, and **WEW** sales document types. |
| SprzedazVAT_MarzaSelector     | The value of gross sales of supplies of goods and services that are taxed based on a margin, in accordance with articles 119 and 120 of the VAT Act | Use this lookup field to define the **SprzedazVAT_Marza** marker for sales documents. |
| PurchaseDocumentTypesSelector | A designation of the type of the purchase document | Use this lookup field to define the **MK**, **VAT_RR**, and **WEW** purchase document types. |

To set up application-specific parameters, follow these steps:

1. In the **Electronic reporting** workspace, select the **Reporting configurations** tile.
1. On the **Configurations** page, expand **Standard Audit File (SAF-T)**, and select **JPK-V7 XML format (PL)**.
1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.

:::image type="content" source="../media/setup-app-spec-params.jpg" alt-text="Screenshot of Setup button in the Application specific parameters group on the Configurations tab.":::

1. On the **Application specific parameters** page, select the latest version of the format that you want to define conditions for.
1. On the **Lookups** FastTab, select each lookup, and define appropriate conditions for it.
1. On the **Conditions** FastTab, define which tax codes or other available criteria must correspond to a specific lookup result. 

    If you define conditions on one line, the system generally applies them to a source tax transaction by using the **AND** operator. If conditions must be applied by using the **OR** operator, define them on separate lines. When a tax transaction from the reporting period meets a condition in the list, the related marker from the lookup result is reported for the related document. For more information about the setup of each lookup field, see the rest of this article.

1. When you finish setting up conditions, in the **State** field, select **Completed**, and then save the configuration.

:::image type="content" source="../media/complete-app-spec-params.jpg" alt-text="Screenshot of State field set to Completed.":::

You can easily export the setup of application-specific parameters from one version of a report and import it into another version. You can also export the setup from one report and import it into another report, provided that both reports have the same structure of lookup fields.

> [!NOTE]
> Enable the **Align ER application specific parameters while importing** feature in the **Feature management** workspace. This feature is available as of Finance version 10.0.24. When it's enabled, if the structure of application-specific parameters that you're importing differs from the structure of the corresponding data sources in the target ER format that is selected for import, the import can succeed. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md). 

### Import transactions (ImportSelector)

| Name           | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------------|------------|------------|------------------|------------------|
| ImportSelector | Import | Import | A designation that relates to input tax on imports of goods, including goods that are taxed in accordance with article 33a of the VAT Act | Oznaczenie dotyczące podatku naliczonego z tytułu importu towarów, w tym importu towarów rozliczanego zgodnie z art. 33a ustawy |

For this lookup field, you can set up the following master data sources:

- Sales tax codes
- Sales tax group
- Supplier account ID
- Supplier group

Define conditions from the current company's master data sources to determine which purchase document must be reported with a value of **1** in the **\<IMP\>** element under the **\<ZakupWiersz\>** tag.

The following table shows the lookup results for **ImportTransaction**.

| Name     | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------|------------|------------|------------------|------------------|
| Import   | Import | Import | A designation that relates to input tax on the import of goods, including goods that are taxed in accordance with article 33a of the VAT Act | Oznaczenie dotyczące podatku naliczonego z tytułu importu towarów, w tym importu towarów rozliczanego zgodnie z art. 33a ustawy |
| Inne     | Other | | | |

> [!NOTE]
> Add **Inne** (**Other**) as the last item in the list. It collects data from other cases. The **Line** value is the last value in your table. In the **Tax code** column in the **Inne** lookup result, select **\*Not blank\***.

### Procedural markings (ProceduralMarkingsSelector)

| Name                       | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------------------------|------------|------------|------------------|------------------|
| ProceduralMarkingsSelector | Procedural markings | Oznaczenia dotyczące procedur | Designations that are related to the procedures | Oznaczenia dotyczące procedur |

For this lookup field, the following master data sources are available to set up conditions:

- Sales tax codes
- Sales tax group
- Customer account ID
- Customer group
- Supplier account ID
- Supplier group

Conditions that you define in **Customer account ID** and **Customer group** apply independently from those that you define in **Supplier account ID** and **Supplier group**. Additionally, conditions that you define in **Supplier account ID** and **Supplier group** apply only to those transactions that you post in the scope reverse changes scenario. Therefore, when you set up conditions for **Supplier account ID** and **Supplier group**, specify **\*Blank\*** in both the **Customer account ID** column and the **Customer group** column of conditions.

This lookup field defines conditions that are based on the current company's master data sources. These conditions produce a mark of **1** for the corresponding element from the list of designations that are related to the procedures under the **\<SprzedazWiersz\>** tag. You can mark several designations for the same output VAT record. Therefore, if a company must report different designations, you must define separate conditions.

**Procedural markings** aren't required for documents of **RO** (Internal summary document) type (**\<TypDokumentu\>** tag under the **\<SprzedazWiersz\>** tag).

The following table shows the lookup results (designations) for **ProceduralMarkingsSelector**.

| Name           | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------------|------------|------------|------------------|------------------|
| SW <br> (*Only for reporting periods before July 1, 2021. Not applicable in JPK-V7(3).*) | Mail order sale | Sprzedaży wysyłkowej | Delivery as part of a mail order sale from the territory of the country/region, as referred to in article 23 of the VAT Act | Dostawa w ramach sprzedaży wysyłkowej z terytorium kraju, o której mowa w art. 23 ustawy |
| EE  (*Only for reporting periods before January 1, 2022. Not applicable in JPK-V7(3).*) | Telecommunications | Usług telekomunikacyjnych | The provision of telecommunications, broadcasting, and electronic services that are referred to in article 28k of the VAT Act | Świadczenie usług telekomunikacyjnych, nadawczych i elektronicznych, o których mowa w art. 28k ustawy |
| TP             | Links between the buyer and the supplier | Istniejące powiązania między nabywcą a dokonującym | Existing links between the buyer and the supplier of goods or the provider of services, as referred to in article 32, section 2, point 1 of the VAT Act. There's an exception for the case of supplies of goods and the provision of services where the relationship between the purchaser and the supplying service provider arises solely from a link with the State Treasury or local authorities or their associations. | Istniejące powiązania między nabywcą a dokonującym dostawy towarów lub usługodawcą, o których mowa w art. 32 ust. 2 pkt 1 ustawy. Z wyjątkiem sytuacji, gdy przypadku dostaw towarów oraz świadczenia usług, gdy powiązania między nabywcą a dokonującym dostawy towarów lub usługodawcą wynikają wyłącznie z powiązania ze Skarbem Państwa lub jednostkami samorządu terytorialnego lub ich związkami. |
| TT_WNT         | Intra-community acquisition as part of a three-party transaction | Wewnątrzwspólnotowe nabycie w ramach transakcji trójstronnej | The intra-community acquisition of goods by the second-most-taxable person as part of a three-party transaction, under the simplified procedure that is referred to in section XII, chapter 8 of the VAT Act | Wewnątrzwspólnotowe nabycie towarów dokonane przez drugiego w kolejności podatnika VAT w ramach transakcji trójstronnej w procedurze uproszczonej, o której mowa w dziale XII rozdziale 8 ustawy |
| TT_D           | Delivery of goods outside Poland as part of a three-party transaction | Dostawa towarów poza terytorium kraju w ramach transakcji trójstronnej | The supply of goods outside the territory of the country/region by the second VAT payer in a three-party transaction, under the simplified procedure that is referred to in section XII, chapter 8 of the VAT Act | Dostawa towarów poza terytorium kraju dokonana przez drugiego w kolejności podatnika VAT w ramach transakcji trójstronnej w procedurze uproszczonej, o której mowa w dziale XII rozdziale 8 ustawy |
| I_42           | Customs procedure 42 (import) | Procedury celnej 42 (import) | The intra-community supply of goods after they are imported under customs procedure 42 (import) | Wewnątrzwspólnotowa dostawa towarów następująca po imporcie tych towarów w ramach procedury celnej 42 (import) |
| I_63           | Customs procedure 63 (import) | Procedury celnej 63(import) | The intra-community supply of goods after they are imported under customs procedure 63 (import) | Wewnątrzwspólnotowa dostawa towarów następująca po imporcie tych towarów w ramach procedury celnej 63 (import) |
| B_SPV          | Transfer by article 8a, paragraph 1 of the VAT Act | Transfer z art. 8a ust. 1 ustawy | The transfer of a single-purpose voucher that a taxpayer acts on their own behalf, and that is taxed in accordance with article 8a, paragraph 1 of the VAT Act | Transfer bonu jednego przeznaczenia dokonany przez podatnika działającego we własnym imieniu, opodatkowany zgodnie z art. 8a ust. 1 ustawy |
| B_SPV_DOSTAWA  | Goods and services that the single-purpose voucher is related to (article 8a, paragraph 4 of the VAT Act) | Dostawa towarów oraz świadczenie usług (art. 8a ust. 4 ustawy) | The supply of goods and the provision of services, where the single-purpose voucher is related to a taxable person who issued the voucher in accordance with article 8a, paragraph 4 of the VAT Act | Dostawa towarów oraz świadczenie usług, których dotyczy bon jednego przeznaczenia na rzecz podatnika, który wyemitował bon zgodnie z art. 8a ust. 4 ustawy |
| B_MPV_PROWIZJA | Brokering services for multi-purpose vouchers | Usług pośrednictwa o transferu bonu różnego przeznaczenia | The provision of brokering and other services that are related to the transfer of multi-purpose vouchers that are taxed in accordance with article 8b, paragraph 2 of the VAT Act | Świadczenie usług pośrednictwa oraz innych usług dotyczących transferu bonu różnego przeznaczenia, opodatkowane zgodnie z art. 8b ust. 2 ustawy |
| WSTO_EE | Intra-community distance selling of goods | Wewnątrzwspólnotowej sprzedaży na odległość towarów | Intra-community distance sales of goods that, at the time when their dispatch or transport begins, are within the territory of the country/region, and the supply of telecommunications, broadcasting, and electronic services that are referred to in article 28k of the Act to non-taxable persons who are established or have their permanent address or place of residence in the territory of a Member State other than the territory of the country/region. | Wewnątrzwspólnotowej sprzedaży na odległość towarów, które w momencie rozpoczęcia ich wysyłki lub transportu znajdują się na terytorium kraju, oraz świadczenia usług telekomunikacyjnych, nadawczych i elektronicznych, o których mowa w art. 28k ustawy, na rzecz podmiotów niebędących podatnikami, posiadających siedzibę, stałe miejsce zamieszkania lub miejsce pobytu na terytorium państwa członkowskiego innym niż terytorium kraju |
| IED | Delivery of goods that are referred to in article 7a, paragraphs 1 and 2 of the Act | Dostawy towarów, o której mowa w art. 7a ust. 1 i 2 ustawy | The supply of goods that are referred to in article 7a, paragraphs 1 and 2 of the Act by a taxable person who facilitates that supply but doesn't benefit from the special scheme that is referred to in chapter 6a or 9 of section XII of the Act or in the corresponding regulations for which the place of supply is within the territory of the country/region. | Dostawy towarów, o której mowa w art. 7a ust. 1 i 2 ustawy, dokonanej przez podatnika ułatwiającego tę dostawę, który nie korzysta z procedury szczególnej, o której mowa w dziale XII w rozdziale 6a lub 9 ustawy lub w odpowiadających im regulacjach, dla której miejscem dostawy jest terytorium kraju |
| Inne           | Other | | | |

> [!NOTE]
> Add **Inne** (**Other**) as the last item in the list. It collects data from other cases. The **Line** value is the last value in your table. In the **Tax code** column in the **Inne** lookup result, select **\*Not blank\***.

### Goods and services supplying types (ServiceDeliverySelector)

| Name                    | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|-------------------------|------------|------------|------------------|------------------|
| ServiceDeliverySelector | Delivery and provision of services | Dostawy i świadczenia usług | An indicator that is related to the delivery and provision of services | Oznaczenie dotyczące dostawy i świadczenia usług |

For this lookup field, you can set up the following master data sources:

- Sales tax code
- Item sales tax group
- Customer account ID
- Customer group

This lookup field defines conditions that are based on the current company's master data sources. These conditions assign a mark of **1** for the corresponding element from the list of designations related to the supply of goods and services (**GTU_\*** markers) under the **\<SprzedazWiersz\>** tag. You can mark several designations for the same output VAT record. Therefore, if a company must report different designations, the company's master data must include separate conditions.

**GTU_\*** markers aren't required for documents of **WEW** (internal document) and **RO** (Internal summary document) type (**\<TypDokumentu\>** tag under the **\<SprzedazWiersz\>** tag).

The following table shows the lookup results (designations) for **ServiceDeliverySelector**.

| Name     | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------|------------|------------|------------------|------------------|
| GTU_01   | Supply of alcoholic beverages | Dostawa napojów alkoholowych | The supply of alcoholic beverages with an alcohol content above 1.2%, beer, and alcoholic beverages that are a mixture of beer and non-alcoholic beverages with an alcohol content exceeding 0.5% (CN codes from 2203 to 2208) | Dostawa napojów alkoholowych o zawartości alkoholu powyżej 1,2%, piwa oraz napojów alkoholowych będących mieszaniną piwa i napojów bezalkoholowych, w których zawartość alkoholu przekracza 0,5% (CN od 2203 do 2208) |
| GTU_02   | Goods that are referred to in article 103, item 5aa | Dostawa towarów, o których mowa w art. 103 ust. 5aa | The delivery of goods that are referred to in article 103, item 5aa of the VAT Act | Dostawa towarów, o których mowa w art. 103 ust. 5aa ustawy |
| GTU_03   | Supply of heating oil | Dostawa oleju opałowego | The supply of heating oils not included in GTU_02, lubricating oils, and other oils (CN codes from 2710 19 71 through 2710 19 83, and from 2710 19 87 through 2710 19 99, excluding  plastic greases  included in CN 2710 19 99), lubricating oils (CN code 2710 20 90) and lubricating preparations (CN 3403, excluding plastic lubricants under this heading) | Dostawa olejów opałowych nieujętych w GTU_02, olejów smarowych i pozostałych olejów (CN od 2710 19 71 do 2710 19 83 i CN od 2710 19 87 do 2710 19 99, z wyłączeniem smarów plastycznych zaliczonych do kodu CN 2710 19 99), olejów smarowych (CN 2710 20 90) oraz preparatów smarowych (CN 3403, z wyłączeniem smarów plastycznych objętych tą pozycją) |
| GTU_04   | Supply of tobacco products | Dostawa wyrobów tytoniowych | The supply of tobacco products, dried tobacco, liquid for electronic cigarettes, and innovative products that fall within the meaning of the provisions on excise duty | Dostawa wyrobów tytoniowych, suszu tytoniowego, płynu do papierosów elektronicznych i wyrobów nowatorskich, w rozumieniu przepisów o podatku akcyzowym |
| GTU_05   | Delivery of waste | Dostawa odpadów | The delivery of waste, but only waste that is specified in items 79 through 91 of annex 15 to the VAT Act | Dostawa odpadów - wyłącznie określonych w poz. 79-91 załącznika nr 15 do ustawy |
| GTU_06   | Supply of electronic devices | Dostawa urządzeń elektronicznych | The supply of electronic devices, and parts and materials for them, as exclusively specified in items 7,8, 59 through 63, 65, 66, 69, and 94 through 96 of annex 15 to the VAT Act, as well as stretch foil specified in pos. 9 of this annex | Dostawa urządzeń elektronicznych oraz części i materiałów do nich, wyłącznie określonych w poz. 7, 8, 59-63, 65, 66, 69 i 94-96 załącznika nr 15 do ustawy, a także folii typu stretch określonej w poz. 9 tego załącznika |
| GTU_07   | Supply of vehicles | Dostawa pojazdów | The supply of vehicles and parts that have only codes CN 8701 through 8708 | Dostawa pojazdów oraz części (CN od 8701 do 8708) |
| GTU_08   | Delivery of precious and base metals | Dostawa metali szlachetnych oraz nieszlachetnych | The delivery of precious and base metals, but only those metals that are specified in items 1 of annex 12 to the VAT Act, and in items 12 through 25, 33 through 40, 45, 46, 56, and 78 of annex 15 to the VAT Act | Dostawa metali szlachetnych oraz nieszlachetnych - wyłącznie określonych w poz. 1 załącznika nr 12 do ustawy oraz w poz. 12-25, 33-40, 45, 46, 56 i 78 załącznika nr 15 do ustawy |
| GTU_09   | Supply of medicines and medical devices | Dostawa leków oraz wyrobów medycznych | The supply of medicinal products, foodstuffs for specific nutritional uses, and medical devices that are only covered by the notification obligation that is referred to in article 37av, section 1 of the Act of September 6, 2001, for the Pharmaceutical Law (Journal of Laws of 2021, item 974 and 981, as amended) | Dostawa produktów leczniczych, środków spożywczych specjalnego przeznaczenia żywieniowego oraz wyrobów medycznych, wyłącznie objętych obowiązkiem zgłoszenia, o którym mowa w art. 37av ust. 1 ustawy z dnia 6 września 2001 r. - Prawo farmaceutyczne (Dz. U. z 2021 r. poz. 974 i 981, z późn. zm.) |
| GTU_10   | Supply of buildings | Dostawa budynków | The supply of buildings, structures, and land and their parts and shares in the ownership right, including the sale of the rights referred to in art. 7 item 1 of VAT Act  | Dostawa budynków, budowli i gruntów oraz ich części i udziałów w prawie własności, w tym również zbycia praw, o których mowa w art. 7 ust. 1 ustawy |
| GTU_11   | Provision of services – Gas emission | Świadczenie usług w - gazów cieplarnianych | The provision of services in the scope of transferring greenhouse gas emission allowances that are referred to in the Act of June 12, 2015, about the trading system for greenhouse gas emission allowances (Journal of Laws of 2021, items 332 and 1047) | Świadczenie usług w zakresie przenoszenia uprawnień do emisji gazów cieplarnianych, o których mowa w ustawie z dnia 12 czerwca 2015 r. o systemie handlu uprawnieniami do emisji gazów cieplarnianych (Dz. U. z 2021 r. poz. 332 i 1047) |
| GTU_12   | Provision of intangible services | Świadczenie usług o charakterze niematerialnym | The provision of intangible services, but only consulting, including legal, tax consultancy and management consultancy (PKWiU 62.02.1, 62.02.2, 66.19.91, 69.20.3, 70.22.11, 70.22.12, 70.22.13, 70.22.14, 70.22.15, 70.22.16, 70.22.3, 71.11.24, 71.11.42, 71.12.11, 71.12.31, 74.90.13, 74.90.15, 74.90.19), accounting and financial audit (PKWiU 69.20.1, 69.20.2), legal (PKWiU 69.1), management (PKWiU 62.03, 63.11.12, 66.11.19, 66.30, 68.32, 69.20.4, 70.22.17, 70.22.2, 90.02.19.1), head offices (PKWiU 70.1), marketing  or advertising (PKWiU 73.1), market and public opinion research (PKWiU 73.2), in the field of scientific research and development work (PKWiU 72) and in the field of out-of-school forms of education (PKWiU 85.5) | Świadczenie usług o charakterze niematerialnym - wyłącznie: doradczych, w tym doradztwa prawnego i podatkowego oraz doradztwa związanego z zarządzaniem (PKWiU 62.02.1, 62.02.2, 66.19.91, 69.20.3, 70.22.11, 70.22.12, 70.22.13, 70.22.14, 70.22.15, 70.22.16, 70.22.3, 71.11.24, 71.11.42, 71.12.11, 71.12.31, 74.90.13, 74.90.15, 74.90.19), w zakresie rachunkowości i audytu finansowego (PKWiU 69.20.1, 69.20.2), prawnych (PKWiU 69.1), zarządczych (PKWiU 62.03, 63.11.12, 66.11.19, 66.30, 68.32, 69.20.4, 70.22.17, 70.22.2, 90.02.19.1), firm centralnych (PKWiU 70.1), marketingowych lub reklamowych (PKWiU 73.1), badania rynku i opinii publicznej (PKWiU 73.2), w zakresie badań naukowych i prac rozwojowych (PKWiU 72) oraz w zakresie pozaszkolnych form edukacji (PKWiU 85.5) |
| GTU_13   | Transport services and storage management | Usług transportowych i gospodarki magazynowej | The provision of transport services and storage management, as described in PKWiU 49.4, 52.1 | Świadczenie usług transportowych i gospodarki magazynowej - PKWiU 49.4, 52.1 |
| Inne     | Other | | | |

> [!NOTE]
> Add **Inne** (**Other**) as the last item in the list. It collects data from other cases. The **Line** value is the last value in your table. In the **Tax code** column in the **Inne** lookup result, select **\*Not blank\***.

### Declaration markers (DeclarationMarkersSelector)

| Name                       | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------------------------|------------|------------|------------------|------------------|
| DeclarationMarkersSelector | Declaration markers | Markery deklaracji | Markers from the declaration part for tax transactions | Znaczniki z części deklaracji dla transakcji podatkowych |

For this lookup field, you can set up the following master data sources:

- Sales tax code
- Item sales tax group
- Sales tax group
- Customer account ID
- Customer group
- Vendor account ID
- Vendor group

This lookup field defines conditions that are based on the current company's master data sources. These conditions set a mark of **1** for the **P_65** and **P_67** elements of the **\<Deklaracja\>** part of the report when at least one document in the reporting period meets them.

The following table shows the lookup results for **DeclarationMarkersSelector**.

| Name     | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------|------------|------------|------------------|------------------|
| P_65     | Activities that are mentioned in article 122 | Czynności o których mowa w art. 122 ustawy | Activities that the taxpayer performed and that are mentioned in article 122 of the VAT Act. There's a tax exemption for the supply, import, and purchase of investment gold. | Podatnik wykonywał w okresie rozliczeniowym czynności, o których mowa w art. 122 ustawy |
| P_67     | Tax liability reduction | Obniżenie kwoty zobowiązania podatkowego | The tax liability reduction that the taxpayer benefits from and that is mentioned in article 108d of the VAT Act | Podatnik korzysta z obniżenia zobowiązania podatkowego, o którym mowa w art. 108d ustawy |
| Inne     | Other | | | |

> [!NOTE]
> Add **Inne** (**Other**) as the last item in the list. It collects data from other cases. The **Line** value is the last value in your table. In the **Tax code** column in the **Inne** lookup result, select **\*Not blank\***.

### Input VAT – Margin (ZakupVAT_MarzaSelector)

| Name                   | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|------------------------|------------|------------|------------------|------------------|
| ZakupVAT_MarzaSelector | Declaration markers | Podatek VAT – marża | The amount of purchases of goods and services from other taxpayers for the direct benefit of tourists, and the amount of second-hand goods, works of art, collectors' items, and antiques that are connected with sales that are taxed based on a margin, in accordance with article 120 of the VAT Act | Kwota nabycia towarów I usług nabytych od innych podatników dla bezpośredniej korzyści turysty, a także nabycia towarów używanych, dzieł sztuki, przedmiotów kolekcjonerskich i antyków związanych ze sprzedażą opodatkowaną na zasadzie marży zgodnie z art. 120 ustawy |

For this lookup field, you can set up the following master data sources:

- Sales tax code
- Item sales tax group

This lookup field lets you define different conditions to collect amounts that you must report in the **ZakupWiersz/ZakupVAT_Marza** element of the report. The system collects the gross amount of tax transactions that meet the specified criteria. If you define the conditions on one line of setup, the system applies them to a source tax transaction by using the **AND** operator. If conditions must be applied by using the **OR** operator, define them on separate lines. As soon as a tax transaction from the reporting period meets a condition in the list, the related gross amount is collected for reporting in the **ZakupWiersz/ZakupVAT_Marza** element of the report in relation to the document.

The following table shows the lookup results for **ZakupVAT_MarzaSelector**.

| Name           | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------------|------------|------------|------------------|------------------|
| ZakupVAT_Marza | Input VAT – Margin | Podatek VAT – marża | The amount of purchases of goods and services from other taxpayers for the direct benefit of tourists, and the amount of second-hand goods, works of art, collectors' items, and antiques that are connected with sales that are taxed based on a margin, in accordance with article 120 of the VAT Act | Kwota nabycia towarów i usług nabytych od innych podatników dla bezpośredniej korzyści turysty, a także nabycia towarów używanych, dzieł sztuki, przedmiotów kolekcjonerskich I antyków związanych ze sprzedażą opodatkowaną na zasadzie marży zgodnie z art. 120 ustawy |

> [!NOTE]
> Add **Inne** (**Other**) as the last item in the list. It collects data from other cases. The **Line** value is the last value in your table. In the **Tax code** column in the **Inne** lookup result, select **\*Not blank\***.

### Document types for sales (SalesDocumentTypesSelector)

| Name                       | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------------------------|------------|------------|------------------|------------------|
| SalesDocumentTypesSelector | Document type | Typ dokumentu | A designation of the type of the sales document | Oznaczenie dowodu sprzedaży |

For this lookup field, you can set up the following master data sources:

- Sales tax code
- Item sales tax group
- Sales tax group
- Customer account ID
- Customer group

The following table shows the lookup results for **SalesDocumentTypesSelector**.

| Name     | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------|------------|------------|------------------|------------------|
| FP       | Invoice that is issued to the receipt by article 109, section 3d | Faktura, o której mowa w art. 109 ust. 3d ustawy | The invoice that is issued to the receipt, as mentioned in article 109, section 3d of the VAT Act | Faktura, o której mowa w art. 109 ust. 3d ustawy |
| RO       | Internal summary document | Dokument zbiorczy wewnętrzny | An internal summary document that includes sales from cash registers | Dokument zbiorczy wewnętrzny zawierający sprzedaż z kas rejestrujących |
| WEW      | Internal document | Dokument wewnętrzny | Internal document | Dokument wewnętrzny |
| Inne     | Other | | | |

> [!NOTE]
> Add **Inne** (**Other**) as the last item in the list. It collects data from other cases. The **Line** value is the last value in your table. In the **Tax code** column in the **Inne** lookup result, select **\*Not blank\***.

For more information about how to report **RO** and **FP** document types for retail operations, see 
[Report RO and FP document types for retail operations](emea-pol-vdek-scenarios.md#report-ro-and-fp-document-types-for-retail-operations).

### Output VAT – Margin (SprzedazVAT_MarzaSelector)

| Name                      | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|---------------------------|------------|------------|------------------|------------------|
| SprzedazVAT_MarzaSelector | Output VAT – Margin | VAT należny – marża | The value of gross sales of supplies of goods and services that are taxed based on a margin, in accordance with articles 119 and 120 of the VAT Act | Wartość sprzedaży brutto dostawy towarów i świadczenia usług opodatkowanych na zasadach marży zgodnie z art. 119 i art. 120 ustawy |

For this lookup field, you can set up the following master data sources:

- Sales tax code
- Item sales tax group

This lookup field lets you define different conditions to report the **MR_T** or **MR_UZ** marker for sales documents in the **SprzedazWiersz** element of the report.

The following table shows the lookup results for **SprzedazVAT_MarzaSelector**.

| Name     | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------|------------|------------|------------------|------------------|
| MR_T     | Tourism services that are taxed based on a margin | Usług turystyki opodatkowane na zasadach marży | The provision of tourism services that are taxed based on a margin, in accordance with article 119 of the VAT Act | Świadczenie usług turystyki opodatkowane na zasadach marży zgodnie z art. 119 ustawy |
| MR_UZ    | Second-hand goods, art, and antiques | Towarów używanych, dzieł sztuki, antyków | The supply of second-hand goods, works of art, collectors' items, and antiques that are taxed based on a margin, in accordance with article 120 of the VAT Act | Dostawa towarów używanych, dzieł sztuki, przedmiotów kolekcjonerskich i antyków, opodatkowana na zasadach marży zgodnie z art. 120 ustawy |
| Inne     | Other | | | |

> [!NOTE]
> Add **Inne** (**Other**) as the last item in the list. It collects data from other cases. The **Line** value is the last value in your table. In the **Tax code** column in the **Inne** lookup result, select **\*Not blank\***.

### Document types for purchases (PurchaseDocumentTypesSelector)

| Name                          | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|-------------------------------|------------|------------|------------------|------------------|
| PurchaseDocumentTypesSelector | Purchase invoice type | Dokument Zakupu | A designation of the type of the purchase document | Oznaczenie dowodu zakupu |

For this lookup field, you can set up the following master data sources:

- Sales tax code
- Item sales tax group
- Sales tax group
- Supplier account ID
- Supplier group

This lookup field defines the combination of a sales tax code (**Tax code**), a vendor account ID (**Account ID**), and a vendor group (**PartyGroup**) from the current company's database that creates a document type under the **\<ZakupWiersz\>** tag. You can define several combinations.

The following table shows the lookup results for **PurchaseDocumentTypesSelector**.

| Name     | Label (En) | Label (Pl) | Description (En) | Description (Pl) |
|----------|------------|------------|------------------|------------------|
| MK       | Invoice that is referred to in article 21 | Faktura art. 21 | The invoice that a taxpayer issues who is a supplier of goods or services, and who chooses the cash accounting method that's specified in article 21 of the VAT Act | Faktura wystawiona przez podatnika będącego dostawcą lub usługodawcą, który wybrał metodę kasową rozliczeń określoną w art. 21 ustawy |
| VAT_RR   | Invoice that is referred to in article 116 | Faktura VAT RR, art.116 | The VAT invoice that is referred to in article 116 of the VAT Act | Faktura VAT RR, o której mowa w art. 116 ustawy |
| WEW      | Internal document | Dokument wewnętrzny | Internal document | Dokument wewnętrzny |
| Inne     | Other | | | |

> [!NOTE]
> Add **Inne** (**Other**) as the last item in the list. It collects data from other cases. The **Line** value is the last value in your table. In the **Tax code** column in the **Inne** lookup result, select **\*Not blank\***.

## <a id="import-data-entities-vdek"></a>Import a package of data entities that includes a predefined electronic message setup

The process of setting up the electronic messaging functionality for JPK-V7 reporting has many steps. Because the names of some predefined entities are used in the ER configurations, it's important that you use a set of predefined values that are delivered in a package of data entities for the related tables.

To import a package of data entities that includes a predefined electronic message setup, follow these steps:

1. In [LCS](https://lcs.dynamics.com/v2), in the Shared asset library, select the **Data package** asset type. Then find **PL JPK_V7 EM setup.zip** in the list of data package files, and download it to your computer.
1. After you download the **PL JPK_V7 EM setup.zip** file, open Finance, select the company that you'll generate the JPK-V7 report from, and then go to **Workspaces** \> **Data management**.

    Before you import setup data from the package of data entities, make sure that the data entities in your application are refreshed and synced.

1. In the **Data management** workspace, go to **Framework parameters** \> **Entity settings**, and then select **Refresh entity list**. Wait for confirmation that the refresh is complete. For more information about how to refresh the entity list, see [Entity list refresh](../../../fin-ops-core/dev-itpro/data-entities/data-entities.md#entity-list-refresh).
1. Validate that the source data and target data are correctly mapped.
1. Before you use the data entities for the first time to import the data, sync the mapping of source data and target data. In the list for the package, select a data entity, and then, on the Action Pane, select **Modify target mapping**. Then, above the grid for the package, select **Generate mapping** to create a mapping from scratch.
1. Save the mapping.
1. Repeat steps 3 through 6 for each data entity in the package.

For more information about Data management, see [Data management](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

Now, import data from the **PL JPK_V7 EM setup.zip** file into the selected company.

To import the data, follow these steps:

1. In the **Data management** workspace, select **Import**, set the **Source data format** field to **Package**, and create a new importing project by selecting **New** on the Action Pane.
1. On the **Select entities** FastTab, select **Add file**.
1. Select **Upload and add**, select the **PL JPK_V7 EM setup.zip** file on your computer, and upload it.
1. When entities from the package are listed in the grid, select **Close**.
1. On the Action Pane, select **Import** to start to import data from the data entities.

:::image type="content" source="../media/import-data-entities.jpg" alt-text="Screenshot of PL JPK_V7 EM setup page.":::

You receive a notification in **Messages**, or you can manually refresh the page to view the progress of the data import. When the import process is completed, the **Execution summary** page shows the results.

:::image type="content" source="../media/data-entities-imported.jpg" alt-text="Screenshot of Execution summary page.":::

> [!IMPORTANT]
> Some records in the data entities in the package include a link to ER configurations. Therefore, be sure to import ER configurations into Finance before you start to import the data entities package.

> [!NOTE]
> As of version 7 of the **PL JPK_V7 EM setup.zip** file, the package of data entities includes setup for two types of electronic messaging processing:
>
> - **JPK-V7M** – Monthly JPK-V7M declaration (Miesięczny Jednolity Plik Kontrolny VAT z deklaracją V7M)
> - **JPK-V7K** – Quarterly JPK-V7K declaration (Kwartalny Jednolity Plik Kontrolny VAT z deklaracją V7K)

## <a id="general-ledger-parameters-vdek"></a>Set up general ledger parameters

To use the electronic messaging functionality, you need to define related number sequences.

To set up general ledger parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **General ledger parameters**.
1. On the **Number sequences** tab, set up two number sequences:

    - Message
    - Message item

## <a id="executable-class-parameters-vdek"></a>Save the executable class parameters for electronic messaging

Both the JPK-V7 processing and the JPK-V7K processing use the **EMGenerateJPKVDEKReportController_PL** executable class to initiate data collection for the report data provider and further report generation. Before you use this class for the first time, save its parameters.

To save the executable class parameters for electronic messaging, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Electronic messaging** \> **Executable class settings**.
1. Select the **Wygenerowanie JPK-V7M** (if your company reports JPK-V7 monthly) or **Wygenerowanie JPK-V7K** (if your company reports JPK-V7 quarterly) executable class (which is set to call **EMGenerateJPKVDEKReportController_PL**), and then, on the Action Pane, select **Parameters**. In the **Generate Polish JPK_VDEK report** dialog box, select **OK**.

In the dialog box for the executable class, the **Retail-specific sales marking** group of parameters is used for retail-specific scenarios. For more information about how to report **RO** and **FP** document types for retail operations, see [Report RO and FP document types for retail operations](emea-pol-vdek-scenarios.md#report-ro-and-fp-document-types-for-retail-operations). A **Retail-specific sales marking** group of parameters is available only in legal entities that have a primary address in Poland.

The dialog box for the executable class includes the **Consider VAT report date codes** parameter. Use this parameter to collect VAT transactions on the report, based on rules that you define in VAT report date codes. This parameter doesn't affect retail-specific transactions that are reported as the **FP** document type. For more information about the VAT report date codes feature, see [Set up VAT report date codes](/dynamicsax-2012/appuser-itpro/pol-set-up-vat-report-date-codes). The **Consider VAT report date codes** parameter is available only in legal entities that have a primary address in Poland.

The dialog box for the executable class includes the **Settlement period** parameter. Use this parameter with the [**Multiple VAT registration numbers**](../global/emea-multiple-vat-registration-numbers.md) feature to collect VAT transactions in specific sales tax settlement periods. 

Use the **Schema version** parameter to specify which additional field contains the version of the schema of JPK-V7 that must be reported. Select **Wersja schematu** as the value for this field.

The dialog box for the executable class includes the **Report in accounting currency** parameter. By default, the amounts on the report are represented in the sales tax code currency. Use this parameter to report amounts in JPK-V7 in the accounting currency.

## <a id="security-roles-vdek"></a>Set up security roles for electronic message processing

Different groups of users might require access to the JPK-V7M or JPK-V7K processing. You can limit access to the processing, based on security groups that you define in the system.

To limit access to the JPK-V7M or JPK-V7K processing, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.
1. Select the **JPK-V7M** (if your company reports JPK-V7 monthly) or **JPK-V7K** (if your company reports JPK-V7 quarterly) processing, and then, on the **Security roles** FastTab, add the security groups that must work with it. If you don't define a security group for the processing, only a system admin can see it on the **Electronic messages** page.

## <a id="office-code-vdek"></a>Set up an office code for electronic message processing

To set up an office code for electronic message processing, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.
1. Select the **JPK-V7M** (if your company reports JPK-V7 monthly) or **JPK-V7K** (if your company reports JPK-V7 quarterly) processing.
1. On the **Additional field** FastTab, select the **KodUrzedu** additional field, and then, in the **Default value** field, specify the office code that should be reported in the **\<KodUrzedu\>** element of the report.

## <a id="sklad-pliku"></a>Set up a "Sklad pliku" (file composition) for electronic message processing

Both the **JPK-V7M** electronic message processing and the **JPK-V7K** electronic message processing contain the **Sklad pliku** additional field. Use this additional field to define the composition of the XML file that you generate:

- **Pelny plik XML** – For the full XML file. The file contains the complete set of elements: `Naglówek`, `Podmiot1`, `Deklaracja`, and `Ewidencja`.
- **Tylko Ewidencja** – For the **Ewidencja** node only. The file contains the following elements: `Naglówek`, `Podmiot1`, and `Ewidencja`.

The default value for the **Sklad pliku** additional field in the **JPK-V7M** and **JPK-V7K** electronic message processing is **Pelny plik XML**.

## <a id="wariant-jpk-vat"></a>Set up a "Wariant JPK_VAT" (variant JPK_VAT) for electronic message processing

Both the **JPK-V7M** electronic message processing and the **JPK-V7K** electronic message processing contain the **Wariant JPK_VAT** additional field. Use this additional field to define the variant of the XSD schema of the XML file that you generate.

| Wariant JPK_VAT | Description (En) | Description (Pl) | Default value in EM processing |
|-----------------|------------------|------------------|--------------------------------|
| Miesięczny (Monthly) | JPK_V7M - company reporting JPK-V7 monthly | JPK_V7M - dla podatników, którzy rozliczają się miesięcznie | Default for JPK-V7M |
| Kwartalny (Quarterly) | JPK_V7M - company reporting JPK-V7 quarterly | JPK_V7K - dla podatników, którzy rozliczają się kwartalnie | Default for JPK-V7K |

## <a id="wersja-schematu"></a>Set up a "Wersja schematu" (schema version) for electronic message processing

Both the **JPK-V7M** electronic message processing and the **JPK-V7K** electronic message processing contain the **Wersja schematu** additional field. Use this field to define the version of the XSD schema to apply to the XML file that you generate:

- **1** – JPK-V7(1) – Effective from October 1, 2020 (before January 1, 2022).
- **2** – JPK-V7(2) – Effective from January 1, 2022 (before February 1, 2026).
- **3** – JPK-V7(3) – Effective from February 1, 2026.

The default value for the **Wersja schematu** additional field in the **JPK-V7M** and **JPK-V7K** electronic message processing is **3**.

## <a id="sales-tax-reporting-codes-vdek"></a>Set up sales tax codes and sales tax reporting codes

The [sales tax reporting code](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md) is an integer value. Number sales tax reporting codes according to your company's rules. However, vary the codes by tax direction. For example, use a five-digit code. Then, for all outgoing transactions that the first part of the VAT scheme reflects, set the codes so that they're less than or equal to 19999. For all incoming transactions that the second part of the VAT scheme reflects, set the codes so that they're more than or equal to 20000. By using this approach, you simplify the setup for reports and for data export that is based on tax transactions that the system aggregates by sales tax reporting codes. The following example shows how you can use sales tax reporting codes to generate a SAF VAT sales and purchase register. For this example, sales tax reporting codes are in the format *ABBCC*. This format consists of the following parts:

- **A** – The transaction direction. The value is **1** for outgoing transactions, **2** for incoming transactions, and **3** for corrections.
- **BB** – The tax code. The numbering is sequential among all tax codes.
- **CC** – The transaction type number in a tax code. See the following table.

    | Transaction type                  | Transaction type number     |
    |-----------------------------------|-----------------------------|
    | Taxable Sales                     | 01                          |
    | Tax-free sales                    | 02                          |
    | Sales tax payable                 | 03                          |
    | Taxable sales credit note         | 04                          |
    | Tax exempt sales credit note      | 05                          |
    | Sales tax on sales credit note    | 06                          |
    | Taxable purchases                 | 07                          |
    | Tax-free purchase                 | 08                          |
    | Sales tax receivable              | 09                          |
    | Taxable import                    | 10                          |
    | Offset taxable import             | 11                          |
    | Use tax                           | 12                          |
    | Offset use tax                    | 13                          |
    | Taxable purchase credit note      | 14                          |
    | Tax exempt purchase credit note   | 15                          |
    | Sales tax on purchase credit note | 16                          |
    | Taxable import credit note        | 17                          |
    | Offset taxable import credit note | 18                          |

The following table shows the sales tax codes and sales tax reporting codes for this example.

| Sales tax code | Sales tax reporting code | Description | Tag name in JPK-V7M | Sign in JPK-V7M |
|---|---|---|---|---|
| ExportCust | 10101 | Taxable sales | K_11 | - |
| ExportCust | 10102 | Tax-free sale | K_11 | - |
| ExportCust | 10104 | Taxable sales credit note | K_11 | - |
| ExportCust | 10105 | Tax exempt sales credit note | K_11 | - |
| Art100_1.4 | 10201 | Taxable sales | K_11, K_12 | - |
| Art100_1.4 | 10204 | Taxable sales credit note | K_11, K_12 | - |
| VAT22_23 | 10301 | Taxable sales | K_19 | - |
| VAT22_23 | 10302 | Tax-free sale | K_10 | - |
| VAT22_23 | 10303 | Sales tax payable | K_20 | - |
| VAT22_23 | 10304 | Taxable sales credit note | K_19 | - |
| VAT22_23 | 10306 | Sales tax on sales credit note | K_20 | - |
| VAT7_8 | 10401 | Taxable sales | K_17 | - |
| VAT7_8 | 10402 | Tax-free sale | K_10 | - |
| VAT7_8 | 10403 | Sales tax payable | K_18 | - |
| VAT7_8 | 10404 | Taxable sales credit note | K_17 | - |
| VAT7_8 | 10406 | Sales tax on sales credit note | K_18 | - |
| VAT5 | 10501 | Taxable sales | K_15 | - |
| VAT5 | 10502 | Tax-free sale | K_10 | - |
| VAT5 | 10503 | Sales tax payable | K_16 | - |
| VAT5 | 10504 | Taxable sales credit note | K_15 | - |
| VAT5 | 10506 | Sales tax on sales credit note | K_16 | - |
| VAT0 | 10601 | Taxable sales | K_13 | - |
| VAT0 | 10602 | Tax-free sale | K_10 | - |
| VAT0 | 10604 | Taxable sales credit note | K_13 | - |
| ART129 | 10701 | Taxable sales | K_13, K_14 | - |
| ART129 | 10702 | Tax-free sale | K_13, K_14 | - |
| ART129 | 10704 | Taxable sales credit note | K_13, K_14 | - |
| ART129 | 10705 | Tax exempt sales credit note | K_13, K_14 | - |
| VAT17_1.5 | 11901 | Taxable sales | K_31 | - |
| VAT17_1.5 | 11903 | Sales tax payable | K_32 | - |
| VAT17_1.5 | 11904 | Taxable sales credit note | K_31 | - |
| VAT17_1.5 | 11906 | Sales tax on sales credit note | K_32 | - |
| IntraEUGoods | 10801 | Tax-free sale | K_21 | - |
| IntraEUGoods | 10810 | Taxable import | K_23 | + |
| IntraEUGoods | 10811 | Taxable sales (Reverse charge) | K_23 | - |
| IntraEUGoods | 10812 | Use tax | K_24 | + |
| ExportOfGoods | 10901 | Tax-free sale | K_22 | - |
| ExportOfGoods | 10905 | Tax exempt sales credit note | K_22 | - |
| BeveragePackagingDeposit *<br>With these Reporting codes the general tax base Reporting codes are used:<br>- 23%: 10301, 10304(K_19)<br>- 5%: 10501, 10504(K_15)<br>These Reporting codes also contribute in:<br>- 23%: 10303, 10306(K_20)<br>- 5%: 10503, 10506(K_16)<br>As a result, the tax base reported in K_19/K_15 respectively and the tax amount reported in K_20/K_16 AND in the K_360.* | 12003 | Sales tax payable (5%) | K_360 | - |
| BeveragePackagingDeposit | 12006 | Sales tax on sales credit note (5%) | K_360 | - |
| BeveragePackagingDeposit | 12103 | Sales tax payable (23%) | K_360 | - |
| BeveragePackagingDeposit | 12106 | Sales tax on sales credit note (23%) | K_360 | - |
| ImportOfGoodsART33 | 20207 | Taxable import | K_45 | + |
| ImportOfGoodsART33 | 11010 | Offset Taxable import | K_25 | - |
| ImportOfGoodsART33 | 20209 | Use tax | K_46 | + |
| ImportOfGoodsART33 | 11012 | Offset use tax | K_26 | - |
| ImportOfServices | 20207 | Taxable import | K_45 | + |
| ImportOfServices | 11110 | Offset Taxable import | K_27 | - |
| ImportOfServices | 11117 | Taxable sales (Reverse charge) | K_27 | + |
| ImportOfServices | 20209 | Use tax | K_46 | + |
| ImportOfServices | 11112 | Offset use tax | K_28 | - |
| ImportART28 | 20207 | Taxable import | K_45 | + |
| ImportART28 | 11210 | Offset Taxable import | K_29 | - |
| ImportART28 | 11119 | Taxable sales (Reverse charge) | K_29 | + |
| ImportART28 | 20209 | Use tax | K_46 | + |
| ImportART28 | 11212 | Offset use tax | K_30 | - |
| FixedAssetPurch | 20107 | Taxable purchases | K_40 | + |
| FixedAssetPurch | 20109 | Sales tax receivable | K_41 | + |
| FixedAssetPurch | 20115 | Taxable purchase credit note | K_40 | + |
| FixedAssetPurch | 20116 | Sales tax on purchase credit note | K_44 | + |
| GoodServPurch | 20207 | Taxable purchases | K_42 | + |
| GoodServPurch | 20209 | Sales tax receivable | K_43 | + |
| GoodServPurch | 20215 | Taxable purchase credit note | K_42 | + |
| GoodServPurch | 20216 | Sales tax on purchase credit note | K_44 | + |
| CorrATR89b1 | 30101 | Sales tax payable | K_46 | + |
| CorrATR89b1 | 30102 | Sales tax receivable | K_47 | + |
| CorrATR89b4 | 30201 | Sales tax payable | K_47 | + |
| CorrATR89b4 | 30202 | Sales tax receivable | K_47 | + |

For invoices that aren't paid within 150 days, you can apply an [**Overdue debt VAT**](emea-pol-sales-tax-reports.md#allowance-for-bad-debts) periodic task. In this case, use the same reporting codes that are used for K_41 and K_43. The system automatically interprets transactions for reporting in K_46 (Overdue invoice) and K_47 (Paid overdue invoice).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
