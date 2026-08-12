<div align="center">

BASANOS

Web3 Security Assessment Playbook

Find the weakness. Prove the impact. Kill the false positive. Disclose responsibly.

<br>






<br>

BASANOS is an adapted and expanded Web3 security assessment methodology for authorized security research and responsible disclosure.

</div>

What BASANOS Is

BASANOS is a structured security assessment playbook for independent security researchers, bug bounty hunters, audit teams, and security-focused developers working across:

EVM smart contracts

DeFi protocols

Rust / Solana programs

Solana consensus and validator systems

The methodology is designed to move beyond simply searching for known vulnerability patterns.

AUTHORIZE
    ↓
SCOPE
    ↓
RECON
    ↓
MODEL
    ↓
EXTRACT INVARIANTS
    ↓
MODEL ATTACKER
    ↓
ENUMERATE STATE TRANSITIONS
    ↓
ANALYZE
    ↓
TEST
    ↓
PROVE
    ↓
COUNTER-PROVE
    ↓
QUANTIFY IMPACT
    ↓
RATE
    ↓
REPORT
    ↓
VERIFY FIX

A hypothesis is not a finding until its reachability, violated security property, attacker capability, and impact have been demonstrated in an authorized test environment.

Core Philosophy

BASANOS does not treat known vulnerability classes as the complete search space.

Known patterns are used as heuristics alongside:

Research Lens

Purpose

🧩 Protocol & architecture modeling

Understand how the system actually works

🔒 Invariant analysis

Identify properties that must always hold

🎯 Attacker modeling

Define realistic attacker capabilities

🔄 State-machine analysis

Find bugs that emerge across sequences

🧬 Composition analysis

Examine interactions between components

💰 Economic reasoning

Determine whether a weakness creates real value

🧪 Fuzzing & dynamic testing

Stress assumptions and boundaries

🛡️ Adversarial verification

Attempt to kill false positives

📐 Reproducible proof

Establish evidence another researcher can validate

The objective is not to manufacture findings.

The objective is to produce correct, reproducible, and defensible security conclusions.

Operating Principles

<details>
<summary><strong>01 — Authorized scope only</strong></summary>

BASANOS is intended for authorized security work.

Authorization may come from:

a public bug-bounty scope

a signed engagement / statement of work

an explicit written owner grant

your own deployment

Publicly deployed code is not automatically permission to attack a live system.

</details>

<details>
<summary><strong>02 — Never exploit live systems</strong></summary>

Testing and proof should remain inside:

local deployments

deterministic simulations

unit / integration harnesses

authorized forks

read-only queries

No real user funds should be moved and no live exploit transaction should be broadcast.

</details>

<details>
<summary><strong>03 — Prove before reporting</strong></summary>

A suspicion is not automatically a finding.

The methodology requires establishing:

reachability

attacker capability

affected security property

actual impact

relevant assumptions

reproducible evidence

Candidates that do not survive adversarial review should be rejected.

</details>

<details>
<summary><strong>04 — State the bound</strong></summary>

Severity must reflect the actual demonstrated impact and the assumptions required to reach it.

BASANOS distinguishes:

Theoretical TVL
      ↓
Reachable Value
      ↓
Exposed Value
      ↓
Extractable Value
      ↓
Demonstrated Impact

</details>

<details>
<summary><strong>05 — Kill your own findings</strong></summary>

Before submission, challenge every candidate:

Is it actually reachable?

Is the attacker model realistic?

Is there an upstream protection?

Is the behavior intentional?

Is it already known?

Can the claimed impact actually be reproduced?

What is the strongest argument against the finding?

If the candidate does not survive the counter-test, reject it.

</details>

EVM / DeFi Track

BASANOS provides a broad methodology for analyzing EVM smart contracts and DeFi systems.

Coverage

Reconnaissance and contract mapping

Proxy and implementation discovery

Deployment-vs-source verification

Asset-flow and authority mapping

Authorization and privilege analysis

Accounting and solvency invariants

ERC-20 behavior assumptions

ERC-4626 and vault accounting

Oracle and pricing assumptions

Lending and liquidation logic

AMM / DEX integrations

External calls and callbacks

Signatures and replay

Governance and upgradeability

Cross-contract composition

Differential analysis

Known vulnerability-pattern analysis

Fuzzing and invariant testing

Fork-based proof of concept

Economic impact modeling

Four Independent Analytical Passes

┌───────────────┐
│  PATTERN PASS │
└───────┬───────┘
        ↓
┌─────────────────┐
│ INVARIANT PASS  │
└───────┬─────────┘
        ↓
┌─────────────────┐
│  SEQUENCE PASS  │
└───────┬─────────┘
        ↓
┌───────────────────┐
│ COMPOSITION PASS  │
└───────────────────┘

