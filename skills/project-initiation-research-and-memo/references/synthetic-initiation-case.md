# Synthetic Multi-Round Initiation Case

This case is fictional and exists only to test the iterative behavior of the skill. Do not present it as a real company or as market evidence.

## Baseline

Project: **澄岳工业视觉有限公司（虚构）**

The initial project card says the company sells AI visual-inspection equipment for lithium-battery factories. It claims:

- 2025 revenue of approximately 4,500万元;
- 2026 revenue forecast of 1.2亿元;
- five battery-factory customers;
- an inspection algorithm with a claimed 98.5% defect-recognition rate;
- a planned 6,000万元 Series B financing;
- founder-held patents that are expected to be transferred to the company.

The first-pass report identifies these P0 gaps:

- whether the five customers are paid deployments or only pilots;
- whether the recognition rate is independently tested in production;
- revenue breakdown, gross margin, receivables, and cash runway;
- patent ownership and any founder-related license;
- whether the company can deliver hardware and service at the forecast scale.

## Round 1: Agent research and request generation

The agent finds one public procurement notice naming the company and a company announcement describing a “strategic cooperation” with another manufacturer. It does not find reliable support for five paid customers or the 98.5% production metric.

The correct output should:

- record the procurement notice as external evidence;
- keep the five-customer statement as a management/project-material claim;
- create requests for customer status, production test reports, financial detail, and patent transfer documents;
- not fill the gaps with generic industry knowledge;
- leave the status as `waiting_for_materials` or `researching`, not `ready_for_formal_due_diligence`.

## Round 2: User supplies materials

The user supplies a management accounts spreadsheet and a founder email. The spreadsheet says 2025 revenue was 4,620万元, but 1,700万元 came from hardware resale, gross margin was 21%, and accounts receivable were 1,900万元. The founder email says two customers are in paid pilot, one has a signed annual order, and two are still testing. It also says the founder will transfer three patents by the end of the next quarter.

The correct output should:

- update revenue with the new supplied evidence while preserving the prior estimate;
- split customers into paid pilot, signed order, and testing rather than retaining “five customers” as one status;
- record the financial spreadsheet as `user_provided` and not as audited verification;
- keep patent transfer as a commitment until a transfer document is received and reviewed;
- downgrade or qualify the commercial-traction conclusion;
- add a cash-runway request if the spreadsheet does not contain cash balance and monthly burn;
- show the changed conclusions in the change log and regenerate the report.

## Round 3: Conflict

The agent later finds a customer announcement describing the company as a “technology partner” but not naming a purchase. The project team says it is a paid deployment.

The correct output should retain both sources, mark the commercial status as conflicting or supported-but-not-fully-verified, and request an order, invoice, acceptance record, or other appropriate evidence. It must not silently convert the announcement into proof or treat the team statement as independent verification.
