# CLAUDE.md — infiotinc/frr (Infiot-patched FRRouting)

> DRAFT. `TODO(owner)` = needs a human to fill in.

## What this is
Fork of FRRouting carrying Infiot/Netskope patches for the BWAN product.
It is consumed by the main repo `infiotinc/infiot` (see `cplane/frr/frr.mk`
there, which pins the FRR base version and the Infiot branch, currently
`infiot-frr-6.0.3-rel-r5.2` — verify before assuming).

## Branches
- `infiot-frr-6.0.3-rel-r5.2` — branch the product build uses (check `frr.mk`).
- Upstream FRR docs live in `doc/`; upstream build is autotools (`bootstrap.sh`, `configure.ac`).

## Conventions
- Commit subject starts with the Jira key, e.g. `BWAN-15286: reset bgp for peer timer attribute config`.
- Keep Infiot changes minimal and isolated to ease upstream merges.
- Unit/topology tests: `tests/` (topotests, upstream pytest framework).

## Build / test
- Product build happens from the infiot repo (cross-compiled, `make cplane-publish`).
- Standalone: `./bootstrap.sh && ./configure ... && make` (flags used by the product: see `frr-configure-flags` in infiot `cplane/frr/frr.mk`).
- Functional testing of FRR changes is done through the BWAN testbeds
  (`infiot/dplane/dpe2etest`, e.g. `hub_bgp` suite). `TODO(owner)`: topotests status.

## Known issues
Record in `infiot/doc/known-issues.md` (single place), tagged `Area: frr`.
