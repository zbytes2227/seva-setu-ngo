
# 🧠 Project Title

**SEVASETU — AI-Powered Volunteer & Resource Coordination Platform for NGOs**

---

# Problem Summary

NGOs collect **critical ground-level data** (needs, shortages, crises), but:

* it’s scattered (forms, WhatsApp, paper)
* no real-time visibility
* volunteers are not optimally assigned

 Result: **slow response, wasted resources, unmet urgent needs**

---

#  Solution

**SEVASETU** creates a **central intelligence layer**:

* Collect NGO data (location + needs)
* Analyze urgency using AI
* Show **real-time dashboard**
* Highlight **where help is needed most**

---

#  Tech Stack (v1)

* **Frontend:** Next.js (App Router)
* **Backend:** Node.js / Next API routes
* **Database:** MongoDB / PostgreSQL
* **AI Layer:** Gemini API (for analysis & insights)
* **Location API:** India Post (pincode validation)
* **Realtime:** WebSockets / Firebase (optional)

---

#  Core Features (v1)

---

##  1. Admin Authentication

### Features:

* Admin login (email + password)
* JWT/session-based auth
* Protected dashboard routes

### Form Fields:

```id="login-form"
Email
Password
```

---

## 2. NGO Registration Form

### Purpose:

Admin registers NGO data + local needs

---

### 📋 Form Structure:

```id="ngo-form"
NGO Name
Contact Person Name
Phone Number
Email

Pincode (India Post API autofill)
→ Auto fetch:
   - State
   - District
   - Area

Address (manual)

Category of Work (multi-select):
- Food
- Healthcare
- Education
- Disaster Relief
- Shelter

Current Needs (multi-select):
- Food Supplies
- Medicines
- Volunteers
- Funds
- Clothes

Urgency Level:
- Low
- Medium
- High
- Critical 

Description (free text)

Number of People Affected

Available Volunteers (count)
```

---

### ⚙️ Logic:

* Pincode → fetch location
* Store structured data
* Send description → Gemini → extract insights

---

## 📊 3. AI Processing Layer

### What Gemini does:

* Converts messy description → structured insights
* Detects:

  * urgency signals
  * priority category
  * hidden needs

### Example:

Input:

> “We are running out of food, 200+ people…”

Output:

* Priority: Food
* Urgency: Critical
* Action: Immediate supply required

---

## 📊 4. Real-Time Dashboard

### 🧠 Main Sections:

---

###  A. Urgency Heat Overview

* Total NGOs
* Critical cases
* High priority zones

---

### 📍 B. Location-Based View

* NGOs grouped by:

  * State
  * District

---

### 📋 C. Live Needs Feed

Cards showing:

* NGO name
* location
* urgency badge
* needs

---

### 📈 D. AI Insights Panel

* “Top urgent need today: Food in Lucknow region”
* “Volunteer shortage detected in 3 areas”

---

### ⚡ E. Quick Actions

* Filter by:

  * urgency
  * category
* sort by priority

---

# 🔄 Data Flow

```id="flow"
Admin → fills NGO form  
→ Data stored in DB  
→ Sent to Gemini  
→ AI extracts insights  
→ Dashboard updates in realtime  
→ Admin sees priority areas
```

---

# 🧠 AI Prompts (Core Logic)

Example prompt:

```id="ai-prompt"
Analyze this NGO report:

[TEXT]

Return:
- urgency level (low/medium/high/critical)
- main need category
- suggested action
- summary (1 line)
```

---

# 📁 Suggested Folder Structure

```id="structure"
app/
  login/
  dashboard/
  ngo-form/

components/
  Navbar
  NGOCard
  DashboardStats

lib/
  db.js
  gemini.js
  pincode.js

api/
  auth/
  ngo/
  analyze/
```

---

# 🎯 MVP Demo Flow (Important for judges)

1. Admin logs in
2. Adds NGO with:

   * pincode
   * urgent need
3. AI processes description
4. Dashboard updates
5. Show:
   👉 “Critical need detected”
   👉 “Suggested action”

---

# 🚀 Future Scope (say this in presentation)

* Volunteer matching engine
* Mobile app for field workers
* WhatsApp integration
* Live crisis alerts
* Government API integration

---
