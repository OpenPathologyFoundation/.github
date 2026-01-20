<p align="center">
  <img alt="Open Pathology Foundation" src="https://raw.githubusercontent.com/<ORG>/<REPO>/main/assets/banner.svg" width="900" />
</p>

<p align="center">
  <a href="https://github.com/<ORG>"><img alt="GitHub Org" src="https://img.shields.io/badge/Open%20Pathology-Foundation-2ea44f"></a>
  <img alt="Status" src="https://img.shields.io/badge/status-active%20build-0ea5e9">
  <img alt="Focus" src="https://img.shields.io/badge/focus-workflow%20orchestration%20%2B%20viewing-8b5cf6">
</p>

# Open Pathology Foundation

A shared, modular ecosystem for digital pathology workflows, viewing, and computational pathology.

> [!NOTE]
> The point is not to win an argument about formats or standards.
> The point is to make digital pathology and AI deployable, testable, and safe at scale.

## Why this exists

Digital pathology and AI are advancing faster than institutions can safely adopt them. The bottleneck is not compute. It is structure.

Most pathology stacks are assembled from point integrations and local workarounds. They function, but they do not evolve gracefully. Every upgrade becomes a project. Validation becomes local. Safety arguments become fragile. Innovation becomes slow.

Pathology operations are a chain of stateful handoffs across accessioning, grossing, histology, slide creation, scanning, QC, signout, distribution, and downstream analytics. If the software substrate is not modular and testable, the whole system remains expensive to change.

This foundation exists to build that substrate.

> [!TIP]
> If you have a mature local informatics system, you already know the pattern:
> you end up building the missing layer yourself. This project is about making that effort reusable.

## The boundary we want: tiles, not files

File formats will evolve. They should. New encoders, new compression, new metadata schemes, new ways to represent multi-scale imaging will keep arriving.

The integration boundary should not be the file format.

The integration boundary should be a consistent tile service contract, plus a small set of associated metadata and access-control rules.

If a system can expose tiles in a predictable way, then:
- a viewer can render without vendor-specific client codecs
- AI pipelines can run consistently across sources
- QC can be standardized and automated
- annotations and audit can be governed and transported
- institutions can adopt new formats without rewriting everything above the storage layer

This is not anti-innovation. It is pro-deployment.

> [!IMPORTANT]
> If you can open access to a tile server (with proper authn/authz), you unlock viewing, QC, and AI without forcing every downstream component to care about your underlying file format.

## Projects

### Okapi
Okapi is the orchestration kernel for anatomic pathology workflows.

It targets the missing middle layer:
- explicit state machines for operational workflows
- event capture and provenance
- routing and gating (including failure recovery)
- policy-driven automation with human-in-the-loop handoffs
- auditable integration between LIS, IMS, scanners, QC services, and AI

Okapi is intended to be boring in the best sense: predictable behavior, clear contracts, clean audit trails.

### Pelican
Pelican is the format-agnostic viewing and tile-access layer.

It treats tile delivery and viewer composition as first-class infrastructure:
- a stable tile service contract as the integration target
- a viewer core designed for extension (subspecialty needs differ)
- pluggable adapters for diverse backends and formats
- governance-sensitive capabilities (annotations, QC, audit)

Pelican is meant to be adoptable incrementally. Start with viewing. Add QC hooks. Add annotation governance. Add AI.

## Principles

- Safety and auditability are product requirements.
- Explicit state beats implied convention.
- Stable contracts beat bespoke glue.
- Incremental adoption matters. Institutions should be able to deploy pieces without buying an entire stack.
- Vendor participation is welcome. Differentiation should happen above the shared core, not by locking down the core.

> [!CAUTION]
> Pathology is often underinvested relative to its clinical leverage.
> Waiting for the perfect commercial roadmap is usually a slow way to get to a working system.
> Shared infrastructure reduces the cost of progress.

## How to engage

### Institutions
- Pilot where you feel the most pain: viewing access, QC pipelines, workflow routing, audit, or interoperability testing.
- Contribute requirements, test cases, and de-identified fixtures.
- Help define what “safe enough” means for real operations.

### Vendors
- Build adapters and modules against stable contracts.
- Contribute conformance tooling and reproducible deployment patterns.
- Offer hardened packaging, validation artifacts, and enterprise support on top of the open core.

### Researchers
- Use the substrate for reproducible evaluation and deployment.
- Contribute reference pipelines, evaluation harnesses, and UI extensions.
- Help convert good ideas into code that can survive outside a single lab.

## Governance and sustainability

This has to outlive any one developer, any one institution, and any one funding cycle. The intent is to build:
- transparent technical governance
- interface stability rules
- security practices appropriate for clinical systems
- conformance tests and compatibility badges
- a contribution model that supports both academic and commercial participation

## Get started

- Browse the repositories in this organization.
- Look for issues labeled `good first issue` and `help wanted`.
- Propose interface contracts and test fixtures before large implementations.
- If you are evaluating production use, open a discussion early. Validation and safety expectations should be explicit.

## Selected works informing this model

- Baldwin and Clark, Design Rules: The Power of Modularity
- Defense Innovation Board, Software Is Never Done
- Tozzi and Zittrain, For Fun and Profit
- Gershkovich and Sinard, Customizing Laboratory Information Systems
- Pathology Informatics Summit proceedings (evidence of widespread local software development in pathology)

## License

Per repository. The default intent is permissive licensing for shared core infrastructure (commonly Apache-2.0), with clear governance around project names and compatibility marks.

## Contributing

See `CONTRIBUTING.md` and `CODE_OF_CONDUCT.md`.
