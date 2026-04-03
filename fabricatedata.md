## MASTER INSTRUCTION (TO BE ADDED AT THE BEGINING OF EVERY DATASET FABRICATION PROMPT)

Generate realistic synthetic enterprise finance data for a fictional Indian manufacturing/distribution company for a working capital optimization AI demo.

The data should support CFO-level decision-making across:
- receivables
- payables
- inventory
- billing acceleration
- contract optimization
- financing decisions
- operational inefficiencies
- strategic constraints

Important:
- Include ambiguity, trade-offs, and real-world complexity
- Some opportunities should look obvious but should NOT be recommended due to risk or context
- Ensure all IDs (customer_id, vendor_id, material_id, sales_order_id) are consistent across datasets
- Use realistic INR values
- Output clean CSV format only


## AR OPEN ITEMS

Generate a CSV dataset named ar_open_items.

Columns:
customer_id, customer_name, invoice_id, invoice_date, due_date, invoice_amount, outstanding_amount, aging_days, aging_bucket, dispute_flag, dispute_reason, promise_to_pay_date, last_payment_date, avg_days_to_pay, credit_limit, credit_utilization, strategic_flag, account_owner, region

Constraints:
- 60 rows
- 20–30% overdue invoices
- 10–15% disputed invoices
- At least 3 strategic customers
- At least 2 invoices above INR 50 lakh
- At least 1 large overdue invoice under dispute
- At least 1 strategic customer overdue but should not be aggressively collected
- Mix of regions and account owners
- Output only CSV


## AP OPEN ITEMS

Generate a CSV dataset named ap_open_items.

Columns:
vendor_id, vendor_name, invoice_id, invoice_date, due_date, invoice_amount, outstanding_amount, payment_terms_days, early_payment_discount_flag, discount_percent, supplier_criticality, sole_supplier_flag, penalty_clause_flag, category, procurement_owner, last_payment_days, contract_flag

Constraints:
- 50 rows
- At least 5 high criticality vendors
- At least 3 low criticality vendors
- At least 2 sole-source vendors
- At least 2 vendors with penalty clauses
- Include vendors where delaying payment is safe
- Include vendors where delaying payment is risky
- Realistic INR values
- Output only CSV


## INVENTORY SNAPSHOT

Generate a CSV dataset named inventory_snapshot.

Columns:
material_id, material_desc, plant, on_hand_qty, inventory_value, unit_cost, days_in_inventory, inventory_turns, slow_moving_flag, obsolete_flag, blocked_stock_flag, open_sales_order_qty, forecast_demand_30d, forecast_demand_60d, safety_stock, business_criticality, liquidation_possible_flag

Constraints:
- 40 rows
- At least 6 slow-moving items
- At least 3 obsolete items
- At least 2 blocked stock items
- At least 4 high-value low-demand items
- At least 3 business-critical items that should NOT be liquidated
- Output only CSV


## SALES ORDERS (UNBILLED)

Generate a CSV dataset named sales_orders_unbilled.

Columns:
sales_order_id, customer_id, order_value, order_date, delivery_date, billing_status, unbilled_amount, milestone_billing_flag, advance_payment_flag, advance_payment_received, contract_type, renewal_date, commercial_owner, shipment_block_flag, pricing_dispute_flag

Constraints:
- 20 rows
- At least 5 billing-ready but unbilled orders
- At least 3 milestone billing opportunities
- At least 2 advance payment opportunities
- At least 2 pricing dispute cases
- At least 1 shipment block
- Output only CSV


## CUSTOMER MASTER

Generate a CSV dataset named customer_master.

Columns:
customer_id, customer_name, segment, region, strategic_flag, credit_rating, account_manager, payment_behavior_score

Constraints:
- 25 customers
- At least 5 strategic customers
- Mix of segments (retail, enterprise, distributor)
- payment_behavior_score between 1 and 100
- Output only CSV


## VENDOR MASTER

