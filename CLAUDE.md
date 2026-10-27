# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

This is a course project (CCE395, "Project 1") currently at the **specification stage**: the repo contains only `README.md` (proposal), `SPEC.md` (requirements), and `AI_USE.md` (AI usage log). No source code, dependency manifest, tests, or build tooling exist yet. Commands for build, lint, and tests should be added here once that tooling is introduced.

## What is being built

A Python 3.10+ tool (pandas, numpy, scipy, matplotlib) that reads Wi-Fi RSSI measurements taken across a floor plan and writes a heatmap PNG. `SPEC.md` is the source of truth; its numbered requirements are what the implementation is graded and tested against:

- **R1** Input is a CSV with columns `x,y,rssi` (coordinates plus RSSI in dBm), at least 20 points.
- **R2** 2D spatial interpolation over unmeasured grid points (SciPy).
- **R3** Output a color-coded heatmap saved as `.png`.
- **R4** Include a legible colorbar labeled in dBm.
- **R5** Fewer than 20 points or missing fields → print an error message and exit cleanly (no traceback).

Constraints: must render in under 10 seconds for a live demo, and must run on macOS, Windows, and Linux.

The planned pipeline follows the proposal's role split: CSV ingestion/validation → interpolation onto a grid → matplotlib rendering. Keeping these as separate, independently testable stages maps directly onto R1/R5, R2, and R3/R4.

## Repository conventions

- `AI_USE.md` is a required log of AI assistance (date, tool, purpose, outcome). When AI tools contribute meaningfully to the project, a row should be added there; ask the user before editing it.
- When requirements change, update `SPEC.md` rather than only the code, and keep requirement IDs (R1–R5) stable so they can be referenced from tests.
