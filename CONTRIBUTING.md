# Adding or updating a program

Each program is one YAML file in `programs/`, named for the program (for example `noaa-teacher-at-sea.yml`).
The full list of fields, with descriptions, is in `schema/program.schema.json`.

## Before you add a program

1. **Check it is national.** State, regional, and district professional development is not listed, even when a
   national network runs it through state partners. List the national program, not a state chapter's workshop.
2. **Check who runs it.** The national society or association, or the US federal agency, must be named on its
   own website as running or funding the program. For a "Federally funded program", say which agency in
   `funding_note`.
3. **Check who it is for.** K-12 teachers, informal educators (museums, zoos, aquariums, parks, nature centers,
   libraries, after-school and outreach programs), or both, in a STEM+ field.
4. **Leave out anything you are unsure about,** and anything run by a company or funded only by a private
   foundation. Teacher conferences belong on STEMEd+ Conferences instead.

## Example

```yaml
name: NOAA Teacher at Sea
short: Teacher at Sea
providers: [NOAA Fisheries]
sponsor_type: US federal agency        # US society | International society | US federal agency | Federally funded program
type: field                            # research | field | fellowship | institute | course | webinars | coaching | credential
audiences: [K-12 teachers, Informal educators]
grades: [Middle school, High school]   # leave out if it is for all of K-12
disciplines: [Earth Science, Bioscience]   # leave out for programs open to all STEM+ fields
format: in person                      # in person | online | hybrid | varies
cost: stipend                          # free | stipend | members | fee | varies
cost_note: NOAA covers travel to and from the ship.
credit: Graduate credit is available.  # only if the provider says so
url: https://www.fisheries.noaa.gov/topic/teacher-at-sea-program
frequency: annual                      # annual | twice a year | several times a year | ongoing | irregular
schedule: Applications open November 1 and close November 30 for cruises the following year.
summary: Educators sail on a NOAA ship for about two weeks, then bring the science back to their students.
checked: 2026-11-12                    # the day you checked the provider's pages
offerings:                             # optional: sessions, cohorts, or application rounds with dates
  - name: 2027 field season
    url: https://www.fisheries.noaa.gov/topic/teacher-at-sea-program
    dates_source: official             # official | announced
    deadlines:
      - {label: Applications open, date: 2026-11-01, kind: opens}
      - {label: Applications due, date: 2026-11-30, kind: application}   # application | registration | opens | other
```

A program that is not running this year gets `status: paused` and a `status_note` saying what the provider said.

Write the summary in your own words. Check the file with `python -m stemed_pl --validate`.
