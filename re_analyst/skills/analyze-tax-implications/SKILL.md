---
name: analyze-tax-implications
description: Investigates property tax holding costs, monthly carrying costs, and acquisition cost-per-acre valuation benchmarks for a parcel.
metadata:
  adk_additional_tools:
    - get_tax_assessment_data
---
# Analyze Tax Implications Skill

When investigating financial carrying costs, acquisition basis, or tax implications for a lot:

1. **Retrieve Official Tax Assessment Records**:
   - Locate the `parcel_apn` from the subject lot's property records.
   - Call `get_tax_assessment_data` with that `parcel_apn` to retrieve `annual_tax_amount`, `assessed_land_value`, `assessed_improvement_value`, `total_assessed_value`, `tax_year`, and `payment_status`.

2. **Explicit Acquisition Cost-Per-Acre & Valuation Basis Analysis**:
   - In the **Acquisition Basis and Holding Costs** section, prominently highlight and derive the exact **Acquisition Cost-Per-Acre** using the explicit formula:
     $$\text{Acquisition Cost-Per-Acre} = \frac{\text{Last Sale Price}}{\text{Acreage}}$$
   - Also compute the **Assessed Land Value Per Acre**:
     $$\text{Assessed Land Value Per Acre} = \frac{\text{Assessed Land Value}}{\text{Acreage}}$$
   - Emphasize **Acquisition Cost-Per-Acre** as a core valuation metric, comparing the purchase basis per acre against the county's assessed land value per acre and institutional market benchmarks to evaluate whether the acquisition price is favorable or over-indexed.

3. **Explicit Monthly Tax Holding Cost Calculation**:
   - Calculate and explicitly state the exact **Monthly Tax Holding Cost** during pre-development carrying phases using the official `annual_tax_amount` from `get_tax_assessment_data` (and also note any discrepancy if `estimated_annual_taxes` in the lot record differs from the official county tax assessment):
     $$\text{Monthly Tax Holding Cost} = \frac{\text{Annual Tax Amount}}{12}$$
   - Show the exact formula and monthly dollar figure (e.g., `$23,600.00 / 12 = $1,966.67 per month`) and analyze its impact on pre-construction carrying budgets during entitlement, permitting, and environmental/hydrological due diligence timelines.
