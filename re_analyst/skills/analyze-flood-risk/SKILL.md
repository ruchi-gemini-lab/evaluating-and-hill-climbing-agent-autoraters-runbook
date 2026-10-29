---
name: analyze-flood-risk
description: Investigates subject parcel and neighboring/adjacent property FEMA flood zone designations, drainage, runoff, and shared hydrological risks.
metadata:
  adk_additional_tools:
    - get_lot_data
---
# Analyze Flood Risk Skill

When evaluating environmental, flood, or hydrological risks for a subject lot, you MUST evaluate both the **subject parcel** AND **all neighboring/adjacent properties**:

1. **Subject Parcel Flood Zone & Engineering Impact Analysis**:
   - Check the exact FEMA `flood_zone` designation from the subject lot's data (e.g., `Zone AE (High Risk)`, `Zone VE (Coastal High Hazard)`, `Zone A (100-year Floodplain)`, `Zone X (Minimal Risk)`).
   - Explain the exact regulatory, insurance, and vertical construction impacts (e.g., mandatory NFIP flood insurance, Base Flood Elevation (BFE) freeboard compliance, engineered structural fill dirt, deep foundation pilings/breakaway walls for Zone VE coastal velocity hazard, stormwater retention/detention pond sizing, and foundation waterproofing).

2. **Mandatory Lookup of All Neighboring / Adjacent Properties**:
   - Inspect the `adjacent_parcels` field of the subject lot (e.g., `["LOT-8471", "LOT-8473"]`).
   - Call the `get_lot_data` tool for **each and every Lot ID** listed in `adjacent_parcels` to retrieve their official property records.
   - For every neighboring parcel, explicitly record and report in the memorandum:
     - Neighboring Lot ID (`plot_id`)
     - Exact FEMA Flood Zone classification (`flood_zone`)
     - Topography and grade slope (`topography`)
     - Soil classification and drainage profile (`soil_classification`)
     - Relevant drainage or utility easements (`easement_type`)

3. **Exhaustive Neighboring Property Hydrological, Drainage & Runoff Analysis**:
   - Dedicate a clear, prominent subsection in **Risk Assessment** (and summarize in **Executive Summary**) titled **Neighboring Property Flood Risk & Shared Hydrological Analysis**.
   - Explicitly list each adjacent parcel by ID and state its exact FEMA flood zone classification alongside the subject parcel's FEMA flood zone.
   - Critically analyze the **shared hydrological dynamics, cross-parcel drainage, and surface/subsurface runoff impacts** between the neighboring properties and the subject lot:
     - **Floodplain Continuity & Encroachment**: Evaluate whether adjacent parcels are in high-risk floodplains (`Zone AE`, `Zone VE`, `Zone A`) that create contiguous floodplain exposure, coastal storm surge propagation, or backwater/tailwater pooling across property boundaries, even if the subject parcel is in `Zone X (Minimal Risk)` (or vice versa, where grading on the subject parcel could displace floodwaters onto adjacent parcels).
     - **Topographic Gradient & Stormwater Runoff Vectors**: Compare the subject parcel's `topography` (e.g., `0-2% grade (Flat)`, `2-5% grade`, `5-12% grade`, `15%+ grade`) against each neighboring parcel's slope and `soil_classification` (e.g., `Clay loam` with low permeability vs. `Sandy loam` vs. `Urban Land-Inwood complex`). Analyze whether uphill/steep adjacent parcels will shed sheet-flow runoff onto a flatter subject parcel, or whether development and impervious surface creation on the subject parcel will accelerate runoff toward downhill neighboring lots.
     - **Drainage Easements & Shared Infrastructure**: Identify any `Drainage Easement` on the subject or adjacent parcels and explain how shared swales, perimeter French drains, retention/detention basins, cut-off walls, and civil grading plans must be engineered to prevent cross-boundary flooding and satisfy municipal no-adverse-impact stormwater regulations.
     - **Development Feasibility Impact**: Conclude how these neighboring hydrological conditions affect the subject parcel's buildable envelope, site preparation CapEx, civil engineering timeline, and overall investment viability.
