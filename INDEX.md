# Experiment index

One line per published experiment. The deployed site is a hub page
(`apps/web/src/app/page.tsx`) listing every published microsite; each
experiment's writeup lives under `docs/experiments/<slug>/`.

Format: `- [slug](docs/experiments/<slug>)` (status) one-line pitch

- [sheep-index](docs/experiments/sheep-index) (alive) New Zealand's sheep flock is down 53% since 1994 (49.5m to 23.3m), from the Stats NZ Aotearoa Data Explorer.
- [parliament-party-seats](docs/experiments/parliament-party-seats) (built, not published) Which party held the most seats at each election since 1935, and who held the top job. From NZ Parliament Member Terms via the data.govt.nz CKAN datastore. The site shows one microsite at a time, so this one is waiting in `PUBLISHED_MICROSITES`.
