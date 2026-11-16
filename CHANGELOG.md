# Copperdrop Panel Planner changelog

Versions use MAJOR.MINOR.PATCH. MINOR adds features, PATCH fixes, MAJOR changes the config or workbook format in a way older versions can't read. Every release ships as `PanelPlanner_vX.Y.Z.zip`.

## 3.0.0 (2026-11-15)
- Public release for GitHub.
  - Clean build with no personal configuration.
  - New README covering build-your-own steps, privacy and repository layout.
  - LICENSE, a demo example file (`examples/demo-home.json`) and screenshots.
- **Load demo** button (Overview and Configs) opens a fictional house that uses every feature:
  - every source type: utility, NG standby on ATS, dual fuel portable, diesel pickup with a 12 V inverter charging a BLUETTI AC200L, portable and roof solar, and a disabled Powerwall;
  - a full five-stage cascade, run plan, supplies, recharge and a custom library item;
  - one overloaded circuit, deliberately.
- The demo opens automatically the first time someone opens the tool.
- Help adds a Demo tour section. A Tips entry covers the demo button.
- Fix: a natural gas standby no longer counts against the gasoline of a portable in the same plan. Any NG generator means no tank limit, in the tool and in the Excel formula.
- Fix: the Overview verdict says Yes when power holds and only a wiring or breaker problem is flagged, instead of "Not yet".
- Fix: the baseline delta for unserved energy showed NaN.
- Fix: the vehicle "no battery to charge" warning no longer fires when a plug-in power station is the target.
- Overview lists plug-in power stations separately from whole-home battery kWh.
- Header drops the internal program code.

## 2.9.0 (2026-11-07)
- Run Plan charging logistics: option for a solar generator that must be moved to charge. Its plug-in loads lose power while away (or move to house outlets during generator runs), and solar input stops if the panels don't reach.
- Fix: in the vehicle stage a fridge left on its house circuit was counted as powered during idle runs; the vehicle inverter only charges the solar generator.
- Routine and notes describe the move, and suggest an extension cord to keep the station in place.

## 2.8.1 (2026-11-07)
- Fix: Run Plan timeline names the running source per stage (Generator, Vehicle idling, No engine) with its own color, instead of always "Generator".
- Timeline adds a Charging lane showing when and how much the generator or vehicle inverter charges the solar generator.

## 2.8.0 (2026-11-07)
- New Supplies tab: fuel needed for the Run Plan at each cascade stage (natural gas in cu ft and therms, propane, gasoline, diesel, vehicle idling), days per stage, on hand vs needed, shortfall, cost at your prices, container counts, storage and engine-care suggestions.
- Vehicle presets: full-size gas V8 pickup (about 0.9 gal/hr idle), Cummins 6.7 I6 at high idle (0.8 gal/hr, 110 A spare) or low idle (0.5 gal/hr), midsize gas V6. Vehicle fuel type and fuel on hand fields.
- Dual-fuel generators: choose gasoline or propane for the totals.
- Excel: Supplies sheet with live needed and shortfall formulas. PowerPoint: Supplies slide.

## 2.7.0 (2026-11-07)
- Source cascade on the Run Plan tab: stages built from the configuration in order (utility, whole-house generator, portable generator, vehicle inverter, solar generators only). Each stage re-plans with what is left.
- Runner model per stage: panel-fed generators keep house circuits (portables keep as many priority tiers as they can carry) and run A/C only with capacity; vehicle inverters recharge the solar generator; solar-only stage runs silent.
- Automatic re-prioritizing: keeps the highest-priority plug-in loads the solar generator can sustain (medical, fridge, freezer, comms, chargers, lights, fans) and unplugs the rest.
- Stage ladder diagram with verdict, run hours and how long each stage lasts on fuel on hand; What still works table across stages; click a stage for its full plan.
- All enabled solar generators are pooled in the run plan.
- Indoor temperature now drifts toward an outdoor limit when no A/C or heat is available.
- Excel: Cascade sheet. PowerPoint: Source Cascade slide (native shapes and table).

## 2.6.0 (2026-11-07)
- Run Plan: Generator and Solar generator dropdowns now include the full equipment library. Picking a library model adds it to Sources (solar generators as plug-in only; a new generator turns off the previous one).
- Run Plan: add solar panels from the library with a quantity, and tick which panels charge the solar generator.
- Fix: Run Plan timeline day labels moved above the chart so they no longer overlap the hour axis.

## 2.5.0 (2026-11-07)
- New Run Plan tab: finds the fewest generator hours and starts per day that keep food safe (USDA fridge 4 h, freezer 24 or 48 h), keep the house within a temperature limit (summer cooling or winter heating model) and keep a solar generator from running empty, with no running during quiet hours.
- Pick what is plugged into the solar generator while the generator is off; solar recharge, wall/generator recharge and pass-through modeled hourly.
- Plain-language daily routine, multi-day timeline (generator, sun, solar generator charge, fridge/freezer, indoor temperature), engine care (starts, load, oil-check spacing) and fuel per day (NG cu ft and therms).
- What-if suggestions when no schedule fits (unplug a load, shift quiet hours, allow a warmer house).
- Manual mode to test your own run times.
- Excel: Run Plan sheet (inputs, routine, hourly values). PowerPoint: Run Plan slide with native shapes and charts.

## 2.4.0 (2026-11-07)
- Recharge time calculator (Overview and Simulation tabs, Recharge sheet in Excel). Portable solar by weather and season, capped at the station's solar input; wall, generator and vehicle charge times.
- Load basis toggle: Realistic demand (NEC 220.82 method, default) or Everything at once. Drives continuous, per-leg and surge checks, sizing and Fit.
- Battery connection "Plug-in loads only" keeps a power station out of the house outage plan.
- Generator now also starts when the battery can't cover the next hour.
- Library: separate wall charge and solar input ratings for power stations.

## 2.3.0 (2026-11-07)
- Equipment library expanded to 443 models: full EcoFlow (incl. TITAN 5000) and BLUETTI (incl. AC200L) lines, Jackery, Anker SOLIX, Goal Zero, home batteries, top 5 standby and portable generator brands, hybrid inverters, 12 V inverters, solar panels, LiFePO4 batteries.
- Brand filter and search in the source picker; Add from the Library tab.
- Vehicle / 12 V inverter source (charges battery or powers loads, alternator-limited).
- Battery max charge rate limits recharging.
- Help tab (user manual, glossary) and Tips hover explanations.
- Fix: PowerPoint export library now loads from three CDNs with fallback.

## 2.2.0 (2026-11-06)
- Natural gas generators show "no tank limit" instead of asking for fuel on hand.
- Fix: tier badge overlapped long breaker labels.

## 2.1.0 (2026-11-06)
- Light/dark theme button, remembered per device.

## 2.0.0 (2026-11-05)
- Simple and Engineer modes, Overview verdict, setup wizard.
- Backup priority tiers and Fit to my equipment.
- Per-leg and 240 V checks, two-motor surge, code checks (wire vs breaker, NEC 705.12).
- Multi-day hourly outage simulation with load profiles, battery SOC, generator start/stop and fuel.
- Excel adds Simulation and Profiles tabs; PowerPoint adds summary and simulation charts.

## 1.0.0 (2026-11-05)
- Initial release: panel editor, sources, load moves with live deltas, named configs, Excel export/import with live formulas, PowerPoint and SVG block diagram.
