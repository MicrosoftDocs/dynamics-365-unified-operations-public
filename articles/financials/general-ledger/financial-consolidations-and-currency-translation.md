# Financial consolidations and currency translation
This document takes you through the approach that both Microsoft Dynamics 365 for Finance and Operations and Financial reporting use for consolidations. It describes scenarios that involve multi-company reporting, aggregation, elimination, and minority interest. It also explains how to handle special situations, such as scenarios where legal entities have different fiscal periods or different charts of accounts.
This document was written for users and functional consultants, and it assumes that readers have a general understanding of Finance and Operations and Financial reporting. Basic setup isn’t covered.
Note: The term legal entity is used in Finance and Operations, and the term company is used in Financial reporting. Both these terms are used in this document. However, for the purposes of this document, their meanings are the same.
# Audience
This document is intended for finance and accounting users and application consultants who want to use Finance and Reporting and Financial reporting to consolidate multi-company and multi-currency data.
# Approach
Finance and Operations uses a separate legal entity to process a consolidation. It enables single-instance consolidation but provides an option to bring in data from other sources. The consolidation process must be run every time that changes are made in the source legal entities.
Financial reporting can consolidate multiple companies during report generation. Although the data is stored in a data mart, is versioned, and can be exported, every source company is the owner and container of the data. The report can be run at any time, even every minute (for example). It provides many additional benefits, such as the ability to drill down to all companies and dimensions.
The following illustrations show the steps for doing consolidation in Finance and Operations and Financial reporting.
Users can use Consolidation Online, Financial reporting, or a combination. Their choice depends on the needs of their company and the preferences of their auditors.
### Consolidate Online in Finance and Operations
 
### Consolidation by using Financial reporting
 
# Consolidations
The **Consolidations** module includes options for consolidating multiple legal entities during the consolidation process, and for importing or exporting a company’s balance. You can also set up eliminations and post elimination journals.
# Benefits of using Consolidate online
Customers who use the Consolidations module will gain various benefits:
- **Depth of data** – You can create consolidated reports that bring together actual and budget data at both the account level and the dimension level.
- **Dynamic consolidations** – Consolidations can be processed multiple times.
- **Audit capabilities** – Dimensions and accounts are maintained for analysis and audit, and balances are created by date.
- **Currency translation** – You can set up the account ranges and rates to translate from the accounting currency of the source company to the accounting currency of the consolidation company.
- **Process eliminations in a consolidated or elimination company** – You can process and post eliminations as a single process during consolidation. Alternatively, you can run a proposal separately.
# Supported consolidation scenarios
Here are some of the consolidation scenarios that Consolidate online supports:
- Single-level consolidations across legal entities
- Consolidations that involve eliminations
- Minority interest (For this scenario, manual calculation and entry in the company must be used.)
- Multiple charts of accounts across legal entities
- Different fiscal calendars across multiple legal entities
- Consolidations that involve multiple reporting currencies
# Legal entity setup
Before you process a consolidation, you must set up the legal entity. You can run consolidation as many times as you require, and all data will be translated from the source company’s accounting currency to the currency that is defined for the consolidation company. Therefore, for the following organizational structure, if you must translate all North American companies first to US dollars (USD) and then to euros (EUR), the currency of the parent company, you must have at least two consolidation companies.
 
In the preceding organizational structure, you must have a legal entity for the North American consolidation, because consolidations always consolidate from the accounting currency of the source company to the currency of the consolidation company. In the example, if all companies are included in a single consolidation, the Mexican subsidiary will be translated from Mexican pesos (MXN) to EUR, not from MXN to USD to EUR.
When you create the legal entity, you can specify whether the company is used for both the consolidation process and the elimination process, or for just one of those processes. In the following illustration, the company is used for both processes. Note that you can’t post daily journals in a consolidation company, but you can post them in an elimination company. Therefore, you might want to have a separate elimination company.
 
# Main accounts and consolidation account groups
One of the choices that you must make is how you want to consolidate your chart of accounts. During the consolidation process, you have three options for consolidating main accounts.
The first option is to use the main accounts from the source companies. In this case, every account from all companies will be consolidated. For example, if Cash is account 100000 in the USMF company and account 1100 in the DEMF company, the consolidation company will include both accounts, each of which will have its respective balance.
The second option is to specify a default consolidation account on the **Main accounts** page. The account will then be mapped to the consolidation account. This option can be helpful when you have different charts of accounts or must map to a chart that is defined by the headquarters.
 
