# When Contract Order Becomes API

**A Representation-Invariance Audit for OpenAPI SDK Generation**

Research replication materials for the manuscript submitted to *Empirical Software Engineering*.

**Author:** Huynh Anh Khiem · Faculty of Information Technology, Ton Duc Thang University, Ho Chi Minh City, Vietnam · [ORCID 0009-0007-7210-174X](https://orcid.org/0009-0007-7210-174X)

## Data and code availability

**[Download ESM_1.zip](./ESM_1.zip)** — the complete publicly accessible replication archive, including Python and JavaScript source code, input contracts and transformations, result tables, validation programs, and human-readable projection evidence.

Archive SHA-256:
```text
37d7137df1bb5e85c7e29ef127df2c4e71a2e24af2a1a92a80805b1363dc60cb
```

This is the **same file** submitted as electronic supplementary material (`ESM_1.zip`). The archive preserves the intended nested directories; do **not** upload its individual members separately to Editorial Manager. The repository holds the archive as one file to avoid repeated basenames such as `projection.diff` being mistaken for duplicates.

### Archive contents

| Path inside `ESM_1.zip` | Description |
| --- | --- |
| `scripts/` | Python/JavaScript audit, regeneration, extraction, and checking code |
| `data/` | Pinned 40-contract benchmark, 240 transformed representation files, and manifests |
| `results/` | Clean 7.25.0 and 7.22.0 results, tree/projection hashes, screens, interventions, and reduced compiler evidence |
| `results/projection_evidence/` | Human-readable JSON and unified differences for 20 drift contract–backend pairs |
| `evidence/` | Methodological, prior-art, and engineering provenance notes |
| `README.txt`, `TOOL_VERSIONS.txt` | Full replication instructions and pinned tool versions |

## Reproduce and verify

Requirements: Python, Java (OpenJDK 21 used in the study), and Node.js/npm for TypeScript-related experiments. The original verification environment used Python 3.13.5 and TypeScript 5.8.3.

```bash
git clone https://github.com/huynhanhkhiem-dms/openapi-sdk-representation-invariance.git
cd openapi-sdk-representation-invariance
unzip ESM_1.zip -d replication
cd replication

python -m pip install -r requirements.txt
npm install
python scripts/verify_results.py
```

The final command checks **consistency and selected provenance properties of the published evidence**; it does not independently regenerate all SDK trees. For full regeneration, consult `replication/README.txt`, obtain the official OpenAPI Generator CLI JARs for 7.25.0 and 7.22.0, verify their hashes in `replication/TOOL_VERSIONS.txt`, and place the binaries under `replication/tools/`. Third-party JARs and generated SDK directories are not included.

## Main empirical findings

The fixed benchmark contains **40 pinned OpenAPI contracts**. The 7.25.0 main analysis includes **480 clean SDK generations** (40 contracts × 6 representations × 2 client targets). A reversal of the `paths` mapping changes the normalized public-declaration projection in **10/40 contract instances**, with the same affected set for Python and TypeScript Fetch and the pinned 7.22.0 replication.

Sensitivity analyses retain **8/36** affected contract instances after excluding four specifications with potentially ambiguous template–template route matching and **7/35** affected contract families after also collapsing one near-duplicate pair. On the ten drift cases, the official `openapi-yaml sortOutput` control does not eliminate the observed resolved-content differences; `SORT_MODEL_PROPERTIES` does not remove path-order projection drift. A reduced explicit-title intervention stabilizes the tested naming witness but itself requires migration consideration.

**Outcome definition:** `PROJECTION_INVARIANT` means equality of the study's selected public-declaration projection, **not** byte-identical SDK outputs or guaranteed runtime compatibility. The corpus is a fixed, non-probability benchmark and its fractions are not population prevalence estimates.

## Third-party materials and citation

The input OpenAPI contracts come from the [APIs.guru OpenAPI Directory](https://github.com/APIs-guru/openapi-directory), pinned to commit `f04b8d0bcd39c52e1cf3ad7a5fe744709832ae49`. Upstream ownership, notices, and applicable rights should be respected; no blanket license covering third-party contracts is asserted here.

The corresponding manuscript is titled **“When Contract Order Becomes API: A Representation-Invariance Audit for OpenAPI SDK Generation.”** Until journal bibliographic details exist, cite this repository using a specific commit and the archive checksum above.
