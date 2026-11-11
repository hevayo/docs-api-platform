# docs-api-platform

A Content repo of WSO2 Docs (docs.wso2.com). It holds these Doc spaces, one directory each:

| Directory | Doc space | Editions and branches |
|---|---|---|
| `api-management/` | API Management: Cloud and the unversioned Self-hosted Edition; its Sub Doc spaces below | Cloud and Self-hosted on `docs-v2/main` |
| `api-gateway/` | API Gateway, a Sub Doc space of API Management | `next` on `docs-v2/main`; 1.2.0 on `docs-v2/api-gateway/release/1.2.0`, 2026.10.0 on `docs-v2/api-gateway/release/2026.10.0`, 1.1.0 on `docs-v2/api-gateway/release/1.1.0`, 1.0.0 on `docs-v2/api-gateway/release/1.0.0` |
| `ai-gateway/` | AI Gateway, a Sub Doc space of API Management | `next` on `docs-v2/main`; 1.2.0 on `docs-v2/ai-gateway/release/1.2.0`, 2026.10.0 on `docs-v2/ai-gateway/release/2026.10.0`, 2026.09.24 on `docs-v2/ai-gateway/release/2026.09.24`, 1.1.0 on `docs-v2/ai-gateway/release/1.1.0`, 1.0.0 on `docs-v2/ai-gateway/release/1.0.0` |
| `api-portal/` | API Portal, a Sub Doc space of API Management | `next` on `docs-v2/main`; 1.0.0 on `docs-v2/api-portal/release/1.0.0` |
| `ai-workspace/` | AI Workspace, a Sub Doc space of API Management | `next` on `docs-v2/main`; 1.0.0 on `docs-v2/ai-workspace/release/1.0.0` |
| `api-control-plane/` | API Control Plane, a Sub Doc space of API Management (not listed until its first release) | `next` on `docs-v2/main` |

Until the cutover, `main` is still the legacy MkDocs site (`en/`), which builds https://wso2.com/api-platform/docs/, and writers still merge there. Every branch of the WSO2 Docs layout starts with `docs-v2/`: `docs-v2/main` is the main line (API Management's Cloud and Self-hosted pages, and each product's unreleased `next`), and `docs-v2/<product>/release/<version>` is each released version. Until then the pages on these branches are generated from `main` by a converter run (`tools/onboard-mkdocs/convert-api-platform.mjs` in the onboarding workspace): don't edit them here, the next run overwrites them. At the cutover the branches drop `docs-v2/` and `docs-v2/main` becomes `main`.

Docs releases are tagged `api-management/cloud-<YYYY.MM.DD>.<n>` (Cloud), `api-management/self-hosted-<YYYY.MM.DD>.<n>` (Self-hosted, by hand from the main line) and `<product>/<version>-docs.<n>` (a product version, from its release branch).

Each Doc space directory holds `docspace.yaml` (the Doc space manifest), `editions.yaml` (per-Edition variables), `redirects.yaml` (page moves), `docs/` (pages; folders are the menu) and `assets/` (images, videos and files its pages use).

The repo root holds only shared files: this README, `CODEOWNERS`, the release workflow (`.github/workflows/docs-bundle-release.yml`), the branch ruleset (`.github/branch-ruleset.json`), the editor settings, and `AGENTS.md` and `CLAUDE.md` for agents (they point to `npx @wso2-enterprise/docs help`). The Platform-managed files come from `templates/content-repo/` in `wso2-enterprise/choreolabs-docs`.

The tools are on GitHub Packages. Once per machine, make a classic personal access token with `read:packages` (authorised for the `wso2-enterprise` organisation's SSO if it asks), then run `npm login --scope=@wso2-enterprise --auth-type=legacy --registry=https://npm.pkg.github.com` with your GitHub user name and the token as the password. This repo's `.npmrc` names the registry for `@wso2-enterprise`; it holds no token.

Get started, from setting up your computer to a Docs release going live: the WSO2 Docs Platform's README, https://github.com/wso2-enterprise/choreolabs-docs#readme.
