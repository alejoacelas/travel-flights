# Flight automation decisions

## Core decisions

### Build only the authorized workflow

- [Treat this as a design until a scheduler and airline adapters exist](#treat-this-as-a-design-until-a-scheduler-and-airline-adapters-exist).
- [Use confirmed profile facts and explicit standing preferences](#use-confirmed-profile-facts-and-explicit-standing-preferences).
- [Make retries and failures visible](#make-retries-and-failures-visible).
- [Keep live identifiers out of publishable material](#keep-live-identifiers-out-of-publishable-material).

## Details

### Treat this as a design until a scheduler and airline adapters exist

[README.md](README.md) records that no scheduled task or browser driver exists. [automation.md](automation.md) starts with booking discovery and reminders, then airline-specific check-in. A generic ticket-selling API does not establish check-in support.

### Use confirmed profile facts and explicit standing preferences

The automation contract permits only supported fields and choices. Stop and report missing facts, identity or visa mismatches, CAPTCHA, payments or itinerary alternatives. Keep the preference boundary explicit; the airport-hotel rating threshold means guest rating, not star class.

### Make retries and failures visible

Preserve source emails, reconcile changed itineraries, track check-in windows and save attempts and sent-message IDs. Success requires verified boarding passes and delivery; an error must produce a visible action-required message rather than a silent skip. Repeated execution must not duplicate side effects.

### Keep live identifiers out of publishable material

The intended split in [README.md](README.md) puts identity and booking fields in private/ and secrets in a credential manager. Do not add live identifiers to examples, fixtures or this record. The current Git index already tracks private/ files despite that README claim, so verify actual tracking and privacy before any future publication; this migration does not remove or expose them.
