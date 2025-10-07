🦫 BeaverChoice – Multi-Agent Order Processing System
📖 Project Overview

BeaverChoice is a multi-agent order processing system that simulates a real-world workflow for handling customer requests. It uses a modular agent-based architecture to process orders from request to transaction, ensuring scalability, maintainability, and extensibility.

The system includes:

Extraction Agent – parses raw customer requests.

Catalog Matcher – maps parsed items to known catalog entries.

Inventory Agent – checks stock availability and supplier delivery.

Quoting Agent – calculates prices, discounts, and totals.

Transaction Agent – finalizes successful orders and updates cash/inventory.

🎯 Objectives

Automate customer order handling.

Validate catalog items, stock, and delivery feasibility.

Apply business logic (discounts, loyalty rewards).

Provide clarifications when orders are ambiguous.

Demonstrate the multi-agent system design pattern.

⚙️ Setup Instructions
1. Clone Repository
git clone https://github.com/yourusername/beaverchoice.git
cd beaverchoice

2. Install Dependencies
pip install -r requirements.txt

3. Environment Variables

Create a .env file and add your keys:

OPENAI_API_KEY=your_api_key_here

4. Run the System
python main.py

🚀 Usage Guidelines

Enter a customer request (e.g., “I need 50 sheets of heavy cardstock”).

The agents will process the request step by step.

The system will return one of:

✅ A successful order confirmation.

⚠️ A clarification request.

❌ An error message with reason (stock/delivery issue).

🏗️ System Architecture

The workflow is illustrated below:

Flow Explanation:

Request → Orchestration Agent – starts the pipeline.

Extraction Agent – converts text into structured JSON (ParsedRequest).

Catalog Matcher – ensures item normalization against known catalog.

Inventory Agent – validates stock & supplier delivery.

Quoting Agent – applies discounts, prepares order summary.

Transaction Agent – finalizes successful transactions or raises errors.

🧪 Testing & Results

The system was tested with 20+ customer requests.

Request IDs	Outcome	Notes
4, 6, 7, 8, 10, 11, 12	✅ Successful Orders	Orders processed correctly, discounts applied, inventory/cash updated.
1, 2, 5, 14, 15, 20	⚠️ Clarification Required	Unknown/ambiguous items triggered clarification (e.g., “heavy cardstock”, “poster paper”). System suggested alternatives.
3, 9, 13, 16–19	❌ Ordering Errors	Orders failed due to insufficient stock or delivery date conflicts. Errors were flagged, but no fallback suggestions provided.
✅ Submission Checklist

 Code documented with inline comments and docstrings.

 README with project overview, setup, usage, and architecture.

 Workflow diagram (beaverChoice.png).

 Test results documented.

 Reflection Report (below).

✨ Section 6: Reflection Report
🧪 Test Results Reflection

Reliable for straightforward orders.

Ambiguous terms caused frequent clarifications (limited synonym coverage).

Stock/delivery validation worked but lacked fallback suggestions.

🏗️ Architectural Decisions

Modular agent-based pipeline (Extraction → Catalog → Inventory → Quoting → Transaction).

Trade-off: Limited to 5 agents → simplicity vs. specialization.

Catalog Matcher centralizes normalization.

Inventory checks enforce stock & supplier delivery rules.

💡 Improvement Suggestions

Expand synonym dictionary to reduce clarifications.

Provide fallbacks (smaller quantities, substitutions).

Add dynamic pricing policies (loyalty, seasonal promotions).

Upgrade to a production-grade database for scalability.

Integrate customer feedback loop on clarifications.

⚖️ Strengths & Weaknesses

Strengths

Modular, extensible architecture.

Smooth integration of inventory, quoting, and transaction logic.

Robust clarification mechanism.

Discounts & financial updates applied consistently.

Weaknesses

High reliance on clarifications.

No fallback handling for failed orders.

Strict delivery checks (no partial fulfillment).

Scalability concerns with large catalogs.

📌 Conclusion

BeaverChoice demonstrates a functional, modular, and extensible multi-agent architecture for order processing. The system succeeds in handling realistic workflows but requires enhancements in catalog matching, fallback handling, and scalability to reach production-level robustness.