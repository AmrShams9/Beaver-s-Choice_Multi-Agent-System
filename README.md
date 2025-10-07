# 🦫 BeaverChoice – Multi-Agent Order Processing System

**BeaverChoice** is a modular multi-agent order processing system that simulates real-world workflows for handling customer requests — from natural-language request to final transaction. It’s built for clarity, extensibility, and easy testing.

---

## 📖 Project Overview

BeaverChoice leverages a set of cooperating agents to parse requests, match items to a catalog, validate inventory and delivery, generate quotes (with discounts), and finalize transactions.

**Repository images**

* Workflow diagram: `beaverChoice.png`
* System test screenshot: `Screenshot 2025-09-28 175831.png`

> **Note:** If images do not render on GitHub due to spaces in filenames, rename `Screenshot 2025-09-28 175831.png` to `test_screenshot.png` and update the link below.

---

## 🧩 Agents in the System

![BeaverChoice Workflow](beaverChoice.png)

* **Extraction Agent** – Parses raw customer requests into structured JSON (`ParsedRequest`).
* **Catalog Matcher** – Maps parsed items to canonical catalog entries (normalization & synonyms).
* **Inventory Agent** – Checks local stock and supplier delivery feasibility.
* **Quoting Agent** – Computes prices, applies discounts and loyalty rules, and produces order summaries.
* **Transaction Agent** – Commits successful orders and updates cash & inventory.

---

## 🎯 Objectives

* Automate customer order handling from natural language to transaction.
* Validate catalog items, stock, and delivery feasibility.
* Apply business logic (discounts, loyalty rewards, taxes).
* Request clarifications for ambiguous or unknown items.
* Demonstrate a clean multi-agent system design pattern.

---

## ⚙️ Tech Stack

* **Language:** Python 3.8+ (recommended)
* **Database:** SQLite (local, `munder_difflin.db`)
* **APIs:** OpenAI (optional — OpenAI key used for NLP helpers)
* **Dependencies:** See `requirements.txt`

---

## ⚙️ Installation & Setup

**1. Clone the repository**

```bash
git clone https://github.com/AmrShams9/Beaver-s-Choice_Multi-Agent-System.git
cd Beaver-s-Choice_Multi-Agent-System
```

**2. (Recommended) Create and activate a virtual environment**

```bash
python -m venv venv
# macOS / Linux
source venv/bin/activate
# Windows (PowerShell)
venv\Scripts\Activate.ps1
# Windows (cmd)
venv\Scripts\activate
```

**3. Install dependencies**

```bash
pip install -r requirements.txt
```

**4. Configure environment variables**

Create a `.env` file in the project root with your API keys (example):

```env
OPENAI_API_KEY=your_api_key_here
```

**5. Run the system**

```bash
python main.py
```

---

## 🚀 Usage

* Run `python main.py`.
* Enter a natural-language customer request when prompted (example: `I need 50 sheets of heavy cardstock`).
* The system will produce one of:

  * ✅ **Successful order confirmation** (order ID, totals, and inventory update)
  * ⚠️ **Clarification request** (when items are ambiguous or unknown)
  * ❌ **Error message** (stock/delivery issues or validation failures)

**Example interaction**

```
> "I need 200 A4 heavy cardstock"
> [Extraction Agent] -> ParsedRequest: {"item":"heavy cardstock","qty":200, ...}
> [Catalog Matcher] -> matched: "Heavy Cardstock (A4, 200gsm)"
> [Inventory Agent]  -> stock: 150 (supplier ETA: 2025-10-02)
> [Quoting Agent]    -> quote: subtotal, discounts, total
> [Transaction Agent] -> either finalize or request clarification
```

---

## 🏗️ System Architecture / Workflow

1. **Request → Orchestration Agent**: triggers the pipeline.
2. **Extraction Agent**: turns text into `ParsedRequest` JSON.
3. **Catalog Matcher**: normalization & synonym resolution.
4. **Inventory Agent**: checks stock & supplier delivery windows.
5. **Quoting Agent**: price calculation, discounts, loyalty handling.
6. **Transaction Agent**: finalize order and update DB or return an error/clarification.

---

## 🧪 Testing & Results

The system was tested with **20+ customer requests**.

| Request IDs        | Outcome                 | Notes                                                              |
| ------------------ | ----------------------- | ------------------------------------------------------------------ |
| 4, 6, 7, 8, 10–12  | ✅ Successful Orders     | Discounts applied, inventory/cash updated.                         |
| 1, 2, 5, 14, 15,20 | ⚠️ Clarification Needed | Ambiguous items (e.g., "heavy cardstock") triggered suggestions.   |
| 3, 9, 13, 16–19    | ❌ Ordering Errors       | Insufficient stock or delivery conflicts; no fallback suggestions. |

---

## ✅ Submission Checklist

* [x] Code documented with inline comments and docstrings.
* [x] README with project overview, setup, usage, and architecture.
* [x] Workflow diagram (`beaverChoice.png`) included.
* [x] Test results documented (`test_results.csv`).
* [x] Reflection report included.

---

## ✨ Reflection & Future Work

**Test Results Reflection**

* Reliable for straightforward orders.
* Ambiguous terms often required clarifications (expand synonyms).
* Stock/delivery validation worked but lacked fallback handling.

**Architectural Decisions**

* Chosen pattern: modular agent pipeline for separation of concerns.
* Trade-off: simple 5-agent pipeline for clarity; could be specialized further.

**Improvements**

* Expand synonym dictionary and catalog coverage.
* Add fallback strategies (partial fulfillment, substitutions, smaller quantities).
* Dynamic pricing policies (loyalty tiers, seasonal promos).
* Move to a production-grade DB for concurrency and scaling.
* Add an audit/logging service for better observability.

---

## 📷 Screenshots

![System Test Screenshot](Screenshot%202025-09-28%20175831.png)

> If the screenshot image does not appear on GitHub, rename it to `test_screenshot.png` and replace the link above with `test_screenshot.png`.

---

## 📌 License

Include a license here if desired (e.g., MIT).

---

If you want, I can also:

* Rename the screenshot file and update the repo commands to commit the rename.
* Produce a shorter one-page README summary for GitHub's front page.
* Add a `Tech Stack` badge section or `Contributing` guidelines.
