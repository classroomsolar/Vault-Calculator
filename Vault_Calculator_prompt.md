# Vault_Calculator_prompt
## Electrical Boxes, Enclosures, Handholes & Vaults Calculator

| Item | Detail |
|---|---|
| Calculator | **Vault_Calculator** |
| Status | Existing calculator — continue and complete on the website |
| Website page | `/enclosures` (junction/combiner/pull/pole/wall-drop/termination boxes, handholes, vault cable space, boards, metering panels) |
| Master Prompt V5.0 scope | Group 6 — Electrical Boxes and Enclosures (R115–R140) |
| Project types | P1 utility fixed-tilt, P2 utility single-axis tracker, P3 commercial carport, P4 commercial/industrial rooftop, P5 residential rooftop — applicability recorded per requirement (REQUIRED / CONDITIONAL / NOT APPLICABLE / UNSUPPORTED, Section 19) |
| Revision | Final — 14 November 2026 |

**This is the only .md file for Vault_Calculator.** It holds only what is specific to this calculator. Everything common to all calculators — owner and language rules, the development process (execution cycle, phases, engineering and testing rules, working method, records), report and output presentation, the module completion checklist, website acceptance and the common tool list — is in **Master Prompt V5.0** (`00_MASTER_PROMPT_V5.0.txt`) and is not repeated here. Give the AI both files. If they disagree, the Master Prompt wins.

Every other .md file of this repository (including `00_INDEX.md` and the original prompt file) is copied word for word in the **Appendix** at the end, so nothing is lost when those files are deleted. Sections 1–11 are the working file; the appendix is reference only.

## 1. What this calculator does

Electrical design of DC/AC junction boxes, combiner enclosures, pull boxes, conduit bodies, handholes, pole-mounted and pole-top boxes, wall-drop and transition boxes, termination boxes, terminal blocks, gland plates, internal spacing, enclosure heat dissipation, IP/NEMA ratings, disconnect enclosures, ACDB/DCDB, metering panels, CT/PT compartments, electrical working space and clearances, and the enclosure component and entry schedule (Group 6, R115–R140). Electrical space, arrangement, rating, heat and entry checks only.

**Scope boundary:** Never build, anywhere in this calculator: generator sources or sizing, HV / EHV equipment or studies (above the 35 kV class), substation engineering, field testing / measurement / commissioning, structural / civil / mechanical calculations, and any financial or cost calculation (equipment prices, CAPEX, OPEX, LCOE, tariffs). BESS is deferred (Master Prompt Section 18): do not build it now, but keep data models ready for it. Everything is built on the public website — no spreadsheets, no VBA, no desktop tools.

## 2. Requirements of this calculator

### 2.1 Functional requirements from Master Prompt V5.0

Every requirement below must end up implemented and verified, or marked NOT APPLICABLE / NOT SUPPORTED with a written reason. "Current state" is the starting point found in the earlier work; confirm it in Phase 0.

**Group 6 — Electrical Boxes and Enclosures (R115–R140, 26 active)**

| ID | Requirement (Master Prompt V5.0, verbatim) | Current state |
|---|---|---|
| R115 | DC junction-box electrical design. | Not built — build new · shared engine: DC junction and combiner boxes |
| R116 | AC junction-box electrical design. | Not built — build new |
| R117 | DC combiner enclosure electrical design. | Not built — build new · shared engine: DC junction and combiner boxes |
| R118 | Pull-box internal electrical space assessment. | Built earlier — verify |
| R119 | Pull-box dimension and cable-entry assessment. | Built earlier — verify |
| R120 | Conduit-body size and conductor-space assessment. | Partly built — complete |
| R121 | Handhole internal electrical cable-space assessment. | Built earlier — verify |
| R122 | Pole-mounted electrical-box design. | Not built — build new |
| R123 | Pole-top electrical-box design. | Not built — build new |
| R124 | Pole cable-entry and termination-space assessment. | Not built — build new |
| R125 | Wall-drop electrical-box design. | Not built — build new |
| R126 | Wall-transition and cable-transition-box design. | Not built — build new |
| R127 | Cable termination-box design. | Partly built — complete |
| R128 | Terminal-block quantity and arrangement assessment. | Not built — build new |
| R129 | Gland-plate and cable-entry design checks. | Partly built — complete |
| R130 | Internal electrical-component spacing assessment. | Partly built — complete |
| R131 | Enclosure heat-dissipation assessment. | Partly built — complete |
| R132 | IP and NEMA enclosure-rating selection. | Partly built — complete |
| R133 | Disconnect enclosure electrical suitability assessment. | Not built — build new |
| R134 | ACDB electrical design. | Not built — build new |
| R135 | DCDB electrical design. | Not built — build new |
| R136 | Metering-panel electrical design. | Not built — build new · shared engine: Metering panels |
| R137 | CT/PT compartment electrical arrangement. | Not built — build new |
| R138 | Electrical working-space assessment. | Partly built — complete |
| R139 | Electrical access and clearance checks. | Partly built — complete |
| R140 | Enclosure electrical component and entry schedule. | Partly built — complete |

### 2.2 Additional requirements from this calculator's earlier documents

These came from the earlier README / prompt / requirement documents and are kept because they match Master Prompt V5.0.

