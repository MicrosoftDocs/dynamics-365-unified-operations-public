You can calculate shift depreciation for a value model with a Current status
**selected in the** Posting layer field and a straight line percentage method or
reducing balance depreciation method selected in the Depreciation profile field
i**n the** Value models form, per the Companies Act, 1956.

**Example**

The calculation of the number of days that an asset is used for is described
below.

An asset is used from December 21, 2012 to March 31, 2013. The days for each
period in the fixed asset calendar are as follows:

>   December 21, 2011 to December 31, 2011 = 11 days

>   January 1, 2012 to January 31, 2012 = 31 days

>   February 1, 2012 to February 29, 2012 = 29 days

>   March 1, 2012 to March 31, 2012 = 31 days

The total number of days that the asset is used for is 102 days, which is 11 +
31 + 29 + 31.

Depreciation for non-working days will be calculated as single shift.

>   Single shift depreciation will always calculate on a 365/365 basis. Double
>   and Triple shift depreciation will calculate on regular working days in a
>   year subject to seasonal, 180 days, and non-seasonal, 240 days.

>   If the value model that is attached to the depreciation profile contains the
>   “Straight line percentage or Reducing balance depreciation method, and shift
>   a depreciation type is not defined in the value model, then no depreciation
>   will be calculated for shifts.

>   If shift depreciation is defined in the value model, but shift depreciation
>   rates are not defined in the depreciation profile, then the standard
>   depreciation rate will apply as single shift. If shift depreciation rates
>   are defined, then shift depreciation rates will prevail over the standard
>   rate.  

>   The total number of working days for single, double, or triple shift in a
>   period cannot exceed the number of days that are defined in the ledger
>   period.

>   Depreciation for non-working days (Calendar days in a period less the days
>   defined in a ledger period) is calculated as single shift.

Shift depreciation formulas

Refer to the following table for different formulas that are used to calculate
the shift depreciation.

| Type of depreciation method                         | Type of industry         | Number of working days for the industry                                                                                               | Formula                                                                                                                                                                                                                          |
|-----------------------------------------------------|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Straight-line percentage method                     | Seasonal                 | More than the number of days that are defined in the Min. working days for seasonal industries field. Fixed assets parameters         | [(Cost of acquisition – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Total number of working days in a year                                |
| Straight-line percentage method                     | Seasonal                 | **Less than the number of days that are defined in the** Min. working days for seasonal industries field Fixed assets parameters      | [(Cost of acquisition – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Minimum number of working days for seasonal industries (180 days)     |
| Straight-line percentage method                     | Non-seasonal             | More than the number of days that are defined in the Min. working days for non-seasonal industries field Fixed assets parameters      | [(Cost of acquisition – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Total number of working days in a year                                |
| Straight-line percentage method                     | Non-seasonal             | **Less than the number of days that are defined in the** Min. working days for non-seasonal industries field Fixed assets parameters  | [(Cost of acquisition – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Minimum number of working days for non-seasonal industries (240 days) |
| Reducing-balance method                             | Seasonal                 | More **than the number of days that are defined in the** Min. working days for seasonal industries field Fixed assets parameters      | [(Written-down value – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Total number of working days in a year                                 |
| Reducing-balance method                             | Seasonal                 | Less **than the number of days that are defined in the** Min. working days for seasonal industries field Fixed assets parameters      | [(Written-down value – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Minimum number of working days for seasonal industries (180 days)      |
| Reducing-balance method                             | Non-seasonal             | More than the number of days that are defined in the Min. working days for non-seasonal industries field Fixed assets parameters      | [(Written-down value – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Total number of working days in a year                                 |
| Reducing-balance method                             | Non-seasonal             | **Less than the number of days that are defined in the** Min. working days for non-seasonal industries Fixed assets parameters        | [(Written-down value – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Minimum number of working days for non-seasonal industries (240 days)  |
| Straight-line percentage or Reducing-balance method | Seasonal or Non-seasonal | Value models Select the Override fixed asset calendar days? check box and specify the number of days in the Asset working days field. | [(Cost of acquisition or Written-down value – Scrap value) \* Percentage that is defined for the type of shift] \* Number of days that the asset is used for during the period ÷ Asset working days                              |

Full depreciation is calculated if the value of an asset is less than or equal
to the value that is specified in the Max. acquisition value to avail full
depreciation Fixed assets parameters In this case, the days that are specified
in the Min. working days for seasonal industries field or the Min. working days
for non-seasonal industries field are not considered for calculation of
depreciation.