Generate a CSV dataset named vendor_master.

Columns:
vendor_id, vendor_name, category, supplier_criticality, alternate_supplier_flag, penalty_clause_flag, buyer_owner

Constraints:
- 20 vendors
- Mix of HIGH, MEDIUM, LOW criticality
- At least 3 vendors without alternate suppliers
- Output only CSV


## WORKING CAPITAL TARGETS & POLICIES

Generate a CSV dataset named wc_targets_and_policies.

Columns:
date, working_capital_target, cash_release_target_30d, cash_release_target_60d, min_cash_buffer, max_supplier_stretch_days, finance_cost_percent, factoring_cost_percent, inventory_liquidation_limit

Constraints:
- Single row is enough
- Use realistic INR targets (e.g., 10–50 Cr)
- Include reasonable percentages (5–18%)
- Output only CSV


## BUSINESS CONTEXT NOTES

Generate a CSV dataset named business_context_notes.

Columns:
entity_type, entity_id, context_type, context_note, severity, owner, expiry_date

Constraints:
- 15 rows
- Cover CUSTOMER, VENDOR, MATERIAL, ORDER
- Include:
  - strategic renewal in progress
  - disputes
  - negotiations
  - supplier risk
  - operational issues
- Short realistic business notes
- Output only CSV


## CUSTOMER PAYMENT HISTORY

Generate a CSV dataset named customer_payment_history.

Columns:
customer_id, month, total_invoiced, total_collected, avg_days_to_pay, late_payment_count, dispute_count, promise_to_pay_kept_rate

Constraints:
- Last 6 months
- One row per customer per month
- Values should align with AR behavior
- Output only CSV


## VENDOR PAYMENT HISTORY

Generate a CSV dataset named vendor_payment_history.

Columns:
vendor_id, month, total_billed, total_paid, avg_days_to_pay, discounts_taken, late_payment_penalties

Constraints:
- Last 6 months
- Reflect realistic payment behavior
- Output only CSV


## INVENTORY MOVEMENT HISTORY

Generate a CSV dataset named inventory_movement_history.

Columns:
material_id, month, opening_qty, receipts_qty, issues_qty, closing_qty, inventory_value, days_in_inventory

Constraints:
- Last 6 months
- Reflect slow-moving vs fast-moving patterns
- Output only CSV


## CONTRACTS SUMMARY (IMPORTANT)

Generate a CSV dataset named contracts_summary.

Columns:
contract_id, entity_type, entity_id, contract_value, payment_terms, billing_type, advance_payment_percent, credit_period_days, penalty_clause_flag, early_payment_discount_flag, renewal_date, renegotiation_possible_flag, contract_owner

Constraints:
- 20 contracts
- Mix of CUSTOMER and VENDOR contracts
- Include milestone, subscription, and delivery-based billing
- Include renegotiation opportunities
- Output only CSV


## FINANCING OPTIONS (IMPORTANT)

Generate a CSV dataset named financing_options.

Columns:
option_id, type, applicable_entity, entity_id, eligible_amount, cost_percent, approval_required_flag, processing_time_days, risk_level

Constraints:
- Include FACTORING, SUPPLY_CHAIN_FINANCE, CREDIT_LINE
- At least 10 rows
- Different cost levels (2%–15%)
- Mix of low and high risk options
- Output only CSV


## PROCESS EXCEPTIONS

Generate a CSV dataset named process_exceptions.

Columns:
process_type, entity_id, issue_type, delay_days, impact_amount, owner, status

Constraints:
- 10–15 rows
- Include:
  - billing delays
  - approval bottlenecks
  - invoice mismatches
  - shipment delays
- Output only CSV


## FINAL RULE (TO BE APPENDED AT THE END OF EVERY DATASET FABRICATION PROMPT)

Do not generate perfect or clean data.
Include realistic inconsistencies, edge cases, and conflicting signals so that an AI system must make trade-off decisions instead of simple arithmetic conclusions.
