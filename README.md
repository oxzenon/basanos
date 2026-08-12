BASANOS

Web3 Security Assessment Playbook

BASANOS is an adapted and expanded Web3 security assessment methodology for authorized security research and responsible disclosure.

It is designed for independent security researchers, bug bounty hunters, audit teams, and security-focused developers working across EVM smart contracts, DeFi, Rust, and Solana consensus and validator systems.

Find the weakness. Prove the impact. Kill the false positive. Disclose responsibly.

What BASANOS Is

BASANOS is a structured security assessment playbook built around a repeatable research lifecycle:

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

The methodology does not treat known vulnerability classes as the complete search space.

Known patterns are used as heuristics alongside:

protocol and architecture modeling

invariant analysis

attacker-capability modeling

state-machine analysis

sequence analysis

cross-contract composition

economic reasoning

fuzzing and dynamic testing

adversarial verification

reproducible proof

The objective is not to manufacture findings. The objective is to produce correct, reproducible, defensible security conclusions.

Core Principles

Authorized scope only

BASANOS is intended for authorized security work.

Authorization may come from:

a public bug-bounty scope

a signed engagement / statement of work

an explicit written owner grant

your own deployment

Publicly deployed code is not automatically permission to attack a live system.

Never exploit live systems

Testing and proof should remain inside:

local deployments

deterministic simulations

unit / integration harnesses

authorized forks

read-only queries

No real user funds should be moved and no live exploit transaction should be broadcast.

Prove before reporting

A suspicion is not automatically a finding.

The methodology requires the researcher to establish:

reachability

attacker capability

the affected security property

actual impact

relevant assumptions

reproducible evidence

Candidates that do not survive adversarial review should be rejected.

State the bound

Severity must reflect the actual demonstrated impact and the assumptions required to reach it.

BASANOS distinguishes between:

theoretical TVL
      ↓
reachable value
      ↓
exposed value
      ↓
extractable value
      ↓
demonstrated impact

Separate trust risk from permissionless exploitation

A privileged administrator having powerful capabilities is not automatically equivalent to an unprivileged exploit.

Centralization and trusted-role issues should be reported according to the target's scope and severity rules.

Kill your own findings

Before submission, challenge every candidate:

Is it actually reachable?

Is the attacker model realistic?

Is there an upstream protection?

Is the behavior intentional?

Is it already known?

Can the claimed impact actually be reproduced?

What is the strongest argument against the finding?

If the finding does not survive the counter-test, reject it.

EVM / DeFi Track

BASANOS provides a broad methodology for analyzing EVM smart contracts and DeFi systems.

Coverage includes:

reconnaissance and contract mapping

proxy and implementation discovery

deployment-vs-source verification

asset-flow and authority mapping

authorization and privilege analysis

accounting and solvency invariants

ERC-20 behavior assumptions

ERC-4626 and vault accounting

oracle and pricing assumptions

lending and liquidation logic

AMM / DEX integrations

external calls and callbacks

signatures and replay

governance and upgradeability

cross-contract composition

differential analysis

known vulnerability-pattern analysis

fuzzing and invariant testing

fork-based proof of concept

economic impact modeling

The EVM track explicitly requires multiple analytical passes:

PATTERN PASS
     ↓
INVARIANT PASS
     ↓
SEQUENCE PASS
     ↓
COMPOSITION PASS

This helps reduce dependence on known exploit patterns and forces deeper reasoning about protocol behavior.

Rust / Solana Track

The playbook separates Solana program security from consensus / validator research.

Solana program / Rust

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

Solana consensus / validator

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

A typical proof model is:

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

attacker capital
protocol loss
victim loss
attacker proceeds
fees / slippage
repeatability
net economic result

Multi-Agent Research

BASANOS is designed to support multiple analytical agents without relying on identical prompts.

Suggested lenses include:

Architecture / control-flow
Asset / accounting
Invariant / state-machine
Authorization / privilege
Oracle / economics
Composability / integration
Historical pattern research
Adversarial verification

Every serious finding should pass through an independent verifier whose job is to disprove it.

The goal is to reduce groupthink, duplicated analysis, and AI-generated false positives.

Severity

BASANOS uses impact, attacker capability, preconditions, capital requirements, repeatability, and exposure when reasoning about severity.

Suggested categories:

Critical — unauthorized, high-impact compromise with realistic attacker capability and material loss, corruption, or system-wide safety failure.

High — material compromise or repeatable loss with meaningful conditions or bounded exposure.

Medium — meaningful but limited or conditional impact.

Low — minor impact, edge conditions, or limited practical consequence.

Informational / Trust — design or trust assumptions without an unauthorized exploit path.

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

The intended process is:

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

For bug-bounty programs, follow the exact program scope, duplicate policy, severity criteria, submission channel, and disclosure rules.

Repository

The repository is intentionally simple:

basanos/
├── SKILL.md
├── README.md
└── LICENSE

SKILL.md

The complete operational security assessment playbook.

README.md

The public overview, methodology summary, and usage guidance.

LICENSE

The license and attribution terms governing the repository.

Using BASANOS

As an AI / Agent Skill

Place SKILL.md into the appropriate skills directory for your agent and invoke it when performing an authorized Web3 security assessment.

As a Manual Playbook

Read SKILL.md from start to finish and use the lifecycle, decision gates, coverage requirements, and proof standards as the assessment process.

Philosophy

A strong security assessment is not defined by how many Critical findings it produces.

It is defined by how convincingly the researcher can answer:

What did we test, what assumptions did we make, what did we prove, what did we reject, what could we not test, and what residual risk remains?

BASANOS is built around that discipline.

Author

BASANOS is maintained by Oxzenon.

Attribution & License

BASANOS is an adapted and expanded security assessment playbook derived from the original KENSHO methodology by Duke (@dukedotsol / cryptoduke01). This version has been renamed and substantially adapted by Oxzenon.

Licensed under CC BY 4.0, with attribution required.

See LICENSE.

