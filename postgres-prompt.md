# Postgres MCP Benchmark Prompts (Session-wise)

Use one prompt per fresh chat session. Do not combine tasks in the same session.

You are connected to PostgreSQL via Postgres MCP 

For any quarter-style request, use this fixed window and label it exactly as:
- **Q3 2025 analysis window** = `customerorder.orderdate >= '2025-07-01'` and `customerorder.orderdate <= '2025-09-30'` (inclusive).

General efficiency rules:
- Prefer explicit column lists.
- Avoid `SELECT *` unless explicitly required for comparison.
- Use CTEs, JOINs or controlled subqueries if deemed efficient.
- Minimize total round-trips while preserving correctness and the required details.
- Show the SQL statements you executed.

---

## Session 1 - Task A (Known customer baseline)
You are connected to PostgreSQL via Postgres MCP 

General efficiency rules:
- Prefer explicit column lists.
- Avoid `SELECT *` unless explicitly required for comparison.
- Use CTEs, JOINs or controlled subqueries if deemed efficient.
- Minimize total round-trips while preserving correctness and the required details.
- Show the SQL statements you executed.

Task:
- `customer.id = 2`.
- Return a full, human-readable details of this customer:
  - profile
  - addresses
  - orders in the Q3 2025 analysis window.
  - line items for those Q3 orders

End with the following information:
1. tools/resources used (in order)
2. SQL statements executed (in order)  
3. why you chose that query shape

---

## Session 2 - Task B (Discovery then deep customer)
You are connected to PostgreSQL via Postgres MCP 

General efficiency rules:
- Prefer explicit column lists.
- Avoid `SELECT *` unless explicitly required for comparison.
- Use CTEs, JOINs or controlled subqueries if deemed efficient.
- Minimize total round-trips while preserving correctness and the required details.
- Show the SQL statements you executed.

Task:
- In the `customerorder.orderdate >= '2025-07-01'` and `customerorder.orderdate <= '2025-09-30'` (inclusive), find the `customerorder` with maximum `totalamount` (tie-break: smallest `id`).
- Then return the full graph for the customer who placed that order:
  - profile
  - related addresses
  - orders in the Q3 2025 analysis window only
  - associated line items for those Q3 orders

End with the following information:
1. tools/resources used (in order)
2. SQL statements executed (in order)  
3. why you chose that query shape

---

## Session 3 - Task C (Shallow ranking)
You are connected to PostgreSQL via Postgres MCP 

General efficiency rules:
- Prefer explicit column lists.
- Avoid `SELECT *` unless explicitly required for comparison.
- Use CTEs, JOINs or controlled subqueries if deemed efficient.
- Minimize total round-trips while preserving correctness and the required details.
- Show the SQL statements you executed.

Task:
- Produce top 10 customers by `customer.totalspent` descending.
- Select only these columns: `id`, `email`, `firstname`, `lastname`, `totalspent`, `tier`.
- Add one short paragraph: what would change if `SELECT *` had been used on `customer` instead.

End with the following information:
1. tools/resources used (in order)
2. SQL statements executed (in order)  
3. why you chose that query shape

---

## Session 4 - Task D (Deep query for multiple customers)
You are connected to PostgreSQL via Postgres MCP 

General efficiency rules:
- Prefer explicit column lists.
- Avoid `SELECT *` unless explicitly required for comparison.
- Use CTEs, JOINs or controlled subqueries if deemed efficient.
- Minimize total round-trips while preserving correctness and the required details.
- Show the SQL statements you executed.

Task:
- Customers with id in `{2, 8, 13}`.
- Return a full, human-readable details for all those customers including:
  - profile
  - addresses
  - orders in the `orderdate >= 2025-07-01` and `orderdate <= 2025-09-30` (inclusive) only
  - associated line items for those orders

End with the following information:
1. tools/resources used (in order)
2. SQL statements executed (in order)  
3. why you chose that query shape