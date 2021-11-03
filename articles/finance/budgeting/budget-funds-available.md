## Budget Funds Available 
#### Enhanced calculation feature

Starting in application release 10.0.24 a new feature called  **Only track amounts in the budget funds available calculation** was released to provide a more precise tracking in the underlying budget control tables for document types and states according to the settings marked in budget control for the budget funds available. 

To enable the feature **Only track amounts in the budget funds available calculation**, these are required budget control configuration settings that must be
defined for this feature to work properly.

| If this setting is enabled        | This also needs to be enabled     |
| ----------------------------------|---------------------------------- |
| Budget reservations for pre-encumbrances | Budget reservations for encumbrances **and** Actual expenditures |
| Budget reservations for encumbrances | Actual expenditures |
| When using PR-type General budget reservation documents and Budget reservations for encumbrances | Budget reservations for pre-encumbrances |

