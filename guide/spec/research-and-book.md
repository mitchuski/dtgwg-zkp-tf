## The Book of ZKPs

This section is informative. It describes the explanatory book and its relationship to the construction records.

### One technical record, two reading paths

The specification explains interoperable behavior and the status of each construction. The book explains why a construction is useful, how its cryptography works, which alternatives fit the use case and how to reproduce the evidence. Both use the same claim, disclosure, assumption and version identifiers; an accessible explanation does not strengthen the technical claim it explains.

A book chapter follows this structure: trust-graph use case; formal statement and non-goals; credential/witness requirements; relation to the reference paper; construction options; worked proof and negative examples; privacy and operational limits; open questions. The cryptographic background follows the operational material so readers can first locate the problem they need to solve.

### Matching the paper to a DTG construction

> **WG-08 — Evidence and reviewer request: formal mapping and book.** Ask for review of the exact paper-to-DTG statement and assumptions, an explanatory chapter, and a reproducible worked construction. Record volunteers explicitly; this note assigns nobody. Status: review requested, equivalence not established.


The book is organized by trust-graph outcomes, not by the predicate list of a single source paper. Personhood/liveness is one chapter family. Other families draw on their own relevant cryptographic constructions and requirements.

For each mapping to *A Cryptographic Framework for Proof of Personhood* ([ePrint 2026/333](https://eprint.iacr.org/2026/333)), record the exact paper revision, section/definition, assumptions, DTG interpretation and evidence for compatibility. Separate a directly checked statement, an editorial interpretation and a proposed DTG extension. A matching section number is not a security reduction.

Existing paper section and benchmark references in the records are inherited research pointers. Their exact equivalence to the proposed DTG profiles remains subject to full-text review and author feedback. In particular, transcript binding in a circuit does not by itself establish the paper's stronger proof-system properties; shared credential names do not establish compatible issuance or vouch interfaces. Paper benchmark numbers are not measurements of ADR-001.

The task force needs help reviewing the formal-to-credential mapping, teaching the relevant cryptography accurately and producing reproducible examples. These are proposed reviewer roles, not assignments: cryptographic reviewers check assumptions and composition; credential/task implementers check representability and custody; technical editors check that the book and spec preserve the same claim.

The proposed process for surveying related work and maintaining these shared records is described in the maintenance note in the guide’s editorial worklist.

### From option research to verification

The existing proving-system entries and per-construction option rows are the starting research catalogue. For each option, carry forward its credential/signature compatibility, witness and device requirements, setup/security assumptions, disclosure, and measured versus reported costs. Similar algorithms do not imply interchangeable credentials or profiles.

The **Agent Handoff: Construction Verification Worklist** in the guide’s editorial worklist turns those fit assessments into tasks V01–V12. It separates runnable component checks from missing implementations, full-statement comparisons and real task/VTC integration. Each returned result updates the relevant book explanation and evidence row; a failed fit is a useful recorded result.

### Research option: Lattice Jolt / Akita (10 September 2026)

The [9 September Lattice Jolt announcement](https://a16zcrypto.com/posts/article/lattice-snarks-jolt-post-quantum-faster) introduces Akita, a Module-SIS-based polynomial commitment scheme, as a candidate post-quantum proving route. For the book's option research, assess its fit for membership and request-binding workloads before composed relationship proofs such as construction 010. Reported performance is not yet a DTG measurement.

The announcement describes a forthcoming companion paper adding zero knowledge; verify the selected implementation's witness-hiding properties before considering private credentials. [Akita's security policy](https://github.com/LayerZero-Labs/akita/security), inspected on 10 September, identifies it as research software rather than a formally audited production release. A post-quantum proof backend does not make legacy credential signatures post-quantum or supply missing witnesses, status checks or authorization.

Track this under V07: pin the implementation and security parameters, test an equivalent statement with negative cases, and return measured results and limitations to the relevant construction record and book chapter. Status: research candidate; no adoption or construction-state promotion.

### Existing-credential route: Longfellow and open stewardship (10 September 2026)

Longfellow already appears in the proving-system catalogue as `siros-longfellow`, in construction 010's legacy-credential options and in the V07 comparison worklist. Give it an explicit reading path in the book: **proving selected facts about credentials as already signed**, before asking whether that capability composes into a DTG relationship proof. The [Longfellow documentation](https://google.github.io/longfellow-zk/) describes support for identity standards including ISO mdoc, JWT and W3C Verifiable Credentials; the exact selected circuit and credential format still determine compatibility.

On 2 September 2026, [Google announced its donation of the Longfellow ZKP library to the Post-Quantum Cryptography Alliance under Linux Foundation Europe](https://blog.google/products-and-platforms/platforms/google-pay/zero-knowledge-proof-library-linux-foundation/). Record this as library stewardship and provenance, distinct from the SIROS catalogue's artefact provenance or validation of a DTG profile.

For V07, pin one catalogue entry and its originating library revision, demonstrate its supported attribute proof with negative cases, then identify the additional membership, counterpart-linkage and status requirements for construction 010. Separate the proof system's post-quantum properties from those of the underlying credential signatures: proving over an ECDSA-signed credential does not make ECDSA quantum-resistant. The current catalogue's `postQuantum` label concerns its ECDSA credential route, not a standalone assessment of every Longfellow protocol. No complete 010 result or new adoption status is implied.

### Vetting evidence and the voucher linkage (13 September 2026)

Credential PR [#49](https://github.com/trustoverip/dtgwg-cred-spec/pull/49) closed without merging on 13 September, superseded by [#50](https://github.com/trustoverip/dtgwg-cred-spec/pull/50), which proposes identity vetting as an informative community predicate under the statement credential of PR #47 rather than as an endorsement profile. Neither is current credential-specification text. The bounded question for the book: can the proposed `identityCommitment` or `livenessConfirmed` replace the offline voucher's missing linkage in construction 010? No such substitution is justified by the proposal. Its commitment is to salted identity claims, a different relation from authenticating that a VRC issuer and the relevant membership identifier are controlled by the same party; its liveness member records what a vetter says it confirmed during a session. Neither is a proof of common derivation, unique humanity, current membership or authorization to act, and the proposal itself bounds a pass: verification does not establish that identity claims are true, that the vetter was eligible or competent, or that admission occurred.

A graph may store evidence about an applicant before it has a membership edge for that applicant. A proof can hide evidence while preserving its specified meaning; it cannot turn evidence of a procedure into a membership decision. This is one optional use case within general trust graphs, not a new personhood focus for the book. Mapping: constructions 004/007 (the holder relation), 010 (voucher and membership composition), 005 (distinct credentials versus persons), 003 (byte-exact transcript binding); WG-01 (outcome) and WG-02 (authenticated statement). [PoP-2026] §7.2's shared-witness relations remain a comparison point, not an equivalence claim for this vetting predicate.

One source wording issue is carried rather than adopted: the proposal says its card digest follows Digest Encoding while hashing the card exactly as received, and Digest Encoding's first step is canonical re-serialisation. Do not bind that digest convention into a proof artifact until its byte input is explicit. An eventual voucher-artifact profile has to specify the authenticated relation and its issuer; how the VRC issuer and the membership identifier enter it; credential, status and parameter versions; which inputs are hidden; how it composes into a fresh presentation; and the correlators visible to the verifier and to colluding verifiers over the declared horizon. An artifact existing at issuance is different from a reusable linkage handle published at presentation; the blind-signature option recorded on construction 010 is a private proof of possession, not a public linkage artifact, and the two must not be confused.

### Predicate identity before transcript binding (14 September 2026)

Credential issue [#52](https://github.com/trustoverip/dtgwg-cred-spec/issues/52) proposes a repository-driven predicate vocabulary with community namespaces and machine-readable accept lists, immutable meanings and no automatic equivalence following; a review comment asks for IRI comparison rules and explicit per-predicate version markers. These are open design choices, not settled registry requirements. The bounded question for the book: does the existing reference transcript encoder already implement the predicate identity and acceptance boundary such a registry needs? No. A local probe over `runtimes/canonical/canonical.mjs` (four assertions, 14 September) shows that equal predicate strings yield equal digests, that NFC and decomposed spellings yield different digests, that `v1` and `v2` identifiers yield different digests, and that an unknown predicate string passes the structural validator. The digest distinguishes strings; that distinction alone does not determine which strings have accepted semantics. This is an encoder observation over a synthetic fixture, not an exploit of a deployed verifier, and no proof was generated or verified.

The proof binds a statement; the verifier must first know which statement the identifier means. Two implementations can agree on the hash algorithm and still disagree on the claim if they resolve or normalize identifiers differently. Mapping: construction 003 (transcript binding), construction 010 (the composed presentation), WG-06 and WG-07 (request and implementation profile), the registry revision and use-case policy. [PoP-2026]'s shared-witness relations are cryptographic statements, not a registry resolution protocol. Follow-on tests need the eventual adapter: reject an unrecognized identifier before proving; reject a proof or request bound to a different definition revision; test the selected Unicode rule on producer and verifier; ensure a deprecated or equivalence-linked term cannot silently gain acceptance.

Two adjacent credential proposals are watched, not adopted: [#53](https://github.com/trustoverip/dtgwg-cred-spec/issues/53) proposes a REQUIRED `nodeType` of `person`, `device`, `agent`, `VTC` or `VTN` on every credential subject — declaring `person` would not itself establish personhood, and the scope of this specification (WG-10) is unchanged by it; [#51](https://github.com/trustoverip/dtgwg-cred-spec/issues/51) proposes semantic versioning for a working draft's Document Status, distinct from its Version, across the three DTG specifications — this draft's header follows that convention once the group confirms it.

### Hidden vetting at admission (23 September 2026)

The chair's Round 1 position (PR #11) asks for the admission proof being built for the Linux Plumbers integration. The trust-tasks join manifest (`vtc/join-requests/manifest/0.2`) already makes room for a *hidden-vetting* criterion: it publishes its parameters under `vetting.ext` and marks that namespace in `vetting.extCritical`. A client that cannot honour the namespace then refuses, rather than gathering named statements for a criterion built never to receive them. Construction 024 states that admission: k pairwise-distinct eligible vetters attested the applicant, with a privacy goal of hiding which vetters attested from the community; the disclosed facts can narrow that anonymity set. The bounded question for the book: is it construction 023? No. Construction 023 proves k vouches over relationship credentials that members issued; 024 proves k attestations from eligible vetters and involves no relationship credential. A relationship credential names both ends, so a policy requiring one between applicant and vetters would disclose what the proof withholds.

The lab built a Groth16 route for 024 on 23 September (`runtimes/circom-gadget/test-vetting.mjs`, 12/12 cases). What building it showed:

1. **A proof per vetter.** The distinctness tag must come from the vetter's secret. A tag derived from anything public, such as the vetter's leaf or DID, is one the community could recompute for every vetter. The applicant does not hold vetters' secrets, so each vetter proves its own attestation and the applicant proves one binding over them: k + 1 proofs. Folding them into one needs recursion, aggregation, or a construction over re-randomisable signatures.
2. **Removing one vetter is a new root.** Nobody else is re-enrolled, and an attestation made under the old root is refused.
3. **The rate limit is per vetter, in-circuit.** Each vetter has `cap` serials per period derived from its own secret, with nothing issued, so there is no issuance pattern that could reveal who is vetting.
4. **A single-use challenge.** The community mints it per applicant and spends it when the proof is counted. A proof verifies as often as it is submitted, so without a spent challenge the same bytes count twice. Construction 023's issuance requirements now carry the same rule.
5. **What it does not establish.** Distinct tags mean distinct vetter secrets, not distinct people. "None of the vetters is the applicant" is not built: it holds only while applicants are outside the vetter set. The community keeps the vetter set and verifies the proof, so no third party can audit the admission.

At k = 5, 1,376 B is calculated from compressed point sizes; the measured snarkjs JSON submission is 7,009 B. One attestation proof takes about 0.8 s in snarkjs, and the community verifies all of them in about 110 ms. The setup is lab-only.

Mapping: construction 024 (the statement), 023 (the vouch-shaped sibling), 001 (vetter-set membership), 002 (tags and serials as scoped reuse detection), 005 (distinct credentials versus persons), 003 (challenge and transcript binding), WG-04 (verification, counting and issuance as three acts), WG-16 (how 023 and 024 relate).

### Lean models and implementation evidence (23 September 2026)

The local evidence bench contains Lean models for the ten primitive records (001–009 and 022) and for every composed record: 010, 011, 012, 013, 020, 021, 023 and 024. The audit lists 67 declaration roots; this is not a count of fully verified constructions. All eighteen records carry their statements, theorem names, hypotheses and scope in optional formal metadata (specification PR #12), and each block's scope line names the clauses its model covers. The models exposed requirements for Merkle leaf/node separation or fixed depth (001), strictly sorted revocation handles (006), and shared witness bindings (002, 004 and 022).

Reproduce the core model checks from the evidence repository with `sh formal/scripts/check-axioms.sh`. The Lean sources are currently local and uncommitted; an immutable evidence revision must accompany a public contribution. The separate Clean experiments establish small distinctness and equality kernels, with same-host independent-agent checks; they do not prove complete admission.

Record 024's formal block models the counting rule for a class-credential reading, the construction named for the Linux Plumbers integration. It is not a clause-by-clause verification of the lab's Groth16 route. In particular, applicant exclusion is not built, the asynchronous verifier needs atomic state-transition review, and privacy requires an adversary- and horizon-specific argument. H11 exercises different tags and a particular reconstruction attempt; it is not a proof of unlinkability. No post-quantum privacy result is established by these tests.

Reviewers should follow record clause → theorem and assumptions → pinned implementation → executable evidence. Keep model proofs, circuit proofs, runtime tests and policy enforcement distinct. Adding formal metadata neither promotes a record nor establishes task-force adoption.

### Cap profiles and admission policy (local draft)

Record 024 permits a secret-derived per-vetter quota or a blind-issued transferable-token budget for a defined vetter set. This is a local draft choice pending task-force review. The lab implements the first profile; no transferable-token implementation is established by its tests. The profile must name the community, set, accounting interval, issuance budget, expiry and carry-over rules. Pooling transferable tokens does not preserve a limit on each holder. A stable-secret slot construction also does not identify distinct people or prevent secret sharing.

The common rule is no additional counted spend. A conflicting reuse is refused. A profile can reject every repeat, as the lab does, or acknowledge an identical resubmission without adding a spend or attestation. Neither permits replay of a consumed challenge. Atomic and durable ledger behavior needs its own implementation checks.

Proof verification supplies facts; a named, versioned policy evaluator applies per-method floors, independence caps, validity and eligibility requirements; issuance is a third act. The current lab checks total tag count and returns method facts, so its passing fixtures do not establish the full policy evaluator. The coverage inventory keeps these obligations pending. No private implementation is assessed or described here.

### Composition findings and deferred circuit correspondence

G5 establishes a conditional model for 023 and a self-vouch counterexample; the record now records that boundary. G6 adds chain attenuation, persona/key linkage, star-to-clique common control and 010 composition results. These are bounded model results: signature predicates can be assumed, credential fields must still be tied to authenticated witnesses, and key/transcript relations outside a counting model remain open. A theorem named soundness does not establish every clause of a construction.

Record 013, now specified, adds a model of one direction of the mutual-admissibility proof and of the exchange ordering: over any run, a half is revealed only after both answers are yes, and no commitment changes once an answer exists. No fairness is claimed: a party can learn the yes and walk away.

The evidence inventory covers 18 records and 60 clauses. Its clause review distinguishes partial models, assumed relations and uncovered clauses. The exact-root audit emits a source-hashed receipt; these local hashes do not replace an immutable published evidence revision. G8, full circuit correspondence in Clean, is deferred. No model receipt claims that deferred result.
