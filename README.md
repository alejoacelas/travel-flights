What can I delegate about flying?

Use this folder to discover bookings, complete routine check-ins, deliver boarding passes,
and keep the facts needed for travel forms.

## Read next

- [`automation.md`](automation.md) — the scheduled check-in workflow and safety boundary.
- [`ideas.md`](ideas.md) — other flight work worth delegating, including airport stays.
- `private/profile.md` — exact identity, document, contact, and loyalty fields.
- `private/bookings.md` — active bookings and check-in state.
- `private/preferences.md` — choices automation may make without asking.

`private/` is deliberately gitignored: it contains passport and booking identifiers. Do
not put passwords, payment-card numbers, OAuth tokens, or one-time codes there; use the
system keychain or a secrets manager. The public repository contains the workflow and
field schema, not usable travel credentials.

## Current state

The initial profile and active August 2026 bookings were collected from personal Gmail
and Drive on 2026-08-08. The profile still needs a phone number, current addresses,
verified visa expiries, loyalty numbers, and explicit check-in preferences. No scheduled
task or airline browser driver exists yet.

## Acceptance check

An automated run is successful only when it finds every flight in the next seven days,
records a source email, checks in during the correct airline window, downloads a readable
boarding pass, emails it to `alejoacelas@gmail.com`, and sends an equally visible failure
email when any step needs Alejo.
