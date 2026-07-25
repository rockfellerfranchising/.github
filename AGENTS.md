# Rockfeller GitHub Configuration — Agent Guide

## Purpose

This repository provides organization-level GitHub issue templates, reusable workflows and governance defaults. Treat each workflow input, secret and permission as a cross-repository contract.

## Working rules

1. Use code-review-graph MCP where it covers workflow/configuration relations; otherwise inspect only the relevant YAML and its consumers.
2. Make reusable workflow changes backward-compatible. Preserve input names, required secrets, permissions and output shapes unless a migration is documented.
3. Apply least privilege to `permissions`, do not echo secrets, and pin/maintain trusted actions deliberately.
4. Keep templates concise, actionable and free of customer data, private URLs and operational tokens.

## Validation and documentation

- Validate YAML, action syntax and representative caller workflows before handoff.
- Ensure quality workflows fail closed and deploy workflows run only after their appropriate gate.
- Keep `README.md` in PT-BR and this guide in English. `CLAUDE.md` and `CONTRIBUTING.md` are symlinks to this file.
