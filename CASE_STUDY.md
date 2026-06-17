# Case Study — InsureAllBI Insurance Analytics Lakehouse

*Ready-to-paste content for your portfolio site, Notion, or LinkedIn Featured section.*

---

## Headline
**InsureAllBI — Insurance Analytics Lakehouse on Databricks**

## One-liner
Built an end-to-end **Medallion (Bronze → Silver → Gold)** data pipeline that ingests eight REST API datasets into a governed Databricks lakehouse and surfaces executive KPIs — customer lifetime value, policy profitability, claims/fraud trends, and business health.

## Role & Stack
**Role:** Data Engineer (end-to-end design & build)
**Stack:** Databricks · PySpark · Spark SQL · Delta Lake · Unity Catalog · REST API integration

---

## The Problem
An insurer's data was locked behind paginated REST APIs with no analytical foundation — no clean models, no governance, and no curated metrics for decision-making.

## The Solution
A layered lakehouse following the medallion pattern:

- **Bronze** — Resilient REST ingestion (pagination, Basic Auth, rate-limit retry/backoff) landing eight datasets as Delta tables, with schema enforced from a centralized registry and every run logged for observability.
- **Silver** — A Kimball-style star schema (customer, policy, agent, country dimensions + claims/payments facts) using MD5 surrogate keys, derived business attributes (age, tenure, risk, region), and idempotent Delta `MERGE` loads.
- **Gold** — Nine curated analytics tables answering concrete business questions, governed end-to-end by Unity Catalog.

## Highlights
- **Reusable engine:** a single utilities module powers all three layers — ingestion, cleansing, schema enforcement, MERGE upserts, and logging.
- **Idempotent incremental loads:** dynamic Delta `MERGE` generated from the DataFrame schema; safe to re-run.
- **Governance by design:** Unity Catalog three-level namespace across `bronze / silver / gold / logs`.
- **Business-ready KPIs:** loss ratio, customer acquisition cost, retention, fraud detection rate, and MoM/YoY growth.

## Impact
Delivered a 360° customer view, real-time profitability tracking, and fraud-detection signals on query-ready Gold tables — turning raw API data into decision-grade analytics.

## Links
- **Code:** https://github.com/your-handle/insureallbi-databricks-pipeline
- **Architecture diagram:** included in the repository (`docs/architecture.svg`)

---

### Short version (for LinkedIn / résumé summary)
> Designed and built an end-to-end Medallion lakehouse on Databricks: REST API ingestion → Bronze → Silver star schema → Gold analytics, using PySpark, Delta Lake, and Unity Catalog. Implemented resilient paginated ingestion, a centralized schema registry, idempotent MERGE loads, and curated KPI tables (CLV, profitability, fraud, loss ratio).
