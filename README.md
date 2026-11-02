# Oreslang Language Specification

**Status:** Editor's Draft (2026-11-01)  
**Scope:** Language semantics and cross-toolchain portability.  
**Implementation status:** This repository defines contracts to be implemented and tested; publication here is **not** proof that any backend implements them.

Oreslang is an actor-first systems language intended to combine checked ownership and borrowing, explicit failure propagation, typed functional composition, and portable concurrency with native and managed execution.

## Specification documents

1. [Core language](spec/language.md) — syntax, declarations, types, ownership, actors and ActorGroups, errors, matching, modules, and effects.
2. [Compiler and runtime contract](spec/compiler-runtime-contract.md) — HIR/MIR, LLVM and Truffle/GraalVM, lowering rules, runtime ABI, memory models, hot loading, and portable backends.
3. [Conformance and parity](spec/conformance.md) — shared fixtures, negative tests, optimization-equivalence checks, execution evidence, and CI gates.

4. [State containers and virtual actors](spec/state-containers-and-virtual-actors.md) — proposed contextual declaration grammar, protected mutable state, stable logical actor identity, activation, ownership, and backend admission gates.

## Interpretation

- **Established design decision**: previously chosen Oreslang surface or semantic direction; remains subject to implementation and conformance.
- **Proposed normative contract**: precise rule proposed for ratification; **MUST / MUST NOT / SHOULD** are binding only once accepted.
- **Open question**: intentionally unresolved; no implementation should silently fill the gap with backend-specific behavior.
- **Illustrative syntax**: examples demonstrate intent but do not certify parser support.

This is a versioned **draft**, not a claim of five-backend feature parity. Backend status must be recorded only with attributable compiler/runtime evidence.

## Portability doctrine

**One language semantics, one versioned semantic IR contract, independent execution engines, shared behavioral conformance.**

LLVM IR is not the Oreslang specification. The Java implementation of Truffle nodes is not the Oreslang specification. Each implementation must preserve the same observable language behavior, while retaining freedom to optimize storage, scheduling, JIT/AOT compilation, and memory management.

Targeted implementations:

- Java/GraalVM (Truffle)
- LLVM native
- WebAssembly
- Cranelift/Forge
- .NET Native AOT

Names of the backends denote targets, not a claim that each target currently passes the contract.

## Contribution and evolution

Proposals must identify affected syntax, type/effect rules, error behavior, actor lifecycle, memory safety, and backend portability; add shared positive and negative examples; and state compatibility impact. A grammar change without a cross-backend diagnostic and behavior plan is incomplete.

Normative changes should be accompanied by a conformance fixture ID. Do not mark a behavior as verified based on source inspection alone, a pending test, or a workflow that did not execute any steps.
