# 🛡️ GigShield — AI-Powered Parametric Income Insurance for India's Gig Workers

> **Guidewire DEVTrails 2026 | University Hackathon**
> Protecting the income of India's food delivery partners from uncontrollable external disruptions.
> Powered by Classical ML + **Advanced Generative AI** at every layer.

---

## 📌 Table of Contents

1. [Project Overview](#1-project-overview)
2. [Persona & Problem Scope](#2-persona--problem-scope)
3. [Core Features (Must-Build)](#3-core-features-must-build)
4. [Unique Add-On Features](#4-unique-add-on-features)
5. [Advanced Gen AI Integration](#5-advanced-gen-ai-integration)
6. [User Flow & Scenarios](#6-user-flow--scenarios)
7. [Parametric Triggers](#7-parametric-triggers)
8. [Weekly Premium Model](#8-weekly-premium-model)
9. [AI/ML + Gen AI Architecture](#9-aiml--gen-ai-architecture)
10. [System Architecture](#10-system-architecture)
11. [Tech Stack](#11-tech-stack)
12. [API Integrations](#12-api-integrations)
13. [Fraud Detection Strategy](#13-fraud-detection-strategy)
14. [Dashboard Design](#14-dashboard-design)

---

## 1. Project Overview

**GigShield** is an AI-enabled parametric income insurance platform built exclusively for **food delivery partners** (Zomato / Swiggy) in India. When external disruptions — extreme weather, severe pollution, or social curfews — prevent workers from earning, GigShield automatically detects the disruption, validates the claim, and instantly transfers compensation to the worker's UPI account.

**No forms. No waiting. No middlemen.**

What sets GigShield apart is the deep embedding of **Generative AI** — not as a surface-level chatbot, but as an intelligent reasoning layer that explains decisions, detects fraud narratives, generates personalized financial reports, conducts voice-based onboarding in regional languages, and synthesizes external data into human-readable disruption summaries for both workers and insurers.

> ⚠️ **Coverage Scope: Income Loss Only.**
> We strictly DO NOT cover health, life, accidents, or vehicle repairs.

---

## 2. Persona & Problem Scope

### Chosen Persona: Food Delivery Partner (Zomato / Swiggy)

| Attribute | Details |
|---|---|
| Typical Daily Earnings | ₹600 – ₹1,200/day |
| Peak Hours | 12–2 PM (lunch), 7–10 PM (dinner) |
| Work Location | Urban/semi-urban zones, Tier 1 & 2 cities |
| Primary Risk | Outdoor exposure — weather, pollution, civil disruptions |
| Preferred Payment | UPI / PhonePe / Paytm |
| Tech Comfort | Moderate; WhatsApp-native, low English literacy |

### Persona-Based Scenarios

**Scenario 1 — Rajan, Mumbai (Monsoon)**
Rajan works 10 hours/day for Zomato in Andheri East. On July 15th, IMD issues a Red Alert for heavy rainfall. GigShield detects the trigger, validates Rajan's zone, runs fraud checks, calculates his personalized payout using Earnings DNA, and credits ₹560 to his UPI within 2 minutes. He receives a WhatsApp voice note in Hindi explaining the payout calculation.

**Scenario 2 — Priya, Delhi (Pollution)**
AQI crosses 400 in South Delhi. GRAP Stage IV is declared. GigShield auto-triggers and its Gen AI Explainability Engine sends Priya a voice note: *"Priya ji, aapke zone mein AQI 412 ho gaya hai. Aapka claim approve ho gaya aur ₹700 aapke account mein bhej diya gaya hai."*

**Scenario 3 — Arjun, Bengaluru (Bandh)**
A sudden bandh is declared in Whitefield. GigShield's LLM-based Disruption Intelligence Engine scans news sources, classifies the event as a qualifying social disruption, cross-validates with Arjun's GPS inactivity, and triggers payout — with zero human intervention.

---

## 3. Core Features (Must-Build)

### 3.1 🔐 Optimised Onboarding
- Mobile-first registration (WhatsApp OTP or Aadhaar-based mock KYC)
- Worker profile: city, delivery zone (pin code), platform, avg. weekly earnings
- **Gen AI Voice Onboarding** — workers can onboard by speaking in Hindi/regional language (see Section 5.1)
- Language support: English, Hindi, Tamil, Kannada, Marathi

### 3.2 📊 AI Risk Profiling
- Zone-level risk score: flood history, AQI frequency, curfew events, worker history
- Risk Tier (Low / Medium / High) → feeds premium model
- **Gen AI Risk Narrative** — LLM generates a plain-language explanation of the worker's risk score (see Section 5.2)

### 3.3 📋 Policy Management (Weekly Basis)

| Plan | Weekly Premium | Max Daily Payout | Max Triggers/Week |
|---|---|---|---|
| Basic Shield | ₹29/week | ₹400 | 2 |
| Standard Shield | ₹49/week | ₹700 | 3 |
| Premium Shield | ₹79/week | ₹1,200 | 5 |

- Policy activates Monday 00:00, expires Sunday 23:59
- Auto-renewal via UPI mandate
- **Gen AI Plan Recommender** — LLM explains the best plan for the worker in their language

### 3.4 ⚡ Parametric Claim Automation
- Zero manual claim filing
- Trigger monitoring 24/7 via external APIs
- On breach → zone validation → fraud check → Earnings DNA payout → UPI transfer
- **Gen AI Claim Explanation** — every auto-claim generates a personalized natural language summary (see Section 5.3)

### 3.5 💸 Payout Processing
- Instant UPI transfer via Razorpay test mode / Stripe sandbox
- Payout = disruption hours × worker's Earnings DNA hourly rate (capped at plan max)
- Full history with Gen AI weekly income protection summary

### 3.6 📈 Analytics Dashboard
- Worker view: coverage status, income protected, claims, trust score
- Admin view: policies, claims, loss ratios, zone heatmap, fraud queue
- **Gen AI Insurer Briefing** — daily auto-generated natural language performance summary (see Section 5.5)

---

## 4. Unique Add-On Features

### Add-On 1: 🧠 Earnings DNA — Personalized Income Baseline Engine

Every existing parametric product in India pays **flat, predefined amounts**. GigShield pays based on each worker's actual earning pattern.

**How it works:**
- Worker inputs last 4 weeks of earnings at onboarding (or mock platform API)
- System builds a per-worker earnings model: average earnings by hour, day-of-week, and zone
- Disruption payout = worker's estimated income for the disrupted time window
- Model retrains weekly as new earnings data accumulates

**Payout Example:**
```
Disruption:   Tuesday 7:30 PM – 10:00 PM (2.5 hours)
DNA Rate:     ₹240/hour (Rajan's Tuesday peak average)
Raw Payout:   2.5 × ₹240 = ₹600
Plan Cap:     ₹700/day (Standard Shield)
Final Payout: ₹600 ✅
```

**Tech:** Linear regression (MVP) → Facebook Prophet time-series (Phase 3)

---

### Add-On 2: 📡 Platform Outage as an Insurable Trigger

App downtime during peak dinner/lunch hours = zero orders = direct income loss. No Indian insurer covers this today.

**How it works:**
- Monitor Zomato/Swiggy platform health via UptimeRobot or mock health-check endpoint
- If platform downtime > 30 minutes during peak windows → trigger activated
- Cross-validate with worker's active session status (mock)
- Micro-payout issued for the downtime window

---

### Add-On 3: 🏆 Zone-Based Peer Risk Pool with Cashback

Workers in the same delivery zone share a micro risk pool. Low collective claims = cashback for everyone.

**How it works:**
- Workers in the same pin code zone are auto-grouped
- Target pool loss ratio: 60%
- If actual claims < 60% of pooled premiums → 20% returned as next-week discount
- Pool performance visible to workers → organic peer accountability → reduced fraud

---

## 5. Advanced Gen AI Integration

This is where GigShield goes beyond conventional ML. **Large Language Models (LLMs)** — specifically Claude API (Anthropic) — are embedded as reasoning, explanation, and synthesis engines at 6 distinct points in the product.

---

### 5.1 🎙️ Multilingual Voice Onboarding Agent

**Problem:** Millions of gig workers have low English literacy and struggle with form-based onboarding.

**Solution:** A conversational voice agent powered by LLM + Speech-to-Text (STT) + Text-to-Speech (TTS).

**Flow:**
```
Worker taps "Voice Onboarding"
     │
     ▼
Whisper / Sarvam AI converts spoken Hindi → text
     │
     ▼
Claude (LLM) acts as conversational agent:
  - Asks naturally: "Aap kaun se platform pe deliver karte hain?"
  - Understands free-form: "main zomato pe kaam karta hu andheri mein"
  - Extracts structured JSON: { platform: "Zomato", zone: "Andheri" }
  - Handles confusion gracefully, re-asks if unclear
     │
     ▼
ElevenLabs TTS converts LLM response back to spoken Hindi
     │
     ▼
Profile auto-populated → worker reviews → confirms
```

**System Prompt (simplified):**
```
You are GigShield's onboarding assistant for Indian food delivery workers.
Collect: platform name, city, delivery zone, avg weekly earnings, UPI handle.
Ask one question at a time. Be warm and simple. Use the worker's language.
Extract structured JSON from their answers. Never ask about health or vehicles.
```

**Tech:** Sarvam AI (STT, Indian languages) + Claude claude-sonnet-4-20250514 + ElevenLabs (TTS)

---

### 5.2 📝 Risk Score Explainability Engine

**Problem:** Workers don't trust black-box risk scores. Insurers need to explain premium differences.

**Solution:** After every risk score computation, an LLM generates a plain-language, personalized explanation.

**Flow:**
```
ML Model outputs:
{ zone_flood_score: 0.78, aqi_score: 0.45, final_tier: "High", multiplier: 1.28 }
     │
     ▼
Claude prompt:
"Explain this risk score to a Zomato delivery partner in Andheri East
in simple Hindi (3 sentences). Explain why risk is High and premium impact."
     │
     ▼
Output sent via WhatsApp + shown in app:
"Rajan ji, aapka zone Andheri East mein pichhle 2 saalon mein 8 baar
heavy rain alert aaya hai, isliye aapka risk score zyada hai. Iska
matlab hai aapka weekly premium ₹63 hoga. Lekin baarish mein aapko
₹700 tak ki protection milegi."
```

**Value:** Regulatory explainability + worker trust + insurer compliance documentation.

---

### 5.3 🤖 Claim Explanation & Notification Engine

**Problem:** Workers receive a UPI credit with no context. They don't understand what triggered it or how the amount was calculated.

**Solution:** Every auto-claim generates a personalized explanation via LLM, delivered as WhatsApp text + voice note.

**Flow:**
```
Claim event:
{ trigger: "Heavy Rainfall 89mm", window: "7:30–10 PM", hours: 2.5,
  dna_rate: "₹240/hr", payout: 600, fraud_score: 12 }
     │
     ▼
Claude generates Hindi WhatsApp message + voice note:
"Rajan ji, aaj shaam 7:30 se 10 baje tak 89mm baarish hui — Red Alert.
Iss wajah se aap kaam nahi kar paaye. Hamare AI ne calculate kiya ki
aap is time ₹240/ghante kamate hain. 2.5 ghante ke hisaab se ₹600
aapke UPI mein bhej diya gaya hai. Policy: GS-2847."
```

---

### 5.4 🕵️ LLM Fraud Narrative Detector

**Problem:** Classical anomaly detection misses contextual fraud — a worker whose GPS trail tells an inconsistent story but whose numbers look statistically normal.

**Solution:** For claims flagged by ML (score 30–70), Claude reviews the full claim context and generates a written fraud assessment.

**Flow:**
```
Flagged claim context sent to Claude:
{
  worker_gps: "Indiranagar (8km from claimed zone)",
  session_status: "Active — orders being accepted",
  news_api: "No credible bandh found for this date",
  peer_pool: "83% of zone peers also claimed",
  ml_score: 62
}
     │
     ▼
gpt output (to admin fraud queue):
"Fraud Risk: HIGH
1. Worker GPS 8km outside claimed disruption zone at claim time.
2. Platform session was active — orders were being accepted.
3. No credible source confirms this bandh. 83% zone claim rate
   suggests possible coordinated fraud ring.
Recommendation: REJECT — escalate for investigation."
```

**Value:** 70% reduction in manual review time. Audit-ready written justification for every rejected claim.

---

### 5.5 📊 Gen AI Insurer Daily Briefing Generator

**Problem:** Raw dashboards require expertise to interpret. Insurers need plain-language, forward-looking summaries.

**Solution:** Every morning, a cron job collects metrics + weather forecasts and passes them to Claude, which generates a concise daily brief.

**Output Example:**
```
GIGSHIELD DAILY BRIEF — March 22, 2026

Yesterday: 847 active policies. 34 claims triggered (₹19,400 total).
Loss ratio: 48.2% — within healthy range.

Top Risk Zones Today:
- Andheri East (Mumbai): 90% rain probability
- Koramangala (Bengaluru): AQI forecast 380 (approaching Severe)

3 Recommendations:
1. Consider premium surcharge in Andheri East for new sign-ups this week.
2. Investigate Koramangala pool — 83% claim rate last week is anomalous.
3. 12 Delhi NCR workers approaching trust score 30 — flag before next claim.
```

---

### 5.6 💬 GigShield Saathi — RAG-Powered Policy Assistant

**Problem:** Workers have policy questions but no easy way to get accurate answers.

**Solution:** A RAG (Retrieval-Augmented Generation) chatbot embedded in WhatsApp and the app. It retrieves the worker's actual policy data + product documentation before answering — preventing hallucinations on financial questions.

**Flow:**
```
Worker: "Mera claim kyun kam aaya?"
     │
     ▼
RAG System retrieves: worker's claim record, Earnings DNA data, policy tier, FAQ docs
     │
     ▼
Claude generates grounded response:
"Aapka claim ₹600 isliye aaya kyunki disruption 2.5 ghante ka tha
aur aapki usual earning ₹240/ghante hai (2.5 × 240 = ₹600). Aapka
Standard Shield plan mein max ₹700/din milta hai — poora amount
mil gaya. Premium Shield (₹79/week) upgrade karna chahenge?"
```

**Vector DB:** Pinecone / ChromaDB (stores: policy docs, FAQs, worker-specific records)

---

## 6. User Flow & Scenarios

```
┌──────────────────────────────────────────────────────────────────┐
│                     COMPLETE WORKER JOURNEY                      │
└──────────────────────────────────────────────────────────────────┘

[1. DISCOVERY]
Worker sees GigShield on Zomato partner app or WhatsApp group
        │
        ▼
[2. ONBOARDING — Gen AI Voice Agent 5.1]
Opens GigShield → chooses Voice or Text onboarding
  Voice path: Speaks Hindi → Whisper STT → Claude extracts data → TTS responds
  Text path:  Standard form (English/Hindi)
→ OTP verification → Risk Score generated
→ LLM generates Risk Explanation in Hindi [Gen AI 5.2]
→ LLM recommends best plan [Gen AI 5.2]
        │
        ▼
[3. POLICY SELECTION]
Worker selects plan → pays via UPI (₹29 / ₹49 / ₹79)
→ Policy activated for the week
→ Saathi sends WhatsApp welcome message [Gen AI 5.6]
        │
        ▼
[4. ACTIVE COVERAGE — Trigger Engine running every 15 min]
  ├─ OpenWeatherMap (rainfall, heat)
  ├─ CPCB AQI API (pollution)
  ├─ News API → LLM classifies social disruptions [Gen AI 5.4]
  ├─ UptimeRobot mock (platform outage) [Add-On 2]
  └─ IMD Alert feed
        │
     ┌──┴──────────────────────┐
     │ No disruption           │ Disruption detected
     ▼                         ▼
[5A. CLEAN WEEK]          [5B. DISRUPTION]
Pool cashback calc        Zone match check → Policy check
LLM weekly summary        ML Fraud Score calculated
sent to worker            If 30–70: LLM Fraud Review [5.4]
[Gen AI 5.5]              If < 30: Auto-approve
                          Earnings DNA calculates payout [Add-On 1]
                               │
                               ▼
                    [6. PAYOUT]
                    UPI transfer (Razorpay sandbox)
                    LLM generates WhatsApp text + Hindi voice note [5.3]
                    Trust Score updated | Pool ratio updated
        │
        ▼
[7. WORKER QUERY — anytime]
"Mera policy kab renew hoga?" → Saathi answers instantly [Gen AI 5.6]
        │
        ▼
[8. WEEKLY RENEWAL]
Policy expires Sunday 23:59
→ Risk-adjusted premium shown with LLM explanation
→ Auto-renewal if mandate set
```

---

## 7. Parametric Triggers

| # | Trigger | Data Source | Threshold | Gen AI Role |
|---|---|---|---|---|
| T1 | Heavy Rainfall | OpenWeatherMap / IMD | >64.5 mm/day (Red Alert) | Claim explanation in Hindi |
| T2 | Extreme Heat | IMD Temperature API | >45°C for 3+ hours | Risk narrative generator |
| T3 | Severe Pollution | CPCB AQI API | AQI >400, GRAP Stage IV | Auto-briefing for insurer |
| T4 | Flood/Waterlogging | Civic body mock alerts | Zone declared unpassable | LLM classifies alert severity |
| T5 | Social Disruption | News API + **LLM classifier** | Bandh/curfew declared | **LLM classifies & validates news event** |
| T6 | Platform Outage | UptimeRobot mock | Downtime >30 min in peak hours | Saathi explains payout |

> **Note on T5:** Raw news text is passed to Claude, which classifies whether the event qualifies as a covered disruption, its geographic scope, and expected duration. This replaces brittle keyword-matching with genuine language understanding.

---

## 8. Weekly Premium Model

### Dynamic Pricing Formula

```
Base Weekly Premium (by tier: ₹29 / ₹49 / ₹79)
    + Zone Risk Multiplier        (+0% to +30%, ML risk model)
    - Trust Score Discount        (up to -15%, clean claim history)
    - Pool Cashback Credit        (up to -20%, prior week pool performance)
    ± Predictive Weather Adj.     (±10%, 7-day forecast)
─────────────────────────────────────────────────────────────────
= Final Weekly Premium
  → LLM generates plain-language explanation shown before payment
```

### Earnings DNA Payout Calculation

```
Disruption window:    Tuesday 7:30 PM – 10:00 PM (2.5 hours)
Worker's DNA rate:    ₹240/hour (Rajan's Tuesday peak, Andheri East)
Raw payout:           2.5 × ₹240 = ₹600
Plan cap (Standard):  ₹700/day
Final payout:         ₹600 ✅
```

---

## 9. AI/ML + Gen AI Architecture

```
┌────────────────────────────────────────────────────────────────┐
│                   AI / ML + GEN AI LAYER                       │
└────────────────────────────────────────────────────────────────┘

Classical ML (Python / scikit-learn / XGBoost / Prophet):
├── Risk Scoring Model       → Zone risk tier + premium multiplier
├── Earnings DNA Model       → Prophet time-series per worker
└── Fraud Detection Model    → Isolation Forest anomaly scoring

Generative AI (Claude API — Anthropic):
├── [5.1] Voice Onboarding Agent      → Whisper STT + Claude + ElevenLabs TTS
├── [5.2] Risk Explainability Engine  → Risk scores → Hindi explanation
├── [5.3] Claim Notification Engine   → Claim data → personalized WhatsApp + voice
├── [5.4] Fraud Narrative Detector    → Flagged claims → LLM audit trail
├── [5.5] Insurer Briefing Generator  → Metrics + forecast → daily brief
└── [5.6] GigShield Saathi (RAG)      → Policy Q&A chatbot
         └── Vector DB: Pinecone / ChromaDB
             (stores: policy docs, FAQs, worker-specific records)

All Gen AI calls routed via:
└── LLM Gateway Service (Node.js)
    ├── Prompt templates per use case (stored in /ml-engine/prompts/)
    ├── Language detection + routing (Hindi / English / regional)
    ├── Rate limiting + cost tracking per use case
    └── Response caching (Redis) for common Saathi queries
```

---

## 10. System Architecture

```
┌────────────────────────────────────────────────────────────────────┐
│                    GIGSHIELD FULL ARCHITECTURE                     │
└────────────────────────────────────────────────────────────────────┘

  ┌──────────────┐   ┌──────────────┐   ┌──────────────────────┐
  │  Worker App  │   │ WhatsApp Bot │   │   Admin Dashboard    │
  │  (React PWA) │   │(Twilio/WATI) │   │    (React Web)       │
  └──────┬───────┘   └──────┬───────┘   └──────────┬───────────┘
         └──────────────────┼──────────────────────┘
                            ▼
              ┌─────────────────────────┐
              │      API GATEWAY        │
              │   (Node.js / Express)   │
              └────────────┬────────────┘
                           │
      ┌────────────────────┼─────────────────────┐
      ▼                    ▼                     ▼
┌──────────────┐   ┌───────────────┐   ┌──────────────────┐
│Auth Service  │   │Policy Service │   │  Claims Service  │
│(OTP / KYC)   │   │(Onboarding,   │   │(Trigger Monitor, │
│              │   │ Premium Calc) │   │ Auto-Claims,     │
└──────────────┘   └───────────────┘   │ Payout Process)  │
                                       └──────────────────┘
      ┌────────────────────┬─────────────────────┐
      ▼                    ▼                     ▼
┌──────────────┐   ┌────────────────┐   ┌──────────────────┐
│  ML Engine   │   │  LLM Gateway   │   │  Notification    │
│ (FastAPI /   │   │  (Node.js)     │   │  Service         │
│  Python)     │   │                │   │(WhatsApp/FCM/TTS)│
│              │   │  Claude API    │   └──────────────────┘
│ - RiskScore  │   │  Whisper STT   │
│ - EarningsDNA│   │  Pinecone RAG  │
│ - FraudModel │   │  ElevenLabs TTS│
└──────────────┘   └────────────────┘
                           │
      ┌────────────────────┴──────────────────────┐
      ▼                                           ▼
┌─────────────────────────┐       ┌──────────────────────────┐
│     DATABASE LAYER      │       │     EXTERNAL APIs        │
│ PostgreSQL (core data)  │       │                          │
│ Redis (cache/sessions)  │       │ 🌦 OpenWeatherMap        │
│ Pinecone (vector store) │       │ 💨 CPCB AQI              │
│ TimescaleDB (time-series│       │ 📰 Mock News API         │
│ earnings + weather logs)│       │ 📡 UptimeRobot           │
└─────────────────────────┘       │ 💳 Razorpay Sandbox      │
                                  │ 🗣 Whisper / Sarvam AI   │
                                  │ 🔊 ElevenLabs TTS        │
                                  │ 🗺 Google Maps API       │
                                  │ 🤖 Claude API (Anthropic)│
                                  └──────────────────────────┘
```

### Key Design Decisions

**Why PWA over Native App?**
Zero app-store friction, works on low-end Android, installable to home screen. WhatsApp bot is the primary channel for low-tech workers.

**Why Parametric Insurance?**
Objective triggers from public APIs eliminate disputes, enable zero-touch claims, and allow instant payouts — workers cannot wait 7–30 days.

**Why Gen AI on top of classical ML?**
Classical ML classifies and scores. Gen AI explains, communicates, and reasons contextually. Together they create a product that is not just automated but *understandable and trustworthy* to a low-literacy gig worker in India.

**Why RAG for Saathi?**
RAG grounds every LLM response in actual policy documents and worker-specific data, preventing hallucinations on financial and legal questions — critical for a regulated insurance product.

---

## 11. Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| Frontend | React.js (PWA) | Worker app + admin dashboard |
| Backend | Node.js + Express | Core API services |
| Database | PostgreSQL + Redis | Relational data + session caching |
| Time-series DB | TimescaleDB | Weather logs, earnings history |
| Vector DB | Pinecone / ChromaDB | RAG knowledge store for Saathi |
| ML Engine | Python + FastAPI | Risk model, Earnings DNA, Fraud model |
| ML Libraries | scikit-learn, XGBoost, Prophet | Training + serving |
| LLM | OpenAI API | All 6 Gen AI use cases |
| STT | Sarvam AI / Whisper API | Voice onboarding (Indian languages) |
| TTS | ElevenLabs / Google Cloud TTS | Hindi voice notifications |
| Trigger Engine | Node.js cron + Bull queue | API polling every 15 minutes |
| Payments | Razorpay Test Mode | Simulated UPI payouts |
| Notifications | Twilio WhatsApp API (trial) | Multi-channel alerts |
| Hosting | Azure | Free-tier |
| Version Control | GitHub | Single repo, all 3 phases |


## 12. API Integrations

| API | Purpose | Mode |
|---|---|---|
| OpenWeatherMap | Real-time weather + 7-day forecast | Free tier (live) |
| CPCB AQI | Real-time Air Quality Index | Free tier (live) |
| IMD Alerts | Official Red/Orange weather warnings | Mock / scrape |
| Google Maps Geocoding | Zone validation via pin code | Free tier (live) |
| UptimeRobot | Platform health monitoring | Free tier (live) |
| Razorpay | Simulated UPI payouts | Test mode |
| Twilio | WhatsApp Business notifications | Trial mode |
| News API | Social disruption event feed | Mock / NewsAPI free tier |
| OpenAI API | All 6 LLM Gen AI use cases | API key (pay-per-use) |
| Sarvam AI / Whisper | STT for voice onboarding | Free tier / API key |
| ElevenLabs | TTS for Hindi voice notifications | Free tier |
| Pinecone | Vector store for Saathi RAG chatbot | Free tier |

---

## 14. Fraud Detection Strategy

### Layer 1 — Rule-Based (Real-time)
- Worker GPS pin code must match disrupted zone at claim time
- Claim time must overlap trigger event window
- Max 1 claim per disruption event per worker
- Device ID + account match (no duplicate accounts)

### Layer 2 — ML Anomaly Detection (Batch, every 15 min)
- Isolation Forest: claim frequency, GPS consistency, peer pool deviation
- Score > 70 → auto-reject | Score 30–70 → LLM review | Score < 30 → auto-approve

### Layer 3 — LLM Fraud Narrative (Borderline cases) [Gen AI 5.4]
- Full claim context passed to Claude for contextual reasoning
- OpenAI produces written audit trail with risk level + recommendation
- ~70% reduction in manual review time
- Provides regulatory-grade documentation for every rejected claim

### Layer 4 — Community Accountability [Add-On 3]
- Fraudulent claims reduce pool cashback for entire zone
- Pool anomaly alert: if >75% of a zone claims simultaneously → escalate

### Trust Score System

| Event | Score Change |
|---|---|
| Clean week, no suspicious activity | +2 |
| Valid claim paid | 0 |
| Claim flagged for review (cleared) | -5 |
| Claim rejected (fraud confirmed) | -20 |
| Score > 80 | -10% premium, instant auto-approval |
| Score < 30 | All claims held for manual review |

---

## 15. Dashboard Design

### Worker Dashboard
```
┌──────────────────────────────────────┐
│  👋 Hello, Rajan!                    │
│  📍 Andheri East, Mumbai             │
├──────────────────────────────────────┤
│  🛡️ ACTIVE POLICY                    │
│  Standard Shield — Week of Mar 21    │
│  ₹700/day max | Expires Sun Mar 27  │
├──────────────────────────────────────┤
│  💰 THIS WEEK                        │
│  Income Protected:   ₹700           │
│  Claims Triggered:   1              │
│  Payout Received:    ₹560           │
├──────────────────────────────────────┤
│  🏆 Trust Score:     74/100         │
│  🌦 Zone Risk:       Medium         │
│  👥 Pool Cashback:   ₹9 next week   │
├──────────────────────────────────────┤
│  💬 [Ask GigShield Saathi]  [Hindi] │  ← RAG Chatbot [5.6]
│  📋 Claim History                    │
│  Mar 22 — Heavy Rain — ₹560 ✅      │
│  Mar 15 — Extreme Heat — ₹400 ✅   │
└──────────────────────────────────────┘
```

### Admin / Insurer Dashboard
- Live policy count by city, zone, plan tier
- Claims today (count, value, zone breakdown)
- Loss ratio (real-time gauge)
- Zone-level risk heatmap (Google Maps overlay)
- Fraud alerts queue with LLM narrative summaries [Gen AI 5.4]
- **AI Daily Brief** — OpenAI-generated summary at dashboard top [Gen AI 5.5]
- Predictive next-week claim forecast by zone (weather model + LLM)

---

## 👥 Team

> Mrinank Kavuri
> Aadya Mishra
> Avni Sharma
> Sai Prashanth
> Janesh Prathipati 

---

## 📜 License

MIT License — Built for Guidewire DEVTrails 2026 University Hackathon.

---

*Powered by Classical ML + Generative AI — because automation without explanation is not enough.*
