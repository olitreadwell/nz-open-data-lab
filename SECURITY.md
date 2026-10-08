# Security

`nz-open-data-lab` is a static Next.js site plus a set of scripts. It reads
public data over the network and renders charts. It stores no user accounts
and no personal data.

## Report a vulnerability

Use GitHub's private report form:

<https://github.com/olitreadwell/nz-open-data-lab/security/advisories/new>

That channel is private between you and the maintainer. Please do not open a
public issue for a vulnerability, and do not paste a working exploit into an
issue thread.

## Keys

Any key used by the site comes from the environment:

- `STATS_NZ_SUBSCRIPTION_KEY` unlocks the Stats NZ codelist endpoint.
- Keys are read at build time and never sent to the browser.
- Real keys are never committed. `.env` is gitignored.

If you find a key in the repository or in a deployed bundle, that is a
vulnerability. Report it through the form above.

## What is in scope

- A key reaching the client bundle, a log line, or a committed file.
- A cross-site scripting path through data rendered from a public API. The
  chart labels and tooltips render values that come from third parties.
- A dependency with a known advisory that actually ships to visitors.
- A weakness in the Content Security Policy or the other security headers in
  `apps/web/vercel.ts`.

## What is out of scope

- Findings that only affect development dependencies, the test runner, or the
  build tooling.
- Anything that needs a modified clone or a compromised machine.

## Automated checks

| Check | Where | What it does |
| --- | --- | --- |
| Dependency audit | `.github/workflows/security.yml` | `npm audit` on production dependencies |
| Secret scan | `scripts/security-checks.sh` | Looks for committed credentials |
| Security headers | `apps/web/scripts/check-deployed-security-headers.mjs` | Checks the live response headers |
| Security.txt | `apps/web/public/security.txt` | Published contact route for the deployed site |