The third option is to use consolidation account groups. You can define as many consolidation account groups as you require. Then, on the **Additional consolidation accounts** page, you just map the main account from the chart of accounts to the account that you require for that group.
 
# Consolidate online
After you’ve completed your setup, you enter the details of the consolidation on the **Consolidate [Online]** page. When you’ve finished, you can click **OK** or **Batch** to process the consolidation.
## Criteria
On the **Criteria** tab of the **Consolidate [Online]** page, you define the accounts, periods, and type of data that is being consolidated.
 
Here is an explanation of the various fields on this tab:
- **Description** – Enter a precise description for the period that you’re consolidating.
- **Main account** – Use the fields in this section to define the main accounts that will be processed.
- **From** and **To** – Specify a range of accounts to process. If you leave these fields blank, all accounts from all companies will be moved to the consolidation company. Therefore, if you’re consolidating four companies, and each company has a different chart of accounts, all accounts from all four companies will be created in the consolidation company.
- **Use consolidation account** – If you set this option to **Yes**, the **Select consolidation account from** field becomes available. In this field, select whether you want to consolidate all accounts to the consolidation account that is set on the **Main accounts** page, or whether you want to select the account from one of the consolidation account groups.
- **Consolidation account group** – Select the group to use for the main account mapping for the consolidation.
- **Consolidation period** – Use the fields in this section to define the consolidation period.
- **From** and **To** – Specify a range of dates for the consolidation. If you leave these fields blank, the consolidation will be processed for all periods that are defined in the ledger calendar for the company.
- **Include actual amounts** – Set this option to **Yes** to consolidate your actual data.
- **Include budget amounts** – Set this option to **Yes** to consolidate data from the budget register.
- **Rebuild balances during consolidation** – We don’t recommend to that you set this option to **Yes**. Instead, process it as a separate batch job.
- **Budget models** – If you’ve selected to consolidate budget data, use the fields in this section to define the budget models.
- **From** and **To** – Specify the range of models to use.
- **Budget rate type** – Select the type of budget rate to use for currency translation of budget
data.
# Financial dimensions
On the **Financial dimension** tab, you define the dimensions that should be included in the consolidation company. To select a dimension, set the **Specification** field to **Dimension**, and then define the order of the dimension in the consolidation company.
 
Regardless of the order that you define, Main account will always be the first segment.
# Legal entities
On the **Legal entities** tab, you define the companies that should be included in the consolidation company. You also define the ownership percentage of those companies. If you specify less than 100-percent ownership, the specified percentage will be rolled up to the consolidation company. For any translation differences, the **Account type for conversion differences** field is used to select the main account from the setup on the **Accounts for automatic transactions** page.
 
 
# Elimination
On the **Elimination** tab, you have three options for processing eliminations:
- Select the elimination rule, and then, in the **Proposal options** field, select **Proposal only**. This option will process the elimination during the consolidation process, but it won’t post everything in one step. You can post the journal later.
- Select the elimination rule, and then, in the **Proposal options** field, select **Post only**. This option will process the elimination during the consolidation process and post everything in one step.
- Run an elimination proposal separately from the consolidation process by using the elimination journal.
 
For more information about eliminations see the Elimination rules section later in this document.
# Currency translation
On the Currency translation tab, you define the legal entity, account and exchange rate type, and rate.
Three options are available in the **Apply exchange rate from** field:
- **Consolidation date** – The date of the consolidation will be used to get the exchange rate. This rate is equivalent to the spot or month-end rate. You will see a preview of the rate, but you can’t edit it.
- **Transaction date** – The date of each transaction will be used to select an exchange rate. This option is most often used for fixed assets and is often referred to as a historical rate. You can’t see a preview of the rate, because there will be many rates for the various transactions in the account range.
- **User defined rate** – After you select this option, you can enter the exchange rate that you want. This option can be useful for average exchange rates or if you’re consolidating against a fixed exchange rate.
 
# Managing consolidation transactions
To view the results of the consolidation, you have multiple options:
- Generate a financial report against the consolidation company.
- Review the **Trial balance** list page in the consolidation company.
- In the list of consolidation transactions on the **Consolidations** page, view the balances that are created by date for every source company for every period.
 _____
