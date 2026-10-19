# SQL Problem Solving Guide

Use this approach across all SQL Mastery sections.

**Decide what your data should look like at each step before writing the query.**

Follow this sequence for every problem:

1. **Define the final output clearly.**

   Complete this sentence: **"One row in my answer represents ___."**

   It could represent an employee, a department, a transaction, or a month. Then identify the required columns, sorting, and any rules for ties.

   This decision guides your entire query.

2. **Understand the input tables.**

   Identify what one row represents in each table, which columns uniquely identify it, and how the tables connect.

   Pay attention to duplicates, missing values, and whether matching records are guaranteed. These details affect which rows your query includes and how many times it counts them.

3. **Write the logic in plain English.**

   Describe the work as small steps, such as:

   ```text
   Get the relevant records.
   Attach the information I need.
   Calculate the required value.
   Keep the qualifying results.
   Arrange the output.
   ```

   Write mathematical formulas separately. For an average or percentage, explicitly identify **the numerator and denominator**. For a comparison, identify **what is being compared with what**.

4. **Choose SQL operations based on what must happen to the rows.**

   | What you need to do | SQL tool to consider |
   |---|---|
   | Attach information from another table | `JOIN` |
   | Keep individual rows meeting a condition | `WHERE` |
   | Assign a value based on conditions | `CASE` |
   | Combine rows into one summary per group | `GROUP BY` with aggregates |
   | Filter calculated group results | `HAVING` |
   | Rank or calculate across rows while keeping individual rows | Window functions |
   | Check whether a related record exists | `EXISTS` / `NOT EXISTS` |
   | Build a result in understandable stages | CTE or subquery |

   **Grouping reduces rows into summaries; window functions retain the individual rows.**

5. **Plan the intermediate results.**

   For each stage, write down the columns you need and what one row represents.

   Every CTE or subquery should have a clear purpose, such as "total per department" or "latest record per employee."

   If you cannot explain what an intermediate result contains, clarify that before adding more SQL.

6. **Build and inspect the query in small pieces.**

   Start with the necessary rows and columns. Add joins, calculations, grouping, and filtering gradually.

   **Inspect the result immediately after a join.** A row matching several records produces several joined rows. That may be required, or it may incorrectly inflate your totals.

   At every step, check: "Are these the rows I expected, and does each row still mean what I think it means?"

7. **Check correctness beyond the sample output.**

   Review these common traps:

   - **Duplicates:** should repeated records count separately?
   - **Missing matches:** must records with no activity still appear?
   - **NULLs:** `COUNT(column)` skips them; `COUNT(*)` counts rows.
   - **Arithmetic:** check parentheses, decimal division, and zero denominators.
   - **Boundaries:** distinguish `>` from `>=`, and check date endpoints.
   - **Ties:** decide whether all tied results should be included.
   - **Ordering:** specify it when the question requires it.

Before coding, fill in this short planning template:

```text
One output row represents:
Required input records:
Information I need to join:
Calculation:
Grouping or ranking:
Condition for keeping results:
Required ordering:
```

When you get stuck, identify **which line of this plan you cannot complete**. Work on that specific decision. After receiving a hint, write and inspect the next small piece yourself. This is how the approach becomes familiar enough to use independently.