| # | Requirement | Matches V5.0 |
|---|---|---|
| D01 | Vault/enclosure minimum dimensions (NEC straight/angle/U/splice) | R118–R119, R121 |
| D02 | Cable bend radius | R157/R182 shared engine; R121 space |
| D03 | Wall-entry geometry, clash screening | R119, R129 |
| D04 | Cable stacking/separation; cable support/racking layout | R130 (internal spacing); rack structure excluded |
| D05 | Splice-space and termination working-space checks | R121, R127, R138 |
| D06 | Thermal handoff (screen + external study handoff) | R131 enclosure heat; cable thermal → Cable_Thermal_Calculator |
| D07 | Conduit fill; spare conduits; future expansion reserve | R142, R177 |
| D08 | NEC 314.16 small-box fill | R120 (conduit bodies/boxes) |
| D09 | Vault schedule; BOM; automatic plan/section schematic | R140, R411, R424; schematic ≠ CAD (Group 17 boundary) |
| D10 | Source-backed ampacity + AC voltage-drop planning screen | R089/R092 owned by cable calculators |

### 2.3 Engineering method and verification requirements (Master Prompt Part 7)

Apply Master Prompt Section 40 in full, plus:

- Pull-box and handhole sizing per the selected code edition (straight, angle, U-pull, splice rules) with exact provisions cited; boundary tests at the multiplier limits.
- Conduit-body volume and conductor-space checks against the governing table, not a web summary.
- Working space and clearances per the selected code edition and voltage.

### 2.4 Shared engines and connections to other calculators (Sections 23, 45, 49)

- **Owns:** box / pull box / conduit body / handhole / vault cable-space engine, entry and clearance engine, enclosure heat engine, IP/NEMA selection, enclosure schedule.
- **Uses:** DC box engine from DC_Protection_Combiner (R115, R117); metering-panel engine from LV_Interconnection_Metering (R136); pulling engine from Cable_Tray; heat/thermal from Cable_Thermal; conductor data from the Master Database.
- **Gives:** box and vault results to Documentation_Schedules_QA (R409–R413, R140).

| Direction | Data | From / to |
|---|---|---|
| In | Cable ODs, bend radii, conductor counts | Master DB / the DC calculators (PV_String_MPPT, DC_Protection_Combiner, DC_Cable_Connector) / the LV AC calculators (Inverter_LV_AC, LV_Interconnection_Metering) / the MV calculators (MV_Electrical_Design, Transformer_POI) |
| In | Box electrical ratings and contents | the DC calculators (PV_String_MPPT, DC_Protection_Combiner, DC_Cable_Connector) (DC boxes), the LV AC calculators (Inverter_LV_AC, LV_Interconnection_Metering) (AC boxes, metering panels) |
| In | Conduit entries, routes | Cable_Tray_Calculator |
| In | Heat loads of internal components | the DC calculators (PV_String_MPPT, DC_Protection_Combiner, DC_Cable_Connector) / the LV AC calculators (Inverter_LV_AC, LV_Interconnection_Metering) equipment records |
| Out | Box/vault sizes, entries, clearances, heat check | Documentation_Schedules_QA_Calculator schedules (R409–R413, R140) |
| Out | Pulling cases (until Cable_Tray_Calculator owns the engine) | Cable_Tray_Calculator |
| Out | Thermal handoff (cables in vault) | Cable_Thermal_Calculator |

Every connection is a typed, versioned contract; a changed upstream result marks this calculator's dependent results STALE.

## 3. Work already done

**Status:** the previous version of this calculator (retired) implemented the following. It is rebuilt on the website from this specification.

**Functions specified and previously built:** vault/handhole minimum internal dimensions by the code straight-pull, angle-pull, U-pull and splice rules; cable bend radius; wall/floor/ceiling entry geometry with coordinates, opening sizes, edge/spacing checks and clash screening; duct spacing and conduit-bank arrangement (rows × columns); entry/exit orientation; forward/reverse pulling with segment tension, sidewall pressure, jam ratio, cumulative bends, per-segment friction with low/base/high sensitivity, cable OD/weight tolerance sensitivity; route network (XYZ nodes, blocked links, shortest path, alternate route); rack occupancy and cable clear spacing; splice-space and termination working space; small-box fill (conductors, EGC, yoke, clamps, terminal blocks); conduit fill, spare conduits and future reserve; thermal screen with handoff to a full study; grounding/bonding/shield gates with handoff; vault schedule, BOM quantities and automatic plan/section schematic; redesign advisor (what-if without changing the baseline); 61 hard tests and a 200-case challenge set.

## 4. Functions still to be added

- [ ] R115–R117 junction and combiner enclosures using the DC_Protection_Combiner box engine.
- [ ] R122–R128 pole-mounted and pole-top boxes, pole cable entries, wall-drop and transition boxes, termination boxes, terminal-block arrangement.
- [ ] R132–R137 IP/NEMA selection, disconnect enclosures, ACDB, DCDB, metering panels (LV_Interconnection_Metering engine), CT/PT compartments.
- [ ] R131 enclosure heat dissipation from component loss data.
- [ ] R138–R139 complete electrical working-space and clearance checks (termination working envelope was incomplete).

**Requirements with no implementation yet (build new):**

- [ ] R115 DC junction-box electrical design
- [ ] R116 AC junction-box electrical design
- [ ] R117 DC combiner enclosure electrical design
- [ ] R122 Pole-mounted electrical-box design
- [ ] R123 Pole-top electrical-box design
- [ ] R124 Pole cable-entry and termination-space assessment
- [ ] R125 Wall-drop electrical-box design
- [ ] R126 Wall-transition and cable-transition-box design
- [ ] R128 Terminal-block quantity and arrangement assessment
- [ ] R133 Disconnect enclosure electrical suitability assessment
- [ ] R134 ACDB electrical design
- [ ] R135 DCDB electrical design
- [ ] R136 Metering-panel electrical design
- [ ] R137 CT/PT compartment electrical arrangement

