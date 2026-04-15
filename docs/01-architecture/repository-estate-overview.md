# Repository Estate Overview

This repository now contains two layers:

1. Legacy manual Claude skill-pack artifacts preserved from the older starter repo.
2. Phase-1 n8n-first estate artifacts used for the current Shadow Empire / Creator OS build.

## Phase-1 required artifact families
- Registries: workflow, route, approval, error
- Schemas: dossier + packet contracts
- n8n manifests: parent/system workflow contracts
- n8n workflow JSON exports: importable shells for local runtime
- Bootstrap CSVs: seed content for the five Data Tables
- Windows scripts: local bootstrap and validation helpers
- Docs: deployment state, setup, import order, governance

## Anti-drift rules
- Registries outrank prose.
- Workflow manifests outrank screenshots.
- Dossier writes are patch-oriented and namespace-aware.
- No secrets in tracked markdown or YAML.
- Runtime files never become source-of-truth.
