# SupplySphere AI — Manufacturing (Footwear) Prototype

Live demo: https://mithilpattani.github.io/Public-Links/SupplySphere-Manufacturing/

A hand-authored, single-file HTML/CSS/JS click-through prototype of SupplySphere AI — an AI-powered supply chain risk-intelligence platform. No build step, no Node.js, no install of any kind required — everything (HTML, CSS, and JavaScript) lives in `index.html`.

This is the original/default vertical: a manufacturer of footwear and accessories ("ALDO-style Footwear & Accessories Group"), currently at V21 of that product's iteration history.

## What it demonstrates

- **My Products**: the single pivot point — every product's revenue, risk status, and a ranked "Highest Selling Products/Styles" view (surfaces the true #1 seller by revenue, not just by category).
- **Product profile (Footwear)**: a 6-tab connected page — Overview (with a nested drill-down: sub-category → actual style → size/variant, so the highest-selling size is visible at a glance), Materials & Suppliers (a Bill of Materials with a live order-quantity calculator sized to the highest-selling variant), Signals & Alerts, Financial Impact, Knowledge Graph, and Decide & Act (alternate suppliers, route optimizer, scenario simulation).
- **Global screens**: Alerts & Signals, Supplier & BOM Risk Radar, Reports, Masters, AI Agent Operations Center, and a live crisis-storyline walkthrough (Strait of Hormuz disruption) that traces a real event from geopolitics to shelf impact.

## Notes for anyone picking this up

- This is a prototype/mockup, not a connected product — all data is illustrative and hand-numbered to be internally consistent (sub-category totals reconcile with the sum of their styles, etc.), not live.
- Same product mechanism gets hand-curated per industry/customer for demos — see the sibling `SupplySphere-Onida` folder in this repo for the consumer-electronics version of the exact same tool.