To run the consolidation again, you can just process the consolidation. Alternatively, you can first click **Remove the transactions** on the **Consolidations** page.
# Consolidate with import
The Consolidate with import functionality works like the Consolidate online functionality. When you select the legal entities, you will browse out to the source file that contains the data.
# Export company balances
The Export company balances functionality also works like the Consolidate online functionality. When you select the legal entities, you will set a file path for the output.
# Elimination rules
To eliminate intercompany transactions, you can create an elimination rule. Alternatively, you can do a manual elimination entry in a company that is designated an elimination company. If you create an elimination rule, you have two options for the elimination method: **Net change** and **Fixed**.
# Set up elimination rules
When you set up elimination rules in Finance and Operations, you can create a financial dimension that is used specifically for elimination. Most customers name this financial dimension **Trading Partner** or something similar. If you decide not to use a financial dimension, make sure that you have main accounts that are used only for intercompany transactions.
You can find the setup for eliminations in the **Setup** area of the **Consolidations** module. After you enter a description for the rule, you must select the company that the elimination journal will be posted to. The company that you select should have **Use for financial elimination process** selected in the legal entity setup.
You can set the date when the elimination rule becomes effective and the date when it expires, as you require. If you want the elimination rule to be available in the elimination proposal process, you must set the **Active** option to **Yes**. Select a journal name that has a type of **Elimination**.
 
After you’ve defined the basic properties, click **Lines** to define the actual processing rules. There are two options for eliminations: you can eliminate the net change amount or define a fixed amount.
Select the source accounts. You can use an asterisk (*) as a wildcard character. For example, **1*** selects all accounts that start with a **1** as a source of data for the allocation.
After you’ve selected the source accounts, use the **Account specification** field to specify the account that is used from the destination company. Select **Source** to use the same main account that is defined in the source account. If you select **User defined**, you must specify a destination account.
 
The Dimension specification field works like the Account specification field. Select Source, to use the same dimensions in the destination company and the source company. If you select User defined, you must specify the dimensions in the destination company by clicking Destination dimensions. Then select source dimensions and the financial dimensions and values that are used as a source of the elimination.
Process elimination transactions
There are two ways to process elimination transactions. The transaction can be processed during the Consolidate online process, or you can create an elimination journal and run the elimination proposal process. This section focuses on the second option.
In a company that is defined as an elimination company, click Elimination journal in the Consolidations module. After you’ve selected the journal name, click Lines. To run the proposal, click Proposals > Elimination proposal.
Select the company that is the source of the consolidated data, and then select the rule to process. Enter start and end dates to define the date range that is searched for elimination amounts. The GL posting date field specifies the date that is used to post the journal to the general ledger. After you click OK, you can review the amounts and post the journal.
Note: The elimination journal shows the amounts for account values in the currency of their originating transactions, not in the accounting currency. When you review the amounts in the elimination journal, you might find this behavior confusing.
For more information and examples, see Elimination rules.
Currency revaluation in a consolidation company
When you consolidate data from one accounting currency to another, you must still run currency revaluation if exchange rates change, so that your account balances are correctly revalued. When you originally consolidate the data, use the Currency translation tab to select the initial exchange rates that should be used for translation during the consolidation process. After a new exchange rate is entered (for example, in the next month), you must revalue the account balances. The unrealized gains or losses are then updated based on the new exchange rate and date.
For more information about currency revaluation in a consolidation company see Currency revaluation in a consolidation company.
For more information about how currency revaluation works in the General ledger module, see Foreign currency revaluation for General ledger.
Additional information
●	All posting layers are consolidated when the consolidation is processed.
●	Elimination journals can be posted only to the Current layer.
●	Only operating balances are consolidated. Therefore, to see opening balances, you must still run a year-end close in the consolidation company.
●	You can post a daily journal in an elimination company, but not in a consolidation company.
Benefits of using Financial reporting for financial consolidations and currency translation, or to complement Consolidate online for consolidated reporting
Customers who use Financial reporting for financial consolidations and currency translation, or to complement Consolidate online for consolidated reporting, will gain various benefits:
●	Depth of data – You can create consolidated reports that bring together actual and budget data at both the account level and the dimension level. For Finance and Operations, this data includes data from both budge control and Bbudget planning.
●	Dynamic consolidations – Consolidations can be done at any time and at any level in the organizational hierarchy.
●	Complete audit capabilities – All dimensions, accounts, and transactional detail are maintained for analysis and audit. In addition, Financial reporting provides full drill-back to the original transaction in any of the legal entities that are consolidated.
●	Streamlined currency translation – After minimal setup in Finance and Operations, you can translate any Financial reporting report into any reporting currency that has been set up. In addition, you can set up an unlimited number of reporting currencies.
●	Post eliminations at the source – You can create and print an elimination report to verify elimination transactions. You can then post any new eliminations as standard intercompany transactions. You can also use an elimination legal entity for any transaction that you don’t want in your legal entities.
Supported consolidation scenarios
Here are some of the consolidation scenarios that Financial reporting supports:
●	Single-level and multilevel consolidations across legal entities
●	Consolidations that use organization structures that are created from legal entities
●	Consolidations that involve eliminations
●	Minority interest
●	Multiple charts of accounts across legal entities
●	Different fiscal calendars across multiple legal entities
●	Consolidations that involve multiple reporting currencies
●	Business unit consolidations
Generating consolidated financial statements
This section covers the various scenarios where you might generate consolidated financial statements.
Single-level and multilevel consolidations across legal entities
The simplest method for consolidating by using Financial reporting is to use reporting trees to aggregate data across companies that have the same chart of accounts and fiscal periods.
Here are the high-level steps to consolidate by using a reporting tree.
1	Create a row definition, and make sure that all appropriate accounts in all companies are included in the rows.
2	Create a column definition that includes all the columns that are required for the report that you’re creating.
3	Create a reporting tree that includes a reporting node for each company that you’re using on consolidated reports.
Tip: For more information about how to create and manage row definitions, column definitions, and reporting trees, see Create and manage report components.
The following illustration shows how you can use a reporting tree definition in Financial reporting to identify each company that you will consolidate.
 