## 5. Earlier work still to be completed

- [ ] Rebuild every box/handhole/vault function of Section 3 on the website (R118–R121, R129–R130, R140).
- [ ] Give the pulling and route functions to Cable_Tray_Calculator (shared pulling engine) and the duct-bank arrangement to Cable_Thermal_Calculator (R174) as their reference specifications; this calculator then calls those engines.
- [ ] The final integrated report and QA of the previous version's last batch are done on the website.

**Partly built — complete them:**

- [ ] R120 Conduit-body size and conductor-space assessment
- [ ] R127 Cable termination-box design
- [ ] R129 Gland-plate and cable-entry design checks
- [ ] R130 Internal electrical-component spacing assessment
- [ ] R131 Enclosure heat-dissipation assessment
- [ ] R132 IP and NEMA enclosure-rating selection
- [ ] R138 Electrical working-space assessment
- [ ] R139 Electrical access and clearance checks
- [ ] R140 Enclosure electrical component and entry schedule

**Built earlier — rebuild/carry over to the website and prove with tests:**

- [ ] R118 Pull-box internal electrical space assessment
- [ ] R119 Pull-box dimension and cable-entry assessment
- [ ] R121 Handhole internal electrical cable-space assessment

## 6. Checks and audits still to be done

- [ ] Pull-box and handhole sizing per the adopted code edition with exact provisions; boundary tests at the multipliers.
- [ ] Conduit-body and box-fill volume checks against the governing table.
- [ ] Heat dissipation only from datasheet loss data.
- [ ] Rebuild the 61 hard tests and the 200-case challenge set as website tests; independent hand calculations; invalid geometry.
- [ ] Plus the standard audits and research register of Master Prompt Sections 11 and 72 (engineering, software, data, integration, UI/UX, security, requirements coverage).

## 7. Phases for this calculator
Phase names, "done when" rules and the process are in Master Prompt Section 62 and Section 7. What each phase means here:

| Phase | Work for this calculator |
|---|---|
| 0 Inventory (read-only) | Write the master specification of every function in Section 3; map R115–R140. |
| 1 Engine | Box, handhole and vault cable-space engine; entry and clearance engine; heat engine; IP/NEMA selection. |
| 2 Functional verification | Inputs, units, defaults, overrides, sequence, equations, intermediate values, invalid inputs, lookups, warnings, repeatability |
| 3 Challenge and independent validation | Hand calculations, hard tests, challenge campaign. |
| 4 Customer workflow | Which inputs are visible, auto-filled from the database, inherited from other calculators, optional or advanced |
| 5 UX/UI | Box/vault plan and section views from engine data. |
| 6 Integration | Use DC_Protection_Combiner, LV_Interconnection_Metering, Cable_Tray (pulling) and Cable_Thermal (heat) engines; schedules to Documentation_Schedules_QA. |
| 7 Release | Staging and public-URL tests, monitoring, backup/restore, rollback |

### 7.1 Calculator-specific rules carried over from the earlier documents
- Hard tests 61/61; challenge 200; tool benchmark 100; research register

## 8. Final result — what "finished" looks like

- Verified electrical design of every box, enclosure, handhole and vault type in Group 6 on the website, with plan/section views and the enclosure schedule.
- Every requirement in section 2 implemented, or marked NOT APPLICABLE / NOT SUPPORTED with a written reason, with evidence — plus the module completion checklist, website acceptance, reports/exports and final delivery report of Master Prompt Sections 57, 77–78, 87, 94 and 95.

## 9. Tools specific to this calculator
The common tool list is in Master Prompt Section 8.

| Purpose | Tool |
|---|---|
| Geometry checks | Python (Shapely), Wolfram |
| Feature benchmarking only | Southwire, Polywater, Greenlee pulling and box-sizing tools (documentation) |

Benchmark tools are used to compare features and results only — never copy their code, data or methods without checking them (Section 12).

## 10. Earlier baseline kept in this repository
The retired version is `Vault_Calculator_v4.0_B09` (Excel/VBA): `Underground_Enclosure_Calculator_v4.0_B09_SCHEDULE_BOM_SCHEMATIC.xlsx`, `OneClickReport_v4_0_B09.bas`, `Vault_Calculator_v4.0_B09_FULL_PACKAGE_README.txt`, `v40_B09_audit.json`, `v40_B09_vba_audit.json` and two preview PNGs. Use it only as the reference specification for section 3 (and its 61 hard tests and 200-case set); nothing is built in Excel or VBA any more.

## 11. Status on 22 Nov 2026
- Previous version: retired (v4.0_B09 workbook). Repository: commit `4cb5875`, 15 Nov 2026.
- Phases 0–7 of section 7: **none started.** Next task: Phase 0.

---

# APPENDIX — all other .md files of this repository (word for word)

The documents below are copied word for word from the repository. Only heading levels were moved down so they fit inside this file.


---

## A1. Calculator prompt files — index (00_INDEX.md, same in all five calculator repos)


*Source file: `00_INDEX.md`*

### Calculator prompt files — index

One file per calculator. Each file is the only document that calculator needs; give it to the AI together with Master Prompt V5.0 (`00_MASTER_PROMPT_V5.0.txt`). Every file has the same sections:

0 About this file · 1 What the calculator does · 2 Requirements (V5.0 requirements verbatim + requirements from the earlier documents + method/verification + connections) · 3 Work already done · 4 Functions still to be added · 5 Earlier work still to be completed · 6 Checks and audits still to be done · 7 Process to follow · 8 Final result · 9 Plugins and tools · 10 First task

