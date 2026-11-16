# STEMEd+ Professional Learning

National professional learning for K-12 teachers and informal educators across STEM+ fields, with application
deadlines in one place: **https://jlib271.github.io/stemed-professional-learning/**

STEMEd+ Professional Learning is part of [STEMEd+ Commons](https://stemedplus.hcommons.org/), with
[STEMEd+ Conferences](https://jlib271.github.io/stemed-conferences/), [STEMEd+ Funding](https://jlib271.github.io/stemed-funding/),
[STEMEd+ Jobs](https://jlib271.github.io/stemed-jobs/), the [STEMEd+ Digest](https://jlib271.github.io/STEMEd-Digest/),
and the [Graduate Programs](https://jlib271.github.io/stem-ed-research-programs/) list.

## What is listed

- **Who it is for.** K-12 teachers, and informal educators: staff and volunteers at museums, science centers,
  zoos, aquariums, parks, nature centers, libraries, and after-school and outreach programs.
- **Who runs it.** Only programs run by a national scholarly or professional society or association (in the US
  or internationally), by a US federal agency (NOAA, NASA, NSF, the National Park Service, the Department of
  Energy, ...), by a national program with federal agency funds (for example, NSF-funded RET Sites or the
  NASA-sponsored GLOBE Program), by the Smithsonian Institution, or by a national private foundation or nonprofit
  (for example, the Knowles Teacher Initiative). **If we are not sure, we leave it out.**
- **What kinds.** Research and field experiences, fellowships, workshops and institutes, online courses,
  webinar series, coaching, and certification training.
- **What it shows.** Who it is for and which grades, cost or stipend, credit, format, how often it runs, and
  when applications open and close. Programs open for applications are listed first.

### Not included

- **State, regional, and district professional development.** That includes state education agencies, state
  teacher associations and their chapters, regional service centers, district programs, and the state programs
  of national networks (such as state Ag in the Classroom programs or state GLOBE partners' own workshops).
  The page says so at the top, and teachers are pointed to their state agency, state teacher association, or
  district instead.
- University courses and degrees, programs run by companies, and programs open only to teachers in one city or state.
- Teacher conferences such as NSTA and NCTM, which are on [STEMEd+ Conferences](https://jlib271.github.io/stemed-conferences/).

### Considered but not listed

Math for America fellowships (open only to New York City public school teachers) and AMTE programs (for
mathematics teacher educators, not K-12 teachers).

Disciplines come from the list shared across STEMEd+ Commons, kept in the [HuMeta profile](https://github.com/JLib271/humeta-profile)
(`stemedplus_disciplines.json`). Computer science is listed under Engineering, as on the other sites.

## Feeds and calendars

| | |
|---|---|
| `feeds/deadlines.ics` | When applications open and close, for Google Calendar, Outlook, or Apple Calendar ("add calendar from URL") |
| `feeds/new.xml` | RSS of newly listed programs |
| `programs.json` | Everything on the site, for reuse |

## Add or correct a listing

- [Suggest a program](https://github.com/JLib271/stemed-professional-learning/issues/new?template=suggest_program.yml)
- [Report new dates or a correction](https://github.com/JLib271/stemed-professional-learning/issues/new?template=update_program.yml)
- No GitHub account? Email the maintainer, Julie Libarkin, at libarkin@msu.edu.

To edit directly, see [CONTRIBUTING.md](CONTRIBUTING.md). Each program is one YAML file in `programs/`,
checked against `schema/program.schema.json`.

## How it works

A GitHub Actions workflow (`.github/workflows/update.yml`) runs every day and on every push:

1. refreshes the shared discipline list from HuMeta;
2. runs the tests and checks every file in `programs/`;
3. builds the site into `output/` and publishes it to GitHub Pages. Sessions whose dates have all passed drop
   off, passed deadlines are marked, programs open for applications move to the top, and the date each program
   was first listed is carried over from the published `programs.json` for the RSS feed.

The footer's "For maintainers" box lists files to re-check: any not checked in 180 days, paused programs not
checked in 60 days, and any session with announced (not yet official) dates within 60 days.

Run it locally:

```sh
pip install -r requirements.txt
python -m unittest discover -s tests -t .
python -m stemed_pl --validate
python -m stemed_pl --out output    # then open output/index.html through a local web server
```

To publish: Settings → Pages → Source: **GitHub Actions**.

## License

Code: MIT ([LICENSE](LICENSE)). Listings in `programs/`: CC BY 4.0 ([programs/LICENSE.md](programs/LICENSE.md)).