As the consolidated report in the following illustration shows, when you use the reporting tree together with a report definition, you can view each company separately. The consolidated amounts are shown at the summary level.
 
You can also create a multilevel reporting tree that includes as many levels as you require. The following illustration shows a multilevel reporting tree definition that has roll-ups by worldwide region.
 
The following illustration shows a multilevel reporting tree definition that has roll-ups by function.
 
Viewing companies side by side
Many customers prefer reports where the companies appear side by side, and where a column shows the consolidated total. This format is easy to achieve after you’ve created the reporting tree. Here are the high-level steps to view companies side by side on consolidated financial statements.
1	Create a column definition that includes a Financial Dimension column for each company.
2	Use the Reporting Unit field to select the tree and reporting unit for each column.
3	Optional: Add headers and total columns.
The following illustration shows a column definition in a side-by-side format.
 
Consolidations that use organization structures that are created from legal entities
Organization hierarchies that contain dimensions or legal entities dynamically create reporting tree definitions in Financial reporting. An easy way to streamline consolidations is to add an organization hierarchy to your report in Financial reporting. Based on the report date, Financial reporting will select the organization hierarchy on or before the effective date, as shown in the following illustration.
 
Consolidations that involve eliminations
Elimination transactions are a common part of the consolidation process. In this example, five accounts are eliminated during consolidation: 142600, 211400, 401420, 401180, and 510820. Companies might set up their intercompany accounts differently. For example, some companies set the last digit to 9 if the account is used in intercompany transactions. Regardless of the method, if you know the intercompany accounts, you can show eliminations on your consolidated financial statements.
The following illustration shows a column definition for a consolidated income statement. Three profit and loss intercompany accounts are defined for each company by using the dimension filter. Column D includes the elimination accounts only for the USMF company, and column E includes eliminations only for the DEMF company. Both column D and column E are set up so that they are not printed on the financial statement.
 
When the report is generated, the elimination amounts are calculated in columns F, G, and H, and they are totaled in column I. Column J shows the consolidated amounts, excluding eliminations for the USMF, USRT, and DEMF companies.
Tip: Create a second report that shows only the elimination entries, and use it in a report group that includes your consolidated report. In this way, you have all the necessary information to create any journal entries that are required.
The following illustration shows the consolidated report.
 
Whether you use accounts, dimensions, or both, Financial reporting lets you filter out the elimination entries by using the dimension filtering capabilities.
Minority interest
A company might own only a percentage of another company. In this situation, when you’re producing a consolidated report, it’s important that you account for only the percentage that the company owns. Financial reporting has multiple ways to show minority interest, depending on user preference. One way is to use a roll-up percentage in the reporting tree definition. Another way is to show minority ownership as a separate line on a report.
Using the reporting tree definition
In the reporting tree definition, enter the percentage of ownership in the Rollup % column (column H), as shown in the following illustration. When the report is generated, this percentage will be used to calculate the consolidated amount. In this example, Contoso owns only 80 percent of Contoso Germany. You can enter either 80 or .8 in the Rollup % column, and 80 percent will be rolled up to the consolidated level.
Note: You can apply this ownership percentage to any reporting unit, not just at the company level. This capability is helpful when ownership is a business unit level or division level, not just a legal entity level.
 
