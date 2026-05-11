# QTAC Data Engineer – Technical Assessment

## Hey there!

Thanks for making it this far — we're excited to see what you can do. This is a take-home exercise that reflects the kind of work we do day-to-day at QTAC. 

**Deadline:** 5 days from when you receive this.  
**Expected effort:** 2-3 hours. We're not looking for a production-ready system — focus on demonstrating your thinking.  
**Tools:** Use whatever SQL database engine you're comfortable with (SQL Server, PostgreSQL, DuckDB, SQLite). 

---

## The Scenario

QTAC runs the centralised tertiary admissions system for Queensland. Students apply for uni courses through us, and we manage preferences, offers, and all the data that goes with it.

You've been handed some source data extracts from our application system:

| File | What's in it |
|------|-------------|
| `applicants.csv` | Applicant records (the initial load) |
| `applicants_update.csv` | A later extract with new and changed applicants |
| `courses.csv` | Course offerings from partner institutions |
| `qualifications.csv` | Applicant qualifications (Year 12, diplomas, degrees, etc.) |
| `preferences.csv` | What courses applicants applied for and what happened |

**Fair warning:** The data is messy. That's intentional — real source systems are never clean. Part of the exercise is spotting the issues and deciding what to do about them.

---

## What We'd Like You To Do

### 1. Have a Look Around (Data Profiling)

Explore the source data and tell us:
- What data quality issues did you spot?
- How would you handle each one in a production pipeline?
- What assumptions are you making?

### 2. Design a Data Model

Design a warehouse model to store this data. You can choose either:

- **Kimball dimensional model with SCD Type 2** (slowly changing dimensions), OR
- **Data Vault 2.0** (hubs, links, satellites)

Pick whichever you're more comfortable with — or whichever you think fits better. Give us:
- A diagram or written description of your model
- DDL scripts to create the tables
- A quick explanation of why you went that way

### 3. Load the Data

Write SQL to:

1. Load the initial `applicants.csv` into your model
2. Apply `applicants_update.csv` — show us how you handle changes, new records, and duplicates
3. Load at least one other entity (courses, qualifications, or preferences)

This is where we want to see your SCD2 versioning or Data Vault satellite logic in action.

### 4. Build an Output

Write a query or view that produces a summary showing:
- Applicant name and state
- The course they accepted an offer for (highest preference if multiple - Lowest preference_order = highest preference)
- Institution name
- Their qualification type and ATAR score (if they have one)

Think of this as a "Gold layer" or information mart table — something a business user could consume.

---

## What to Send Back

We're primarily interested in your **final table structures and the data in them** after your ingestion has run. We want to see the end result of your thinking.

1. **CSV exports of your final warehouse tables** — This is the most important part. Show us what your tables look like after the data has been loaded and transformed.
2. **SQL scripts** — Your DDL and DML so we can see your approach (we won't be running these in an engine — we're reading them for logic and thought process)
3. **A README** — covering:
   - What approach you chose and why
   - Data quality issues you found
   - Assumptions you made
   - Your ingestion path / load sequence explained
4. **Bonus points (totally optional):**
   - Data quality tests or assertions
   - A Git repo with meaningful commits (we like seeing how you work)
   - A model diagram

**Send it as:** A Git repo link or a `.zip` file via email.

---

## How We'll Assess It

We're not looking for perfection — we're looking for good thinking.

| What we're looking at | Weight | What impresses us |
|----------------------|--------|-------------------|
| Final Table Output | 30% | Your tables contain the right data, correctly versioned, after the full load |
| Model Design | 25% | Sensible structure that handles change over time |
| Thought Process & SQL Logic | 20% | Clean approach, handles edge cases, shows your reasoning |
| Data Quality Awareness | 15% | You spotted the traps and had a plan for them |
| Documentation | 10% | We can understand your thinking without a phone call |

**Bonus love for:**
- Data quality tests
- Incremental/idempotent patterns
- Git with real commit messages (not just "final version v3 FINAL")
- A model diagram

---

## A Few Last Things

- There's no single "right" answer. We care about your approach and reasoning.
- You don't need to fix every data issue — but we want to see that you noticed them.
- If something in the brief is unclear, email us and ask.

Have fun with it, and good luck!
