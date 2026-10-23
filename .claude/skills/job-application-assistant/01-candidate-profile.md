---
framework_version: 1.1.1
---

# Candidate Profile

<!-- Populated from Bikash_Kushwaha_CV.pdf, the LinkedIn profile notes and the portfolio repos' interview notes (October 2026). -->

## Identity
- **Name:** Bikash Kushwaha
- **Location:** Kathmandu, Nepal
- **Phone:** +977 9761158845
- **Email:** kushwahabikash9580@gmail.com
- **LinkedIn:** https://linkedin.com/in/bikash9cmd
- **GitHub:** https://github.com/bikash9cmd
- **Status:** Part-time BSc (Hons) Computer Science with AI student (Birmingham City University, distance, to Dec 2028). Cloud Architect contract at TekBay Digital ended June 2026. Available now for full-time or contract work.
- **Constraints:** Based in Kathmandu. Open to remote roles worldwide, on-site/hybrid in Kathmandu Valley, and relocation for the right role. Degree is studied alongside work.

### Languages

| Language | Level | Notes |
|----------|-------|-------|
| Nepali | Native | Builds bilingual Nepali/English products |
| English | Professional working proficiency (C1) | English Proficiency Certificate; all study and work in English. Confirm level. |

## Education

| Degree | Period | Institution | Key Topics |
|--------|--------|-------------|------------|
| BSc (Hons) Computer Science with Artificial Intelligence | Nov 2024 - Dec 2028 (expected) | Birmingham City University (distance, via Sunway College Kathmandu) | Cloud Computing, Machine Learning Operations (MLOps), Data Management, Software Engineering |
| Higher National Diploma, Computer Science | Aug 2021 - Jul 2023 | National Infotech Higher Secondary School, Kathmandu | Computer science fundamentals |
| Secondary Education Examination (SEE) | 2012 - 2021 | Galaxy Public School, Nepal | |

### Certifications
- AWS Certified Machine Learning Engineer - Associate
- AWS Certified Data Engineer - Associate
- AWS Certified Solutions Architect - Associate (SAA-C03)
- AWS Certified AI Practitioner
- AWS Certified Cloud Practitioner
- AWS Academy Graduate - Cloud Architecting
- English Proficiency Certificate; SAT (list only if an application asks)

## Professional Experience

### Cloud Architect - TekBay Digital (Apr 2026 - Jun 2026)
Kathmandu, Nepal
- Deployed and maintained AWS infrastructure (EC2, VPC, S3, RDS) with Terraform IaC, reducing manual provisioning time by 40%.
- Supported cloud migration projects: workload assessment, architecture design and implementation aligned with the AWS Well-Architected Framework.
- Monitored systems with CloudWatch; troubleshot networking faults, IAM misconfigurations and service outages.
- Configured IAM roles, security groups and VPC rules for least-privilege access; contributed to operational runbooks and technical documentation.

### Data Analyst - DataCamp (Oct 2024 - Dec 2024)
Remote
- Automated data analysis workflows in Python (Pandas, NumPy), reducing data errors by 30%; used Git for version control and collaboration.
- Delivered technical reports with Matplotlib and Seaborn visualisations; documented analytical procedures for team knowledge sharing.

## Independent Projects
<!-- Portfolio of open-source AWS projects on Nepal's data. Each repo documents design decisions (ADRs), costs, failure modes and a CHALLENGES_AND_BUGS.md. Unless stated, stacks are designed and tested locally/in replay, not deployed to a live AWS account, and costs are estimates. Say "designed", not "runs in production". -->

**ML / forecasting**
- **Hawa** (github.com/bikash9cmd/hawa-kathmandu-air): hour-by-hour next-day PM2.5 forecasts for Kathmandu from Department of Environment sensor data, alerts in English and Nepali. Tree model predicting the log-ratio to a statistical anchor (fixes failure to extrapolate in the monsoon). Month-by-month backtest: 15% lower error than the best naive forecast, 40% fewer missed bad-air days than persistence. Sensor-outage fallback measured. Serverless AWS design, ~$2.60/month.
- **Bijuli**: day-ahead hourly electricity demand forecast for Nepal's grid (NEA bids on India's day-ahead market). Replayed 26 months of operations with injected faults under six retraining policies; gated rollout with shadow mode and automatic rollback cut bad-model days from 28 to 0-5. Hourly error 3.3% vs 4.7% for best naive rule. Hourly load is simulated by a grid twin calibrated to NEA FY 2081/82 tables (2.8% energy error vs 40 real daily reports); weather is real NOAA data. ~$1.63/month serverless design.
- **Pahiro**: landslide early warning for 400 zones in the central Nepal hills from terrain, satellite rain and GFS forecasts, SMS on level rises. Hand-mapped 2,260 landslide scars from Sentinel-2. Replaying the Sept 2024 storm, 30 of 62 storm zones were orange/red the morning before; caught dated failures 10x more often than chance. Spatial block CV reversed the random-CV conclusion. Labels noisy, not deployed. ~$14/month design.
- **Chowk**: traffic counting by vehicle type on an edge camera box, 15-minute Passenger Car Unit flows to AWS IoT Core and Lambda. Off-the-shelf COCO YOLOX overstated PCU by ~55%; a small classifier on detector features brought error to 1.3% per session on held-out data, with session-grouped evaluation. ~$5.70/month for 20 junctions.

