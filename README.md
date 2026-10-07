# When Contract Order Becomes API

**A Representation-Invariance Audit for OpenAPI SDK Generation**

Replication repository for the empirical software engineering study by **Huynh Anh Khiem** (Faculty of Information Technology, Ton Duc Thang University, Ho Chi Minh City, Vietnam).

## Study at a glance

This study investigates whether changes in the representation order of otherwise equivalent OpenAPI contracts alter generated SDK declarations. The evaluated targets are OpenAPI Generator **7.25.0** and **7.22.0**, using Python and TypeScript Fetch client backends.

- Main benchmark: **40 pinned OpenAPI contracts**, 6 variants per contract and 2 language targets (**480 clean generations** on 7.25.0).
- Primary finding: reversing the `paths` mapping changes the normalized public-declaration projection for **10/40 contract instances** on both targets; the same affected set recurs on 7.22.0.
- Sensitivity checks: **8/36** affected contracts after excluding four cases flagged for ambiguous template-template path matching; **7/35** affected contract families after also collapsing one near-duplicate pair.
- Engineering checks: `SORT_MODEL_PROPERTIES`, official `openapi-yaml sortOutput` preprocessing, explicit-title repair, and pre-resolution canonical mapping sorting.
- A reduced TypeScript example demonstrates an unchanged-consumer compilation failure under one ordering.

**Interpretation:** the primary outcome is drift in a specific *generated-source declaration projection*. It is **not** a claim that every drift changes runtime behavior or that the observed fractions estimate population prevalence. The 40 specifications constitute a fixed, non-probability benchmark.

## Replication materials

The versioned supplementary archive **`ESM_1.zip`** contains the pinned input manifest, contract variants, main result tables, whole-project tree hashes, projection JSON/diffs, sensitivity analyses, scripts, and provenance notes. GitHub can preserve this archive as a single file; **do not extract its hundreds of files into the browser's multi-file upload dialog**.

> **Availability status:** The repository's documentation is initialized; the `ESM_1.zip` replication archive still needs to be uploaded. Do not cite this repository as a complete public data deposit until that file appears.

After downloading `ESM_1.zip`, extract it to a working directory to inspect or rerun the study:

```bash
unzip ESM_1.zip -d replication
cd replication
python -m pip install -r requirements.txt
npm install
python scripts/verify_results.py
```

The last command performs **consistency and provenance checks of included evidence**; it does not independently rebuild all generated SDKs.

For full regeneration, install Java and download OpenAPI Generator CLI **7.25.0** and **7.22.0** from the official distribution. Verify their exact SHA-256 hashes against `TOOL_VERSIONS.txt`, place the JARs in `tools/`, and follow the commands in `README.txt` inside the archive. Third-party JARs and generated SDK trees are not redistributed.

## Reuse and provenance

The OpenAPI contracts originate from third parties and retain their own attribution and applicable licenses. Publication of this repository is **not** a blanket relicensing of those contracts. Consult source records and individual upstream terms before redistribution or reuse. No repository-wide license has been asserted for third-party materials.

## Citation

Please cite the journal article when bibliographic details become available. Until then, refer to this repository using its URL and a specific Git commit or release tag.

**Manuscript:** *When Contract Order Becomes API: A Representation-Invariance Audit for OpenAPI SDK Generation*  
**Corresponding author:** Huynh Anh Khiem  
**ORCID:** [0009-0007-7210-174X](https://orcid.org/0009-0007-7210-174X)
