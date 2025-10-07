<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>BeaverChoice – Multi-Agent Order Processing System</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      margin: 40px auto;
      max-width: 900px;
      padding: 0 20px;
      background: #f9fafc;
      color: #222;
    }
    h1, h2, h3, h4 {
      color: #333;
    }
    code {
      background: #f4f4f4;
      padding: 2px 5px;
      border-radius: 4px;
      font-family: monospace;
    }
    pre {
      background: #2d2d2d;
      color: #f8f8f2;
      padding: 12px;
      border-radius: 6px;
      overflow-x: auto;
    }
    img {
      max-width: 100%;
      border-radius: 6px;
      margin: 10px 0;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 20px 0;
    }
    table th, table td {
      border: 1px solid #ccc;
      padding: 8px;
      text-align: left;
    }
    table th {
      background: #eee;
    }
    .checklist li {
      margin: 6px 0;
    }
    .checklist li::before {
      content: "✔ ";
      color: green;
    }
    .section {
      margin-top: 40px;
    }
  </style>
</head>
<body>

  <h1>🦫 BeaverChoice – Multi-Agent Order Processing System</h1>

  <div class="section">
    <h2>📖 Project Overview</h2>
    <img src="Screenshot%202025-09-28%20175831.png" alt="System Test Screenshot">
    <p><strong>BeaverChoice</strong> is a multi-agent order processing system that simulates real-world workflows for handling customer requests. 
    It uses a <strong>modular agent-based architecture</strong> to process orders from request to transaction, ensuring <strong>scalability, maintainability, and extensibility</strong>.</p>
  </div>

  <div class="section">
    <h2>🧩 Agents in the System</h2>
    <img src="beaverChoice.png" alt="BeaverChoice Workflow">
    <ul>
      <li><strong>Extraction Agent</strong> – Parses raw customer requests.</li>
      <li><strong>Catalog Matcher</strong> – Maps parsed items to known catalog entries.</li>
      <li><strong>Inventory Agent</strong> – Checks stock availability and supplier delivery.</li>
      <li><strong>Quoting Agent</strong> – Calculates prices, discounts, and totals.</li>
      <li><strong>Transaction Agent</strong> – Finalizes successful orders and updates cash/inventory.</li>
    </ul>
  </div>

  <div class="section">
    <h2>🎯 Objectives</h2>
    <ul>
      <li>Automate customer order handling.</li>
      <li>Validate catalog items, stock, and delivery feasibility.</li>
      <li>Apply business logic (discounts, loyalty rewards).</li>
      <li>Provide clarifications when orders are ambiguous.</li>
      <li>Demonstrate the multi-agent system design pattern.</li>
    </ul>
  </div>

  <div class="section">
    <h2>⚙️ Installation & Setup</h2>

    <h3>1. Clone the Repository</h3>
    <pre><code>git clone https://github.com/AmrShams9/Beaver-s-Choice_Multi-Agent-System.git
cd Beaver-s-Choice_Multi-Agent-System</code></pre>

    <h3>2. Create a Virtual Environment (Recommended)</h3>
    <pre><code>python -m venv venv
