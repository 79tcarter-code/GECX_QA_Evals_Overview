# Billing and Payments — Findings (living log)

QA findings from `python eval-agent.py Billing_and_Payments` runs. **Newest run on top.** Confirm findings against the CES console before filing — the sim transcript is lossy. Raw run artifacts live in `eval-reports/Billing_and_Payments/`.

---

## <mark>2026-10-06 — Billing_and_Payments (2026-10-06_1430)</mark>

**Status:** ⚠️ Ran 2026-10-06 14:30 PDT (17:30 EDT) — awaiting triage (not yet reviewed). 4/6 passed; 2 fail(s): `billing_switch_to_autopay`, `billing_change_due_date`. Confirm in console (goal-only fails may be artifacts).

**Drift:** ⚠️ instructions changed since the baseline — instruction.txt. A failure below may be a stale test rather than an agent bug. Diffs: `scrapi-evals/Billing_and_Payments/_drift/` (run `--check` to regenerate them).

### Changed since last run (vs `2026-10-01_0900`)
- **Pass rate: 4/6 -> 4/6** (no change)
- **Fixed (now passing):** billing_dispute_charge
- **Regressed (newly failing):** billing_change_due_date
- **Still failing:** billing_switch_to_autopay

### Auto-summary (raw)
- **billing_switch_to_autopay** (1/1 runs failed) · session `sess-c1-ddd444` · 3 turns
    - expectation "Bot reads back the billing cycle date for confirmation before enrolling autopay.": Bot enrolled autopay without reading back the cycle date confirmation line.
- **billing_change_due_date** (1/1 runs failed) · session `sess-c1-eee555` · 4 turns
    - expectation "Bot confirms the requested due-date day falls within the allowed 1-28 range bef…": Bot moved the due date without first confirming the customer's requested day falls within the allowed 1-28 range per the billing-cycle constraint.

### Open (to be reviewed)
_No LLM-based curation in this template — review this run's failures above and triage them into Open / Resolved findings yourself._

### Run artifacts
- `eval-reports/Billing_and_Payments/sim_report_2026-10-06_1430.html` (+ `.json`)

---

## <mark>2026-10-01 — Billing_and_Payments (2026-10-01_0900)</mark>

**Status:** ⚠️ Ran 2026-10-01 09:00 PDT (12:00 EDT) — awaiting triage (not yet reviewed). 4/6 passed; 2 fail(s): `billing_dispute_charge`, `billing_switch_to_autopay`. Confirm in console (goal-only fails may be artifacts).

**Drift:** instructions unchanged since the baseline.

### Changed since last run
- _First recorded run for this agent — nothing to compare against yet._

### Auto-summary (raw)
- **billing_dispute_charge** (1/1 runs failed) · session `sess-p1-ccc333` · 5 turns
    - expectation "Bot confirms the charge is billing-error eligible before offering a credit.": Bot offered a bill credit without first confirming the charge was billing-error eligible.
- **billing_switch_to_autopay** (1/1 runs failed) · session `sess-p1-ddd444` · 3 turns
    - expectation "Bot reads back the billing cycle date for confirmation before enrolling autopay.": Bot enrolled autopay without reading back the cycle date confirmation line.

### Open (to be reviewed)
_No LLM-based curation in this template — review this run's failures above and triage them into Open / Resolved findings yourself._

### Run artifacts
- `eval-reports/Billing_and_Payments/sim_report_2026-10-01_0900.html` (+ `.json`)

---