**Data engineering**
- **Barsha** (github.com/bikash9cmd/barsha-nepal-monsoon-lakehouse): serverless lakehouse ingesting 50 years of NOAA station rainfall for Nepal incrementally, quality gate that quarantines bad files, Athena tables and a next-morning bilingual extreme-rain bulletin. DuckDB in Lambda instead of Spark for 16 MB of data; freshness alarms caught a source that stopped silently. ~$1.20/month.
- **Fohor**: serverless lakehouse over Overture Maps and Meta population data from the AWS Open Data registry, reconciled with the 2021 census, publishing per-municipality waste tonnage, haul distances and a bilingual landfill-blockade report. Reads 0.18% of 119 GB. ~$1.14/month.
- **Bhuktani**: real-time payments lakehouse streaming QR payment events from 20 banks into Apache Iceberg (Kinesis, Lambda, exactly-once writes, per-bank watermarks, Debezium CDC as SCD2, write-audit-publish on Iceberg branches, Terraform). Raises refund alerts within ~3 minutes against NRB deadlines; on a simulated peak day caught all 218 stuck payments with zero false alerts vs ~160 for naive designs. Payments simulated and calibrated to NRB volumes. ~$126/month.

**LLM / GenAI on Amazon Bedrock**
- **Sodhnus** (github.com/bikash9cmd/sodhnus-nepal-rain-assistant): Nepali and English rainfall assistant on Amazon Bedrock that answers only through five read-only tools; every number is checked against tool results before display. 350-case adversarial test: checker stops 97% of wrong answers with no false rejections. ~$8.60/month at 10,000 questions.
- **Kagaj**: Nepali and English agent on Bedrock (Nova Lite, escalating to Nova Pro, then an offline agent) guiding citizens through government document chains. Seven tools, cited fee catalog, deterministic answer gate catching 406/406 corrupted answers, per-request/session/day budgets. ~$10.60/month at 10,000 questions.
- **Parkha**: Nepali and English pesticide-safety assistant on Bedrock for farmers; harvest dates computed in code from label waiting periods, Nepal's ban list overrides Indian labels, deterministic safety gate catching 290/290 mutated answers. RAG for prose, tables for numbers. ~$7/month.

**Cloud architecture / resilience**
- **Surakshit** (github.com/bikash9cmd/surakshit-nepal-quake-checkin): "I'm safe" earthquake check-in service (12 KB web page + SMS, Nepali/English) that activates from the USGS feed. Storage-first API Gateway -> SQS -> DynamoDB with multi-region warm standby. Simulated six designs against AWS limits: naive design loses 45% of check-ins at 15M in 10 minutes, this design loses none. ~$12/month idle.
- **Bato**: trekker safety system for Nepal's high passes: guides check in by SMS, a Step Functions escalation ladder handles overdue groups, and six-hourly NOAA GEFS forecasts put passes on storm hold (replay of 2014 Cyclone Hudhud flagged Thorong La). Sparse DynamoDB GSI deadline buckets, missing-metric alarms. ~$15/month at peak.
- **3-Tier Web App on AWS** (2026): ALB -> Auto Scaling EC2 -> RDS MySQL across 2 AZs in Terraform; VPC with public/private subnets, NAT, Route 53, ACM HTTPS, S3 + DynamoDB remote state.
- **AWS Cost Optimisation & Monitoring Dashboard** (2025): Lambda + CloudWatch + Cost Explorer with Slack alerts; Boto3 idle-resource detection; simulated 20% monthly cost reduction.

**Earlier projects (2025)**
- **MLOps pipeline, depression prediction** (BCU CMP5366): Docker Compose stack (Airflow, FastAPI, Redis, MariaDB) on Linux, Evidently AI drift monitoring, Prometheus and Grafana.
- **MLOps pipeline, bike demand forecasting**: Airflow, Docker, MLflow, Great Expectations, MariaDB + ColumnStore, FastAPI serving, drift-triggered retraining.
- **AI-Powered Diet Tracker & RAG Chatbot**: Django app with RAG chatbot generating meal plans, dashboards, REST APIs.
- **Workflow automation**: Make + Creatomate content pipeline and a booking backend over LinkedIn, WhatsApp and Gmail APIs.

## Technical Skills

### Programming & ML
- **Python** (strong): Pandas, NumPy, Scikit-learn, gradient-boosted trees, time-series forecasting, Matplotlib, Seaborn, FastAPI, Pydantic, Django, Boto3
- **SQL** (strong): Athena, DuckDB, MariaDB/MySQL; **Bash**, **YAML**, **HCL**
- MLOps: MLflow, Apache Airflow, Evidently AI, Great Expectations, model monitoring, shadow deployment and rollback, backtesting
- GenAI: Amazon Bedrock (Converse, tool use, Guardrails, Nova models), agent design, RAG, deterministic output validation, LLM evaluation with adversarial test sets
- Computer vision: YOLOX detection with a custom classifier head (Chowk)

### Domain Expertise
- Data quality and reliability engineering for messy public data (Nepal weather, air quality, census, maps)
- Forecasting and early-warning systems; disaster and public-safety services
- Bilingual (Nepali/English) products
- Cost-aware serverless design on AWS

### Software & Tools
- AWS: EC2, S3, VPC, RDS, Lambda, IAM, CloudWatch, Route 53, Auto Scaling, NAT Gateway, API Gateway, SQS, DynamoDB, Step Functions, Kinesis, Athena, IoT Core, Bedrock, SageMaker (studied for MLA cert)
- Terraform, Docker, Docker Compose, Git/GitHub, CI/CD, Apache Iceberg, Debezium, Prometheus, Grafana, Linux (Ubuntu, Amazon Linux), nginx, networking (TCP/IP, DNS, VPN)
- Not yet: PyTorch in real work, Kubernetes in production (do not claim)

## Publications
None.

## Awards
None listed.

## References
- Khusal Regmi, Director, Sunway College Kathmandu (affiliated with Birmingham City University) (khusal@sunway.edu.np)
- Rojan Sedhai, AWS Certified Cloud Trainer (rojan.sedhai@adex.ltd)

More references available upon request.
