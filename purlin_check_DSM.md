# Roof Purlin Check -- Z8x2.5, DSM (Appendix 1)

| | |
|---|---|
| **Project** | Example PEB Project |
| **Member** | Purlin line P-1, unbraced condition (e.g., during erection, before deck attached) |
| **Specification** | AISI S100-16 |
| **Design method** | ASD |
| **Date** | 2026-08-19 |

## Assumptions

- Mcre/Mcrl/Mcrd are PLACEHOLDER example values -- replace with CUFSM finite-strip output for the actual section

## Demands (illustrative, same as EWM case)

| Quantity | Value | Unit | Reference |
|---|---:|---|---|
| Ma | 34.200 | kip-in | wL^2/8 |


## Flexure -- DSM (Appendix 1 Sec. 1.2.2)

**Flexural strength -- DSM, Appendix 1 Sec. 1.2.2**

| Quantity | Value | Unit | Reference |
|---|---:|---|---|
| My = Sf*Fy | 104.500 | kip-in |  |
| Mcre | 220 | kip-in | input, from finite-strip analysis |
| Mne (global) | 100.791 | kip-in | Eq. 1.2.2-2/3/4 |
| Mcrl | 95 | kip-in | input, from finite-strip analysis |
| Mnl (local, using Mne) | 84.014 | kip-in | Eq. 1.2.2-5/6 |
| Mcrd | 60 | kip-in | input, from finite-strip analysis |
| Mnd (distortional) | 65.983 | kip-in | Eq. 1.2.2-7/8 |
| Mn = min(Mnl, Mnd) | 65.983 | kip-in | governing |
| AVAILABLE STRENGTH Rn/Omega | 39.511 | kip-in | ASD |

> Governing mode: distortional.


## Limit state summary

| Limit state | Demand | Capacity | Ratio | Status |
|---|---:|---:|---:|:---:|
| Flexure, DSM (App. 1) | 34.200 | 39.511 | 0.866 | **OK** |

## Conclusion

All 1 limit states checked are satisfied. Maximum utilisation **0.866** (86.6%), governed by **Flexure, DSM (App. 1)**.

**The member is ADEQUATE for the limit states checked below, under the stated assumptions.**

### Scope of this check

The following were **NOT** evaluated and remain the engineer's responsibility:

- Shear, combined bending+shear, web crippling, deflection -- not repeated here, see EWM sheet

### Warnings

- Elastic buckling values (Mcre, Mcrl, Mcrd) are NOT computed by this script -- they must come from a finite-strip analysis of the exact cross-section.

---

*Computer-generated calculation sheet. Values must be independently verified against the AISI S100-16 Specification (and applicable Supplements/errata) before use in construction. This sheet is not a substitute for review and sealing by a licensed structural engineer. Several functions in this library use simplified or engineer-supplied coefficients (see aisi_s100.py module docstring, "VERIFICATION STATUS") -- confirm those against the current edition before relying on this sheet.*