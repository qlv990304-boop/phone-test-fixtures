# Phone Test Fixtures

Versioned reference data for international phone-number formatting, fictional test fixtures, and E.164 normalization checks.

## What is included

- `data/country-phone-formats.csv` — country calling codes, national presentation patterns, E.164 examples, expected digit notes, safety labels, and source URLs.
- `data/fictional-phone-number-ranges.csv` — the reviewed safety matrix separating documented creative-use examples from structural examples that may overlap an assigned subscriber.
- `data/e164-normalization-test-cases.csv` — six explicit input-to-output contracts for country-aware normalization tests.
- `docs/fixture-methodology.md` — source hierarchy, review checklist, safety classification, reproducibility, and known limitations.

## How to use the files

Use the country-format CSV as reference data for form tests and deterministic QA fixtures. Keep the `fixtureSafety` label beside every generated value and keep generated fixtures separate from production contacts.

Use the fictional-range matrix to distinguish documented reserved or creative-use examples from structural examples. A structural example is not proof that a number is fictional, unassigned, reachable, or safe to contact.

For normalization tests, pass the explicit ISO region with the original input and assert the exact `expectedE164` value. Add negative cases beside these happy-path cases for unsupported prefixes, wrong lengths, extensions, and ambiguous context.

## Reproducibility

The country-format dataset page identifies version `2026-07-20`. Pin the version used by a test suite and review the linked source URL before accepting a numbering-plan change.

For the source notes and the current dataset version, see the [GetPhoneNum dataset page](https://getphonenum.com/phone-number-dataset).

## Safety boundary

These are test fixtures and formatting references, not subscriber data. Do not use generated values for account verification, lead lists, outbound calls, SMS, or production contact records. Structural examples require isolated testing, provider sandbox credentials, and real delivery disabled.
