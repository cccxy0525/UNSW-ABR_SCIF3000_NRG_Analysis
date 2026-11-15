# UNSW&ABR_SCIF3000_NRG_Analysis
An analytical companion to the SCIF3000 Australian BioResources (ABR) feasibility report. The notebook compares supplied mouse price schedules, constructs an illustrative NRG pricing benchmark, estimates initial establishment costs, and explores sales-volume scenarios. It also plots research-funding and Garvan financial context.

This is an exploratory scenario model, not evidence that an ABR NRG launch is commercially viable. ABR demand, breeding yields, ongoing production costs, customer substitution and an approved ABR NRG price have not been supplied.


## Files and Folder Structure

```text
ABR_NRG_Analysis/
├── README.md
├── requirements.txt
├── SCIF3000_ABR_NRG_Analysis.ipynb
├── SCIF3000_Dataset.xlsx
├── medical-research-future-fund-mrff-grant-recipients_0.xlsx
└── outputs/
    ├── ABR_NRG_analysis_tables.xlsx
    ├── fig_nsg_abr_vs_ozgene.png
    ├── fig3_price_regression.png
    ├── fig4_break_even.png
    ├── fig5_avg_setup_cost.png
    ├── fig1_nhmrc.png
    ├── fig2_mrff.png
    └── fig_garvan.png
```
The `outputs/` directory is automatically created when the notebook is executed and contains exported figures and analysis tables.

### Required Data Files

`SCIF3000_Dataset.xlsx` must contain the following worksheets:

| Worksheet | Description |
| --- | --- |
| `Prices 1-8 weeks` | Ozgene and ABR mouse prices by age |
| `Summary` | Garvan consolidated financial summary (2018–2025) |
| `NHMRC disease areas` | NHMRC expenditure by disease area (2016–2025) |

The MRFF workbook must contain a worksheet named `Grants List`. Worksheet names and required column structures should remain unchanged.

## Installation and Reproducibility

1. Download or clone the repository.
2. Install the required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Open a terminal in the project folder and launch Jupyter:

   ```bash
   jupyter notebook
   ```

4. Open `SCIF3000_ABR_NRG_Analysis.ipynb`.
5. Select **Kernel → Restart & Run All**.

The notebook generates analytical tables and figures in the `outputs/` directory. If a required input file cannot be located automatically, a file-selection dialogue may appear.

**Software environment:** Python 3.14.6; pandas 3.0.3; NumPy 2.4.6; matplotlib 3.11.0; openpyxl 3.1.5.
  
## Analytical Components

| Notebook cells | Analysis | Report reference |
| --- | --- | --- |
| 3 | Price–age regression | Table C1 |
| 4–5 | ABR and Ozgene NSG price comparison | NSG comparison figure |
| 6 | Price regression visualisation | Figure 3 |
| 7 | Estimated NRG pricing by age | Table 3 |
| 8 | Initial establishment cost | Table 4 |
| 9–10 | Break-even scenarios | Table 5; Figure 4 |
| 11 | Average establishment cost by sales volume | Figure 5 |
| 12–14 | MRFF and NHMRC funding trends | Figures 1–2 |
| 15 | Garvan financial context | Appendix E2 |
| 16 | Export of analytical tables | `outputs/ABR_NRG_analysis_tables.xlsx` |

## Key Results

The following results are generated using the notebook's default assumptions and should not be interpreted as validated ABR operating forecasts.

### Pricing Analysis

- Ozgene NSG and NRG prices increase by approximately AUD 1.40 per week (R² = 1.00).
- ABR NSG prices increase by approximately AUD 1.32 per week (R² = 0.983).
- ABR and Ozgene NSG prices differ by no more than AUD 0.48 across ages 3–8 weeks.
- Ozgene NRG prices are approximately 2.3 times its NSG prices.

### Establishment Cost and Break-even Scenarios

The model estimates a one-time establishment cost of **AUD 10,820.59**.

Using an illustrative selling price of **AUD 238.22 per mouse**, the estimated quantities required to recover this cost are:

| Assumed contribution margin | Estimated mice required |
| --- | ---: |
| 20% | 228 |
| 30% | 152 |
| 40% | 114 |

The average establishment cost per mouse decreases from approximately AUD 108.21 at 100 mice to AUD 21.64 at 500 mice.

These results represent scenario-based recovery of the modelled establishment cost, rather than a complete operational break-even forecast.

## Methodological Assumptions

### Pricing Benchmark

The illustrative NRG selling price is based on Ozgene's 3-week NRG price of AUD 238.22, incorporating an AUD 88 academic licence fee according to the source price list.

This competitor-specific fee may not apply to ABR. The assumed selling price is therefore a benchmarking scenario rather than an approved ABR quotation.

The ±AUD 0.50 price-comparison tolerance is an analytical assumption, not a statistical confidence interval.

### Break-even Analysis

