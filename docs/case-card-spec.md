# Case Card Spec

This document defines the minimum structure for a public Lucidity-Bench case card.

## Required Sections

Every case card should include:

1. `Summary`
2. `Task`
3. `What Went Wrong`
4. `When the Agent Should Have Woken Up`
5. `Outcome and Waste`
6. `Metric Snapshot`
7. `Lower-Cost Path`
8. `Evidence`

## Required Fields

Each published case should make the following fields explicit:

- case title,
- agent name or anonymized label,
- task family,
- environment or constraints,
- final status,
- failure family,
- pivot point,
- estimated turns or steps,
- estimated token burn or cost,
- LEI,
- DEE,
- Wake-Up Rate,
- Waste Ratio,
- key lesson.

## Evidence Standard

Accepted evidence can include:

- public raw trace,
- redacted trace excerpt,
- reviewer-visible private trace,
- structured event table derived from the trace.

Every case must state which evidence tier it uses.

## Redaction Rule

Redaction is allowed for secrets, internal identifiers, and private business context. Redaction is not allowed to remove the turns that explain the failure pattern.

## Publication Rule

Public case cards should optimize for clarity, not spectacle. The goal is to make loop and waste behavior legible enough that another reader can audit the lesson.
