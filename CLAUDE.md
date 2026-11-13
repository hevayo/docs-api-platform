@AGENTS.md

## This repo

- API Management (`api-management/`) has two Editions built from `docs-v2/main`: Cloud and Self-hosted. A whole folder shown in one Edition only says so in its `_category_.yml` (`customProps: { editions: cloud }`).
- API Gateway, AI Gateway, API Portal and AI Workspace are its Sub Doc spaces: their `docs/` on `docs-v2/main` is the unreleased `next`; each released version is a release branch `docs-v2/<product>/release/<version>`. API Control Plane has no release yet and is not listed.
- Until the cutover the pages here are generated from `main` (MkDocs, `en/`) by the onboarding workspace's `tools/onboard-mkdocs/convert-api-platform.mjs`: fix the source on `main` or the script's rules, not the pages here.
- Link to another Doc space with `docs:<doc-space>/<edition>/<page>`; to a product page that is not released yet with `#` until it is.
