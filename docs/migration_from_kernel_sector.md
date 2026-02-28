# Migration From Kernel Sector
Origin sector: xdv-kernel/sector/xdv_dal
## Immediate state
- Source files copied into standalone src/.
- Kernel sector remains intact for current build compatibility.
## Recommended migration sequence
1. Keep behavior parity tests passing in both locations.
2. Switch kernel consumers to dependency on this standalone package.
3. Remove duplicated sector implementation only after dependency cutover and parity validation.
