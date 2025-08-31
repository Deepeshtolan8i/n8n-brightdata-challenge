# Lead Gen + Qualification + Hyper‑Personalized Emails (n8n Workflows)

End‑to‑end automation that:
- Scrapes leads from Google Maps (by Neighborhood + Industry)
- Enriches & cross‑verifies companies via Bright Data SERP + Apollo
- Scrapes websites (company site + Owler when available) and captures emails
- Generates HTML cold emails (Subject, Body, CTA, Follow‑ups) tailored to each lead
- Uploads everything to Google Sheets and flags Qualified/Disqualified leads

Built with *n8n, **Bright Data* (Google Maps & SERP + website snapshot), Apollo API, an LLM (provider‑agnostic), and *Google Sheets API*.

---

## 🚀 Features
- *Lead Generation*: Automated scraping from Google Maps using neighborhood and industry queries
- *Lead Enrichment*: Multi-source data enrichment with intelligent verification
- *Email Personalization*: AI-powered cold email generation with HTML formatting
- *Lead Qualification*: Automated filtering based on available contact information
- *Data Management*: Seamless Google Sheets integration for lead tracking

---

## 📋 What Gets Stored

For each lead we store:
- *Company*: name, domain, address, city, neighborhood, rating
- *Identifiers*: Owler URL (when found), snapshot URL, source links
- *Enrichment*: revenue, employee count, socials, phone, founded year
- *Contacts*: email(s) captured from site (or disqualification reason)
- *Email Output*: subject, HTML body, CTA, follow‑up notes
- *Status*: qualified (true/false), disqualified reason, timestamps

---

## 🧩 Workflows

### 1. Lead Generation (workflows/main-agent.json)

- Scrapes Google Maps using BrightData
- Input: Neighborhood + Industry search queries
- Output: Business name, address, website, city, neighborhood, ratings

### 2. Lead Enrichment (workflows/main-agent.json)
*Primary Path (with Owler)*:

- Google search for Owler company profiles
- LLM analyzes search results to identify best Owler link
- Scrapes Owler data using BrightData
- Cross-verifies with Apollo for revenue, employee count, socials
- Scrapes company website for email addresses
- Qualified: Leads with valid email addresses
- Disqualified: Leads without discoverable contact information
- Creates hyper-personalized HTML email content
- Includes: Subject line, body, CTA, follow-up notes
- Compiles comprehensive lead profiles

*Fallback Path (without Owler)*:

- Direct Apollo search for company enrichment
- Scrapes company website for email addresses
- Qualified: Leads with valid email addresses
- Disqualified: Leads without discoverable contact information
- Creates hyper-personalized HTML email content
- Includes: Subject line, body, CTA, follow-up notes
- Compiles comprehensive lead profiles

---

## 📊 Output Data

Each processed lead includes:
- Complete company details
- Email address (if found)
- Lead summary and qualification status
- Employee count and founding year
- Phone number
- Formatted HTML email content
- Follow-up recommendations

---

## 📈 Results
All processed leads are automatically uploaded to Google Sheets with complete qualification status and ready-to-use email templates.

Built for efficient B2B lead generation and personalized outreach at scale.

---

## 🎬 Demo / Live Access

Demo Video: [Add Loom/YouTube link here]

---

## 📷 Architecture Diagram

<img width="1336" height="175" alt="image" src="https://github.com/user-attachments/assets/a79127b2-a8ac-4816-a16f-4dfe7afaa18b" />


<img width="1881" height="133" alt="image" src="https://github.com/user-attachments/assets/8bbe0860-98ce-428c-b1c5-72ab2655373f" />


<img width="1667" height="537" alt="image" src="https://github.com/user-attachments/assets/a7dc2834-e9c4-48b4-a761-3a0cb21b3f06" />


<img width="1552" height="282" alt="image" src="https://github.com/user-attachments/assets/2d98a15c-3d8f-4964-b3bb-18c9674f590b" />