**Existing calculators**

| File | Calculator | V5.0 group |
|---|---|---|
| Fault_Current_Studio_prompt.md | Fault current, protection, arc flash, load flow, harmonics | 14 |
| Production_Calculator_prompt.md | Site, resource, shading, tracker, bifacial, plant sizing, energy yield | 1, 16 |
| Cable_Thermal_Calculator_prompt.md | Trench, underground cable, duct bank thermal | 8 |
| Grounding_Calculator_prompt.md | Grounding and bonding | 9 |
| Cable_Tray_Calculator_prompt.md | Conduit, raceway, cable tray, routing, cable pulling | 7 |
| Vault_Calculator_prompt.md | Boxes, enclosures, handholes, vaults | 6 |

**New calculators**

| File | Calculator | V5.0 group |
|---|---|---|
| PV_String_MPPT_Calculator_prompt.md | PV module, string and MPPT design | 2 |
| DC_Protection_Combiner_Calculator_prompt.md | DC protection, fuses, combiner/junction boxes | 3 |
| DC_Cable_Connector_Calculator_prompt.md | DC cables and connectors | 4 |
| Inverter_LV_AC_Calculator_prompt.md | Inverter and LV AC design | 5 |
| Lightning_Surge_Protection_Calculator_prompt.md | Lightning and surge protection | 10 |
| LV_Interconnection_Metering_Calculator_prompt.md | LV interconnection, export control, metering | 11 |
| MV_Electrical_Design_Calculator_prompt.md | Medium-voltage design | 12 |
| Transformer_POI_Calculator_prompt.md | Transformers and POI | 13 |
| Interconnection_Architecture_Calculator_prompt.md | Interconnection architectures | 15 |
| Documentation_Schedules_QA_Calculator_prompt.md | Schedules, BOM, reports, design QA | 17 |

**Shared (used by every calculator)**

| File | Role |
|---|---|
| Engineering_Master_Database_prompt.md | The single equipment database |
| Platform_Website_prompt.md | The website itself: pages, projects, network model, shared engines, security, deployment |

All 428 Master Prompt requirement IDs are covered, each in exactly one file.

**Suggested order:** Engineering_Master_Database → Platform_Website → Fault_Current_Studio → Production_Calculator → Grounding, Cable_Thermal, Cable_Tray, Vault → PV_String_MPPT → DC_Protection_Combiner → DC_Cable_Connector → Inverter_LV_AC → Transformer_POI → MV_Electrical_Design → LV_Interconnection_Metering → Lightning_Surge_Protection → Interconnection_Architecture → Documentation_Schedules_QA.


---

## A2. Original prompt file (as it was before this merge)


*Sections 1–11 above contain all of its calculator-specific content; the common parts are in Master Prompt V5.0. Kept here only so nothing is lost word for word.*


*Source file: `Vault_Calculator_prompt.md`*

### Vault_Calculator_prompt
#### Electrical Boxes, Enclosures, Handholes & Vaults Calculator

| Item | Detail |
|---|---|
| Calculator | **Vault_Calculator** |
| Status | Existing calculator — continue and complete on the website |
| Website page | `/enclosures` (junction/combiner/pull/pole/wall-drop/termination boxes, handholes, vault cable space, boards, metering panels) |
| Master Prompt V5.0 scope | Group 6 — Electrical Boxes and Enclosures (R115–R140) |
| Project types | P1 utility fixed-tilt, P2 utility single-axis tracker, P3 commercial carport, P4 commercial/industrial rooftop, P5 residential rooftop — applicability recorded per requirement (REQUIRED / CONDITIONAL / NOT APPLICABLE / UNSUPPORTED, Section 19) |
| Revision | Final — 14 November 2026 |

#### 0. About this file

- This is the **only** project document for this calculator. It replaces every earlier README, prompt, handoff and requirement document; everything still needed from them is written here.
- Governing specification: **Master Prompt V5.0** (Integrated Electrical PV Design Engineering Platform, 9 November 2026). Give the AI both this file and the Master Prompt at the start of every session. If the two ever disagree, the Master Prompt wins.
- The calculator is part of **one integrated public website** (Master Prompt Sections 2, 43, 80): its own route/page, shared project data, shared equipment database, shared reports.
- Reply to the owner in **Hinglish** (simple Hindi–English). Write code, reports and documents in English.
- The owner is an electrical / PV design engineer, not a software developer. The AI does the research, design, coding, testing, debugging and documentation itself (Master Prompt Sections 1–4).


#### 1. What this calculator does

Electrical design of DC/AC junction boxes, combiner enclosures, pull boxes, conduit bodies, handholes, pole-mounted and pole-top boxes, wall-drop and transition boxes, termination boxes, terminal blocks, gland plates, internal spacing, enclosure heat dissipation, IP/NEMA ratings, disconnect enclosures, ACDB/DCDB, metering panels, CT/PT compartments, electrical working space and clearances, and the enclosure component and entry schedule (Group 6, R115–R140). Electrical space, arrangement, rating, heat and entry checks only.

**Scope boundary:** Never build, anywhere in this calculator: generator sources or sizing, HV / EHV equipment or studies (above the 35 kV class), substation engineering, field testing / measurement / commissioning, structural / civil / mechanical calculations, and any financial or cost calculation (equipment prices, CAPEX, OPEX, LCOE, tariffs). BESS is deferred (Master Prompt Section 18): do not build it now, but keep data models ready for it. Everything is built on the public website — no spreadsheets, no VBA, no desktop tools.


