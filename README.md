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

# 🧩 Assignment 2 – Backlog Refinement & User Story Writing

## Part A – Turning Ambiguity into Clarity

### 🎯 User Story

**As a** Marketing Manager  
**I want** to ingest purchase data from Shopify into the CDP  
**So that** I can create audience segments based on customers’ purchase behavior and run more targeted campaigns.

---

### ✅ Acceptance Criteria

1. The system ingests **purchase events** from Shopify, including customer ID, product, price, currency, and timestamp.
2. Purchase data is available for segmentation **within near real-time**; if real-time is not feasible, updates occur at least **3 times per day**.
3. In case of connection failures or sync interruptions, the system retries ingestion and guarantees **no data loss**.
4. Purchase events can be used as conditions in the Audience Builder (e.g. “users who purchased product X”).
5. Data consistency between Shopify and the CDP can be validated via logs or monitoring.

---

### 🚫 Out of Scope (V1)

- Generating insights or recommendations from purchase data  
- AI-based interpretation of purchase behavior  
- Advanced cross-analysis between purchase data and other event types

---

### 📋 Definition of Ready

- Shopify API access and permissions are approved  
- Event schema for purchase data is defined and reviewed  
- Error handling and retry strategy are agreed with engineering  
- Stakeholders have validated the scope and success criteria  
- Rollout strategy (progressive or limited availability) is defined  

---

## Part B – Vertical Slicing

### 🥇 Slice 1 – Single-Event Segmentation
Enable users to create an audience based on **a single event type** (e.g. “visited a product page”) within a 7-day window.

**User value:** Marketers can target recent high-intent visitors.

---

### 🥈 Slice 2 – Multi-Event Sequence (Basic)
Allow users to build an audience combining **two events** (e.g. “visited a product page AND added to cart”) within the same 7-day window.

**User value:** Marketers can focus on users with stronger purchase intent.

---

### 🥉 Slice 3 – Full Multi-Event Journey
Enable segmentation using **three events** (visited product page → added to cart → subscribed to newsletter) within a unified 7-day timeframe.

**User value:** Marketers can activate highly engaged users across multiple touchpoints.

---

# 🧬 Assignment 3 – CDP Logic & Identity Resolution

## 1️⃣ Identity Merge Logic (9:15 AM)

At **9:15 AM**, both the Laptop (cookieID: ABC-123) and the Phone (cookieID: XYZ-789) have been authenticated with the same identifier (**cristiano@gmail.com**).

At this point, I would **merge the two anonymous profiles into a single unified user profile**, using the authenticated identifier as the primary key.

However, this merge should be:
- **Logical, not destructive**  
- Fully **auditable and reversible**

All historical events remain linked to their original identifiers (cookieIDs), while the unified profile maintains a clear mapping between:
- cookieID → authenticated user
- event → original source

This avoids hard-coded data mutations and preserves a reliable audit trail.

---

## 2️⃣ Edge Case – Login Change on the Same Device (9:20 AM)

When the user logs out of **cristiano@gmail.com** on the Phone and logs back in as **messi@gmail.com**, the system should **not retroactively reassign past events**.

Specifically:
- Events from **9:05–9:15 AM** remain associated with the profile authenticated as **Cristiano**
- New events after **9:20 AM** are attributed to **Messi**

The phone’s cookieID continues to exist as a shared device identifier, but **identity ownership is determined by authentication state at the time of each event**.

This ensures historical accuracy and prevents unintended cross-user data leakage.

---

## 3️⃣ Product Decision Considerations

There is no single correct technical solution for this scenario. As a Product Owner, I would consider the following factors when defining product behavior:

- **Data Accuracy:** Events must reflect the user’s state at the moment they occurred.
- **Privacy & Compliance:** Prevent exposing one user’s behavior to another, especially in shared-device scenarios (GDPR, consent, and user trust).
- **Auditability:** Identity merges and splits must be traceable and reversible.
- **User Intent:** Logging in as a different user represents an explicit change in identity and should be respected.
- **Customer Expectations:** Marketers and analysts need predictable, explainable segmentation behavior.

Balancing these factors, I would intentionally favor a conservative identity resolution model that prioritizes data accuracy, user intent, privacy, and auditability over aggressive identity merging.
Even if this approach limits short-term attribution power or reduces audience size, it protects long-term customer trust, regulatory compliance, and the credibility of the CDP as a reliable source of truth.

---

# 🤝 Assignment 4 – Stakeholder Conflict & Process Design

