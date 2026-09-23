## Reading this guide

Start with the application outcome, then identify the credentials, witnesses and policy before choosing a proving system. Read the implementation walkthrough for the process, the trust-graph chapter for context, and the cryptographic background for the mathematics. The SIROS review pack provides a focused route for the planned 29 September session.

The [ZKP specification](https://trustoverip.github.io/dtgwg-zkp-spec/) owns construction definitions, public-input conventions, conformance and evidence states. This guide explains them. Implementation source stays with its maintainers; the [evidence repository](https://github.com/mitchuski/dtgwg-zkp-mage) carries experiments and reproduction records. No new construction registry is introduced.

### The admission proof and the community-anchored proof

Record 010 includes the presenter’s own community membership. Record 023 describes an applicant presenting multiple voucher credentials without requiring the applicant’s membership. Neither description proves that the applicant is not already a member. The membership policy, distinctness definition and offline voucher artifact must be settled with the implementation team. Distinct leaves do not by themselves prove independent controllers.

The 22 September notes identify [zkBricks](https://zkbricks.com/) as Berkeley’s deployable home. That website is not a pinned implementation reference for 023. Request the exact repository, revision, interface and statement; record integration deviations in the construction’s provenance.

### Revision boundary

Read records 022 and 023 from [the pinned PR #11 snapshot](https://github.com/trustoverip/dtgwg-zkp-spec/tree/315cf4466bfcfe3d70c88a6706d0a6ca633c60c9) until it merges. A moving published page and a pinned source revision can differ. Links to the proposed guide page are publication targets until the guide PR is merged and Pages is configured.
