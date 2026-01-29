# 🧠 Product Owner – Customer Data Platform (CDP) Assessment

This repository contains my structured responses to the **Product Owner – Customer Data Platform** assessment.

The goal of this document is to clearly demonstrate my **decision-making process**, **trade-off analysis**, and **product thinking** in a complex B2B SaaS environment — not only the final answers.

---

## 📌 Context

This assessment simulates a **Product Owner role in a fast-growing B2B SaaS Customer Data Platform (CDP)**.

**Operating context:**
- Cross-functional squad: **2 Backend Engineers, 1 Frontend Engineer**
- Sprint cadence: **2-week sprints**
- Average team velocity: **25 Story Points per sprint**

**Platform overview:**
- Ingests high-volume behavioral events (page views, purchases, clicks)
- Performs **identity resolution** to build unified customer profiles
- Enables marketers to create **audience segments** for activation across ad platforms, CRMs, and email providers

Throughout this document, I focus on **maximizing business value while managing technical risk**, aligning stakeholders, and ensuring sustainable delivery.

---

# 🚀 Assignment 1 – Sprint Planning & Prioritization

## 🎯 Sprint Commitment

**Sprint Capacity:** 25 Story Points  
**Committed Work:** 20 Story Points *(intentional buffer included)*

---

### ✅ Selected for this Sprint

| Priority | Item | Story Points | Why it Matters |
|---------|------|--------------|----------------|
| 1️⃣ | **Critical Bug: Audience Segment timeout (>1M events)** | 8 | Core CDP functionality; impacts enterprise customers and platform trust |
| 2️⃣ | **Sales Blocker: CSV Export for Audience List** | 5 | Unblocks a confirmed **$50k deal** in the current week |
| 3️⃣ | **Tech Debt: Database Driver Upgrade (Security)** | 3 | Urgent InfoSec flag; security risks are non-negotiable |
| 4️⃣ | **Analytics: Track “Create Segment” button usage** | 2 | Enables data-driven decisions for future prioritization |
| 5️⃣ | **Bug: Typos in Help Documentation** | 2 | Low effort; improves customer-facing quality |

**Total committed:** **20 / 25 Story Points**  
🧠 *Intentional buffer: 5 points reserved to absorb unforeseen issues or critical spillover.*

---

### ⛔ Explicitly Excluded from this Sprint

- **AI Audience Suggestions (CEO priority – 13 pts)**  
- **Meta Ads Integration (Top 3 customer request – 8 pts)**  
- **UX Polish: Dark Mode (5 pts)**  

These items remain high priority in the backlog and will be reassessed for the next sprint.

---

## 🧩 Rationale

### ⚖️ CEO AI Feature vs. Critical Bug

While the **AI Audience Suggestions** feature has high visibility and was promised to the board, it depends directly on **accurate, scalable segmentation** and a stable data foundation.

Given that:
- Segment calculation currently fails at scale (>1M events)
- AI features amplify data quality issues rather than fix them

I intentionally prioritized stabilizing core CDP functionality first.

During this sprint, I would work with stakeholders to:
- Validate the expected impact of the AI feature  
- Define a clear, demoable **MVP scope**  
- Align expectations on what can realistically be delivered next sprint  

This approach reduces delivery and reputational risk, increasing the likelihood of a **credible and successful board-facing outcome**.

---

### 💰 Sales Blocker

The CSV Export feature directly unblocks a **confirmed $50k deal** closing within days.  
With relatively low effort and immediate revenue impact, it was a clear inclusion and reinforces trust between Product, Sales, and Leadership.

---

### 🔐 Tech Debt & 📊 Analytics

Security-related tech debt flagged by InfoSec represents **systemic and legal risk** and should not be postponed.

Additionally, adding lightweight analytics to the “Create Segment” button enables:
- Better understanding of real user behavior  
- Data-informed prioritization of future segmentation features (e.g. Meta Ads)  
- A more evidence-driven product roadmap  

---

## ⚠️ Risk Assessment

### 🚨 Biggest Risk

The main risk is **stakeholder frustration**, particularly from leadership, due to the AI feature not being delivered in this sprint despite its board-level visibility.

---

### 🛠️ Mitigation Strategy

To mitigate this risk, I would:
- Clearly communicate that the feature is **postponed, not deprioritized**  
- Share progress on MVP definition, assumptions, and data readiness  
- Commit to structuring the following sprint to deliver a stable, demo-ready version  

This balances **short-term expectations** with **long-term product credibility, quality, and team sustainability**.

---

## Assignment 2 – Backlog Refinement & User Stories
...

---

## Assignment 3 – Identity Resolution
...

---

## Assignment 4 – Stakeholder Conflict & Process Design
...

---

## Assignment 5 – CDP Fundamentals
...

---

## Tools Used
- ChatGPT (for structuring and clarity)
- Personal experience in CDP and B2B SaaS products
