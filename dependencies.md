# Third-Party Dependency Dossier

**Purpose:** compliance-review record for the third-party dependencies pinned in production by our service.

**Exact pinned versions audited:**

| Package | Pinned version | Registry |
|---|---|---|
| React | 18.3.1 | npm |
| Express | 4.19.2 | npm |
| Lodash | 4.17.21 | npm |
| Requests | 2.32.3 | PyPI |
| Flask | 3.0.3 | PyPI |

**Sources consulted:**

- npm registry per-version endpoints: `https://registry.npmjs.org/<package>/<version>`
- PyPI JSON API: `https://pypi.org/pypi/<project>/<version>/json`
- The public source repositories those registries point at (GitHub): `facebook/react`, `expressjs/express`, `lodash/lodash`, `psf/requests`, `pallets/flask`

## At-a-glance summary

| Package | Version | Registry | License declared by registry | License granted in source repo | Version published | Homepage / repository reported by registry |
|---|---|---|---|---|---|---|
| React | 18.3.1 | npm | MIT | MIT | 2024-04-26 | https://reactjs.org/ · https://github.com/facebook/react |
| Express | 4.19.2 | npm | MIT | MIT | 2024-03-25 | http://expressjs.com/ · https://github.com/expressjs/express |
| Lodash | 4.17.21 | npm | MIT | MIT | 2021-02-20 | https://lodash.com/ · https://github.com/lodash/lodash |
| Requests | 2.32.3 | PyPI | Apache-2.0 | Apache-2.0 | 2024-05-29 | https://requests.readthedocs.io · https://github.com/psf/requests |
| Flask | 3.0.3 | PyPI | *not declared* (classifier: "BSD License") | BSD 3-Clause | 2024-04-07 | *no homepage field* (documentation: https://flask.palletsprojects.com/) · https://github.com/pallets/flask/ |

## Data availability notes

Everything below was looked up for the exact pinned version only. Where something was not exposed, it is recorded rather than inferred:

1. **npm publish dates.** npm's per-version endpoint does not return a publish timestamp as a public field (the full package document does, but not the per-version view). The npm dates in this dossier are the upload timestamps npm records internally in each version's `_npmOperationalInternal` metadata, in UTC: React 18.3.1 `2024-04-26T16:42:26Z`, Express 4.19.2 `2024-03-25T14:30:35Z`, Lodash 4.17.21 `2021-02-20T15:42:16Z`. React's `v18.3.1` project release is dated the same day (published 2024-04-26T19:53:42Z), which corroborates it.
2. **PyPI publish dates.** PyPI exposes an explicit `upload_time_iso_8601` per distribution file; the dates above are the wheel upload times for the pinned versions.
3. **Flask license on PyPI.** The PyPI `license` field for Flask 3.0.3 is empty (`null`) — the registry does not declare a license for this version. The trove classifier on the project does say `License :: OSI Approved :: BSD License`, and the source repository's `LICENSE.txt` grants BSD 3-Clause (see §5).
4. **Flask homepage on PyPI.** The PyPI `home_page` field for Flask 3.0.3 is empty (`null`). The project URLs PyPI does list are: Documentation `https://flask.palletsprojects.com/`, Source `https://github.com/pallets/flask/`, Changes `https://flask.palletsprojects.com/changes/`, Chat `https://discord.gg/pallets`, Donate `https://palletsprojects.com/donate`.
5. **React changelog.** The repository's root `CHANGELOG.md`, read at tag `v18.3.1`, contains no 18.3.1 section — its most recent entry is 18.1.0. The 18.3.1 changes are therefore taken from the project's GitHub release notes for that tag.

---

## 1. React — `react@18.3.1` (npm)

### Registry metadata (npm, exact version 18.3.1)

| Field | Value reported by npm |
|---|---|
| License (declared) | MIT |
| Homepage | https://reactjs.org/ |
| Repository | git+https://github.com/facebook/react.git (package subpath: `packages/react`) |
| Bugs | https://github.com/facebook/react/issues |
| Description | React is a JavaScript library for building user interfaces. |
| Publish date | 2024-04-26 (npm exposes no public publish-date field for a single version; see Data availability note 1) |
| Tarball | https://registry.npmjs.org/react/-/react-18.3.1.tgz |
| Integrity | `sha512-wS+hAgJShR0KhEvPJArfuPVN1+Hz1t0Y6n5jLrGQbkb4urgPE/0Rve+1kMB1v/oWgHgm4WIcV+i7F2pTVj+2iQ==` (shasum `49ab892009c53933625bd16b2533fc754cab2891`) |
| Runtime | `engines.node >= 0.10.0`; runtime dependency: `loose-envify ^1.1.0` |

### License granted by the source repository

The repository npm points at — https://github.com/facebook/react — carries an MIT `LICENSE`. The notice, quoted in full:

> MIT License
>
> Copyright (c) Meta Platforms, Inc. and affiliates.
>
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:
>
> The above copyright notice and this permission notice shall be included in all
> copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
> SOFTWARE.

### What changed in 18.3.1

Per the project's release notes for tag `v18.3.1` ("18.3.1 (April 26, 2024)"), the release contains exactly one change:

- **Export `act` from `react`** — commit [f1338f](https://github.com/facebook/react/commit/f1338f8080abd1386454a10bbf93d67bfe37ce85).

In other words, the `act()` testing helper, previously reached through `react-dom/test-utils` (where using it was already deprecated), is now exported directly from the `react` package itself.

Context from the same release line: `v18.3.0` (April 25, 2024) is described by the project as *identical to 18.2* but adding the deprecation warnings needed to prepare for React 19 — warnings for `findDOMNode`, the deprecated `test-utils` methods, Legacy Context, string refs, `defaultProps` on function components, spreading `key`, `unmountComponentAtNode` and `renderToStaticNodeStream`, plus allowing writes to `this.refs` to support the string-ref codemod. 18.3.1 is the follow-up patch on top of that.

---

## 2. Express — `express@4.19.2` (npm)

### Registry metadata (npm, exact version 4.19.2)

| Field | Value reported by npm |
|---|---|
| License (declared) | MIT |
| Homepage | http://expressjs.com/ |
| Repository | git+https://github.com/expressjs/express.git |
| Bugs | https://github.com/expressjs/express/issues |
| Description | Fast, unopinionated, minimalist web framework |
| Publish date | 2024-03-25 (see Data availability note 1) |
| Tarball | https://registry.npmjs.org/express/-/express-4.19.2.tgz |
| Integrity | `sha512-5T6nhjsT+EOMzuck8JjBHARTHfMht0POzlA60WV2pMD3gyXw2LZnZ+ueGdNxG+0calOJcWKbpFcuzLZ91YWq9Q==` (shasum `e25437827a3aa7f2a827bc8171bbbb664a356465`) |
| Runtime | `engines.node >= 0.10.0`; 31 runtime dependencies (qs 6.11.0, send 0.18.0, body-parser 1.20.2, serve-static 1.15.0, path-to-regexp 0.1.7, …) |

### License granted by the source repository

The repository npm points at — https://github.com/expressjs/express — carries an MIT `LICENSE` titled "(The MIT License)", with copyright held by TJ Holowaychuk (2009-2014), Roman Shtylman (2013-2014) and Douglas Christopher Wilson (2014-2015). It grants the standard MIT permission to use, copy, modify, merge, publish, distribute, sublicense and/or sell, subject to retaining the copyright and permission notice, with the software provided "AS IS" without warranty. This matches the MIT license npm declares for 4.19.2.

---

## 3. Lodash — `lodash@4.17.21` (npm)

### Registry metadata (npm, exact version 4.17.21)

| Field | Value reported by npm |
|---|---|
| License (declared) | MIT |
| Homepage | https://lodash.com/ |
| Repository | git+https://github.com/lodash/lodash.git |
| Bugs | https://github.com/lodash/lodash/issues |
| Description | Lodash modular utilities. |
| Publish date | 2021-02-20 (see Data availability note 1) |
| Tarball | https://registry.npmjs.org/lodash/-/lodash-4.17.21.tgz |
| Integrity | `sha512-v2kDEe57lecTulaDIuNTPy3Ry4gLGJ6Z1O3vE1krgXZNrsQ+LFTGHVxVjcXPs17LhbZVGedAJv8XZ1tvj5FvSg==` (shasum `679591c564c3bffaae8454cf0b3df370c3d6911c`) |

### License granted by the source repository

The repository npm points at — https://github.com/lodash/lodash — carries a `LICENSE` granting MIT terms, copyright "OpenJS Foundation and other contributors", and noting it is based on Underscore.js (Jeremy Ashkenas, DocumentCloud and Investigative Reporters & Editors). Two additional clauses are worth recording for compliance:

- copyright and related rights for **sample code** (source code displayed within the prose of the documentation) are waived via **CC0** (`http://creativecommons.org/publicdomain/zero/1.0/`);
- files under `node_modules` and `vendor` are externally maintained libraries with their own licenses, which may differ from the above.

This matches the MIT license npm declares for 4.17.21.

---

## 4. Requests — `requests` 2.32.3 (PyPI)

### Registry metadata (PyPI, exact version 2.32.3)

| Field | Value reported by PyPI |
|---|---|
| License (declared) | Apache-2.0 (also declared via the classifier `License :: OSI Approved :: Apache Software License`) |
| Homepage | https://requests.readthedocs.io |
| Source | https://github.com/psf/requests |
| Documentation | https://requests.readthedocs.io |
| Summary | Python HTTP for Humans. |
| Publish date | 2024-05-29 (`upload_time_iso_8601` of the wheel: `2024-05-29T15:37:47.027275Z`; the sdist followed at `15:37:49.536140Z`) |
| Distributions | `requests-2.32.3-py3-none-any.whl` (64,928 bytes), `requests-2.32.3.tar.gz` (131,218 bytes); not yanked |
| Runtime | `requires-python >= 3.8`; charset-normalizer <4,>=2 · idna <4,>=2.5 · urllib3 <3,>=1.21.1 · certifi >=2017.4.17 |
| Ownership | Owners on PyPI: Lukasa, graffatcolmingov, nateprewitt |

### License granted by the source repository

The repository PyPI points at — https://github.com/psf/requests — carries a `LICENSE` containing the standard **Apache License, Version 2.0** text ("Apache License Version 2.0, January 2004", `http://www.apache.org/licenses/`), including the definitions, copyright and patent grants, redistribution conditions (§4) and the limitation-of-warranty and liability sections. This matches the Apache-2.0 value PyPI declares for 2.32.3.

### Supplementary registry-reported note

The PyPI JSON API for this version also surfaces known vulnerabilities, recorded here for completeness since the registry reports them: a `.netrc` credential leak for specific maliciously-crafted URLs (CVE-2024-47081 / GHSA-9hjg-9r4m-mvj7, fixed in 2.32.4) and a predictable-temporary-filename issue in `requests.utils.extract_zipped_paths()` (CVE-2026-25645). Remediation decisions are outside this dossier's scope.

---

## 5. Flask — `Flask` 3.0.3 (PyPI)

### Registry metadata (PyPI, exact version 3.0.3)

| Field | Value reported by PyPI |
|---|---|
| License (declared) | *not declared* — the PyPI `license` field is empty (`null`) for this version; the classifier does say `License :: OSI Approved :: BSD License` |
| Homepage | *not declared* — the PyPI `home_page` field is empty (`null`) |
| Source | https://github.com/pallets/flask/ |
| Documentation | https://flask.palletsprojects.com/ |
| Changes | https://flask.palletsprojects.com/changes/ |
| Summary | A simple framework for building complex web applications. |
| Publish date | 2024-04-07 (`upload_time_iso_8601` of the wheel: `2024-04-07T19:26:08.569305Z`; the sdist followed at `19:26:11.035227Z`) |
| Distributions | `flask-3.0.3-py3-none-any.whl` (101,735 bytes), `flask-3.0.3.tar.gz` (676,315 bytes); not yanked |
| Runtime | `requires-python >= 3.8`; Werkzeug >=3.0.0 · Jinja2 >=3.1.2 · itsdangerous >=2.1.2 · click >=8.1.3 · blinker >=1.6.2 (+ importlib-metadata on Python <3.10) |
| Maintainer | Pallets <contact@palletsprojects.com> (owned by the `pallets` organization) |

### License granted by the source repository

The repository PyPI points at — https://github.com/pallets/flask — carries `LICENSE.txt` (there is no file named exactly `LICENSE` in the repo root) granting **BSD 3-Clause** ("Copyright 2010 Pallets"): redistribution in source and binary forms is permitted provided the copyright notice, the conditions and the disclaimer are retained, the notice is reproduced in documentation for binary distributions, and neither the copyright holder's nor contributors' names are used to endorse derived products without prior written permission; the software is provided "AS IS" with a disclaimer of warranties and limitation of liability.

This is consistent with — and more precise than — the BSD License classifier PyPI publishes for the project; the registry itself declares no license value for this version.

### Supplementary registry-reported note

The PyPI JSON API for this version also surfaces a known vulnerability affecting versions 3.1.2 and below, recorded here for completeness since the registry reports it: the `Vary: Cookie` header may not be set for some forms of session access such as the Python `in` operator (CVE-2026-27205 / GHSA-68rp-wp8r-4726, fixed in 3.1.3). Remediation decisions are outside this dossier's scope.

---

*Dossier assembled for the production-pinned versions listed above; all values reflect what the named registries and source repositories reported at the time of the audit.*
