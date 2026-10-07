# When Contract Order Becomes API

**A Representation-Invariance Audit for OpenAPI SDK Generation**

Public replication materials for the manuscript submitted to *Empirical Software Engineering*.

**Author:** Huynh Anh Khiem · Faculty of Information Technology, Ton Duc Thang University, Ho Chi Minh City, Vietnam · [ORCID 0009-0007-7210-174X](https://orcid.org/0009-0007-7210-174X)

## Public data and code

The repository now exposes both archives used by the manuscript:

- **[ESM_1.zip](./ESM_1.zip)** — complete frozen benchmark, transformations, original analysis scripts, recorded main-study outputs, projection evidence, and replication instructions.
- **[ESM_2.zip](./ESM_2.zip)** — clean rerun audits and real-contract Python/TypeScript consumer-witness materials for OpenAPI Generator 7.25.0 and 7.22.0.

SHA-256:

```text
ESM_1.zip  37d7137df1bb5e85c7e29ef127df2c4e71a2e24af2a1a92a80805b1363dc60cb
ESM_2.zip  992055e9e8be147bfaa047b6a5bcb4016e0575957c9bdc96c728c4ddb2904ec8
```

The archives are retained as ZIP files so their intended nested directory structure is preserved and repeated basenames are not flattened by manuscript-submission systems.

### ESM_1 contents

| Path inside `ESM_1.zip` | Description |
| --- | --- |
| `scripts/` | Python/JavaScript audit, regeneration, extraction, and checking code |
| `data/` | Pinned 40-contract benchmark, 240 transformed representation files, and manifests |
| `results/` | Clean 7.25.0 and 7.22.0 results, tree/projection hashes, screens, interventions, and reduced compiler evidence |
| `results/projection_evidence/` | Human-readable JSON and unified differences for drift contract-backend pairs |
| `evidence/` | Methodological, prior-art, and engineering provenance notes |
| `README.txt`, `TOOL_VERSIONS.txt` | Full replication instructions and pinned tool versions |

### ESM_2 contents

`ESM_2.zip` adds the clean binary-pinned rerun audits and unchanged-consumer witnesses used in the revised manuscript, including Python and TypeScript results for the ten path-order drift contracts on both 7.25.0 and 7.22.0.

## Reproduce and verify

Requirements: Python, Java (OpenJDK 21 used in the study), and Node.js/npm for TypeScript-related experiments. The verification environment used Python 3.13.5 and TypeScript 5.8.3.

```bash
git clone https://github.com/huynhanhkhiem-dms/openapi-sdk-representation-invariance.git
cd openapi-sdk-representation-invariance
unzip ESM_1.zip -d replication
cd replication

python -m pip install -r requirements.txt
npm install
python scripts/verify_results.py
```

The packaged verification command checks consistency and selected provenance properties of the recorded evidence. Full regeneration additionally requires the official OpenAPI Generator CLI JARs for 7.25.0 and 7.22.0. Their hashes are pinned in `TOOL_VERSIONS.txt`; the third-party JARs and complete generated SDK trees are not redistributed.

## Main empirical findings

The fixed benchmark contains **40 pinned OpenAPI contracts**. The 7.25.0 main analysis contains **480 clean SDK generations**. Reversing only the `paths` mapping changes the selected public-declaration projection in **10/40 contracts**, with the same affected set for Python and TypeScript Fetch and in the pinned 7.22.0 replication.

Clean reruns with the exact pinned binaries completed **480/480** generations for 7.25.0 and **160/160** for 7.22.0 with no generation failures and reproduced the recorded projection-level fields. The unchanged-consumer checks in `ESM_2.zip` demonstrate source incompatibility for the ten drift contracts in both Python and TypeScript direct-model imports across both releases.

**Outcome scope:** declaration-projection equality is not byte-identical SDK equality, and source incompatibility is not a claim of runtime behavioral incompatibility. The corpus is a fixed, non-probability benchmark; observed fractions are not population-prevalence estimates.

## Third-party materials

The input OpenAPI contracts come from the [APIs.guru OpenAPI Directory](https://github.com/APIs-guru/openapi-directory), pinned to commit `f04b8d0bcd39c52e1cf3ad7a5fe744709832ae49`. Upstream ownership, notices, and applicable rights remain with the respective sources; no blanket license over third-party contracts is asserted here.

When citing the replication package before journal bibliographic details are available, cite this repository using a specific commit together with the archive checksums above.
