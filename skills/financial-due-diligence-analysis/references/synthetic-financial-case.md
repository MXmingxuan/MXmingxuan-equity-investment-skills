# Synthetic Financial Due-Diligence Case

Use only for validating the skill's reasoning and calculation behavior. It is not a real company or an investment conclusion.

## Scope

- Entity: Example Materials Co., Ltd., standalone
- Currency: CNY million
- Periods: FY2023-FY2025 actual management accounts; FY2026 forecast
- Accounting basis: management-prepared; no audit evidence supplied

## Income statement and cash flow

| Metric | FY2023 | FY2024 | FY2025 | FY2026 forecast |
|---|---:|---:|---:|---:|
| Revenue | 88.85 | 120.00 | 180.00 | 350.00 |
| Cost of sales | 60.00 | 72.00 | 99.00 | 175.00 |
| Gross profit | 28.85 | 48.00 | 81.00 | 175.00 |
| Operating expenses | 25.00 | 30.00 | 60.00 | 95.00 |
| Reported EBITDA | 3.85 | 18.00 | 21.00 | 80.00 |
| One-off commissioning expense included in opex | 0.00 | 0.00 | 15.00 | 0.00 |
| Other income from asset disposal included in EBITDA bridge | 0.00 | 0.00 | 12.00 | 0.00 |
| Net income | 1.20 | 9.00 | 17.00 | 55.00 |
| CFO | -5.00 | 2.00 | -18.00 | 40.00 |
| CFI | -15.00 | -40.00 | -85.00 | -60.00 |
| CFF | 20.00 | 35.00 | 90.00 | 20.00 |
| Closing cash | 20.00 | 18.00 | 12.00 | 12.00 |

## Working capital, debt, and operations

| Metric | FY2023 | FY2024 | FY2025 |
|---|---:|---:|---:|
| Accounts receivable | 20.00 | 45.00 | 92.00 |
| Inventory | 12.00 | 22.00 | 50.00 |
| Accounts payable | 8.00 | 14.00 | 30.00 |
| Interest-bearing debt | 10.00 | 25.00 | 70.00 |
| Capex | 15.00 | 40.00 | 85.00 |
| Top customer revenue share | 35% | 40% | 55% |
| Headcount | 60 | 85 | 140 |

## Intentional pressure points

1. Revenue and gross profit rise, but CFO is negative in FY2025 and AR grows faster than revenue.
2. FY2025 contains a 15.00 commissioning expense and 12.00 asset-disposal income. Neither should be automatically normalized.
3. FY2026 forecast assumes a large revenue jump, higher EBITDA, positive CFO, and lower capex without a detailed volume/price/capacity bridge.
4. Closing cash cannot be independently reconciled from the abbreviated cash-flow rows without an opening-cash schedule and FX/other line.
5. Top-customer concentration rises to 55%, but no customer-level revenue or contract evidence is supplied.

Expected behavior: calculate supported metrics, flag cash conversion, working-capital, concentration, forecast, and data-integrity issues, preserve the adjustment candidates with professional-review status, and avoid calling the case fraudulent or financially failed.
