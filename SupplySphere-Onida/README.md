# SupplySphere AI — Onida (Consumer Electronics) Prototype

Live demo: https://mithilpattani.github.io/Public-Links/SupplySphere-Onida/

The same SupplySphere AI prototype as the sibling `SupplySphere-Manufacturing` folder, hand-curated for a different industry — a consumer electronics manufacturer (TVs, chips, ACs), referenced internally as "Onida - Consumer Electronics Group." Same mechanism and screens, different product lines, materials, suppliers, and disruption story, so a prospect in that industry sees their own business reflected back rather than a generic mockup. No build step — everything lives in `index.html`.

## What's different from the Manufacturing version

- **Flagship product**: Televisions (LED/LCD, Smart TV, OLED/QLED Premium), with Air Conditioners and Small Kitchen Appliances as secondary lines. Chips/semiconductors are not a separate product — they're the System-on-Chip (SoC) material inside the Televisions Bill of Materials, which is where the real supply risk lives.
- **Drill-down story**: Televisions → OLED/QLED Premium → Infinity View OLED → screen size, with 55" flagged as both the best-selling size and the most stock-critical (6-day cover vs. a 10-day reorder point).
- **Disruption storyline**: a Taiwan Strait naval-exercise disruption affecting OLED display panels and SoC chips, replacing the Strait of Hormuz story used in the Manufacturing version.
- **Built-in AI voice narration**: click the "AI Narration" button (bottom-left of the screen, opposite the Sphere assistant) to have each screen explained aloud automatically as you navigate — uses the browser's built-in speech synthesis, no API key or backend required, works offline. Starts off by design (browsers require a user click before allowing audio); one click enables it for the rest of the session.

## Notes for anyone picking this up

- This is a prototype/mockup, not a connected product — all data is illustrative and hand-numbered to be internally consistent (sub-category revenue reconciles with the sum of its models/styles, etc.), not live.
- The fictional client name and every number here were built for a specific demo meeting and can be re-curated for a different customer in this same industry by editing `index.html` directly (single file, no dependencies).