#### 2. Requirements of this calculator


##### 2.1 Functional requirements from Master Prompt V5.0

Every requirement below must end up implemented and verified, or marked NOT APPLICABLE / NOT SUPPORTED with a written reason. "Current state" is the starting point found in the earlier work; confirm it in Phase 0.


**Group 6 — Electrical Boxes and Enclosures (R115–R140, 26 active)**

| ID | Requirement (Master Prompt V5.0, verbatim) | Current state |
|---|---|---|
| R115 | DC junction-box electrical design. | Not built — build new · shared engine: DC junction and combiner boxes |
| R116 | AC junction-box electrical design. | Not built — build new |
| R117 | DC combiner enclosure electrical design. | Not built — build new · shared engine: DC junction and combiner boxes |
| R118 | Pull-box internal electrical space assessment. | Built earlier — verify |
| R119 | Pull-box dimension and cable-entry assessment. | Built earlier — verify |
| R120 | Conduit-body size and conductor-space assessment. | Partly built — complete |
| R121 | Handhole internal electrical cable-space assessment. | Built earlier — verify |
| R122 | Pole-mounted electrical-box design. | Not built — build new |
| R123 | Pole-top electrical-box design. | Not built — build new |
| R124 | Pole cable-entry and termination-space assessment. | Not built — build new |
| R125 | Wall-drop electrical-box design. | Not built — build new |
| R126 | Wall-transition and cable-transition-box design. | Not built — build new |
| R127 | Cable termination-box design. | Partly built — complete |
| R128 | Terminal-block quantity and arrangement assessment. | Not built — build new |
| R129 | Gland-plate and cable-entry design checks. | Partly built — complete |
| R130 | Internal electrical-component spacing assessment. | Partly built — complete |
| R131 | Enclosure heat-dissipation assessment. | Partly built — complete |
| R132 | IP and NEMA enclosure-rating selection. | Partly built — complete |
| R133 | Disconnect enclosure electrical suitability assessment. | Not built — build new |
| R134 | ACDB electrical design. | Not built — build new |
| R135 | DCDB electrical design. | Not built — build new |
| R136 | Metering-panel electrical design. | Not built — build new · shared engine: Metering panels |
| R137 | CT/PT compartment electrical arrangement. | Not built — build new |
| R138 | Electrical working-space assessment. | Partly built — complete |
| R139 | Electrical access and clearance checks. | Partly built — complete |
| R140 | Enclosure electrical component and entry schedule. | Partly built — complete |

##### 2.2 Additional requirements from this calculator's earlier documents

These came from the earlier README / prompt / requirement documents and are kept because they match Master Prompt V5.0.

| # | Requirement | Matches V5.0 |
|---|---|---|
| D01 | Vault/enclosure minimum dimensions (NEC straight/angle/U/splice) | R118–R119, R121 |
| D02 | Cable bend radius | R157/R182 shared engine; R121 space |
| D03 | Wall-entry geometry, clash screening | R119, R129 |
| D04 | Cable stacking/separation; cable support/racking layout | R130 (internal spacing); rack structure excluded |
| D05 | Splice-space and termination working-space checks | R121, R127, R138 |
| D06 | Thermal handoff (screen + external study handoff) | R131 enclosure heat; cable thermal → Cable_Thermal_Calculator |
| D07 | Conduit fill; spare conduits; future expansion reserve | R142, R177 |
| D08 | NEC 314.16 small-box fill | R120 (conduit bodies/boxes) |
| D09 | Vault schedule; BOM; automatic plan/section schematic | R140, R411, R424; schematic ≠ CAD (Group 17 boundary) |
| D10 | Source-backed ampacity + AC voltage-drop planning screen | R089/R092 owned by cable calculators |

##### 2.3 Engineering method and verification requirements (Master Prompt Part 7)

Apply Master Prompt Section 40 in full, plus:

- Pull-box and handhole sizing per the selected code edition (straight, angle, U-pull, splice rules) with exact provisions cited; boundary tests at the multiplier limits.
- Conduit-body volume and conductor-space checks against the governing table, not a web summary.
- Working space and clearances per the selected code edition and voltage.


##### 2.4 Shared engines and connections to other calculators (Sections 23, 45, 49)

- **Owns:** box / pull box / conduit body / handhole / vault cable-space engine, entry and clearance engine, enclosure heat engine, IP/NEMA selection, enclosure schedule.
- **Uses:** DC box engine from DC_Protection_Combiner (R115, R117); metering-panel engine from LV_Interconnection_Metering (R136); pulling engine from Cable_Tray; heat/thermal from Cable_Thermal; conductor data from the Master Database.
- **Gives:** box and vault results to Documentation_Schedules_QA (R409–R413, R140).

| Direction | Data | From / to |
|---|---|---|
| In | Cable ODs, bend radii, conductor counts | Master DB / the DC calculators (PV_String_MPPT, DC_Protection_Combiner, DC_Cable_Connector) / the LV AC calculators (Inverter_LV_AC, LV_Interconnection_Metering) / the MV calculators (MV_Electrical_Design, Transformer_POI) |
| In | Box electrical ratings and contents | the DC calculators (PV_String_MPPT, DC_Protection_Combiner, DC_Cable_Connector) (DC boxes), the LV AC calculators (Inverter_LV_AC, LV_Interconnection_Metering) (AC boxes, metering panels) |
| In | Conduit entries, routes | Cable_Tray_Calculator |
| In | Heat loads of internal components | the DC calculators (PV_String_MPPT, DC_Protection_Combiner, DC_Cable_Connector) / the LV AC calculators (Inverter_LV_AC, LV_Interconnection_Metering) equipment records |
| Out | Box/vault sizes, entries, clearances, heat check | Documentation_Schedules_QA_Calculator schedules (R409–R413, R140) |
| Out | Pulling cases (until Cable_Tray_Calculator owns the engine) | Cable_Tray_Calculator |
| Out | Thermal handoff (cables in vault) | Cable_Thermal_Calculator |

