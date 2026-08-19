# Roof Purlin Check -- Z8x2.5, EWM

| | |
|---|---|
| **Project** | Example PEB Project |
| **Member** | Purlin line P-1, typical interior span |
| **Specification** | AISI S100-16 |
| **Design method** | ASD |
| **Date** | 2026-08-19 |

## Assumptions

- Simple-span, uniformly loaded, single span 20 ft
- Purlin spacing 3.0 ft
- Loads: D=3.0 psf, Lr=16.0 psf (ASD combination D+Lr)
- Top flange assumed continuously braced by roof panel for this EWM run -- LTB (Sec. C3.1.2) not evaluated; see DSM sheet below for an unbraced-condition example instead

## Demands (illustrative)

| Quantity | Value | Unit | Reference |
|---|---:|---|---|
| w (D+Lr) | 0.0570 | kip/ft | ASD |
| Ma | 34.200 | kip-in | wL^2/8 |
| Va | 0.5700 | kips | wL/2 |
| Deflection | 0.8330 | in | 5wL^4/384EI |


## Flexure (Sec. C3.1.1)

**Flexural strength -- section (yielding), C3.1.1**

| Quantity | Value | Unit | Reference |
|---|---:|---|---|
| Se | 1.850 | in^3 | user-supplied Se_top/Se_bot |
| Fy | 50 | ksi | A1003 Gr.50 (ST50H) |
| Mn = Se*Fy | 92.500 | kip-in | Eq. C3.1.1-1 |
| AVAILABLE STRENGTH Rn/Omega | 55.389 | kip-in | ASD |


## Shear (Sec. C3.2.1)

**Shear strength, C3.2.1**

| Quantity | Value | Unit | Reference |
|---|---:|---|---|
| h/t | 125.424 |  |  |
| branch | elastic buckling |  |  |
| Fv | 9.063 | ksi |  |
| Aw = h*t | 0.4400 | in^2 |  |
| Vn = Aw*Fv | 3.988 | kips | Eq. C3.2.1-1/2/3 |
| AVAILABLE STRENGTH Rn/Omega | 2.388 | kips | ASD |

> phi_v=0.90/Omega_v=1.67 used as a single conservative pair across all h/t ranges -- verify the range-dependent phi_v/Omega_v split in Table C3.2.1-1 of your edition before final use.


## Combined bending + shear (Sec. C3.3.1)


## Deflection


## Limit state summary

| Limit state | Demand | Capacity | Ratio | Status |
|---|---:|---:|---:|:---:|
| Deflection <= L/180 | 0.8330 | 1.333 | 0.625 | **OK** |
| Flexure, Se*Fy (C3.1.1) | 34.200 | 55.389 | 0.617 | **OK** |
| Combined bending + shear, C3.3.1 | 0.4382 | 1 | 0.438 | **OK** |
| Shear (C3.2.1) | 0.5700 | 2.388 | 0.239 | **OK** |

## Conclusion

All 4 limit states checked are satisfied. Maximum utilisation **0.625** (62.5%), governed by **Deflection <= L/180**.

**The member is ADEQUATE for the limit states checked below, under the stated assumptions.**

### Scope of this check

The following were **NOT** evaluated and remain the engineer's responsibility:

- Lateral-torsional buckling (Sec. C3.1.2) -- assumed continuously braced by roof panel; verify actual bracing and fastener pattern per Sec. D6.1
- Web crippling at supports/load points (Sec. C3.4) -- needs the actual bearing length N and support condition
- Continuous-span (2-/3-span) moment and shear envelope -- this example used a conservative single simple span only
- Fastener/connection design to structural frame

### Warnings

- ALL section properties are illustrative placeholders -- replace with verified SSMA catalog or section-software output before use on a real project.

---

*Computer-generated calculation sheet. Values must be independently verified against the AISI S100-16 Specification (and applicable Supplements/errata) before use in construction. This sheet is not a substitute for review and sealing by a licensed structural engineer. Several functions in this library use simplified or engineer-supplied coefficients (see aisi_s100.py module docstring, "VERIFICATION STATUS") -- confirm those against the current edition before relying on this sheet.*