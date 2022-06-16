# Intl Temporal Proposal

To specify necessary details of using Temporal in internationalization setting (such as calendar other than "iso8601").

## Stage
This proposal is currently Stage 0 for ECMA402

## Scope
[Temporal proposal](https://tc39.es/proposal-temporal/) is a ECMA262 Stage proposal to “provide standard objects and functions for working with dates and times.” The Temporal proposal specification text clearly specified how the “iso8601” Calendar and “UTC” TimeZone should behave as well as define name and some basic aspect of Calenders other than “iso8601” and TimeZone other than “UTC”. However, there are additional requirements needed for implementation purposes. This proposal aims to define these details which should be eventually merged into ECMA402 specification.

Ref: [Temporal Internationalization Calendars Design Doc](https://notes.igalia.com/o7MT_yQJTV2Ka06sjyuJ5g#).

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
## Before creating a proposal

Please ensure the following:
  1. You have read the [process document](https://tc39.github.io/process-document/)
  1. You have reviewed the [existing proposals](https://github.com/tc39/proposals/)
  1. You are aware that your proposal requires being a member of TC39, or locating a TC39 delegate to "champion" your proposal

## Create your proposal repo

Follow these steps:
  1. Click the green ["use this template"](https://github.com/tc39/template-for-proposals/generate) button in the repo header. (Note: Do not fork this repo in GitHub's web interface, as that will later prevent transfer into the TC39 organization)
  1. Update the biblio to the latest version: `npm install --save-dev --save-exact @tc39/ecma262-biblio@latest`.
  1. Go to your repo settings “Options” page, under “GitHub Pages”, and set the source to the **main branch** under the root (and click Save, if it does not autosave this setting)
      1. check "Enforce HTTPS"
      1. On "Options", under "Features", Ensure "Issues" is checked, and disable "Wiki", and "Projects" (unless you intend to use Projects)
      1. Under "Merge button", check "automatically delete head branches"
<!--
  1. Avoid merge conflicts with build process output files by running:
      ```sh
      git config --local --add merge.output.driver true
      git config --local --add merge.output.driver true
      ```
  1. Add a post-rewrite git hook to auto-rebuild the output on every commit:
      ```sh
      cp hooks/post-rewrite .git/hooks/post-rewrite
      chmod +x .git/hooks/post-rewrite
      ```
-->
  3. ["How to write a good explainer"][explainer] explains how to make a good first impression.

      > Each TC39 proposal should have a `README.md` file which explains the purpose
      > of the proposal and its shape at a high level.
      >
      > ...
      >
      > The rest of this page can be used as a template ...

      Your explainer can point readers to the `index.html` generated from `spec.emu`
      via markdown like

      ```markdown
      You can browse the [ecmarkup output](https://ACCOUNT.github.io/PROJECT/)
      or browse the [source](https://github.com/ACCOUNT/PROJECT/blob/HEAD/spec.emu).
      ```

      where *ACCOUNT* and *PROJECT* are the first two path elements in your project's Github URL.
      For example, for github.com/**tc39**/**template-for-proposals**, *ACCOUNT* is "tc39"
      and *PROJECT* is "template-for-proposals".


## Maintain your proposal repo

  1. Make your changes to `spec.emu` (ecmarkup uses HTML syntax, but is not HTML, so I strongly suggest not naming it ".html")
  1. Any commit that makes meaningful changes to the spec, should run `npm run build` and commit the resulting output.
  1. Whenever you update `ecmarkup`, run `npm run build` and commit any changes that come from that dependency.

  [explainer]: https://github.com/tc39/how-we-work/blob/HEAD/explainer.md
