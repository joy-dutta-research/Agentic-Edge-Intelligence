# Third-Party Notices

This repository combines original study software with publicly available third-party components.

- **RESCO:** The benchmark networks, demand, signal programs, and reference controllers are obtained from the [RESCO repository](https://github.com/Pi-Star-Lab/RESCO) at commit `f1ed9a174f8de41fc9d8689373b836bc882570dc`. RESCO is licensed under the GNU General Public License v3.0. Its source is fetched during setup and is not committed here. The patch in `patches/resco_v2_deterministic_seed.patch` modifies RESCO files and is distributed under the same GPL v3 terms.
- **SUMO 1.27.1, TraCI, and sumolib:** These components provide microscopic traffic simulation and signal control. SUMO is licensed under EPL-2.0 with GPL-2.0-or-later as a secondary option.
- **OpenAI Python SDK 3.6.0:** The SDK is used to access the remote model evaluated in the experiment and is licensed under Apache-2.0. Model weights are not included in this repository.
- **Other dependencies:** Exact versions are listed in `requirements/*.lock` and retain their respective upstream licences.

The MIT licence in the repository root applies only to the original study code and documentation, except where another licence is explicitly stated.
