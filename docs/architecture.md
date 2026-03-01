# Architecture

XDV Domain Abstraction Layer (`xdv-dal`) is structured in two layers:

1. Stable interface surface (`src/dal_interface.ds`)
2. Deterministic implementation layer (`src/dal.ds`)

## Core Components
- Capability model
  - negotiation (`request_capability`)
  - validation (`validate_capability_token`)
  - revocation (`revoke_capability`)
- Lifecycle model
  - state transition gate (`domain_lifecycle_transition`)
  - cross-domain transition gate (`request_cross_domain_transition`)
- Operation lifecycle API
  - `dal_init`, `dal_request_resources`, `dal_execute`, `dal_project`, `dal_terminate`, `dal_report_fault`

## Determinism Contract
- No implicit cross-domain path.
- No direct manager-to-manager transition bypass.
- Status-code return values are stable and contract-visible.
