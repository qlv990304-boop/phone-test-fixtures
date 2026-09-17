# Fixture methodology

This document records the review rules behind the fixture files in this repository.

## Maintained record

Each country record contains an ISO region, country calling code, national presentation pattern, an E.164-shaped example, an expected national length note, a safety classification, and a source URL. The record is intended for form tests, documentation, and deterministic QA. It is not a subscriber database and does not claim current assignment, carrier, reachability, or consent.

## Source hierarchy

1. National regulator or numbering administrator for national formats, trunk rules, and published creative-use examples.
2. ITU numbering material when an authoritative national reference is unavailable in an accessible form or for international calling-plan context.
3. Standards such as ITU-T E.164 and RFC 3966 for international representation and telephone URI behavior.
4. Maintained software metadata for implementation checks, never as proof that a subscriber owns a number.

Every data row keeps the source used for that row so a reviewer can reproduce the rule and detect a numbering-plan change.

## Safety classification

Documented creative-use examples are kept separate from structural examples. A structural example may overlap an assigned subscriber and must not be labeled fictional merely because it matches a national pattern. The safety label stays beside the value when data is imported into another tool.

## Review checklist

- Confirm the calling code and whether it is shared with another country or territory.
- Record the domestic trunk prefix separately from the international value.
- Preserve significant leading digits instead of applying one global zero-removal rule.
- Check expected length and whether the plan is fixed or variable.
- Label each fixture as documented creative-use or structural.
- Run generation and normalization tests before publishing generated pages or data files.

## Reproducibility and change control

Pin the dataset version used by a test suite. A change to a calling rule updates the source record, generated files, related country guide, and test expectation together. A correction should identify the country, current output, expected output, and an official source before the fixture contract changes.

## Known limitations

Numbering plans change, regulator pages move, and some official material is not available in English. This compact dataset does not enumerate every area code, carrier prefix, premium service, or local dialing convention. Production systems need maintained numbering metadata and separate workflows for reachability and user consent.

## Safe execution boundary

Use fixtures only in local development, isolated staging, or a test runner. Disable real delivery, use provider sandbox credentials, keep an explicit allowlist for integrations that can send SMS, and never use generated data for lead lists, account creation, or one-time-password collection.
