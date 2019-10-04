## Fiscal calendar period to msdyn_fiscalcalendarperiods

This template synchronizes data between Finance and Operations and Common Data Service.

Source field | Map type | Destination field
---|---|---
COMMENTS | = | msdyn_comments
ENDDATE | = | msdyn_enddate
MONTH | >< | msdyn_month
CALENDAR | = | msdyn_fiscalcalendar.msdyn_calendar
QUARTER | >< | msdyn_quarter
SHORTNAME | = | msdyn_shortname
STARTDATE | = | msdyn_startdate
TYPE | >< | msdyn_fiscalperiodtype
PERIODNAME | = | msdyn_periodname
FISCALYEAR | = | msdyn_fiscalcalendaryear.msdyn_name
CALENDAR | = | msdyn_fiscalcalendaryear.msdyn_fiscalcalendarname
