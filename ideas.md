# Other delegation

## Airport stays

Yes. Search live inventory by airport, dates, one adult, total price, and a radius that
expands only when needed. Rank by total price plus the actual transfer burden: walking or
shuttle time, shuttle operating hours, late check-in, cancellation policy, taxes, rating,
and whether an overnight airside stay is legal.

The best first integration is Booking.com's Demand API if access is available: its
[accommodation search](https://developers.booking.com/demand/docs/accommodations/search-for-available-properties)
accepts an airport or coordinates and returns live availability, the best matching rate,
policies, and booking links; its [sorting guide](https://developers.booking.com/demand/docs/accommodations/filter-sorting)
documents radius searches and cheapest-product behavior. Expedia's
[Rapid Lodging API](https://developers.expediagroup.com/rapid/lodging) is a credible second
supplier. Google Places [Nearby Search](https://developers.google.com/maps/documentation/places/web-service/nearby-search)
is useful for discovering and distance-ranking hotels, but not as the price source.

## Next useful jobs

- Detect schedule changes, cancellations, tight connections, terminal changes, and visa or
  transit-document requirements; email only changes that alter what Alejo must do.
- Fill recurring passenger, visa, accommodation, and arrival-card fields from the private
  profile, with a review step before submission.
- Claim missing loyalty credit from past receipts and boarding passes, then attach the right
  account number to future bookings.
- Keep baggage allowances, receipts, boarding passes, delay evidence, and claim deadlines
  together per journey.
- Compare airport hotel, lounge, sleeping-pod, and ground-transport options for long or
  overnight connections.
- Generate a departure brief: check-in status, terminal, ground-transport deadline,
  baggage rule, entry documents, weather, and one-tap links.
- Maintain the existing travel log automatically from ticketed itineraries while keeping
  confirmation codes out of the public file.
