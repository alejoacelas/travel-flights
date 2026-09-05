# Check-in automation

## Recommended design

Use Gmail as the booking inbox, a small durable state file or database as the ledger, and
one browser adapter per airline. A generic flight API is not enough: public travel APIs
sell or describe trips, while check-in changes a passenger record and commonly requires
the passenger to complete airline-specific declarations.

1. Every hour, search personal Gmail for the `Flights` label plus known airline and travel
   senders. Parse itinerary, passenger, confirmation, ticket, operating carrier, airports,
   local times, and source-message ID into a strict schema.
2. Reconcile duplicate and changed itineraries. Keep one record per ticketed journey and
   preserve every source message.
3. Calculate the carrier's check-in opening time. Queue a one-off attempt then, with
   bounded retries before the airport cutoff.
4. Open the airline's manage-booking page in an authenticated browser profile. Fill only
   fields supported by `private/profile.md` and choices allowed by
   `private/preferences.md`.
5. Apply the standing choices in `private/preferences.md`: accept any free assigned seat,
   add no bags, decline paid seats and voluntary bumps, and answer no to dangerous-goods
   and health declarations. Email every schedule change and recalculate its check-in time.
6. Stop and email `ACTION REQUIRED` for CAPTCHA, identity or visa mismatch, payments,
   proposed itinerary alternatives, or any missing required fact. Never convert an error
   into a silent skip.
7. Download PDF and wallet passes, verify that each file is nonempty and names the right
   passenger and flight, then email the files to `alejoacelas@gmail.com`.
8. Record attempts, outcome, boarding-pass hashes, and the sent-message ID. A rerun must
   be idempotent.

## First implementation

Build discovery and reminders before browser check-in. Gmail's API supports mailbox
queries, attachment retrieval, and sending MIME messages with attachments. An hourly
Google Apps Script trigger is easy to host, but airline browser automation needs a
persistent signed-in browser elsewhere; use a small always-on machine or managed browser
worker for that step.

Start with JetBlue, United, and Emirates because they appear in the current mailbox.
Replay historical emails as fixtures, redact identifiers in committed tests, and add one
carrier only after its happy path and every stop condition above are exercised.

## Required secrets and access

- Personal Gmail OAuth: read bookings and attachments; send only to Alejo.
- Browser session for each airline, preferably an airline account rather than booking
  reference plus surname.
- Keychain or secrets-manager entries for OAuth refresh tokens and airline credentials.
- An email sender that can attach the boarding pass and emit failure alerts.

Do not hardcode credentials or commit live booking fixtures. CAPTCHA is a human handoff,
not an engineering obstacle to bypass.

## Sources

- Gmail can [search messages](https://developers.google.com/workspace/gmail/api/guides/filtering),
  [retrieve attachments](https://developers.google.com/workspace/gmail/api/reference/rest/v1/users.messages.attachments/get),
  and [send messages with attachments](https://developers.google.com/workspace/gmail/api/guides/sending).
- Apps Script has [time-driven triggers](https://developers.google.com/apps-script/guides/triggers/installable#time-driven_triggers),
  though their firing time may be slightly randomized and failures must be monitored.
- Duffel's flight guide says [the passenger must complete check-in](https://duffel.com/docs/guides/getting-started-with-flights),
  evidence against expecting one generic booking API to issue boarding passes.
