# It-from-bit model — reproducibility code

Open reproducibility scripts for the it-from-bit / finite-QEC-substrate paper series.
This first set backs the baryogenesis paper:

> **Baryogenesis as a quantum-error-correction residue** — the matter–antimatter asymmetry
> as the undetectable-fault rate of a finite QEC substrate.
> Zenodo: https://zenodo.org/records/20723973

The central result is parameter-free given the fine-structure constant:

```
eta = n_B / n_gamma = (3/14) * alpha_0^4 = 6.08e-10     vs Planck 6.12(4)e-10  (-0.9 sigma)
```

## Running

```sh
pip install -r requirements.txt        # numpy, scipy
python3 python_code/item126_channel_ledger.py
```

Each script is **standalone** (numpy / scipy / standard library only) and **self-asserting**:
it prints its checks and exits `0` if and only if every assertion passes. Run any of them
directly; no configuration or data files are needed.

## What each script verifies

| Script | Verifies | Paper |
|--------|----------|-------|
| `item126_channel_ledger.py` | `eta = (3/14) alpha_0^4 = 6.08e-10` (−0.9σ); the 14 weight-4 logical channels are the AG(3,2) affine hyperplanes; the uniform 1/14 measure is derived | §4 |
| `item126_colour_count.py` | the 2-bit colour veto admits exactly 3 of the 14 weight-4 channels (the numerator of 3/14) | §4.3 |
| `item126_48set_count.py` | the honest state-ledger contrast: the 48-word matter set has 11 weight-4 *states* (not 14) — why the channel ledger, not the state ledger, carries the branching | §4.4 |
| `item126_sphaleron_conversion.py` | the `(B−L) → B = 28/79` electroweak-sphaleron conversion on the substrate's content (N_g=3, §2.8 hypercharges, ν_R), with B−L the unique conserved mode | §5 |
| `item126_baryon_sign_analysis.py` | the §2.7 bitwise complement is the CPT-*mass* map, not charge conjugation; under §2.8 C the census is symmetric except the Majorana neutrino — so the sign is dynamical, not a static count | §6 |
| `ckm_walk_signed_template.py` | the quark walk-CP engine reproduces a correct CKM (\|V_us\|=0.237), the canon bare \|J\|=4.33e-5, and the correct Jarlskog sign for the e^{+ikπ/4} orientation | §6 |
| `item87_lepton_cp_obstruction.py` | leptonic CP = 0 in the walk substrate, root-caused: the generation-flip CNOTs are gated by I3 and χ, so a generation decouples in every neutrino sector | §6 |
| `item87_missing_operator_search.py` | the virtual-colour-bridge route is a structural no-go; the type-I seesaw supplies the PMNS *angles* but not CP | §6 |
| `item87_majorana_cp_operator.py` | a complex-symmetric Majorana M_R *does* give physical leptonic CP (basis-invariant weak-basis invariants), with the sign tracking the M_R phase | §6 |
| `item87_MR_derivation_attempt.py` | δ_ν cannot be a dynamical walk output — the all-zeros ν_e is an exact eigenvalue-real eigenstate of the walk — so the phase is a geometric primitive | §6 |

## Status tiers (as in the paper)

- **Computed / parameter-free:** the magnitude `eta = (3/14) alpha_0^4`, the `alpha^4` scaling, the 3/14 branching, the existence of a non-cancelling net.
- **Inherited:** the `28/79` sphaleron conversion (standard physics on substrate inputs).
- **Geometric primitive / open:** the absolute sign of the asymmetry (the δ_ν phase; not walk-derivable).

See the paper for full definitions, the historical background, the discredited mechanisms, and the
honest scope of each claim.
