<h3 align="center">Vraj Patel</h3>

<p align="center"><b>I make data boring.</b></p>

<p align="center">
  <a href="https://vrajdataverse.vercel.app/">Site</a> &nbsp;&middot;&nbsp;
  <a href="https://www.linkedin.com/in/vrajpatel19061/">LinkedIn</a> &nbsp;&middot;&nbsp;
  <a href="mailto:vrajpatel19061@gmail.com">Email</a>
</p>

---

Boring is the goal. Boring means the numbers agree, the 6am refresh already happened, and nobody is on a call arguing about which dashboard is right.

Most of my work starts the same way: data in six places, a report that's wrong, and a deadline. 3.5+ years of building the thing that turns that into one place, correct, and quiet.

I do it from both sides. I work at a product company, on a platform that has to keep running long after I've stopped thinking about it, and I run delivery for service-based clients alongside it. Product work punishes shortcuts, because you are the one who gets paged. Client work punishes rigidity, because the next stack is never the last one. I like having both hands on the wheel.

Right now I'm deep in two things: retrieval systems that answer questions from messy internal documents, and workflow automation that removes the human from the parts of a process that never needed one.

| 10M+ | 10B+ | 50% | 30% |
|:---:|:---:|:---:|:---:|
| records landed daily | records governed | extraction cost cut | faster refresh |

---

## What I actually build

Six of them. Stack up front, then the part that was actually hard, because that's the only part worth reading.

### 01 &nbsp;Multi-tenant e-commerce data and AI platform

`Magento + BigQuery GA4 + Klaviyo → EKS extractors → Glue → 4-layer S3 medallion · Step Functions · Lambda control planes · Terraform + CloudFormation nested stacks`

Onboarding a new retail tenant used to be a project measured in months. Now it's one repeatable deploy: a config file, a pipeline run, and a tenant that exists end to end. I lead three engineers on it, and it feeds 5+ ML workflows including a recommendation engine.

> **The hard part.** Isolation without a fork per customer. Every tenant gets its own S3 buckets, Glue databases, IAM boundaries, KMS keys and Secrets Manager entries, all templated, so the blast radius of one tenant's data is exactly that tenant and nothing else. The version of this that works is the one where adding customer number two changes zero lines of shared code.

### 02 &nbsp;RAG-powered policy assistant

`Python · FastAPI · Gemini 2.5 Flash · text-embedding-004 · Pinecone · Supabase · GCP`

An internal assistant that answers questions from policy documents instead of routing every quick doubt to a person. Ingestion takes PDF and DOCX, splits them into overlapping chunks, embeds them, and pulls the 30 closest matches per question.

> **The hard part.** Every interesting constraint was a negative one. Answers stay inside retrieved context. Conflicting policies resolve to the newest document version. The assistant says it doesn't know rather than inventing a policy. A confident wrong answer about leave entitlement is worse than no answer at all, so most of the work went into making the system comfortable saying nothing.

### 03 &nbsp;Marketing analytics pipeline

`Google Ads + Facebook Ads + Bing Ads + Adobe Analytics → Supermetrics → Airflow → Snowflake → dbt · GitLab CI/CD`

Paid-media reporting across four ad platforms, run as Phase 1 lead over a three-person team. **10M+ records land per day.** The governed Snowflake and dbt models on top cover **10B+ records** and power **20+ business dashboards**.

> **The hard part.** Not the volume. The release process. Promoting changes through dev, UAT and production on CI/CD is what stopped deploys being an event people scheduled their week around, and it's the reason four platforms' worth of metric definitions still agree with each other a year later.

### 04 &nbsp;Multi-source extraction platform

`HubSpot + Stripe + DynamoDB + Adyen → Python/PySpark → Databricks → dbt Kimball models`

Four source systems into analytics-ready dimensional models. Mine, solo, start to finish. Parallelizing extraction cut execution cost by **50%** and made downstream dbt models refresh **30% faster**. It replaced work previously split across a two-engineer delivery team.

### 05 &nbsp;Multi-agent storefront assistant

`Multi-agent LLM orchestration · NLP catalog search · order-tracking APIs`

Three cooperating agents behind one chat box: storefront FAQs, search across the product catalog, live order tracking.

> **The hard part.** Routing is the whole problem. "Where's my order" and "do you have this in blue" look almost identical and need completely different tools, so intent has to be settled before retrieval, not after.

### 06 &nbsp;Sales and marketing workflow automation

`n8n · REST APIs · Webhooks · CRM integrations`

Manual CRM handoffs, replaced with event-driven workflows that move lead and customer data between systems on their own. Third-party APIs are where automation goes to die, so the real work was safe retries, duplicate prevention, rate-limit handling, and loud failure paths for the cases where a human genuinely does need to look.

---

## How I work

- **Idempotent by default.** A pipeline you can't safely re-run is a pipeline you will be awake for.
- **Loud failures over quiet ones.** Silence is the most expensive log level.
- **Verified, not assumed.** "It should work" is not a status.

---

## Stack

**Where I'd stake a claim.** AWS, Databricks, Snowflake and GCP, with dbt, Python/PySpark, Airflow and Terraform running through all four. Medallion and Kimball modelling, plus the operational half that keeps them honest: idempotent loads, tests before deploy, CI/CD promotion, rollback you've actually rehearsed.

**Exposure, not depth.** Azure. ADF, ADLS, Synapse, Functions. I've shipped on it, I wouldn't call myself deep, and I'd rather tell you that than pad the list.

<details>
<summary><b>The full inventory</b></summary>

<br>

| | |
|---|---|
| **Data platforms** | Databricks, Snowflake, BigQuery, Amazon S3 |
| **Transformation and modelling** | dbt, dbt Semantic Layer, SQL, Python, PySpark, Spark, Kimball modelling, medallion architecture |
| **AWS** | S3, Lambda, Glue, Step Functions, EventBridge, Athena, DynamoDB, EKS, EMR, Kinesis, CloudFormation, IAM, KMS, Secrets Manager, SNS, SQS, CloudWatch, VPC |
| **GCP** | BigQuery, Cloud Run, Cloud Storage, Artifact Registry, Workflows, Data Fusion, Cloud Scheduler, Dataform |
| **Azure** | ADF, ADLS, Synapse, Azure Functions |
| **Orchestration and automation** | Airflow, AWS Step Functions, EventBridge Scheduler, n8n, Supermetrics, Fivetran, Airbyte |
| **IaC, containers and CI/CD** | Terraform, CloudFormation, Docker, Kubernetes (EKS), Git, GitLab CI/CD, GitHub Actions |
| **AI and retrieval** | Gemini APIs, Pinecone, LangChain, FAISS, embeddings, RAG, multi-agent LLM systems |
| **Reporting** | Power BI, Looker Studio, Hashboard |

</details>

<sub>Databricks Certified Data Engineer Associate.</sub>

---

If you're untangling a pipeline nobody trusts, or wondering whether RAG actually helps with your documents, the inbox is open.

**[vrajdataverse.vercel.app](https://vrajdataverse.vercel.app/)** &nbsp;&middot;&nbsp; **[LinkedIn](https://www.linkedin.com/in/vrajpatel19061/)** &nbsp;&middot;&nbsp; **[vrajpatel19061@gmail.com](mailto:vrajpatel19061@gmail.com)**
