# The Churn — Detention Paths

**Map prototype.** An interactive visualization of the ICE detention transfer network in the United States, built from federal detention records obtained under FOIA.

🔗 **[View the map](https://jonnealon.github.io/TheChurn/)** — access is password-gated; contact me for credentials.

---

## What this shows

Each line on the map is a single **transfer between two ICE detention facilities**. The backdrop is the full network of transfers since January 20, 2025. Selecting an individual traces one person's journey through that network — every facility they were held in, in order, with dates, distance, and outcome.

Filters isolate parts of the network: people transferred three or more times, people transferred five or more times, cases ending in deportation, release, or voluntary departure, journeys that return to their point of origin, and movement into the Fifth Circuit (Texas, Louisiana, Mississippi).

## Data

Detention records released by ICE in response to Freedom of Information Act requests, processed and published by the [Deportation Data Project](https://deportationdata.org). Current release covers ICE enforcement actions through early March 2026. Facility locations come from DDP's companion facilities file.

## Method

Raw records are one row per *stint* — a single booking at a single facility. Reconstructing a journey means:

1. Removing records DDP flags as likely duplicates
2. Grouping stints into continuous detention stays and ordering them by book-in time
3. Collapsing consecutive stints at the same facility (a book-out and re-book-in at the same place is paperwork, not a move)
4. Dropping transit points — hold rooms and field/district offices are processing stops, not placements — and dropping sub-hour records as booking artifacts
5. Re-collapsing, since removing a transit point can leave two real placements adjacent at the same facility

What remains is an ordered sequence of distinct, real detention placements. Every figure shown — transfer counts, states touched, distance, days in custody, whether a path returns to its origin — is computed from that sequence.

Both filters in step 4 are conservative by design: they remove artifacts rather than real detentions, so counts run low rather than high.

## Important caveats

**These are transfers, not flights.** The data records where people were held and when. It does not record how they traveled. Nothing here should be read as a flight path, and the map never describes movement that way.

**The featured individuals are illustrative, not representative.** Each traced path is a faithful, unmodified rendering of one real detention record. But *which* people are shown was an editorial selection made to span different outcomes, nationalities, ages, and journey types. Patterns should be read from the aggregate network, not from the featured cases.

**Records are de-identified.** No names, and no individual detail beyond what appears in the government's own released data.

**This is a prototype.** Design, framing, and features are in progress and subject to change.

## Technical

Standalone HTML — Deck.gl and Mapbox GL, no build step, no backend. Best viewed on desktop in a current browser.

## Credit and citation

Analysis and visualization by **Jon Nealon** / `<verify>`

> Government data provided by ICE in response to a FOIA request, processed by the Deportation Data Project. Analysis & visualization: Jon Nealon/`<verify>`

Please get in touch before citing, reproducing, or republishing while this remains a prototype.