This reduces dependence on known exploit patterns and forces deeper reasoning about protocol behavior.

Rust / Solana Track

BASANOS separates Solana program security from consensus / validator research.

Solana Program / Rust

Focus areas include:

instruction and account modeling

signer and ownership validation

PDA derivation and authority relationships

account substitution

initialization and reinitialization

CPI trust boundaries

arithmetic and truncation

serialization / deserialization

panic and error paths

upgrade authority

migration and state-version handling

Solana Consensus / Validator

Focus areas include:

consensus safety

liveness

certificate verification

stake thresholds

stake double-counting

BLS aggregation and domain separation

boundary conditions

split-vote semantics

equivocation

persistence ordering

migration / handover seams

dissemination and repair-response validation

adversarial state-machine testing

Evidence & Proof

BASANOS emphasizes reproducible evidence.

A proof should be:

deterministic

reproducible

pinned to a commit or block

isolated from live funds

explicit about assumptions

quantitative where appropriate

Typical Proof Model

BEFORE
  ↓
AUTHORIZED TEST SEQUENCE
  ↓
AFTER
  ↓
SECURITY PROPERTY / INVARIANT VIOLATION
  ↓
IMPACT

For financially material issues, quantify:

Attacker Capital
      ↓
Protocol Loss
      ↓
Victim Loss
      ↓
Attacker Proceeds
      ↓
Fees / Slippage
      ↓
Repeatability
      ↓
Net Economic Result

Multi-Agent Research

BASANOS is designed to support multiple analytical agents without relying on identical prompts.

Suggested Lenses

Agent

Lens

01

Architecture / control-flow

02

Asset / accounting

03

Invariant / state-machine

04

Authorization / privilege

05

Oracle / economics

06

Composability / integration

07

Historical pattern research

08

Adversarial verification

Every serious finding should pass through an independent verifier whose job is to disprove it.

The goal is to reduce:

groupthink

duplicated analysis

AI-generated false positives

Severity

BASANOS considers:

Impact
×
Attacker Capability
×
Preconditions
×
Capital Requirement
×
Repeatability
×
Exposure

Suggested Categories

Severity

Meaning

🔴 Critical

Unauthorized, high-impact compromise with realistic attacker capability and material loss, corruption, or system-wide safety failure

🟠 High

Material compromise or repeatable loss with meaningful conditions or bounded exposure

🟡 Medium

Meaningful but limited or conditional impact

🔵 Low

Minor impact, edge conditions, or limited practical consequence

⚪ Informational / Trust

Design or trust assumptions without an unauthorized exploit path

The target program's own bounty rules always take precedence.

Reporting

A BASANOS finding should clearly communicate:

ROOT CAUSE
SECURITY PROPERTY VIOLATED
ATTACKER MODEL
PRECONDITIONS
STATE SEQUENCE
IMPACT
EVIDENCE
PROOF
COUNTER-PROOF
RECOMMENDED FIX
SCOPE / ASSUMPTIONS

The objective is a report that another researcher or protocol team can independently validate.

Responsible Disclosure

BASANOS is designed around good-faith, private disclosure.

IDENTIFY
    ↓
VERIFY
    ↓
DOCUMENT
    ↓
PRIVATELY DISCLOSE
    ↓
SUPPORT REMEDIATION
    ↓
VERIFY THE FIX

Never threaten, extort, or condition disclosure on payment.

For bug-bounty programs, follow the exact:

program scope

duplicate policy

severity criteria

submission channel

disclosure rules

Repository

basanos/
├── SKILL.md
├── README.md
└── LICENSE

File

Purpose

SKILL.md

Complete operational security assessment playbook

README.md

Public overview, methodology summary, and usage guidance

LICENSE

License and attribution terms governing the repository

Using BASANOS

As an AI / Agent Skill

Place SKILL.md into the appropriate skills directory for your agent and invoke it when performing an authorized Web3 security assessment.

As a Manual Playbook

Read SKILL.md from start to finish and use the lifecycle, decision gates, coverage requirements, and proof standards as the assessment process.

Philosophy

A strong security assessment is not defined by how many Critical findings it produces.

It is defined by how convincingly the researcher can answer:

What did we test?
What assumptions did we make?
What did we prove?
What did we reject?
What could we not test?
What residual risk remains?

BASANOS is built around that discipline.

Author

<div align="center">

Oxzenon

BASANOS is maintained by Oxzenon.

</div>

Attribution & License

BASANOS is an adapted and expanded security assessment playbook derived from the original KENSHO methodology by Duke (@dukedotsol / cryptoduke01).

This version has been renamed and substantially adapted by Oxzenon.

Licensed under CC BY 4.0, with attribution required.

See LICENSE.

<div align="center">

BASANOS

Find the weakness. Prove the impact. Kill the false positive.

</div>
