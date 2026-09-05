# Construction record

## 2026-08-08

Decisive request: rename `other/places` to `other/travel`, create `flights/`, collect the
facts needed for check-ins and travel forms from email and Drive, and explore further work
that can be delegated there. The intended next step is a scheduled task that discovers
upcoming flights, checks in, and emails the boarding pass.

Method:

1. Read the repository and nearest folder instructions; preserved the nested private visa
   repository while moving the parent folder with Git history.
2. Searched the connected Gmail and Drive account, found it was the 80,000 Hours contractor
   account, then used the signed-in personal Google account in Chrome.
3. Searched Gmail's `Flights` label and identity-related mail. Read the current JetBlue and
   United receipts and the passport and visa-result messages.
4. Searched personal Drive for `pasaporte`; visually checked the current passport scan in
   `Personal IDs` against Gmail's visa-result details.
5. Recorded exact identifiers only in gitignored `private/`. Passwords encountered in old
   correspondence were intentionally not recorded.
6. Checked primary API documentation for Gmail, Apps Script, Duffel, Booking.com, Expedia,
   and Google Places; translated the constraints into `automation.md` and `ideas.md`.

Checks: inspect `git status --ignored`, run the repository sync script after the folder
rename, verify Markdown links, and confirm no exact passport or booking identifier enters
tracked files.

Alejo supplied the standing seat, baggage, bump, schedule-change, declaration,
notification, destination-arrival, and airport-hotel choices later that day. They were
recorded in `private/preferences.md`; the public automation contract was updated to match
without publishing the private profile.
Alejo confirmed that the airport-hotel threshold means a guest rating above 4/5, not hotel
star class.

Expanded the existing loyalty-credit job after recovering credit from historical flight
receipts in email; kept it in `ideas.md` rather than adding another root file.
