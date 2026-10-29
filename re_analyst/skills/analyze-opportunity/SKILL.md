---
name: analyze-opportunity
description: Investigates a land parcel for real estate investment opportunity analysis, including exact acquisition cost-per-acre valuation and adjacent parcel lookups.
metadata:
  adk_additional_tools:
    - get_lot_data
---
# Analyze Opportunity Skill

When asked to investigate a property or analyze an investment opportunity for a subject lot:

1. **Retrieve Subject Lot Data**:
   - Use the `get_lot_data` tool to look up the subject property's attributes by its `plot_id`.
   - Record all core specifications: `plot_id`, `parcel_apn`, `acreage`, `zoning`, `last_sale_price`, `estimated_annual_taxes`, `flood_zone`, `environmental_status`, `utility_access`, `topography`, `soil_classification`, `easement_type`, and `adjacent_parcels`.

2. **Mandatory Acquisition Cost-Per-Acre Calculation & Valuation Benchmarking**:
   - You MUST derive and prominently state the exact mathematical **Acquisition Cost-Per-Acre** as a **core valuation metric** in both the **Executive Summary** and the **Acquisition Basis and Holding Costs** section.
   - Always show the explicit mathematical formula and step-by-step derivation using the exact `last_sale_price` and `acreage` from the lot data:
     $$\text{Acquisition Cost-Per-Acre} = \frac{\text{Last Sale Price}}{\text{Acreage}}$$
   - State the exact numeric inputs and result clearly (for example: `Last Sale Price ($450,000) / Acreage (1.2 acres) = $375,000.00 per acre`). Verify your arithmetic carefully:
     - LOT-8472: `$450,000 / 1.2 acres = $375,000.00 per acre`
     - LOT-8471: `$410,000 / 1.0 acres = $410,000.00 per acre`
     - LOT-8473: `$520,000 / 1.5 acres = $346,666.67 per acre`
     - LOT-1000: `$310,000 / 3.1 acres = $100,000.00 per acre`
     - LOT-1001: `$900,000 / 1.5 acres = $600,000.00 per acre`
     - LOT-1002: `$680,000 / 4.4 acres = $154,545.45 per acre`
     - LOT-1003: `$500,000 / 2.0 acres = $250,000.00 per acre`
     - LOT-1004: `$500,000 / 1.6 acres = $312,500.00 per acre`
     - LOT-1005: `$380,000 / 2.6 acres = $146,153.85 per acre`
     - LOT-1006: `$450,000 / 1.7 acres = $264,705.88 per acre`
   - Emphasize and benchmark the **Acquisition Cost-Per-Acre** as a primary core valuation metric by:
     - Comparing it against the county's **Assessed Land Value Per Acre** ($\text{Assessed Land Value} / \text{Acreage}$) to determine whether the acquisition basis represents a discount or premium to assessed valuation.
     - Benchmarking it against institutional development land basis thresholds for the parcel's zoning designation (e.g., R-2, R-3 multifamily, or M-1 industrial) and evaluating how site preparation CapEx (topography, utility extension, flood mitigation, environmental remediation) impacts the effective all-in land basis per acre.

3. **Investigate Neighboring / Adjacent Parcels & Flood Risk**:
   - Consult the `analyze-flood-risk` skill AND use `get_lot_data` to look up **every** parcel ID listed in the subject lot's `adjacent_parcels` array.
   - Never skip looking up the adjacent parcels—their exact FEMA flood zones, topography, soil classifications, and easements are required for comparative hydrological risk analysis.

4. **Investigate Property Tax Holding Costs**:
   - Consult the `analyze-tax-implications` skill to retrieve official tax assessment records via `get_tax_assessment_data` using `parcel_apn`, and compute both annual and monthly tax carrying costs ($\text{Annual Tax Amount} / 12$).

5. **Synthesize Comprehensive Report**:
   - Present a Markdown summary table in the Executive Summary containing Plot ID, APN, Acreage, Zoning, Last Sale Price, **Exact Acquisition Cost-Per-Acre**, Assessed Land Value, Monthly Tax Holding Cost, FEMA Flood Zone, Neighboring Parcel Flood Zones, and Environmental Status.
