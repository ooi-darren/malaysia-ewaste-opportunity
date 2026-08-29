# Data Dictionary

This document defines every variable used in the Malaysia E-Waste Opportunity analysis. Every dataset is classified as **PUBLIC** (published directly by an official/verifiable source), **DERIVED** (calculated from a source this session directly fetched and read), or **ESTIMATED** (third-party or secondary-cited figures, not independently verified against a primary document).

**This case study leans more heavily on ESTIMATED data than 001–003.** Malaysia does not have a DOSM-style official e-waste statistics series; the best available figures come from a UN monitor report and academic literature, several of which were only accessible via secondary citation, not the primary document itself. That limitation is stated here and repeated in the notebook, not hidden.

**A separate "Why Is This Happening?" section at the end of Notebook 02 adds qualitative context**; secondary-sourced explanation (news reporting, research on Malaysia's informal recycling sector) for the mechanism behind the capture-gap finding. That content is deliberately *not* classified PUBLIC/DERIVED/ESTIMATED like the datasets in this file, since it's explanatory reporting rather than a number this project is asserting; full citations are in [`references/SOURCES.md`](./references/SOURCES.md) under "Context / Secondary Sources."

---

## ewaste_generation_estimate.csv

**Source:** UN Global E-waste Monitor 2020, as cited by Monash Lens (2023), "Understanding Malaysia's informal e-waste recycling sector"
**Classification:** ESTIMATED
**Description:** Malaysia's total e-waste generation for 2019, across all UNU-KEYS product categories (all types of discarded electronics, not just computers).

### Known limitations
- **The primary GEM 2020 report was not independently verified.** This session attempted to fetch the original UN Global E-waste Monitor report directly, the 2024 edition is gated behind an ITU registration form (not submitted, to avoid entering personal details into a form on the user's behalf), and the 2020 PDF was retrieved but could not be parsed/rendered by the tools available this session. The 364,000-tonne figure is therefore sourced via a secondary academic citation (Monash Lens), not a primary document this session read directly.
- **2019 is the only year available.** There is no multi-year Malaysia e-waste generation time series in this analysis, a single-point estimate, not a trend.

## formal_collection.csv

**Source:** Malaysia Department of Environment (DOE), as cited by Monash Lens (2023)
**Classification:** ESTIMATED (same secondary-citation caveat as above; DOE's original release was not independently located and fetched this session)
**Description:** Tonnes of **household** e-waste formally collected by DOE in 2021.

### Known limitations
- **Household-only, not total formal collection.** Commercial and industrial e-waste collection (if any is formally tracked) is not included in this figure.
- **Different year than the generation estimate** (2021 collection vs. 2019 generation), the notebook treats any comparison between them as illustrative of scale, not a precise year-matched capture rate.

## pcb_metal_content.csv

**Source:** Bizzo, W.A.; Figueiredo, R.A.; de Andrade, V.F. (2014). "Characterization of Printed Circuit Boards for Metal and Energy Recovery after Milling and Mechanical Separation." *Materials*, 7(6), 4555–4566. Fetched and read directly this session (PubMed Central, open access).
**Classification:** DERIVED: this session read the actual paper, not a secondary summary.
**Description:** Copper, gold, and silver content of printed circuit boards (PCBs), sampled from discarded desktop computers.

### Known limitations
- **Sampled PCBs were from XT/486/Pentium-era desktop computers**: old technology, not representative of current laptops, phones, or other device categories with different PCB designs.
- **The paper itself reports that gold content in PCBs has declined over time** (from above 1,000 ppm in studies from 1993–1995 to 142 ppm in this 2014 study) meaning even "citable" academic figures vary substantially by study vintage and device type. This analysis uses one dated, specific study, not an industry-wide current average.
- **Palladium is excluded from this analysis.** This study did not detect palladium in its samples; rather than substitute a figure from a different, methodologically inconsistent source, palladium's contribution to recoverable value is left out entirely, a conservative choice that understates total value, stated explicitly in the notebook.

## pcb_share_of_ewaste.csv

**Source:** Multiple academic reviews on e-waste/PCB recycling, sourced via search-result summaries (not a single directly-fetched primary paper)
**Classification:** ESTIMATED, the weakest-sourced assumption in this analysis
**Description:** Printed circuit boards' share of total e-waste weight, commonly cited as a 3–6% range across the recycling literature.

### Known limitations
- **This range was not verified against a single primary source this session read directly**, unlike `pcb_metal_content.csv`, this is a web-search-summarized "commonly cited" figure. It is used here as a rough scaling assumption, not a precise number, and the notebook presents results across the full 3–6% range rather than picking one point value.
- **PCB weight share varies by device category** (e.g., ~9.7% in laptops vs. lower in bulkier appliances), the 3–6% range is a whole-e-waste-stream average, which may not match Malaysia's actual device mix.

## metal_prices.csv

**Source:** Kitco.com spot precious/base metals price pages
**Classification:** PUBLIC: live market data, independently verifiable at any time
**Description:** Spot prices for gold, silver, and copper, fetched 27–28 August 2026.

### Known limitations
- **Spot prices move daily.** Figures are a snapshot, not representative of any other date. Anyone re-running this analysis later should refresh these values.