When the report is generated, the Contoso Germany report will show 100 percent of the sales amount, and 80 percent of the amount will be allocated and rolled up to the consolidated level for sales.
If you own less than 1 percent of a company, you can select the Allow rollup less than 1% check box on the Additional Options tab of the Report Settings form, as shown in the following illustration. In this case, values in the Rollup % column in the reporting tree will be treated as less than 1 percent. For example, if you enter .8, 0.8 percent will be rolled up to the consolidated level, not 80 percent. Alternatively, you can achieve the same result by leaving the Allow rollup less than 1% check box cleared and entering .008 in the Rollup % column.
 
Showing ownership as a separate row on the consolidated report
Another option for minority interest is to show 100 percent of the subsidiary for every line on the report but subtract the non-controlling interest from the net income.
As the following illustration shows, an IF THEN ELSE statement and column restriction in the row definition can be used to calculate minority interest on financial reports.
 
Multiple charts of accounts across legal entities
Often, different legal entities have different charts of accounts but still want to produce consolidated financial statements. In this situation, Financial reporting can be used to consolidate the data, so that you can generate consolidated financial reports.
Here are the high-level steps to consolidate when different charts of accounts exist across legal entities.
1	Create a row definition that has multiple links to financial dimensions. There should be one link for each chart of accounts.
2	Use the reporting unit restriction in the column definition to assign each company to the appropriate column.
3	Use the reporting unit restriction in the column definition to assign each company to the appropriate column.
Multiple links to financial dimensions can be added to each row in the row definition for each unique company’s chart of accounts.
In the following illustration, the USMF company uses the set of accounts in the first Link to Financial Dimensions column (column J), and the DEMF company uses the accounts in the second Link to Financial Dimensions column (column K).
Tip: For more information about the Link to Financial Dimensions cell, see Specify Link to Financial Dimensions cell.
 
You can use a reporting tree to define which link to financial dimensions from the row definition is used with each company. Select the row definition in column E, and then select the appropriate row link in column F, as shown in the following illustration.
 
Tip: When you create links to financial dimensions, use the description to identify the companies that each link applies to. In this way, you can more easily select the correct company when you create a reporting tree.
In the column definition, the Reporting Unit field lets you restrict each column to a unit of the reporting tree, so that you can view the data side by side. If you don’t indicate a specific company for a column, consolidated data for all companies will be shown.
Different fiscal calendars across multiple legal entities
Different legal entities might have different fiscal calendars but still be required to produce consolidated financial statements.
There are two ways to consolidate when different fiscal periods exist across legal entities:
●	Create a column definition, and use the period and year to map the appropriate periods for each company.
●	At Settings > Other > Additional Options, select whether to consolidate by using the period end date or the period number.
Tip: When you’re designing the column definition for multiple companies that have different fiscal periods, it’s important that you consider which company will be assigned to the Company name field in the report definition. That company’s fiscal calendar will be used as the base fiscal calendar for the report definition.
For example, the following table shows the fiscal period setup for the USMF and INMF companies. For consolidated reports, you want to use the fiscal calendar that USMF uses. The “Mapping” column shows the equivalent period and year for each company if a report is generated for June 30, 2018.
Company	Fiscal year	Mapping
USMF	Fiscal year, July 1 through June 30	Period 12, fiscal year 2018
INMF	Calendar year, January 1 through December 31	Period 6, fiscal year 2018
In the following illustration, the USMF company is specified in the Company name field in the report definition. Therefore, the USMF company’s fiscal calendar will be used as the base fiscal calendar. In this example, when a report is generated for June 30, 2018, the USMF company will use the BASE period, which is defined as period 12 in the report definition. The INMF company will use BASE–6, which is period 6. Both columns will include data for June 2018.
 
The following illustration shows the options in the report definition that let you select whether the period number or the period end date is used for the consolidation.
 
Business unit consolidations
This document has focused on using reporting tree definitions and organization hierarchies in Financial reporting for consolidation purposes. You can also use the reporting tree to create business unit consolidation reports, such as reports about worldwide sales or operations. These reports are a common requirement. To create them, select a company and a dimension for each unit that you want to consolidate on. For example, in the following illustration, the business unit roll-up is accomplished by repeating each company in the Company column (column A) and identifying a group of Department dimension values per company in the Dimensions column (column D).
 
