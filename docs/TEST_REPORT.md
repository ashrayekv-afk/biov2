# Verification — 7.6.0-compact-outlook

## Release scope

Display-only update to the existing biological-domain drawer. The observed domain algorithm, extraction files, trained artifact bytes and inference computations are retained. No forecasting model is included or validated. The six-month display always says **Not available**; client-injected forecast values and NKPI outputs cannot become a probability.

## Current verification

- The progression regression suite covers all six strict boundaries, grouped OR rules, four-domain counts, structural sensitivity, short/ambiguous intervals, treatment/quality holds, missing data and held results.
- New checks cover one closed-by-default outer drawer below NKPI, four collapsed per-domain details, observed-first ordering, actual interval labels, unavailable forecast states, rejection of client-provided forecast values, and no chart.
- Parent calculator integration uses real Python service results with a DOM adapter, including bilateral examples, frame-height events, edits, stale responses, source changes and patient clearing.
- Production renderer interactions are additionally inspected with a DOM implementation at build time; no live Streamlit deployment or visual browser test is claimed.
- Extraction/model files are compared byte-for-byte with release 7.5; extraction regression and model interval suites are retained and rerun. Real-report OCR accuracy results below are inherited from 7.5, not a new clinical validation.

## Previous extraction verification — 7.5.0-smart-extraction


## Scope and limits

This is an engineering update to browser OCR and review workflow. The NKPI artifacts, inference feature mapping, interval coefficient, and biological-domain rules are unchanged. It is not a newly trained or calibrated progression model. The domain panel continues to use actual observations and actual scan intervals.

The automatic-reading policy is a development policy: at least three literal numeric readings with OCR confidence >=80, a correctly located label with confidence >=80, and no competing literal reading with confidence >=60. Confidence belongs to OCR, not clinical certainty. Repeated reads are correlated and remain one printed occurrence. These constants have not been optimized or validated on an independent clinical dataset. Before wider use, measure wrong auto-acceptances, eye/date association errors, exception burden and time on untouched, independently labelled report exports.

Only a strong reread of the same labelled occurrence can supersede its older noisy OCR candidates. Separate report disagreements remain exceptions. Superseded candidates stay visible in source details. An approximate ARTmax candidate is never accepted solely because it was calculated.

## Numerical consistency

- Printed ARTmax is compared with C/PPImax using all values compatible with printed rounding: C ±0.5 µm; PPImax ±0.005; ARTmax ±0.5. Their intervals must overlap. The formula is supporting evidence from the same scan, not an independent measurement.
- The calculation runs only with usable PPImax evidence. An unreliable PPI read is marked unavailable; it cannot manufacture a match or override a direct ARTmax.
- Changing C or ARTmax reruns the identity check. A newly conflicting pair opens the relevant review controls, blocks automatic submission, and invalidates stale related acknowledgments. The clinician can confirm actual source values that disagree, without silently adjusting the measurements to fit the formula.
- ARC <= PRC prompts label/unit review and never swaps values automatically. Measurement bounds and finite-number validation remain enforced.
- Kmax is not calculated as 337.5/ARC: these measurements sample different aspects of the surface. BAD-D is not calculated from an average of its component indices.
- A fixed, undated progression-table row is excluded from primary BAD-D selection; only the date-matched summary may corroborate an examination.
- Recognized acquisition-quality warnings propagate through the existing numeric-only quality contract. Unknown quality is not promoted to OK. Extraction correctness does not establish good scan quality.

## Real-report development check

Three supplied ZIP archives contain six eye-level examinations (36 target measurements). Production Tesseract.js WebAssembly extraction retained both OD and OS in all three archives and matched all 36 previously source-checked expected values. This is a development set already used during implementation, not an independent holdout or a general 100% accuracy claim.

| Archive / eye | Previous field confirmations | 7.5 field confirmations |
| --- | ---: | ---: |
| Visit 1 / OD | 4 | 3 |
| Visit 1 / OS | 6 | 3 |
| Visit 2 / OD | 3 | 2 |
| Visit 2 / OS | 5 | 3 |
| Archive 3 / OD | 2 | 1 |
| Archive 3 / OS | 3 | 2 |
| Total | 23 | 14 |

All three archives produced 6/6 populated inputs for both eyes. ARTmax 147 and 27 remained explicitly derived candidates requiring review when reliable direct recognition was insufficient. True report disagreements were not discarded to improve the acceptance rate. The runs used 631 OCR operations in total; clinic/browser timing has not been benchmarked. Recognized scan-quality warnings were also retained. These tests establish software behavior and fixture agreement only.

## Automated regression checks

- Literal precision, missing-decimal rejection, wrong labels, competing confident reads, unit-only glyph normalization, single-source versus multiple-report badges.
- ARTmax cases 236 vs 296 and 2 vs 27, rounded mathematical consistency, derived-only review, and cross-report disagreements.
- Height-scaled and double-resolution OCR bounding-box conversion.
- Production review/submission through a DOM adapter: automatic fields have no required individual checkbox; unresolved fields remain blocking; next-exception action, manual edits, source selection, confirmation invalidation, both-eye completeness, explicit single-eye choice, stale interval/order errors, and quality flag propagation.
- Biological-domain strict thresholds and scope, source/edit/reset invalidation, Python model inference and impact-audit regression.