Every connection is a typed, versioned contract; a changed upstream result marks this calculator's dependent results STALE.


#### 3. Work already done

**Status:** the previous version of this calculator (retired) implemented the following. It is rebuilt on the website from this specification.

**Functions specified and previously built:** vault/handhole minimum internal dimensions by the code straight-pull, angle-pull, U-pull and splice rules; cable bend radius; wall/floor/ceiling entry geometry with coordinates, opening sizes, edge/spacing checks and clash screening; duct spacing and conduit-bank arrangement (rows × columns); entry/exit orientation; forward/reverse pulling with segment tension, sidewall pressure, jam ratio, cumulative bends, per-segment friction with low/base/high sensitivity, cable OD/weight tolerance sensitivity; route network (XYZ nodes, blocked links, shortest path, alternate route); rack occupancy and cable clear spacing; splice-space and termination working space; small-box fill (conductors, EGC, yoke, clamps, terminal blocks); conduit fill, spare conduits and future reserve; thermal screen with handoff to a full study; grounding/bonding/shield gates with handoff; vault schedule, BOM quantities and automatic plan/section schematic; redesign advisor (what-if without changing the baseline); 61 hard tests and a 200-case challenge set.


#### 4. Functions still to be added

- [ ] R115–R117 junction and combiner enclosures using the DC_Protection_Combiner box engine.
- [ ] R122–R128 pole-mounted and pole-top boxes, pole cable entries, wall-drop and transition boxes, termination boxes, terminal-block arrangement.
- [ ] R132–R137 IP/NEMA selection, disconnect enclosures, ACDB, DCDB, metering panels (LV_Interconnection_Metering engine), CT/PT compartments.
- [ ] R131 enclosure heat dissipation from component loss data.
- [ ] R138–R139 complete electrical working-space and clearance checks (termination working envelope was incomplete).

**Requirements with no implementation yet (build new):**

- [ ] R115 DC junction-box electrical design
- [ ] R116 AC junction-box electrical design
- [ ] R117 DC combiner enclosure electrical design
- [ ] R122 Pole-mounted electrical-box design
- [ ] R123 Pole-top electrical-box design
- [ ] R124 Pole cable-entry and termination-space assessment
- [ ] R125 Wall-drop electrical-box design
- [ ] R126 Wall-transition and cable-transition-box design
- [ ] R128 Terminal-block quantity and arrangement assessment
- [ ] R133 Disconnect enclosure electrical suitability assessment
- [ ] R134 ACDB electrical design
- [ ] R135 DCDB electrical design
- [ ] R136 Metering-panel electrical design
- [ ] R137 CT/PT compartment electrical arrangement

#### 5. Earlier work still to be completed

- [ ] Rebuild every box/handhole/vault function of Section 3 on the website (R118–R121, R129–R130, R140).
- [ ] Give the pulling and route functions to Cable_Tray_Calculator (shared pulling engine) and the duct-bank arrangement to Cable_Thermal_Calculator (R174) as their reference specifications; this calculator then calls those engines.
- [ ] The final integrated report and QA of the previous version's last batch are done on the website.

**Partly built — complete them:**

- [ ] R120 Conduit-body size and conductor-space assessment
- [ ] R127 Cable termination-box design
- [ ] R129 Gland-plate and cable-entry design checks
- [ ] R130 Internal electrical-component spacing assessment
- [ ] R131 Enclosure heat-dissipation assessment
- [ ] R132 IP and NEMA enclosure-rating selection
- [ ] R138 Electrical working-space assessment
- [ ] R139 Electrical access and clearance checks
- [ ] R140 Enclosure electrical component and entry schedule

**Built earlier — rebuild/carry over to the website and prove with tests:**

- [ ] R118 Pull-box internal electrical space assessment
- [ ] R119 Pull-box dimension and cable-entry assessment
- [ ] R121 Handhole internal electrical cable-space assessment

#### 6. Checks and audits still to be done

- [ ] Pull-box and handhole sizing per the adopted code edition with exact provisions; boundary tests at the multipliers.
- [ ] Conduit-body and box-fill volume checks against the governing table.
- [ ] Heat dissipation only from datasheet loss data.
- [ ] Rebuild the 61 hard tests and the 200-case challenge set as website tests; independent hand calculations; invalid geometry.
- [ ] Engineering audit (Section 72): methods, editions, equations, assumptions, units, correction factors, limits, source applicability, independent results, unsupported conditions, false PASS results.
- [ ] Software audit: logic, architecture, types, validation, error handling, edge cases, duplication, hard-coded values, feature preservation.
- [ ] Data audit: units, types, sources, revisions, duplicates, conflicts, missing values, overrides.
- [ ] Integration audit: schemas, IDs, dependencies, STALE results, unit and method compatibility with connected calculators.
- [ ] UI/UX audit: workflow, labels, units, help, warnings, responsiveness (desktop/tablet/mobile), WCAG 2.2 AA accessibility, diagram accuracy, persistence.
- [ ] Security audit: authentication, authorisation, private/public separation, secrets, input validation, dependencies.
- [ ] Requirements coverage audit: every ID in Section 2 traced to code and tests.
- [ ] Research register and benchmark matrix (Section 11): relevant calculators, manufacturer tools and papers actually reviewed (count only real sources).