source venv/bin/activate   # On macOS/Linux
venv\Scripts\activate      # On Windows</code></pre>

    <h3>3. Install Dependencies</h3>
    <pre><code>pip install -r requirements.txt</code></pre>

    <h3>4. Configure Environment Variables</h3>
    <pre><code>OPENAI_API_KEY=your_api_key_here</code></pre>

    <h3>5. Run the System</h3>
    <pre><code>python main.py</code></pre>
  </div>

  <div class="section">
    <h2>🚀 Usage Guidelines</h2>
    <p>Enter a customer request (e.g., <em>“I need 50 sheets of heavy cardstock”</em>). The agents will process the request step by step.</p>
    <ul>
      <li>✅ Successful order confirmation</li>
      <li>⚠️ Clarification request</li>
      <li>❌ Error message (stock/delivery issue)</li>
    </ul>
  </div>

  <div class="section">
    <h2>🏗️ System Architecture</h2>
    <ol>
      <li><strong>Request → Orchestration Agent</strong> – Starts the pipeline.</li>
      <li><strong>Extraction Agent</strong> – Converts text into structured JSON (<code>ParsedRequest</code>).</li>
      <li><strong>Catalog Matcher</strong> – Normalizes items against the catalog.</li>
      <li><strong>Inventory Agent</strong> – Validates stock & supplier delivery.</li>
      <li><strong>Quoting Agent</strong> – Applies discounts, prepares order summary.</li>
      <li><strong>Transaction Agent</strong> – Finalizes transactions or raises errors.</li>
    </ol>
  </div>

  <div class="section">
    <h2>🧪 Testing & Results</h2>
    <p>The system was tested with <strong>20+ customer requests</strong>:</p>
    <table>
      <tr>
        <th>Request IDs</th>
        <th>Outcome</th>
        <th>Notes</th>
      </tr>
      <tr>
        <td>4, 6, 7, 8, 10–12</td>
        <td>✅ Successful Orders</td>
        <td>Discounts applied, inventory/cash updated.</td>
      </tr>
      <tr>
        <td>1, 2, 5, 14, 15, 20</td>
        <td>⚠️ Clarification Needed</td>
        <td>Ambiguous items (e.g., “heavy cardstock”) triggered suggestions.</td>
      </tr>
      <tr>
        <td>3, 9, 13, 16–19</td>
        <td>❌ Ordering Errors</td>
        <td>Insufficient stock or delivery conflicts. No fallback suggestions.</td>
      </tr>
    </table>
  </div>

  <div class="section">
    <h2>✅ Submission Checklist</h2>
    <ul class="checklist">
      <li>Code documented with inline comments and docstrings.</li>
      <li>Project overview, setup, usage, and architecture documented.</li>
      <li>Workflow diagram (<code>beaverChoice.png</code>) included.</li>
      <li>Test results documented.</li>
      <li>Reflection Report included.</li>
    </ul>
  </div>

  <div class="section">
    <h2>✨ Reflection Report</h2>

    <h3>🧪 Test Results Reflection</h3>
    <ul>
      <li>Reliable for straightforward orders.</li>
      <li>Ambiguous terms often required clarifications.</li>
      <li>Stock/delivery validation worked well but lacked fallback handling.</li>
    </ul>

    <h3>🏗️ Architectural Decisions</h3>
    <ul>
      <li>Modular agent pipeline (Extraction → Catalog → Inventory → Quoting → Transaction).</li>
      <li><strong>Trade-off:</strong> Limited to 5 agents → simplicity vs. specialization.</li>
      <li>Centralized catalog normalization.</li>
      <li>Strong delivery & stock validation rules.</li>
    </ul>

    <h3>💡 Improvement Suggestions</h3>
    <ul>
      <li>Expand synonym dictionary to reduce clarifications.</li>
      <li>Add fallback handling (smaller quantities, substitutions).</li>
      <li>Support dynamic pricing (loyalty, seasonal promotions).</li>
      <li>Upgrade to production-grade database for scalability.</li>
      <li>Integrate customer feedback loop for clarifications.</li>
    </ul>

    <h3>⚖️ Strengths & Weaknesses</h3>
    <p><strong>Strengths:</strong></p>
    <ul>
      <li>✔ Modular, extensible architecture</li>
      <li>✔ Smooth integration of quoting & transaction logic</li>
      <li>✔ Robust clarification mechanism</li>
      <li>✔ Discounts & financial updates applied consistently</li>
    </ul>
    <p><strong>Weaknesses:</strong></p>
    <ul>
      <li>✘ High reliance on clarifications</li>
      <li>✘ No fallback handling for failed orders</li>
      <li>✘ Strict delivery checks (no partial fulfillment)</li>
      <li>✘ Scalability concerns with large catalogs</li>
    </ul>
  </div>

  <div class="section">
    <h2>📌 Conclusion</h2>
    <p><strong>BeaverChoice</strong> demonstrates a <strong>functional, modular, and extensible multi-agent architecture</strong> for order processing. 
    It successfully handles realistic workflows but needs improvements in <strong>catalog matching, fallback handling, and scalability</strong> to reach production-level robustness.</p>
  </div>

</body>
</html>