No live deployed Streamlit/browser end-to-end session or external clinical validation was performed. The local report test uses the production JavaScript pipeline with Tesseract.js WebAssembly and Node Canvas; the exact tested English recognition-data bytes are now bundled with deployment. Browser/canvas differences can still affect OCR results. The archive retains 99 files by omitting two historical, retired projection/treatment-preview documents; no active runtime files were removed.

## Deployment

Upload the complete package, preserving folders and replacing matching files. The entry point remains kcn_dual_calculator_app.py. A fresh 7.5 component identity and resource cache versions prevent reuse of an older embedded app. Model checksums must remain unchanged.

---

# Verification — 7.4.1-domain-replacement

- `node tests/test_progression_summary.cjs` passes with the actual corrected parent app and real Python responses. It checks there is exactly one domain dropdown below the results; no map/projection tabs, retired gallery script or trajectory iframe; and only the importer iframe remains.
- No gallery or viewer stub is supplied to the parent test. Startup, model response, source-change invalidation, edits, stale-response rejection, clear/reset and drawer resizing work without those dependencies. Legacy extractor map broadcasts and foreign trajectory messages are safely ignored.
- The 7.4 strict boundary and domain-mathematics tests remain in this suite. The domain module is byte-for-byte identical to 7.4.0.
- NKPI model/interval and bilateral extraction/review regression suites pass. Inference, model artifacts, numeric contract and extractor code are unchanged. JavaScript/Python syntax and the release manifest/ZIP are checked.
- This is a DOM-adapter integration test with real service responses, not a live browser/Streamlit end-to-end or clinical-validation test.

---

# Verification — 7.4.0-source-domains

## New domain assessment

- `node tests/test_progression_summary.cjs` passed: all six strict threshold boundaries (exact equality, just below and just above), direction signs, both OR rules, no double counting, baseline-relative percent thinning, and the structural sensitivity check excluding BAD-D.
- A synthetic regression fixture uses the reported changes: ARC +0.07 mm, PRC +0.13 mm, thickness 437→425 µm, Kmax +1.9 D over 80 days. BAD-D and ARTmax are held constant in this test because their actual changes were not supplied. Result: two domains cross, the 2-of-3 structural criterion is met, ARC/Kmax disagreement is visible, and the short interval prevents SOURCE classification.
- Checked age endpoints 18/50 and outside range, short and boundary calendar intervals (180–184 days), unknown quality/history, prior treatment, poor-quality holds, all-six completeness, invalid/nonfinite inputs, independent eyes, held/source/stale states, HTML escaping and score/age/interval independence of the count.
- Production parent-app handlers were exercised with real Python service responses through a DOM adapter: collapsed default, bilateral rendering, separate single-visit/two-visit states, source/edit invalidation, stale-response rejection, reset and expansion height messages.
- Regression suites passed: `tests/test_model_interval.py`, `tests/test_bilateral_review.cjs`, `tests/test_extraction_integrity.cjs`, `tests/test_trajectory_ui.cjs`.
- Model files, numerical contract, inference/impact audit, entry point, requirements and extractor/cornea/trajectory files are unchanged from 7.3. The new panel does not change NKPI. No new OCR experiment was run because extraction is unchanged.
- The layout reuses the existing responsive bilateral cards and native keyboard-accessible dropdown, with scoped styles. A browser executable is not installed in this build environment, so these are DOM-adapter integration tests rather than live browser/Streamlit end-to-end or visual-render tests.

## Scientific scope

Rules were transcribed from SOURCE_P0175_Resubmission_Answers.docx, pp. 3–4, dated 2026-09-28. The four-domain criterion is a prespecified research endpoint. Numerical threshold crossings are not evidence that this composite rule has been clinically validated. The app checks available comparison metadata and discloses unknown information; full SOURCE study enrollment and clinical diagnosis are not certified.

Exact decimal arithmetic is used for strict thresholds. Display precision never determines the crossing. Six calendar months is not treated as a fixed 180 days: the app conservatively flags 181–183 days for date review because only interval days are retained in its result contract. Age and interval do not weight the domain count.

The prior interval-coefficient amendment remains unvalidated. No new performance claim or calibrated progression probability is supplied.

---

# Verification — 7.3.0-observed-progression

## Added panel

- `node tests/test_progression_summary.cjs` passed: exact deltas, correct A/B/C sign conventions, rounding, no double-counting of supporting indices, disagreement between A and Kmax, age/interval independence, one visit, missing/held/changed inputs, separate eyes, and HTML escaping.
- The same test runs production parent-app handlers and obtains real responses from the Python service. Verified closed initial state, two-eye rendering, source-change invalidation, edit invalidation, stale-response rejection, new-patient reset, and iframe height notification on expansion.
- This is a DOM-adapter integration test, not a live Streamlit/browser end-to-end or clinical validation test.
- The new panel has scoped responsive CSS and native keyboard-accessible details/summary controls. No external UI library or network request is added.
- Model, extraction, bilateral review and trajectory regression tests passed. Model artifacts and extractor/trajectory/cornea component files are byte-for-byte identical to v7.2. The original inference, ranked score impact, source gallery, entry point and requirements are unchanged.
- No OCR accuracy experiment was repeated because the extraction code is unchanged; the earlier fixture limits below still apply.