#### 7. Process to follow to finish everything

This is the Master Prompt V5.0 development process applied to this calculator. Follow it for every task.

##### 7.1 Rules that never change (Master Prompt Sections 5, 6, 27, 34)
- Never invent a standard, clause, formula, coefficient, equipment rating, curve, clearing time, test result or repository state. Missing critical input → **INPUT REQUIRED**; never a guessed value.
- Every numerical result comes from a deterministic, tested calculation engine — never from AI text.
- Every result shows a status: PASS, FAIL, REVIEW REQUIRED, INPUT REQUIRED, NOT APPLICABLE, NOT VERIFIED, NOT SUPPORTED or STALE. Never PASS when inputs, sources, methods or validation are missing. Every warning says what is wrong, why it matters, which input to check and how to fix it.
- Never claim "complete", "100 %", "certified" or "compliant" without the evidence of Section 8 of this file.
- Preserve working calculations and verified results; change a validated method only with a documented reason and tests (Sections 52, 58).
- No paid service, subscription or usage-based dependency without the owner's approval (Section 84). No credentials, secrets or private data in code or Git (Sections 6, 60, 82).

##### 7.2 Execution cycle for every task (Master Prompt Section 7)
**A Inspect** existing code, data, tests and behaviour → **B Research** primary standards, editions, manufacturer documents, papers and benchmark tools → **C Design** inputs, outputs, units, equations, sequence, error states, tests → **D Implement** the deterministic engine first, then UI, diagrams, data and integration, in small reversible changes → **E Test** (unit, golden, independent, boundary, invalid input, regression, UI, export, security, end-to-end) → **F Audit and fix** (separate engineering and software reviews; repeat until no critical/high defect) → **G Improve** (low-risk improvements; scope expansion only with approval) → **H Report** (files changed, tests run, results, limitations, next step). Do not stop after a plan, a draft or a good-looking screen.

##### 7.3 Phases (Master Prompt Section 62)
| Phase | Work for this calculator | Done when |
|---|---|---|
| 0 Inventory (read-only) | Write the master specification of every function in Section 3; map R115–R140. | Phase 0 report delivered: inventory, current state of every requirement with evidence, risks, batch plan, single best next task |
| 1 Engine | Box, handhole and vault cable-space engine; entry and clearance engine; heat engine; IP/NEMA selection. | Every engine has a master specification, version ID, typed contract and test harness, separate from UI |
| 2 Functional verification | Inputs, units, defaults, overrides, sequence, equations, intermediate values, invalid inputs, lookups, warnings, repeatability | All found defects fixed and retested |
| 3 Challenge and independent validation | Hand calculations, hard tests, challenge campaign. | Golden and independent checks pass within justified tolerances; real challenge-case count reported |
| 4 Customer workflow | Which inputs are visible, auto-filled from the database, inherited from other calculators, optional or advanced | Workflow specification written |
| 5 UX/UI | Box/vault plan and section views from engine data. | Screens use the shared design system; visuals come from the same data as the calculation |
| 6 Integration | Use DC_Protection_Combiner, LV_Interconnection_Metering, Cable_Tray (pulling) and Cable_Thermal (heat) engines; schedules to Documentation_Schedules_QA. | End-to-end tests pass; STALE tracking works |
| 7 Release | Staging and public-URL tests, monitoring, backup/restore, rollback | Owner approves the production release |

##### 7.4 Engineering rules for every engine (Master Prompt Sections 28–33, 46–48)
- Before coding: master specification (purpose, inputs with units and sources, outputs, standard and edition, equations, assumptions, valid range, warnings, test cases) and data-dictionary entries with stable names (no "Value1", "Factor2").
- Engine: defined inputs/outputs/units, equations with variable definitions, source references (standard, edition, clause/table/equation), assumptions, valid range, input validation, numerical precision/convergence, version ID; identical results for identical inputs; handles zero/negative/huge/tiny/missing values; never shows a failed calculation as a normal result; separate from the UI.
- Units: one central unit service; SI internally; feet/inches and metric display; never mix units silently; full precision internally, round only for display.
- Assumptions classified CONFIRMED / DEFAULT / ENGINEERING ASSUMPTION / NEEDS USER CONFIRMATION / REFERENCE-DERIVED. Show DATABASE VALUE, USER OVERRIDE and VALUE USED IN CALCULATION for every overridable value, with an audit trail.
- Equipment data only from the Master Engineering Database (Section 44), auto-populated from the selected record, with the database revision stored with every result.
- Traceability chain for every important result: user input → database value → intermediate values → correction factors → equation/method → final result, with the limit used, status, warnings, sources and engine version.
- Results passed to other calculators go through typed, versioned contracts; changed upstream inputs mark downstream results **STALE** (Sections 47–50). Never propagate a result whose study case, topology, voltage level or assumptions do not match.

##### 7.5 Testing rules (Master Prompt Sections 66–71)
- Golden tests with source of expected values; independent hand calculations or separate scripts (never only against code that shares the implementation); tolerances justified, never chosen to make a test pass.
- Boundary, invalid-input, unit-conversion, unsupported-case and regression tests; end-to-end tests for every applicable project type P1–P5.
- Challenge campaign toward **200 meaningful cases** designed to make the calculator fail; report the real number completed.
- Every reported defect: reproduce → trace UI → validation → lookup → calculation → result → saved state → fix the root cause → add a regression test → rerun all golden tests.

