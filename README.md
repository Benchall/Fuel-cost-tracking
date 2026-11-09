# EV Charging Log

A single web page (`index.html`) for logging EV charging for the DPD vans. It is in the same style as the Driver Pay Log and the DPD P&L Tracker, and it produces files that go straight into both.

The page is published as a claude.ai Artifact, which stores the log in its own database. If you open `index.html` straight from this repo instead, it saves to that browser only.

## What each charge records

Date, driver, van reg, charging method (home / public / on route), charge point or network, kWh, cost (£) and mileage (odometer reading).

## Allowance rules

Each driver is set up as **public-charging** or **home-charging** under *Drivers & rules*.

- **Public-charging drivers:** the business covers up to **£20 a day**. Anything over £20 is taken off their wages. If they spend less than £20, they don't keep the difference.
- **Home-charging drivers:** a flat **£10 a day** for each home-charging day, whatever they use. Tick these days under *Log charges → Home-charging days*.
- **Home-charging driver who has to charge on route:** you choose the rule under *Drivers & rules*. The default is: the business covers on-route charging up to the £20 daily cap, the driver pays the rest, and the £10 home allowance is still paid. The other choices are cap minus the home allowance, business pays it all, or driver pays it all.

The rules are worked out per driver per day from all of that day's charges. Each charge keeps the rules it was saved with, so changing a rate later doesn't change past figures.

## Views

- **Dashboard:** daily, weekly and 4-week pay period totals, filtered to all drivers, a depot, a charging method, a driver or a van. Tables by driver, method, depot, van and charge point / network (cheapest per kWh first), plus week by week and day by day.
- **Log charges:** the charge form with a live preview of the allowance for that driver's day, home-charging days, and the day's charges with the allowance worked out per driver.
- **Wage deductions:** per driver for the pay period: deductions for each week, days over the cap, home days, home allowance and net to wages, plus every day with a deduction and why.
- **Averages:** over this pay period, or the last 3, 6 or 13. Averages per driver, depot, method, driver type and van, and a pay-period-by-pay-period trend: cost to business per driver-day, spend and kWh per charge, £ per kWh, £ per mile, miles per kWh, and how often public drivers go over the cap.
- **All charges:** every charge in a pay period, with edit, delete and CSV download.

## Feeding the Driver Pay Log and the P&L

On *Wage deductions*:

- **Download for Driver Pay Log:** one line per driver per day. Deductions are type *Fuel over allowance* (a charge off pay). If "Pay the home allowance through wages" is ticked, home days are type *Top up*. Add them in the pay log under "Add a charge or payment". Driver names must match the pay log.
- **Download for P&L:** the cost to the business for each FD for each day, for the *Charging £* box on the P&L daily entry. Give each driver their FD number under *Drivers & rules*. This figure already takes off what drivers pay back and includes the home allowance.
- **Copy summary:** a short per-driver text summary for the pay period.

## Pay period

The 4-week pay period starts on the date set under *Drivers & rules* (2 Nov 2026 by default, the same as the Driver Pay Log) and resets every 28 days.
