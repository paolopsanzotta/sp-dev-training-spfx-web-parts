# SPFx Web Parts Training Constitution

## Core Principles

### I. Training-First and Demo Isolation
The repository exists to support learning outcomes for the "Developing with the SharePoint Framework: Web Parts" module.
Each demo under `Demos/01-webpart`, `Demos/02-testing`, and `Demos/03-spfxapi` is an independent learning stage and must remain runnable in isolation.
Changes in one demo MUST NOT introduce hidden dependencies on assets, code, or build artifacts from another demo.

### II. Version and Toolchain Consistency
All demos must remain aligned to the same SPFx baseline unless a coordinated module refresh is planned:
- SPFx packages: `1.20.x`
- Node.js engine: `>=18.17.1 <19.0.0`
- TypeScript: `4.7.4`
- Build stack: `gulp 4`, `@microsoft/sp-build-web 1.20.2`, ESLint SPFx config
Version drift across demo folders is not allowed without updating documentation and validating all exercises.

### III. SharePoint-Hosted Workbench Compatibility
The module targets the SharePoint-hosted workbench workflow (`/_layouts/workbench.aspx`) and modern pages.
Code and configuration must preserve hosted workbench scenarios, including tenant-domain placeholders and package settings that support classroom/demo usage.
Breaking compatibility with hosted workbench requires explicit justification and curriculum updates.

### IV. Safe-by-Default Web Part Implementation
Web part code must follow SPFx safety and maintainability practices:
- Escape user or property-derived values before rendering into HTML.
- Use typed SPFx APIs and keep property contracts explicit.
- Respect theming and host context (SharePoint/Teams/Outlook/Office) where applicable.
- Keep behavior deterministic for demo reproducibility.

### V. Documentation and Learning Clarity
Every meaningful code or config change must preserve instructional clarity.
README content, exercise expectations, and demo behavior should stay synchronized.
Prefer small, incremental examples over clever abstractions that obscure SPFx fundamentals.

## Technical Constraints and Standards

1. Per-demo commands:
	- Install: `npm install`
	- Build: `npm run build` (maps to `gulp bundle`)
	- Test: `npm test` (maps to `gulp test`)
	- Local run for exercise validation: `gulp serve`
2. Packaging conventions:
	- Keep `config/package-solution.json` coherent with solution metadata and `.sppkg` output paths.
	- Preserve tenant-safe defaults (`skipFeatureDeployment`, `includeClientSideAssets`) unless intentionally changed.
3. Project layout conventions:
	- SPFx entry points and manifests remain under `src/webparts/...`.
	- Localization resources remain in `src/webparts/.../loc`.
	- Styling remains scoped via module SCSS files.
4. Security/compliance baseline:
	- Do not introduce secrets, tenant-specific credentials, or private endpoints into source.
	- Keep repository-wide legal and policy files (`LICENSE`, `SECURITY.md`) authoritative.

## Development Workflow and Quality Gates

1. Scope changes to the minimum demo(s) required by the exercise objective.
2. Before merge, validate in each changed demo folder:
	- `npm install`
	- `npm run build`
	- `npm test`
3. For functional/demo behavior changes, also run `gulp serve` and verify hosted workbench load.
4. Update markdown documentation when:
	- Toolchain versions change
	- Exercise steps change
	- Expected runtime behavior changes
5. Pull requests should include:
	- Which demo(s) were touched
	- Which validation commands were executed
	- Any curriculum impact or migration notes

## Governance

This constitution governs all planning and implementation artifacts under `.specify/` and all technical contributions in the repository.
In case of conflict, this document takes precedence over ad-hoc practices.
Amendments require:
1. A clear rationale tied to training goals or platform evolution.
2. A documented impact analysis across all three demos.
3. Synchronized updates to related templates or guidance documents when applicable.

Compliance checks are mandatory in reviews; non-compliant changes must be corrected before approval.

**Version**: 1.0.0 | **Ratified**: 2026-06-16 | **Last Amended**: 2026-06-16
