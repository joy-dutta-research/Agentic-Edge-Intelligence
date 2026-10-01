# Scenario Provenance

The experiment uses the public [RESCO traffic-signal benchmark](https://github.com/Pi-Star-Lab/RESCO) at commit `f1ed9a174f8de41fc9d8689373b836bc882570dc`. Cologne-8 supplies the eight-signal urban network for the confirmatory evaluation; Cologne-3 supplies the smaller three-signal corridor for the separate cross-network follow-up. The experiment keeps the benchmark road geometry, routes, demand, and signal programs rather than redrawing them.

## Licence scope at the pinned RESCO commit

| Material | Upstream licence | Scope in this study |
|---|---|---|
| [RESCO software](https://github.com/Pi-Star-Lab/RESCO/blob/f1ed9a174f8de41fc9d8689373b836bc882570dc/LICENSE) | GNU GPL v3.0 | Fetched into `external/RESCO`; not committed here. |
| `patches/resco_v2_deterministic_seed.patch` | GNU GPL v3.0 | A modification of RESCO source files; distributed under GPL v3. |
| [Cologne-3 scenario/data files](https://github.com/Pi-Star-Lab/RESCO/blob/f1ed9a174f8de41fc9d8689373b836bc882570dc/resco_benchmark/environments/cologne3/LICENSE) | CC-BY-NC-SA-3.0 | The road network, routes and demand, signal programs, and related scenario assets used for the cross-network follow-up. |
| [Cologne-8 scenario/data files](https://github.com/Pi-Star-Lab/RESCO/blob/f1ed9a174f8de41fc9d8689373b836bc882570dc/resco_benchmark/environments/cologne8/LICENSE) | CC-BY-NC-SA-3.0 | The road network, routes and demand, signal programs, and related scenario assets used for the confirmatory evaluation. |

The Cologne environments retain their own CC-BY-NC-SA-3.0 licences; they are not relicensed by RESCO's GPL-3.0 software licence. Their data derive from the [TAPAS Cologne scenario](https://sumo.dlr.de/docs/Data/Scenarios/TAPASCologne.html#availability), whose source and availability conditions are recorded by SUMO. The upstream checkout is fetched rather than copied into this repository. Original study code outside the GPL patch remains under the repository's MIT licence. Anyone redistributing or adapting the fetched Cologne assets must follow their upstream attribution, non-commercial, and share-alike terms.

From the repository root, run:

```bash
python scripts/fetch_resco.py
```

The script clones RESCO into `external/RESCO`, checks the exact remote and commit, and applies `patches/resco_v2_deterministic_seed.patch`. It refuses an unexpected checkout so a silent scenario change cannot enter the evaluation.

## Five Confirmatory Conditions

| Case | Plain-language meaning |
|---|---|
| S0 | Normal morning traffic with no injected incident or system fault. |
| S1 | A busier morning with traffic demand increased by 20%. |
| S2 | A 600-second lane closure with an emergency vehicle introduced during the disruption. |
| S3 | The same incident while sensing, WAN communication, the remote service, and peer freshness are impaired. |
| S4 | The incident plus misleading stale, replayed, and unauthenticated messages from a faulty or compromised neighbor. |

The exploratory follow-up combines 1.3-times demand with a longer 900-second lane closure on Cologne-8 and Cologne-3. Exact lane identifiers, event times, fault rates, seeds, and network profiles are frozen in `configs/experiment.yaml` and `configs/followup_cologne*.yaml`.
