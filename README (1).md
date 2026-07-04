# MISP Practice Lab

A self-contained, browser-based simulation of **MISP (Malware Information Sharing Platform & Threat Sharing)** — the open-source threat intelligence platform used by CERTs, SOCs, and ISACs worldwide. Built to practice the analyst workflow (events, attributes, tags, galaxies, objects, correlation, feeds) without needing a real MISP deployment, and to demonstrate that workflow to others.

**[Live demo →](#) &nbsp;·&nbsp; No install, no backend — open `misp-practice-lab.html` in any browser**

---

## Why I built this

MISP is a core tool in threat intelligence and SOC work, but spinning up a real instance (Docker, MySQL, Redis, a full LAMP-ish stack) is overkill just to learn the interface and workflow. This project recreates the **layout, terminology, and core analyst actions** of real MISP as a single static HTML/CSS/JS file, with a built-in guided curriculum so the practice is structured rather than aimless clicking.

## Features

- **Realistic MISP UI** — dark top navbar with dropdown menus (Event Actions, Global Actions, Input Filters, Administration), event index, event detail pages — modeled directly on the real product
- **Seeded reference data** — read-only demo events from simulated CIRCL / Nordic-SOC / ACME-CERT / Global-ISAC sources, so the instance feels like a live shared community rather than an empty sandbox
- **Full CRUD analyst workflow**
  - Create/edit/delete events (threat level, analysis stage, distribution)
  - Add attributes (category, type, value, IDS flag) — including attribute-level tagging
  - Tag events (TLP + custom taxonomy tags)
  - Attach MISP Galaxy clusters (Threat Actor / Malware / MITRE ATT&CK)
  - Build structured MISP Objects (e.g. `file`, `domain-ip` templates)
  - Record sightings on indicators
  - Correlate indicators across events, with a visual Event Graph
  - Export an event as MISP-style JSON
  - Enable/fetch external OSINT feeds (simulated)
  - Free-text import — paste raw text and auto-extract IOCs
  - Create Sharing Groups and bind them to event distribution
  - Leave discussion comments on any event, including read-only ones
  - Propose corrections on another org's event (simulated review workflow)
  - Check indicator decay scores and warninglist matches
  - Automation/API reference page with sample requests
- **30-lesson guided curriculum** — Beginner → Intermediate → Expert, each lesson auto-validates against real actions taken in the app (no manual "mark complete"), capped with a completion celebration
- **Persistent progress** — work is saved automatically (browser `localStorage`) and survives page reloads

## Concepts practiced

| Area | What it covers |
|---|---|
| Event lifecycle | Draft → enriched → published, threat level & analysis workflow |
| Indicator hygiene | Categories/types, IDS signature flagging, MISP Objects vs. loose attributes |
| Sharing control | TLP tagging, distribution levels (org-only → all communities) |
| Correlation | How shared indicator values link separate incidents/events |
| Context enrichment | Galaxies/clusters for threat actor & MITRE ATT&CK attribution |
| Automation | Feed ingestion (how MISP pulls in external OSINT automatically) |
| Interoperability | JSON export, the shape of MISP's event/attribute/object data model |

## Tech stack

Deliberately dependency-free:

- Plain **HTML / CSS / JavaScript** — no framework, no build step, no server
- State kept in-memory and persisted via a simple key-value storage API
- Single file — clone it, open it, done

## Run it locally

```bash
git clone https://github.com/<your-username>/misp-practice-lab.git
cd misp-practice-lab
open misp-practice-lab.html   # or just double-click it
```

## What I learned building this

- The structure of MISP's core data model (Event → Attribute/Object → Tag/Galaxy)
- Why distribution levels, TLP tagging, and IDS flags exist and how analysts use them
- How correlation and sighting data actually help prioritize threat intel
- Building a small in-browser "SPA" pattern (state object + re-render) without a framework

## Roadmap / possible extensions

- [ ] Proposal/collaboration workflow (org B suggesting edits to org A's event)
- [ ] Decaying indicator scores
- [ ] STIX 2.1 export format alongside MISP JSON
- [ ] Larger galaxy/taxonomy library

## Screenshots

<img width="1365" height="681" alt="Screenshot 2026-07-04 162747" src="https://github.com/user-attachments/assets/47f4ea51-ed1d-4c03-baed-3e4625d28216" />

<img width="1360" height="685" alt="Screenshot 2026-07-04 162803" src="https://github.com/user-attachments/assets/881f13df-0bb5-42b0-b012-54e35bea2268" />

## License

MIT — free to reuse for your own learning or teaching.
