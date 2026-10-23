---
framework_version: 1.0.0
---

# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

<!-- These are populated by /setup from your actual experience. Below are templates showing the format. -->

<!-- Built from the portfolio repos' interview notes. Full detail lives in each repo's docs/CHALLENGES_AND_BUGS.md. -->

### 1. Barsha (data quality, reading data before trusting it)
**S:** Nepal's public NOAA rainfall record has 4,599 days of 0.00 that actually mean "not reported", and missing days cluster on rainy days.
**T:** Build a lakehouse whose seasonal totals people can trust.
**A:** Read the source flags before the values, quarantined bad files behind a quality gate, published totals only at 90% completeness, validated outlier rules against real floods (the 2014 Surkhet flood was being flagged as a sensor error; neighbour corroboration fixed it), and added freshness alarms that treat a missing metric as breaching.
**R:** Clean Athena tables for 50 years at ~$1.20/month; the freshness alarm caught a feed that had silently stopped in August 2025 while every run said OK.
**Use for:** "Tell me about a data quality problem", "A time you found a hidden bug"

### 2. Bijuli (MLOps, safe model rollout)
**S:** A day-ahead demand forecast for Nepal's grid drives power purchases, and the grid keeps changing.
**T:** Keep the model right for years, not just score well once.
**A:** Replayed 26 months of operations with injected faults under six retraining policies; built a gated rollout with shadow mode and automatic rollback. Was upfront that hourly load is simulated by a grid twin calibrated to NEA tables.
**R:** Auto-deploying monthly retrains left a bad model in charge for 28 days; the gated rollout kept it to 0-5. Hourly error 3.3% vs 4.7% naive. Learned that two of three planted bugs did not fail the tests, so tests must be checked for failing.
**Use for:** "How do you deploy and monitor models", "A time your own process failed"

### 3. Sodhnus (LLM reliability on Amazon Bedrock)
**S:** After storms, people ask how much rain fell; a chatbot will invent a number in either language.
**T:** Build a Nepali/English assistant that cannot state an unverified number.
**A:** Chose tools over RAG or text-to-SQL (a missing day reads 0.00 and would be averaged in); the model gets facts only through five read-only tools, and a checker verifies every number against tool outputs. Improved the checker from 0/35 to 34/35 on swapped numbers by requiring one figure per tool result; measured that a Guardrail cost eight times the model.
**R:** In a 350-case adversarial test the checker stops 97% of wrong answers and never rejects a correct template answer; ~$8.60/month at 10,000 questions.
**Use for:** "How do you prevent hallucinations", "A design trade-off you made"

### 4. Chowk (questioning an off-the-shelf model)
**S:** Kathmandu traffic is mostly motorcycles; congestion is measured in Passenger Car Units.
**T:** Count traffic by vehicle type accurately on an edge camera.
**A:** Found COCO YOLOX called 65% of cars and 81% of microbuses "truck/bus" (+55% PCU bias) and only looked fine because two errors cancelled; added a small classifier on detector features; recovered 31 recording sessions from file timestamps for a grouped split.
**R:** 1.3% PCU error per session on held-out data; serverless backend for 20 junctions at ~$5.70/month.
**Use for:** "Tell me about evaluating a model", "A time a metric was misleading"

### 5. Surakshit (cloud architecture for scale)
**S:** After the 2015 Gorkha earthquake, families could not reach each other.
**T:** Design an "I'm safe" check-in service that never loses an accepted check-in.
**A:** Storage-first API Gateway -> SQS -> DynamoDB with multi-region warm standby; simulated six designs against documented AWS limits; backtested the activation rule on 88 USGS quakes.
**R:** Naive design loses 45% of check-ins at 15 million in ten minutes; this one loses none, at ~$12/month idle. Retries with jitter alone saved nothing; the queue did.
**Use for:** "Design a system for a traffic spike", "System design interview"

### 6. TekBay Digital (infrastructure on the job)
**S:** Client AWS environments were provisioned by hand.
**T:** As Cloud Architect, deploy and maintain infrastructure and support migrations.
**A:** Codified EC2, VPC, S3 and RDS in Terraform, enforced least-privilege IAM and security groups, monitored with CloudWatch and wrote runbooks.
**R:** Manual provisioning time down 40%; contributed to Well-Architected-aligned migrations.
**Use for:** "Tell me about your work experience", "Working with a team/clients"

<!-- Add more STAR examples as needed. Aim for 4-6 covering different competencies. -->

## Common Tough Questions

### "Why did you leave TekBay Digital?"
> [CONFIRM THE FACTS] Draft: "It was a fixed-term role from April to June 2026. I used the time since to build ML and data systems on AWS, which is the direction I want to grow in."

### "You don't have much production experience." / "You don't have [PyTorch/Kubernetes]."
> Acknowledge it plainly. Bridge: each portfolio project is built like a production system, with costs, failure modes, alarms and bug write-ups, and Bijuli/Pahiro replay real faults. Show the learning plan and how fast the AWS certifications came.

### "Where do you see yourself in 5 years?"
> A senior ML engineer who owns production ML systems end to end, from data quality through deployment and monitoring, having finished the BSc in Computer Science with AI.

### "What's your biggest weakness?"
> [CONFIRM] Suggested: most of my work so far is solo, so I have had less code review from senior engineers than I want. I compensate by writing design decisions and bug write-ups for every project, and I'm looking for a team where reviews are the norm.

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