##### 7.6 Working method
- GitHub is the home of the code (Section 60): tag the known-good state before work, feature branch, small commits, pull request for engineering/data/security changes, tests run before merge, tagged releases with rollback points.
- Work in controlled batches (Section 61); after each batch give the delivery report of Section 87 (requested, done, requirement IDs, preserved, files changed, sources, tests run with results, remaining gaps, next step).
- Keep these records up to date in the repository (Section 85): REQUIREMENTS.md (traceability for every ID in Section 2), MASTER_SPECIFICATION.md, DATA_DICTIONARY.md, DECISIONS.md, SOURCE_REGISTER.md, TEST_MATRIX.md, ISSUES.md, PROGRESS.md, CHANGELOG.md.
- Ask the owner only when a decision changes safety, correctness, scope, cost, privacy or is irreversible (Section 5). The only open items the Master Prompt leaves to the owner are: jurisdiction and code editions to target first, hosting provider and budget, which calculator becomes the first fully verified reference module, whether 35 kV stays the MV limit (Appendix F) — plus approval of production releases and paid services.

##### 7.7 Calculator-specific rules carried over from the earlier documents
- Hard tests 61/61; challenge 200; tool benchmark 100; research register


#### 8. Final result — what "finished" looks like

- Verified electrical design of every box, enclosure, handhole and vault type in Group 6 on the website, with plan/section views and the enclosure schedule.
- **Every requirement in Section 2** is implemented, or marked NOT APPLICABLE / NOT SUPPORTED with a written reason, with evidence in REQUIREMENTS.md (file, function, test). Status per requirement follows Section 57 (IMPLEMENTED — NOT VERIFIED → SOFTWARE TESTED → ENGINEERING VALIDATED → DEPLOYED → APPROVED).
- **Module completion checklist (Master Prompt Section 94) fully satisfied:** scope documented; existing behaviour preserved; methods and standard editions verified or flagged; deterministic engine separated from UI; inputs/outputs/units/assumptions/overrides/limits traceable; equipment data from the Master Database with revision recorded; golden and independent checks pass within justified tolerances; boundary, invalid-input, unsupported-case and regression tests pass; engineering and software reviews recorded; integration and STALE control work; UI and diagrams match the engine; reports and exports reproduce the screen; security and privacy satisfied; limitations disclosed; no known critical or high-severity defect.
- **Website acceptance (Section 95):** works on the public domain over HTTPS; its route opens directly and after refresh; desktop, tablet and mobile; private projects stay private; save/load/scenarios/recovery work; tested through the real public URL.
- **Reports and exports (Sections 77–78):** PDF calculation package, CSV, JSON (and schedules where applicable) containing inputs, units, equipment and database revision, method and standard edition, intermediate values, results with status, assumptions, warnings, sources and engine version — identical to the screen.
- **Honest status:** a final delivery report (Section 87) states exactly what is complete, what is not, and why.


#### 9. Plugins and tools

| Capability (Master Prompt Section 8) | Use it for | Example plugin / tool |
|---|---|---|
| Git repository connector | Branches, commits, pull requests, issues, diffs | GitHub connector |
| Coding agent + execution environment | Write code, run builds and tests, debug | Coding agent with terminal (e.g. Claude Code / similar), Node.js, Python |
| Web research and browser | Official standards information, manufacturer datasheets, benchmark tool documentation | Web search, web fetch, browser |
| PDF / OCR document reader | Read code books, datasheets, manuals, papers page by page | PDF reader with OCR |
| Owner's document storage | The owner's books and reference PDFs (for example the NEC books kept in Dropbox) | Google Drive / Dropbox connector |
| Academic research search | Peer-reviewed papers and DOIs | Semantic Scholar / Google Scholar / IEEE Xplore search |
| Independent maths check | Hand-check equations and reference values | Python (NumPy, SciPy, SymPy), Wolfram |
| Browser / UI automation | End-to-end tests on desktop and mobile, downloads, console errors | Playwright (Chromium, Firefox, WebKit) |
| Accessibility check | WCAG 2.2 AA audit | axe-core / Lighthouse |
| UI / diagram design | Wireframes, screen flows, engineering diagrams | Figma or similar design tool |
| Database connector | Schemas, migrations, records, permissions | Connector for the chosen database |
| Hosting / deployment connector | Deployments, logs, domains, rollback | Connector for the chosen host (Wix connector only for the existing live sites) |
| Security analysis | Dependency, secret and code scanning | Dependabot / npm audit / pip-audit, CodeQL, secret scanning |

Use a tool only when it has a real role, check access/permissions/quota/cost first, never claim a tool ran when it did not (Sections 8–9). Do not use Formula Genius or Coursera. When delegation is available, split work into specialist reviews — standards, independent calculation, equipment data, code/architecture, UX, security, testing — and have an independent checker that never sees the builder's code (Section 9).

**Specific to this calculator:**

| Purpose | Tool |
|---|---|
| Geometry checks | Python (Shapely), Wolfram |
| Feature benchmarking only | Southwire, Polywater, Greenlee pulling and box-sizing tools (documentation) |

Benchmark tools are used to compare features and results only — never copy their code, data or methods without checking them (Section 12).


#### 10. First task and first reply

1. Reply in Hinglish: confirm that Master Prompt V5.0 governs and that this is **Vault_Calculator**; say what you can and cannot access.
2. Do Phase 0 only (read-only): inventory, current state of every requirement in Section 2 with evidence, risks, batch plan for Phases 1–3, and the single best next task.
3. Wait for the owner to approve the Phase 0 report, then work through Sections 4, 5 and 6 using the process of Section 7 until Section 8 is true.
