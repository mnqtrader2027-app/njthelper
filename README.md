# MNQ OIF Trade Planner

A static HTML/Tailwind/JavaScript dashboard for MNQ-only NinjaTrader OIF file generation and trade planning.

## Features

- MNQ-only OIF generator
- PLACE, REVERSEPOSITION, CANCEL, CHANGE, CLOSEPOSITION, CANCELALLORDERS, FLATTENEVERYTHING, CLOSESTRATEGY
- Defaults to `Sim101`
- Maximum-quantity guard
- OIF `.txt` download
- Configurable live MNQ JSON price endpoint
- Start/stop price polling
- Demo price mode
- Historical CSV import (`date,time,open,close` or `datetime,open,close`)
- Open/close historical chart
- Trade planning table with local browser storage
- Trade CSV export
- Light/dark modes
- Font size 14–36 px
- Mobile-friendly layout
- Help popups and official reference links

## Run

The page can be opened directly:

1. Unzip the project.
2. Open `index.html` in Chrome, Edge, Firefox, or Safari.

For best results, serve it locally:

```bash
python3 -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

## Live Price Server

The page can call any HTTP endpoint you provide. A simple response can look like:

```json
{
  "symbol": "MNQ",
  "price": 24512.25,
  "timestamp": "2026-09-27T17:30:00-05:00"
}
```

Default JSON price field:

```text
price
```

If the endpoint is on another host/port, it must allow browser CORS requests.

## Historical CSV

Example:

```csv
date,time,open,close
2026-09-25,09:30,24600.25,24618.50
2026-09-25,09:31,24618.50,24612.00
```

or:

```csv
datetime,open,close
2026-09-25 09:30,24600.25,24618.50
2026-09-25 09:31,24618.50,24612.00
```

## NinjaTrader OIF

NinjaTrader documents OIF files as semicolon-delimited text files whose filenames begin with `oif` and are placed into the NinjaTrader `incoming` folder.

The browser intentionally **downloads** the OIF rather than attempting to write directly to your NinjaTrader folder.

Practice with `Sim101` before using any live account.

## Official references

- NinjaTrader OIF:
  https://static.ninjatrader.com/support/helpGuides/nt8/order_instruction_files_oif.htm
- NinjaTrader Commands and Valid Parameters:
  https://static.ninjatrader.com/support/helpGuides/nt8/commands_and_valid_parameters.htm
- NinjaTrader Information Update Files:
  https://static.ninjatrader.com/support/helpGuides/nt8/information_update_files.htm
- CME Micro E-mini Nasdaq-100:
  https://www.cmegroup.com/markets/equities/nasdaq/micro-e-mini-nasdaq-100.html

## Important

This is an educational trade-planning and file-generation utility. It is not a broker, brokerage API, or guarantee that an order is appropriate. Verify generated instructions inside NinjaTrader.