Consolidations that involve multiple reporting currencies
Financial reporting offers increased flexibility when you view actual, budget, budget control, and budget planning data in multiple currencies. By bringing across key setup data, you don’t have to do any additional setup in Financial reporting to view any report, in any currency, at any time, for any user.
Prerequisites
To correctly calculate translated balances, Financial reporting requires that the Retained Earnings Account category be assigned to the Retained Earnings account in the Main account list. Financial reporting doesn’t support posting to the Retained Earnings account. If transactions are posted to the Retained Earnings account, the translated balances won’t be calculated correctly. We recommend that users set up an additional Retained Earnings account to post adjustments to the Retained Earnings account.
On the main account, the Financial reporting exchange rate type and Currency translation type fields on the Financial reporting FastTab must be set for each account, as shown in the following illustration. You can complete this task on an account-by-account basis, or you can use the account templates to easily roll down changes.
●	In the Financial reporting exchange rate type field, select the exchange rate type that contains the currencies and exchange rates to apply to the account. This table of currencies and exchange rates will be applied to actual data in Financial reporting.
●	In the Currency translation type field, select the method that is used to calculate the exchange rate for the account. This currency method is used for both actual and budget data in Financial reporting.
 
For budget, budget control, and budget planning data, the exchange rate type is defined in the Ledger form. That table will be used to pull the exchange rates, and the currency translation type that is assigned to the account will be used.
Currency translation methods
There are four options for calculating exchange rates in Financial reporting:
●	Weighted average – This method is used most often for profit and loss accounts. It uses the following formula:
(Exchange rate × Days in effect) ÷ Days in period
●	Average – This method is an alternative method for profit and loss accounts. It uses the following formula:
Total of exchange rates ÷ Number of exchange rates
●	Current – This method is used most often for balance sheet accounts. The exchange rate that is used is the rate on or before the date of the report or column in Financial reporting.
●	Transaction date – This method is used for fixed assets accounts. The exchange rate that is used is the rate on the day when the asset was acquired. If a rate isn’t entered for that date, the previous rate that was entered closest to the asset acquisition date is used.
Report designer options for currency translation
In Financial reporting, any report can be shown in any number of reporting currencies. The following fields in the report definition support this capability:
●	The Currency Information section in the Report Definition form. This section shows the currency that the values are shown in when a report is generated.
●	A new Include all reporting currencies check box. When this check box is selected, the reporting currencies will queue up after the report that uses the company’s functional currency is generated. If the check box is cleared, you can still select a reporting currency in the Web Viewer. In this case, the reporting currency will be processed only when you select it.
The options in the report definition let you easily translate a report into all your reporting currencies. Therefore, you might be able to eliminate duplicate report definitions that differ only in the currencies that are used. If you require a report that shows multiple currencies side by side, you can continue to use the Currency display field in the Column Definition form to translate just that column of the report into an alternate reporting currency.
Currency translation adjustment
The currency translation adjustment (CTA) is the difference between the rates that are used to calculate the balance sheet accounts and the rate that is used for the income statement accounts. This difference will cause the balance sheet to be out of balance.
You can use Financial reporting to calculate the CTA in two ways:
●	Use the Rounding Adjustments form in the row definition, as shown in the following illustration.
 
When you specify the row that should show the rounding adjustment (CTA), the Total assets row, the total liabilities and equity row, and the threshold that you’re comfortable with, Financial reporting will calculate the difference and put it on the desired row. A line that is named Rounding Adjustment will be created and shown upon drill-down, as shown in the following illustration.
 
●	Put all the accounts in a range, from assets to expenses. As shown in the following illustration, the difference will be the same amount as the rounding adjustment (CTA). Therefore, you can use it as a check total to make sure that the rounding adjustment form doesn’t include any account balances that were missed.
 
Balance calculation approach
To get correctly translated amounts when currencies are used, Financial reporting uses the following calculation methods for the balances:
●	Weighted average and average – Each period is calculated at its weighted average, and is totaled for columns such as quarterly and year to date.
●	Historical – Any account that uses the historical translation method always goes back to the transaction date. If an acquisition date is associated with the transaction, that date is used to get the exchange rate. Each period is then totaled and stored to help improve the calculation time.
●	Current – Calculated and total columns, such as quarterly and year-to-date, are calculated at the spot rate that is determined in the column or on the report. For example, the Quarter 1 column will use the March 31 rate if a calendar year is used.

