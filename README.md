# XDV Domain Abstraction Layer
Version: 0.1.1
Status: active-split
Language: Dust Programming Language (DPL)

## Specification Alignment
Primary specification: XDV-011 in `xdv-spec`.

## Purpose
`xdv-dal` defines the deterministic domain interface boundary across K, Q, and Phi domains.
It provides:
- capability negotiation and token validation,
- lifecycle transition validation,
- operation precondition enforcement,
- deterministic status/error signaling for orchestration.

## Scope Implemented in 0.1.1
- Versioned interface surface (`0.1.0`) plus DAL API version markers.
- Capability model with operation-specific requirements.
- Deterministic lifecycle state machine:
  - `Unbound -> Bound -> Initialized -> Active -> Suspended/Terminated -> Released`
- Cross-domain transition guardrails and scope validation.
- Negative tests for invalid transitions and invalid cross-domain paths.

## Stable Interface Contract
- Core implementation: `src/dal.ds`
- Interface surface: `src/dal_interface.ds`
- Contract doc: `docs/interface_contract.md`

Exported interface version functions:
- `xdv_dal_interface_version_major()`
- `xdv_dal_interface_version_minor()`
- `xdv_dal_interface_version_patch()`

Exported API model version functions:
- `xdv_dal_capability_model_version()`
- `xdv_dal_lifecycle_api_version()`

## Repository Layout
- `src/` implementation and tests (`dal.ds`, `dal_interface.ds`, `dal_tests.ds`)
- `tests/` standalone suite placeholders
- `docs/` architecture and interface references
- `State.toml` workspace manifest
- `changelog.md` release notes

## Build
`cargo run --manifest-path dust/Cargo.toml -- check xdv-dal/src`

## Integration Notes
- Consumers should call DAL operations through versioned interfaces and status codes.
- Cross-domain transitions must route through `request_cross_domain_transition`.
- Direct manager-to-manager transition calls are treated as invalid by DAL contract.
