# Heathrow Airport (heathrow-airport)

Heathrow Airport Limited operates London Heathrow (IATA LHR, ICAO EGLL), the United Kingdom's principal international hub and Europe's busiest airport by passenger numbers, under the ultimate ownership of FGP Topco Limited — whose largest shareholder since December 2024 is Ardian, alongside Saudi Arabia's Public Investment Fund and a residual Ferrovial holding. In the travel distribution chain Heathrow is infrastructure, not an intermediary — it sells no seats, holds no bookable inventory, issues no PNRs or e-tickets, and sits entirely outside the GDS and IATA NDC value chain, earning aeronautical charges, retail concessions, car parking and property income instead. Its API posture is unusual for an airport — Heathrow does run a real, branded, publicly reachable developer portal at developer.heathrow.com, built on Microsoft Azure API Management, which publicly describes three products in prose — Flights, Flight Connections and Weather — but publishes no OpenAPI, no endpoint reference, no rate limits, no pricing and no SLA to anonymous visitors. The API catalogue and Products list return empty to unauthenticated callers, sign-in is via Azure Active Directory, and the portal's own How It Works page requires a prospective developer to email support@heathrow.com and be enrolled before any access is granted. The gateway at api.heathrow.com goes further and rejects requests with "400 No required SSL certificate was sent", meaning mutual TLS with a Heathrow-issued client certificate. So — public docs, gated contracts, no exit path beyond a UK GDPR data portability request to privacy@heathrow.com.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/heathrow-airport/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/heathrow-airport/refs/heads/main/apis.yml)

## Tags

- Travel
- United Kingdom
- Airports
- Aviation
- Airport Infrastructure
- Flight Information
- Transportation
- Passenger Experience

## Timestamps

- **Created:** 2026-07-28
- **Modified:** 2026-07-28

## APIs

### Heathrow Flights API

Heathrow's Flights API provides up to date information on real time flights to and from Heathrow, covering destinations, arrivals, airlines, aircraft types, flight status, gates and terminals, with scheduled flight information enriched by real-time gate and terminal updates. Described publicly on the Heathrow developer portal; the endpoint reference and machine-readable contract are visible only to enrolled, Azure AD authenticated accounts.

- **Human URL:** [https://developer.heathrow.com/api-flights](https://developer.heathrow.com/api-flights)

#### Tags

- Flights
- Flight Status
- Arrivals
- Departures
- Aviation

#### Properties

- [Documentation](https://developer.heathrow.com/api-flights)
- [Developer Portal](https://developer.heathrow.com/)
- [Onboarding](https://developer.heathrow.com/how-it-works)
- [Authentication](https://developer.heathrow.com/signin)

### Heathrow Flight Connections API

Heathrow's Connections API provides up to date information on real time flight connections to and from Heathrow, returning connection information together with flight detail. The portal documents four query shapes — flight to flight, flight to terminal, terminal to terminal, and terminal to flight. Described publicly on the Heathrow developer portal; the endpoint reference and machine-readable contract are visible only to enrolled, Azure AD authenticated accounts.

- **Human URL:** [https://developer.heathrow.com/api-connections](https://developer.heathrow.com/api-connections)

#### Tags

- Connections
- Transfers
- Terminals
- Aviation

#### Properties

- [Documentation](https://developer.heathrow.com/api-connections)
- [Developer Portal](https://developer.heathrow.com/)
- [Onboarding](https://developer.heathrow.com/how-it-works)
- [Authentication](https://developer.heathrow.com/signin)

### Heathrow Weather API

Heathrow's Weather API provides up to date information on weather conditions at most airports worldwide, exposing temperature, weather categories, a countries list and lookup of weather by IATA code, positioned as a companion to the Flights API for connection and arrival/departure context. Described publicly on the Heathrow developer portal; the endpoint reference and machine-readable contract are visible only to enrolled, Azure AD authenticated accounts.

- **Human URL:** [https://developer.heathrow.com/api-weather](https://developer.heathrow.com/api-weather)

#### Tags

- Weather
- Forecast
- Aviation

#### Properties

- [Documentation](https://developer.heathrow.com/api-weather)
- [Developer Portal](https://developer.heathrow.com/)
- [Onboarding](https://developer.heathrow.com/how-it-works)
- [Authentication](https://developer.heathrow.com/signin)

## Common Properties

- [Website](https://www.heathrow.com/)
- [Developer Portal](https://developer.heathrow.com/)
- [Documentation](https://developer.heathrow.com/apis)
- [Plans](https://developer.heathrow.com/products)
- [Onboarding](https://developer.heathrow.com/how-it-works)
- [Sign Up](https://developer.heathrow.com/signup)
- [Authentication](https://developer.heathrow.com/signin)
- [Change Log](https://developer.heathrow.com/api-changelog)
- [Support](mailto:support@heathrow.com)
- [Company](https://www.heathrow.com/company)
- [Flight Status](https://www.heathrow.com/arrivals)
- [Terms of Service](https://www.heathrow.com/terms-and-conditions)
- [Privacy Policy](https://www.heathrow.com/privacy-notice)
- [LinkedIn](https://www.linkedin.com/company/heathrow-airport/)

## Switching Cost

| Dimension | Finding |
| --- | --- |
| Interface shape | `proprietary-documented` — prose product pages, no OpenAPI/AsyncAPI/GraphQL, no ACRIS or OpenTravel reference |
| Second source | `alternatives-with-migration` — OAG, Cirium, FlightAware AeroAPI for flights; commodity weather providers; but no second source for LHR terminal, gate, transfer and wait-time data |
| Exit path | `export-on-request` — UK GDPR data portability via privacy@heathrow.com; no export, dump or bulk operation documented |
| Identifier portability | IATA/ICAO codes travel (LHR, EGLL, airline designators, weather-by-iatacode); the opaque `flightIds` key and the Heathrow terminal model do not |
| Contractual lock-in | No API terms of service published — the portal's own terms page is `careers.heathrow.com` boilerplate and its privacy page is Lorem ipsum. Website terms forbid systematic downloading into a database (5.5.2) and caching for third parties (5.3) |
| Distribution model | `not-applicable` — airport infrastructure, no inventory, no GDS, no NDC |
| Access gate | `application-approval` — email support@heathrow.com, justify use, complete enrolment, sign in with Azure Active Directory, and obtain a client TLS certificate for api.heathrow.com |

Full evidence, including all 44 probed URLs with HTTP status, is in [review.yml](review.yml).
