# Interface Contract
Project: XDV Domain Abstraction Layer
Specification: XDV-011
Forge: XdvDal

## Versioning
- Interface version: 0.1.0
- Capability model API version: 1
- Lifecycle API version: 1
- Stability tier: frozen_normative

## Contract Rules
- All domain invocations must pass through DAL API operations.
- Capability negotiation must occur before execute/project/transition operations.
- Lifecycle transitions are deterministic and table-driven.
- Cross-domain transitions require explicit cross-domain scope and token checks.
- Return code semantics are stable contract data.

## Public Surface
### Version APIs
- `xdv_dal_interface_version_major()`
- `xdv_dal_interface_version_minor()`
- `xdv_dal_interface_version_patch()`
- `xdv_dal_capability_model_version()`
- `xdv_dal_lifecycle_api_version()`

### Capability APIs
- `request_capability(...)`
- `validate_capability_token(...)`
- `revoke_capability(...)`
- `validate_capabilities(...)`

### Lifecycle APIs
- `domain_lifecycle_transition(...)`
- `request_cross_domain_transition(...)`
- `dal_init(...)`
- `dal_request_resources(...)`
- `dal_execute(...)`
- `dal_project(...)`
- `dal_terminate(...)`
- `dal_report_fault(...)`

## Deterministic Lifecycle States
- `Unbound`
- `Bound`
- `Initialized`
- `Active`
- `Suspended`
- `Terminated`
- `Released`

Allowed transitions are deterministic and enforced by DAL.

## Negative Enforcement Coverage
`src/dal_tests.ds` includes negative tests for:
- invalid lifecycle jumps,
- same-domain usage of cross-domain path,
- cross-domain scope violations,
- execute/project precondition failures,
- token age revocation path.

## Migration Notes
`xdv-dal` was split from `xdv-kernel/sector/xdv_dal` and now serves as the standalone versioned interface provider for kernel integration.