## Scientific scope

Actual values and differences are displayed. A/B/C directional counts are descriptive, not independent statistical evidence. There are no empirical repeatability limits in the panel, no calibrated progression probabilities, and no assertion of stability or persistent progression. Those capabilities require repeat acquisitions, applicable measurement-error estimates and clinical validation. Current two-visit data alone do not identify them. Age/interval do not change directional findings.

The 7.2 interval coefficient amendment remains unvalidated, as before. No new performance claim is made.

---

# Verification — 7.2.0-extraction-interval

## Scope

Six required NKPI inputs per eye and visit: A/ARC, B/PRC, thinnest pachymetry,
Kmax, BAD-D, ARTmax. Both eyes are retained. Extraction completeness is distinct
from correctness and source verification. No universal 6/6 guarantee is made.

## Regression checks

- Production verification/submission functions reproduce 236 versus 296 ARTmax:
  the field shows Conflict, both-eye calculation is blocked, and corrected 296
  is submitted only after explicit source verification.
- Multiple OCR passes of one printed value count as one source. Disagreements
  between full-row and cell OCR remain visible. A C/PPImax calculation does not
  count as a second directly printed ARTmax.
- Date matching rejects unmatched dates, unknown dates and ambiguous repeated
  same-day scans. A filename eye cannot silently override conflicting laterality.
- Severe-value bounds, label/border parsing, partial and missing-eye inputs,
  both-eye submission, explicit exclusions, source recovery, cancelled recovery,
  source/input edits, session clearing and chronological interval gates pass.
- The interval coefficient is exactly 50% of its parent value; the intercept,
  centers, scales and all other coefficients are unchanged. Baseline artifact
  bytes are unchanged. Independent effect audits agree with inference in both
  eyes. Corrected example inputs (ARTmax 296, age 22, 80 days) return 29.3279107752.
- The amended two-visit artifact has no inherited active AUROC/calibration claim.
  This change is not fitted or clinically revalidated. Halving its coefficient
  is not evidence of improved clinical accuracy.
- Existing source-map, bilateral, surface and conditional-scenario suites pass.
  Real report-pixel map comparison/viewer tests use native Canvas plus a DOM
  harness. All 8 paired map comparisons and 16 map crops pass their existing
  compatibility checks. These tests do not validate a new clinical map method.
- Python/JavaScript syntax, local HTML references, model SHA-256 checks and PDF
  generation pass. The release manifest and ZIP are checked before distribution.

## Real-report OCR

All six fields were populated for both eyes in each of three available ZIPs:
**36/36 displayed values matched the printed source panels** after the fixes.
Two ARTmax values used the explicitly approximate C/PPImax candidate path; both
matched the printed integer and remained flagged for human source verification.
This result includes the full three-archive WebAssembly pass and a targeted rerun
of the third archive after correcting PPI source precedence. The first four
studies' selected PPI values and single-digit ART fallback decisions were unchanged.
Several other fields retain source-review flags because independent corroboration
was unavailable or OCR readings conflicted. Filled fields are not all automatically
verified. During development, mismatches were flagged and blocked rather than
receiving automatic agreement status.

The three previously supplied ZIPs cover six eye/examination reports. Report
values were visually checked from cropped printed measurement panels. These are
small development fixtures, not an independent accuracy benchmark. Source files,
images, raw OCR, dates and patient records are excluded from this distribution.

The exact March/June source ZIPs from the reported 296→236 error were not available;
the photos establish the discrepancy, and the logic is reproduced in regression
tests, but that specific original upload has not been tested end to end.

## Limits

Tesseract.js 7.0.0/core 7.0.0 was run through Node Canvas with locally available
English trained data. This exercises the production JavaScript extraction logic
and WebAssembly engine; it is not a full browser or deployed Streamlit test.
Browser language downloads, rendering and different scan layouts can still
produce different OCR. Full live Streamlit testing was unavailable here.

Unreadable or inconsistent values require review. An approximate C/PPImax ARTmax
candidate is labeled and never substitutes for source verification. Identical OCR
reads can still be identically wrong; Reports agree is not a guarantee. No
clinical decision or treatment threshold is validated by these software tests.

## Run

```bash
node tests/test_extraction_integrity.cjs
node tests/test_bilateral_import.cjs
node tests/test_bilateral_review.cjs
python tests/test_model_interval.py
node tests/test_trajectory.cjs
node tests/test_trajectory_ui.cjs
python tools/verify_package.py
```

The optional map tests require two local report ZIP paths and `@napi-rs/canvas`.
The private real-OCR QA adapter and source files are not distributed.

Bundled 7.5 English OCR data SHA-256: `7d4322bd2a7749724879683fc3912cb542f19906c83bcc1a52132556427170b2`.
