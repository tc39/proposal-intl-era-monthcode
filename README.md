# Intl era and monthCode Proposal
(old name "Intl Temporal Proposal")

To specify necessary details about era, eraYear and monthCode usage with Temporal in internationalization setting (for calendars other than "iso8601").

## Stage - Stage 2
This proposal is advanced to Stage 2 for ECMA402 during the TC39 meeting, Feb 1 2023. (Link to be added after the meeting notes is approved by TC39 in March)
This proposal is [advanced to Stage 1 for ECMA402 during the TC39 meeting, Dec 1 2022](https://github.com/tc39/notes/blob/main/meetings/2022-11/dec-01.md#intl-era-and-monthcode-proposal-for-stage-1).

## Stage 3 Reviwers
During the Feb 1 2023 TC39 meeting, the following members agree to serve as the Stage 3 Reviewers of this proposal:
* EAO (Eemeli Aro) from Mozilla
* SFC (Shane Carr) from Google

## Presentation:
* [Intl era and monthCode proposal for Stage 1, TC39 Nov 2022 Meeting, Nov 29-Dec 1, 2022](https://docs.google.com/presentation/d/1hoQUYL_mfdLXMHRsNcG27aJirukuDGsVbqntd_tcR0A)
* [Intl era and monthCode proposal for Stage 2, TC39 Jan 2023 Meeting, Jan 23-Jan 26, 2023](https://docs.google.com/presentation/d/1TlhwLfCBsH9MjJTZYpQxfGs4jVnsMX0U8X0hi8WSoxc)
## References:
* [Draft Spec](https://frankyftang.github.io/proposal-intl-temporal/)
* [Study of modles of year and era in ICU Calendar](https://docs.google.com/presentation/d/1WFRajsWR2Nh_SPQPzEe7yXpjj-EDvUweUrikNV_jzI4/edit#slide=id.g153d52938b6_0_619)
* [Temporal Internationalization Calendars Design Doc](https://notes.igalia.com/o7MT_yQJTV2Ka06sjyuJ5g#).

## Scope
[Temporal proposal](https://tc39.es/proposal-temporal/) is a ECMA262 Stage proposal to “provide standard objects and functions for working with dates and times.” The Temporal proposal specification text clearly specified how the “iso8601” Calendar and “UTC” TimeZone should behave as well as define name and some basic aspect of Calenders other than “iso8601” and TimeZone other than “UTC”. However, there are additional requirements needed for implementation purposes. This proposal aims to define these details which should be eventually merged into ECMA402 specification.


### Abstract Operations in Temporal proposal to be specified
We believe the following Abstract Opertaions defined in the [Temporal proposal](https://tc39.es/proposal-temporal) need to be defined in more details in this proposal:
* [15.6.1.3 CalendarDateToISO ( calendar, fields, overflow )](https://tc39.es/proposal-temporal/#sec-temporal-calendardatetoiso)
  * Need to specify the condition of throwing RangeError exception
* [15.6.1.4 CalendarDateAddition ( calendar, date, duration, overflow )](https://tc39.es/proposal-temporal/#sec-temporal-calendardateaddition)
  * Need to specify the condition of throwing RangeError exception
* [15.6.1.5 CalendarDateDifference ( calendar, one, two, largestUnit )](https://tc39.es/proposal-temporal/#sec-temporal-calendardatedifference)
  * Need to specify the condition of throwing RangeError exception
* [15.6.1.6 CalendarDateEra ( calendar, date )](https://tc39.es/proposal-temporal/#sec-temporal-calendardateera)
  * Need to define the possible era codes for each calendar and which calnedar will return undefined.
* [15.6.1.7 CalendarDateEraYear ( calendar, date() )](https://tc39.es/proposal-temporal/#sec-temporal-calendardateerayear)
  * Need to define which calnedar will return undefined.
* [15.6.1.9 CalendarDateMonth ( calendar, date )](https://tc39.es/proposal-temporal/#sec-temporal-calendardatemonth)
  * Need to define the meaning of month for some calendars.
* [15.6.1.10 CalendarDateMonthCode ( calendar, date )](https://tc39.es/proposal-temporal/#sec-temporal-calendardatemonthcode)
  * Need to define the valid set of monthCodes for each calendar.
* [15.6.1.20 CalendarDateFields ( calendar, fields )]()
  * Need to define which calendar will add "era" and "eraYear".
* [15.6.1.21 CalendarDateMergeFields ( calendar, fields, additionalFields )]()
  * Need to define which calendar will merge "era" and "eraYear" and how it merge "era" and "eraYear" .

We may choose to specify certain calendar arithmetic for some calendars if they are very simple to conver from/to "iso8601" calendar- For example, for "gregory", "roc", "buddhist", "japanese" calendar, but leave the arithmetic in vague language for others.

We are NOT aiming to specify the calendar arithmetic for the following part of Temporal proposal:
* 15.6.1.8 CalendarDateYear ( calendar, date )
* 15.6.1.11 CalendarDateDay ( calendar, date )
* 15.6.1.12 CalendarDateDayOfWeek ( calendar, date )
* 15.6.1.13 CalendarDateDayOfYear ( calendar, date )
* 15.6.1.14 CalendarDateWeekOfYear ( calendar, date )
* 15.6.1.15 CalendarDateDaysInWeek ( calendar, date )
* 15.6.1.16 CalendarDateDaysInMonth ( calendar, date )
* 15.6.1.17 CalendarDateDaysInYear ( calendar, date )
* 15.6.1.18 CalendarDateMonthsInYear ( calendar, date )
* 15.6.1.19 CalendarDateInLeapYear ( calendar, date )

### Calendars

### Values of Era for Calendars
Related spec text in [Temporal proposal](https://tc39.es/proposal-temporal/):
* [15.6.2.6 Temporal.Calendar.prototype.era ( temporalDateLike )](https://tc39.es/proposal-temporal/#sec-temporal.calendar.prototype.era)
* [15.6.5.2 get Temporal.PlainDate.prototype.era](https://tc39.es/proposal-temporal/#sec-get-temporal.plaindate.prototype.era)
* [15.6.6.2 get Temporal.PlainDateTime.prototype.era](https://tc39.es/proposal-temporal/#sec-get-temporal.plaindatetime.prototype.era)
* [15.6.9.2 get Temporal.PlainYearMonth.prototype.era](https://tc39.es/proposal-temporal/#sec-get-temporal.plainyearmonth.prototype.era)
* [15.6.10.2 get Temporal.ZonedDateTime.prototype.era](https://tc39.es/proposal-temporal/#sec-get-temporal.zoneddatetime.prototype.era)
* [15.6.1.3 CalendarDateToISO ( calendar, fields, overflow )](https://tc39.es/ecma262/#implementation-defined)

For Calendar:
* List of 'calendar':
CLDR and ICU support the following calendars beside "iso8601" and currently supported by Intl.DateTimeFormat API in different browsers.
  * "gregory""
  * "roc" (same as "gregory" except handling of era and year)
  * "buddhist" (same as "gregory" except handling of era and year)
  * "japanese" (same as "gregory" except handling of era and year)
  * "persian"
  * "coptic"
  * "ethiopic"
  * "ethiopic-ameta-alem"  (same as "ethiopic" except handling of era and year)
  * "indian""
  * "hebrew"
  * "chinese"
  * "dangi" (same as "chinese" except the referencing timeZone)
  * "islamic"
  * "islamic-tbla"
  * "islamic-umalqura"
  * "islamic-civil"

* Requirement for era and eraYear:
  * The combination of *era* and *eraYear* in a calendar need to be able to uniquely identify a particular year in the timeline.
  * *era* need to be a String (per [15.6.1.1 CalendarEra](https://tc39.es/proposal-temporal/#sec-temporal-calendarera) in Temporal).
  * *eraYear* need to be an Integer (per [15.6.1.2 CalendarEraYear](https://tc39.es/proposal-temporal/#sec-temporal-calendarerayear) in Temporal).
  * If there is only one era in a calendar, we do not need to and should avoid using the era/eraYear in that calendar (e.g. "hebrew", "persian")
  * If we define era, we need to also define the behavior if the field(s) is/are absent. (fallback to use year or fallback to a default value and what is the default value)
  
* 'gregory': TBW
### Values of EraYear for Calendars
Related spec text in [Temporal proposal](https://tc39.es/proposal-temporal/):
* [15.6.2.7 Temporal.Calendar.prototype.eraYear ( temporalDateLike )](https://tc39.es/proposal-temporal/#sec-temporal.calendar.prototype.erayear)
* [15.6.5.3 get Temporal.PlainDate.prototype.eraYear](https://tc39.es/proposal-temporal/#sec-get-temporal.plaindate.prototype.erayear)
* [15.6.6.3 get Temporal.PlainDateTime.prototype.eraYear](https://tc39.es/proposal-temporal/#sec-get-temporal.plaindatetime.prototype.erayear)
* [15.6.9.3 get Temporal.PlainYearMonth.prototype.eraYear](https://tc39.es/proposal-temporal/#sec-get-temporal.plainyearmonth.prototype.erayear)
* [15.6.10.3 get Temporal.ZonedDateTime.prototype.eraYear](https://tc39.es/proposal-temporal/#sec-get-temporal.zoneddatetime.prototype.erayear)
* [15.6.1.3 CalendarDateToISO ( calendar, fields, overflow )](https://tc39.es/ecma262/#implementation-defined)

For Calendar:
* 'gregory': TBW

### Values of Month for Calendars
Related spec text in [Temporal proposal](https://tc39.es/proposal-temporal/):
*

For Calendar:
* 'gregory': TBW
* 
### Values of MonthCode for Calendars
Related spec text in [Temporal proposal](https://tc39.es/proposal-temporal/):
*

For Calendar:
* 'gregory': TBW
* 