## Part A – Retrospective Conflict

### 1️⃣ In-the-Moment Response

> “I hear your frustration, and I agree this is not sustainable.  
> Shipping half-baked ideas and rushing quality hurts both the team and the product.  
> This is not about blaming Sales, but about fixing a process gap that puts pressure on engineering.  
> I’ll take ownership of addressing this and making sure we have better alignment before commitments are made.”

This response validates the engineer’s concern, avoids blame, and clearly signals ownership and accountability.

---

### 2️⃣ Process Fix

I would introduce a **Sales–Product Discovery Alignment** ritual with the following structure:

- **Who:** Product Owner, Tech Lead, Sales representative, and Product leadership  
- **When:** Bi-weekly, ahead of sprint planning  
- **What:**  
  - Review upcoming sales requests and opportunities  
  - Translate them into **problems and expected business impact**, not features  
  - Identify risks, dependencies, and rough sizing signals  
- **Outcome:**  
  - A refined, prioritized intake of requests  
  - Clear guardrails on what can and cannot be committed externally  

This ensures Sales commitments are grounded in shared understanding and realistic delivery expectations.

---

## Part B – Competing Priorities

### 1️⃣ Message to Both Teams

> “Both stability and usability are critical to the success of the CDP.  
> Before making a decision, we need to understand the concrete business impact of each initiative, including revenue risk, customer experience, and long-term platform health.  
> I propose we align on data-driven criteria to decide sequencing, rather than debating features in isolation.”

---

### 2️⃣ Decision-Making Process

I would start by **quantifying impact** with both teams:
- Data Engineering: risk reduction, scalability, future cost of not migrating  
- Marketing: revenue impact, deal blockers, customer churn risk  

If trade-offs remain, I would **escalate with a clear recommendation**, prioritizing the **schema migration first**, while defining a narrow UX improvement scope to address the most critical Marketing pain points.

This approach balances long-term platform stability with short-term business needs, without blocking all progress.

---

### 3️⃣ Critical Soft Skill

The most critical soft skill in this situation is **structured communication under pressure**.

I would apply it by:
- Making trade-offs explicit  
- Clearly stating decision criteria  
- Communicating decisions early and transparently  
- Ensuring all teams understand not just *what* was decided, but *why*

This reduces rework, frustration, and misalignment over time.

---

# 📚 Assignment 5 – CDP Fundamentals

## 1️⃣ Event Types

### Track Event
A **track event** records a specific action a user performs, such as clicking a button, completing a purchase, or submitting a form.

**Example:**  
A `Purchase Completed` event fires when a user finishes a checkout.

---

### Identify Event
An **identify event** connects an anonymous user or device to a known user profile once an identifier (such as email or userID) becomes available.

**Example:**  
When a user logs in or signs up, an identify event links their previous anonymous activity to their authenticated profile.

---

### Page Event
A **page event** captures page-level interactions, such as page views, URLs, referrers, or load errors, providing context about how users navigate the product.

**Example:**  
A `Page Viewed` event fires when a user visits a product detail page.

---

## 2️⃣ Identifier Types

### UserID
A **userID** is a stable, unique identifier assigned to a user once they are authenticated.  
It is used to consistently associate events and attributes with a specific user across sessions and devices.

---

### AnonymousID
An **anonymousID** identifies users who have not yet logged in.  
It allows the CDP to track pre-authentication behavior and later link it to a user profile once the user becomes known.

---

### Internal Database ID
The **internal database ID** is the system’s primary identifier used to consolidate and manage all related identifiers (userID, anonymousID, external IDs).

It acts as the **single source of truth** for identity resolution and ensures consistent data management across integrations and storage layers.

---

## 3️⃣ Identity Merging Risk

CDPs merge user profiles to create a unified view of the customer journey, especially when users move from anonymous to authenticated states or use multiple devices.

The primary risk of incorrect identity merging is **data leakage and loss of trust**, where one user’s behavior or attributes are incorrectly attributed to another.

For example, on shared devices, an incorrect merge could cause a user who already purchased a product to continue seeing acquisition banners or receive irrelevant campaigns.  
Beyond user experience issues, this can lead to **incorrect attribution, compliance risks, and erosion of customer trust**.

For this reason, identity merging must prioritize accuracy, privacy, and clear separation of user intent.

---

## Tools Used
- ChatGPT (for structuring and clarity)
- Personal experience in CDP and B2B SaaS products