The model evaluates hypothetical contribution margins of 20%, 30% and 40%.

The estimated sales quantity is calculated as:

```text
Required mice = ceiling(
    One-time establishment cost /
    (Assumed selling price × Assumed contribution margin)
)
```

These margins are not estimated from ABR's internal financial records. The calculation does not establish the time required to recover costs and excludes unmodelled ongoing fixed expenses.

### Research Funding Analysis

**MRFF:** Cancer-related grants are identified through keyword screening using `CANCER_KEYWORDS`. Each grant's full value is allocated to its contract commencement year. These values represent grant commitments rather than annual expenditure and should not be directly compared with NHMRC expenditure.

**NHMRC:** The descriptive linear trend for 2021–2025 is approximately +AUD 7.04 million per year. The result is sensitive to the selected period; a 2016–2025 fit produces approximately −AUD 0.55 million per year.

### Financial Context

Garvan's consolidated financial information provides organisational context but does not establish ABR's available cash, allocated investment budget or capacity to finance an NRG launch.


## Data Sources

| Dataset | Source and version | Accessed |
| --- | --- | --- |
| ABR mouse pricing | [Australian BioResources (2026), *ABR 2026 Price List (Partners)*](https://abr.org.au/ordering/price-lists/) | 30 September 2026 |
| Ozgene mouse pricing | [Ozgene (2026), *Ozgene ARC April 2026 Price List*](https://www.ozgene.com/price-lists/) | 30 September 2026 |
| NHMRC expenditure | [NHMRC, *Research Funding Statistics and Data*](https://www.nhmrc.gov.au/funding/outcomes-and-data-research/research-funding-statistics-and-data) | 7 November 2026 |
| MRFF grants | [Australian Government Department of Health, *MRFF Grant Recipients*](https://www.health.gov.au/resources/publications/medical-research-future-fund-mrff-grant-recipients?language=und); dataset version dated 10 July 2026 | 7 November 2026 |
| Garvan annual reports | [Garvan Institute of Medical Research, *Annual Reports*](https://www.garvan.org.au/about-us/annual-report) | 14 October 2026 |
| ACNC charity financial records | [ACNC Charity Documents – Record 1](https://www.acnc.gov.au/charity/charities/408b0620-38af-e811-a963-000d3ad244fd/documents/) and [Record 2](https://www.acnc.gov.au/charity/charities/e1484f4e-5736-ea11-a813-000d3ad1cc03/documents/) | 7 November 2026 |

### Supplementary Financial References

- [Australian National Audit Office (2021), *Audits of the Financial Statements of Australian Government Entities for the Period Ended 30 June 2021*](https://www.anao.gov.au/work/financial-statement-audit/audits-the-financial-statements-australian-government-entities-the-period-ended-30-june-2021). Accessed 7 November 2026.
- [NHMRC (2021), *Annual Report 2020–21*](https://www.nhmrc.gov.au/about-us/publications/annual-report-2020-21). Accessed 7 November 2026.

Project-specific and third-party data must only be redistributed where permission has been obtained.

## Updating the Analysis

- **Financial assumptions:** Modify the `ASSUMPTIONS` dictionary in Cell 1 to adjust cost inputs, contribution margins, selling-price age and sales-volume scenarios.
- **Pricing data:** Update the `Prices 1-8 weeks` worksheet while preserving its structure. An ABR NRG price schedule can be added using the supplier and strain labels expected by the notebook.
- **Disease-area analysis:** Modify `AREA` in Cell 13 to examine a different NHMRC disease category.
- **Recalculation:** Restart the kernel and run all cells after updating any input.

## Limitations

This preliminary analysis has several limitations:

- ABR-specific demand, breeding yield, mortality, production capacity and customer substitution behaviour are not modelled.
- The establishment-cost estimate excludes certain potential expenses, including health screening, courier services, licensing, housing infrastructure, approvals and overheads.
- Selected cost rates are derived from ABR's existing Partners price list and applied hypothetically to NRG.
- MRFF cancer-grant classification relies on keyword screening rather than an official classification.
- Research-funding trends are contextual indicators and do not directly measure commercial demand for NRG mice.
- The analysis does not provide a validated profitability forecast or an investment recommendation.

## Interpretation

The model provides an initial analytical framework for evaluating NRG pricing and establishment-cost recovery under alternative assumptions.

Its outputs are intended to support feasibility discussions and identify information required for further evaluation. Commercial decisions would require ABR-specific demand forecasts, breeding performance data, operating costs and validated pricing assumptions.

## Data Access and Reuse

This repository was prepared for academic assessment and project review as part of the SCIF3000 Work Integrated Learning project at UNSW in collaboration with Australian BioResources.

Project-specific datasets and third-party pricing information remain subject to applicable ownership, confidentiality and usage restrictions.

No open-source licence is granted for the project-specific code or datasets. Permission should be obtained from the relevant authors and data owners before redistribution or reuse.
  
