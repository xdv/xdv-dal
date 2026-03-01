# Changelog

## 0.1.1 - XDV-011 Capability/Lifecycle Finalization
- Finalized deterministic capability model in `src/dal.ds`:
  - operation-specific required capabilities,
  - explicit capability negotiation (`request_capability`),
  - token validation/revocation helpers.
- Finalized lifecycle API in `src/dal.ds`:
  - deterministic lifecycle transition table,
  - cross-domain transition enforcement path,
  - operation precondition checks (`dal_execute`, `dal_project`, etc.).
- Versioned interface surface in `src/dal_interface.ds`:
  - namespaced interface surface version methods,
  - capability model and lifecycle API surface version markers.
- Added concrete negative tests in `src/dal_tests.ds` for invalid cross-domain and lifecycle transitions.

## 0.1.0 - Sector Split Baseline
- Created standalone project from `xdv-kernel/sector/xdv_dal`.
- Copied source module and tests into `src/`.
- Added stable interface file: `src/dal_interface.ds`.
- Added initial docs and interface contract.
- Added LICENSE copied from `xdv-os/LICENSE`.
