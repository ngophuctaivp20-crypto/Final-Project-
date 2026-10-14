# Final-Project-
💰 Savings Goal Coach

A finance assistant that helps users set savings goals, track their progress, understand where their money goes, and get practical tips to save more through AI collaboration. 


## Project overview

Everything is in **one notebook**, `Saving Goal Coach Final Project`. It has 9 code cells, each under a heading. Cells 2–7 only create functions, so they print nothing (except a short message about the Gemini key in cell 2). The tests and the app are separate cells at the end.

| Cell | Heading in the notebook | What it does |
|---|---|---|
| 1 | *-Pips-Gradio Pandas requests-* | Installs the libraries: `gradio`, `pandas`, `requests` |
| 2 | **1. Imports and settings** | Imports libraries, sets the website addresses and category tips, reads the Gemini key |
| 3 | **2. My custom tool: the savings-goal calculator** | `savings_goal_calculator` and the optional text calculator |
| 4 | **3. Goals (nested dictionaries)** | Functions to add goals, add money, and show progress |
| 5 | **4. pandas: reading the CSV** | Loads the CSV, works out income, spending and savings tips |
| 6 | **5. `requests`: currency converter and Gemini chat with custom tools** | Currency converter, the custom tools, Gemini chat, offline coach |
| 7 | **6. Sample data** | Function that creates `sample_transactions.csv` |
| 8 | **7. Tests with `assert`** | Runs all the tests and prints `✅ All tests passed` |
| 9 | **8. Gradio app** | Builds the interface and **starts the app** |

---

## How to run it

**Quick way:**
1. Open `Saving Goal Coach Final Project` in Google Colab (or click the "Open in Colab" button at the top).
2. *(Optional, for the Gemini chat)* Add your key in Colab's 🔑 **Secrets** panel with the name `GEMINI_API_KEY`, and turn on notebook access.
3. Run **cell 1** (under the title) to install the libraries. You only need to do this once per Colab session.
4. Run the cells under headings **1** to **8**, in order. Each cell uses functions from the cells above it, so the order matters.
5. Gradio app** will appear at cell 8 to start the application.

**Using the app:**
- **Goals** tab: add a goal, then add money to it.
- **Calculator** tab: enter a goal amount, the money already saved and the months.
- **Spending** tab: click **Use sample data**, or upload `student_transactions.csv` from your computer and click **Load my CSV**.
- **Currency** tab: enter an amount and two currency codes, e.g. USD and AUD.
- **Coach** tab: ask a question, e.g. "How are my goals going?" Without a Gemini key it uses the offline coach.

**Good to know:**
- The last cell keeps showing **"Executing"** while the app is open. This is normal. Click ■ to stop the app.
- To change the code, stop the app, edit the cell, then run that cell and the **8. Gradio app** cell again.

## What it does

| Feature | Description |
|---|---|
| **Goals** | Add savings goals (e.g. "Laptop: $2000 in 10 months"), add or take out money, and see your progress and status |
| **Calculator** | My custom tool: enter a goal, the money already saved and the months, and get how much to save each month and each week |
| **Spending** | Upload a CSV of your transactions to see spending by category, money left over each month, and tips to save more |
| **Currency** | Convert money between currencies using live exchange rates |
| **Coach** | Chat with a Gemini-powered coach that uses custom tools to get real numbers instead of guessing |

## Files

| File | What it is |
|---|---|
| `Saving Goal Coach Final Project` | The main notebook (all the code) |
| `sample_transactions.csv` | Small test data: 21 transactions over 3 months |
| `student_transactions.csv` | More realistic test data: 67 transactions over 3 months |
| `README.md` | This file |
|`Developer's Diary`|showing the learning progress of each coding concept
|`my_transactions.csv`|transaction data and income|
## Sample input and output

### 1. Calculator tab (my custom tool)

**Input:**

| Goal amount | Already saved | Months |
|---|---|---|
| 3000 | 600 | 8 |

**Output:**
```
You still need $2400.00 (20.0% done).
Save $300.00 a month, which is about $69.23 a week.
```

### 2. Goals tab

**Input:** Goal name `Laptop`, target `2000`, months `10`, already saved `100`

**Output:**
```
Added Laptop. Save $190.00 each month.
```

| Goal | Target | Saved | Percent | Per month | Status |
|---|---|---|---|---|---|
| Laptop | 2000.0 | 100.0 | 5.0 | 190.0 | Started |

### 3. Spending tab

**Input:** click **Use sample data** (or upload `sample_transactions.csv`)

**Output:**
```
Loaded 21 transactions.

Money left over each month: $786.00
Your goals need: $190.00 a month
Good news: you can afford your goals!

Ideas to save more:
- Groceries: save about $37.00 a month. Plan meals and shop with a list.
- Dining Out: save about $46.50 a month. Cook at home more often.
- Subscriptions: save about $33.50 a month. Cancel the ones you don't use.
- Entertainment: save about $21.75 a month. Look for free events and student discounts.
- Shopping: save about $34.50 a month. Wait 48 hours before buying something.
```

### 4. Currency tab

**Input:** amount `100`, from `USD`, to `AUD`

**Output** (the rate is live, so the number changes each day):
```
100.0 USD = 152.3 AUD
```

### 5. Coach tab

**Input:**
```
I want $3000 in 8 months and I have $600. How much should I save?
```

**What happens:** Gemini asks for the `calculate_plan` tool, and Colab prints:
```
Tool used: calculate_plan -> {'remaining': 2400.0, 'per_month': 300.0, 'per_week': 69.23, 'percent_done': 20.0}
```

**Output** (Gemini's wording can change each time):
```
You need to save $300 a month (about $69 a week) to reach your $3000 goal in 8 months. You're already 20% of the way there!
```

**Offline mode** (no API key), input `How are my goals?`:
```
Laptop: 5.0% done, Started, save $190.00 a month
```

## Python features used

- Variables, `if` / `elif` / `else`, `and`, `or`, `in`, `not in`
- Loops: `for ... in ...`, `for i in range(...)`, `while`, `break`, `continue`
- Functions with `def` and `return`, plus `input()`, `float()`, `len`, `max`, `min`, `round`
- Lists and dictionaries, including nested ones; `.get`, `.items`, `.values`
- Error handling with `try` / `except`
- **pandas** for reading and analysing the CSV
- **requests** for the Frankfurter currency API and the Gemini API
- **Gradio** for the interface
- **assert** for testing
