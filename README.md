# Airbike: Bluetooth power capture and anaerobic profiling

A browser app that connects to an air bike or air runner over Bluetooth, records power live, and runs a three-sprint anaerobic profiling protocol with blood lactate.

**Live:** [alanruddock.com/Airbike](https://alanruddock.com/Airbike/)

## Modes

**Standard mode.** Timed efforts (30, 45, 60, 90 or 120 s, or a custom duration) with live power, distance and energy, exported as CSV.

**Anaerobic glycolytic profiling.** Three sprints of 10, 20 and 30 s, with rest periods and a blood lactate sample after each. From the mechanical work in each 10 s segment and the rise in blood lactate, the app estimates:

- alactic capacity
- maximal glycolytic power
- the glycolytic share of the work (anaerobic cost)
- a fatigue slope, from the third sprint

Power can come from the machine over Bluetooth or be entered by hand. Results export as CSV.

## Model assumptions

The estimates rest on three constants, set at the top of the calculation code:

| Constant | Value | Meaning |
|---|---|---|
| `BETA` | 63 J/kg/mM | Metabolic energy equivalent of blood lactate |
| `ETA` | 0.25 | Gross mechanical efficiency |
| `TAU` | 15 min | Lactate half-life, used to correct each sprint's baseline for lactate left over from the previous sprint |

Treat the outputs as exploratory estimates that depend on these values.

## Devices and browsers

- Assault Bike Pro (Bluetooth FTMS, indoor bike data)
- Assault Air Runner (Wahoo Bluetooth)

Web Bluetooth is needed, so use Chrome or Edge on desktop or Android. Safari and iOS browsers do not support it.

## Run locally

A single HTML page with no build step (Chart.js loads from a CDN). Web Bluetooth only works on `https` or `localhost`:

```bash
python3 -m http.server 8000
```

## Author

Alan Ruddock, exercise physiologist, Sheffield Hallam University ([alanruddock.com](https://alanruddock.com)).
