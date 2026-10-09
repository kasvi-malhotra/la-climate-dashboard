# How clean is LA's grid right now?

A single-file dashboard showing live carbon intensity and generation mix for
Los Angeles (LADWP) and neighbouring California balancing authorities.

Open `index.html` in a browser. Nothing to install.

## Setup

The data comes from the US Energy Information Administration, which needs a
free API key. Get one at <https://www.eia.gov/opendata/register.php> and paste
it in when the page asks.

The key is stored in your browser's local storage, never in this file — so
this repository is safe to make public, and anyone who opens the page uses
their own key against their own quota.

## How the carbon number is calculated

EIA reports generation by fuel type, not emissions. The page multiplies each
fuel by an IPCC AR5 lifecycle emission factor (g CO2e/kWh) and takes a
generation-weighted average. The factors live in the `FUELS` object at the top
of the script, so they are easy to inspect and change.

This makes the headline number an **estimate**, not a measurement.

## Why LADWP and not "California"

The City of Los Angeles is served by LADWP, which is its own balancing
authority and is not part of CAISO. CAISO figures describe most of California
but exclude LA proper, so the two are reported separately here.

## Data source

US EIA Hourly Electric Grid Monitor, `electricity/rto/fuel-type-data`.
Readings are hourly and typically lag a few hours behind real time.
