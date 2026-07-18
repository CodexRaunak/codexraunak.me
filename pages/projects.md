---
title: "Projects"
description: "Selected projects — FHIR terminology services, docs infrastructure, and OpenRewrite tooling."
---

A few things I've built or meaningfully moved forward.

## NAMASTE–ICD-11 Integration API

A FHIR R4–compliant terminology microservice that integrates India's NAMASTE codes with
the WHO ICD-11 Traditional Medicine Module 2 (TM2), for interoperability across Indian
EHR/EMR systems. I designed an automated terminology pipeline that curated 468 clinical
mappings (218 equivalent + 250 related) across 296 NAMASTE and 437 ICD-11 TM2 concepts
using a five-stage mapping workflow with automated validation, and exposed it through
high-performance REST APIs (FastAPI + SQLite FTS5) with millisecond-level lookup and
FHIR ConceptMap generation.

*Winner, Smart India Hackathon 2025 internal round.*
**Stack:** Python, FastAPI, SQLite, FTS5, Pandas, fhir.resources

## Meshery docs: Jekyll → Hugo migration

Migrated `docs.meshery.io` — 2,800 documentation pages and 31,400 static files — from
Jekyll to Hugo, cutting full builds by 4–5× and incremental builds by ~90×. Also resolved
API wire-contract drift after an upstream snake_case → camelCase schema migration.

**Stack:** Hugo, Jekyll, Go, JavaScript, Next.js, OpenAPI Specification

## Jenkins Plugin Modernizer (GSoC)

A CLI tool that automates the modernization of Jenkins plugins. I implemented automated
extraction and storage of modernization metadata, and multiple declarative and imperative
OpenRewrite recipes that drive the transformations.

**Stack:** Java, OpenRewrite, Python, JSON Schema

## TaskHub

A small project I use as a running example when explaining containers and deployment —
including in the Docker series on this site.

[github.com/CodexRaunak/taskhub](https://github.com/CodexRaunak/taskhub)

---

More on [GitHub](https://github.com/CodexRaunak).
