# EV Charging Log

A single web page (`index.html`) for logging EV charging for the DPD vans. It is in the same style as the Driver Pay Log and the DPD P&L Tracker, and it produces files that go straight into both.

The page is published as a claude.ai Artifact, which stores the log in its own database. If you open `index.html` straight from this repo instead, it saves to that browser only.

## What is recorded

- **Home charging:** tick each driver who charged at home that day. Nothing else is needed.
- **Public and on-route charges:** date, driver, method (public / on route), charge point or network, cost (£) and mileage (odometer).

## Allowance rules

Worked out per driver per day from everything they charged that day:

- **Home-charged day:** a flat **£10**. Any other charging that day (public or on route) is paid back by the driver in full. Cost to the business: £10.
- **Day with no home charge:** a **£20 credit** for public and on-route charging. Anything over comes off their wages, so a £31 day means £11 off wages. Spending less earns nothing. Cost to the business: up to £20.

Both amounts can be changed under *Drivers & rules*. Each charge keeps the amounts it was saved with, so changing them later doesn't change past days.

## Views

- **Dashboard:** daily, weekly and 4-week pay period totals, filtered to all drivers, a depot, a charging method or a driver. Tables by driver, method, depot and charge point / network, plus week by week and day by day.
- **Log charges:** tick who home-charged, log public and on-route charges with a live preview of the driver's day, and see the allowance worked out per driver.
- **Wage deductions:** per driver for the pay period: deductions for each week, home and public days, home allowance, net to wages and cost to the business, plus every day with a deduction and why.
- **Averages:** over this pay period, or the last 3, 6 or 13. Per driver, depot and method, home-charged days against public days, and a pay-period trend.
- **All charges:** everything in a pay period, with edit, delete and CSV download.

## Feeding the Driver Pay Log and the P&L

On *Wage deductions*:

- **Download for Driver Pay Log:** one line per driver per day. Deductions are type *Fuel over allowance*. If "Pay the home allowance through wages" is ticked, home-charged days are type *Top up*. Driver names must match the pay log.
- **Download for P&L:** the cost to the business for each driver for each day, for the *Charging £* box on the P&L daily entry.
- **Copy summary:** a short per-driver text summary for the pay period.

## Pay period

The 4-week pay period starts on the date set under *Drivers & rules* (2 Nov 2026 by default, the same as the Driver Pay Log) and resets every 28 days.
