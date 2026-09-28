# Codex Agent Pack

This directory contains the executable Codex custom-agent pack for PIETY / Convicta AI Agency.

## Format
Each file uses the Codex custom-agent TOML fields:
- name
- description
- developer_instructions

## Installation
Copy the TOML files from `integrations/codex/agents/` to `~/.codex/agents/` on the machine running Codex.

## Entry point
Use **PIETY Convicta Orchestrator** as the default agent. It delegates to specialists according to `config/routing.yaml` and enforces `config/quality-gates.yaml`.

## Security
Do not add credentials, OAuth tokens, passwords, customer PII or unredacted production payloads to these files.
