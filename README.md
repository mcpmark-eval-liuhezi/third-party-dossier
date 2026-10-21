# Third-Party Dependency Dossier

Compliance dossier covering the third-party dependencies our service pins in production. For each pinned version it records what the package registry reports — the declared license, the project homepage/repository link, and the publish date of that exact version — and, where the registry points at a public source repository, the license actually granted by that project's LICENSE file.

The full dossier lives in [`dependencies.md`](dependencies.md).

## Pinned dependencies in scope

| # | Package | Pinned version | Registry | License (as granted by the source project) |
|---|---------|----------------|----------|----------------------------------------------|
| 1 | React | 18.3.1 | npm | MIT |
| 2 | Express | 4.19.2 | npm | MIT |
| 3 | Lodash | 4.17.21 | npm | MIT |
| 4 | Requests | 2.32.3 | PyPI | Apache-2.0 |
| 5 | Flask | 3.0.3 | PyPI | BSD 3-Clause (PyPI itself declares no license value; its classifier says "BSD License") |

## What the dossier contains

For each of the five pinned versions:

- the license the registry declares for that exact version;
- the homepage and/or repository link the registry reports;
- when that version was published;
- the license granted by the source project's LICENSE file (the React notice is quoted in full);
- for React, additionally: a summary of what changed in 18.3.1 per the project's release notes.

Where a registry or project does not expose a piece of information, the dossier says so explicitly rather than guessing. See the *Data availability notes* section of [`dependencies.md`](dependencies.md) for the full list of gaps and how publish dates were obtained.
