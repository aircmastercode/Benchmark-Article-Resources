# ORMCP Benchmark Prompts (Session-wise)

Use one prompt per fresh chat session. Do not combine tasks in the same session.

For any quarter-style request, use this fixed window and label it exactly as:
- **Q3 2025 analysis window** = `orderdate >= 2025-07-01` and `orderdate <= 2025-09-30` (inclusive).

---

## Session 1 - Task A (Known customer baseline)

You are connected to the ecommerce Gilhari microservice via ORMCP (object-level tools and resources).  
Optimize for end-to-end efficiency: choose the retrieval strategy that minimizes total round-trips while preserving correctness and the required details.

Task:
- Customer primary key `id = 2`.
- Return a full, human-readable details of this customer:
  - profile
  - addresses
  - orders in the `orderdate >= 2025-07-01` and `orderdate <= 2025-09-30` (inclusive).
  - line items for those Q3 orders

End with the following information:
1. tools/resources used (in order)  
2. approximate number of round-trips  
3. anything you intentionally avoided to reduce token use

---

## Session 2 - Task B (Discovery then deep customer)

You are connected to the ecommerce Gilhari microservice via ORMCP (object-level tools and resources).  
Optimize for end-to-end efficiency: choose the retrieval strategy that minimizes total round-trips while preserving correctness and the required details.

Task:
- Consider only `CustomerOrder` objects in the `orderdate >= 2025-07-01` and `orderdate <= 2025-09-30` (inclusive).
- In the `orderdate >= 2025-07-01` and `orderdate <= 2025-09-30` (inclusive), find the order with highest `totalamount` (tie-break: smallest order id).
- Then return the full graph for the customer who placed that order:
  - profile
  - related addresses
  - orders in the `orderdate >= 2025-07-01` and `orderdate <= 2025-09-30` (inclusive)
  - associated line items for those Q3 orders

End with the following information:
1. tools/resources used (in order)  
2. approximate number of round-trips  
3. anything you intentionally avoided to reduce token use

---

## Session 3 - Task C (Shallow ranking)

You are connected to the ecommerce Gilhari microservice via ORMCP (object-level tools and resources).  
Optimize for end-to-end efficiency: choose the retrieval strategy that minimizes total round-trips while preserving correctness and the required details.

Task:
- Produce top 10 customers by `totalspent` descending.
- Include only: `id`, `email`, `firstname`, `lastname`, `totalspent`, `tier`.
- Briefly note whether the tool supported narrow projection directly, or if a wider fetch had to be trimmed.

End with the following information:
1. tools/resources used (in order)  
2. approximate number of round-trips  
3. anything you intentionally avoided to reduce token use

---

## Session 4 - Task D (Deep query for multiple customers)

You are connected to the ecommerce Gilhari microservice via ORMCP (object-level tools and resources).  
Optimize for end-to-end efficiency: choose the retrieval strategy that minimizes total round-trips while preserving correctness and the required details.

Task:
- Customers with primary key id in `{2, 8, 13}`.
- Return a full, human-readable details for all those customers including:
  - profile
  - addresses
  - orders in the `orderdate >= 2025-07-01` and `orderdate <= 2025-09-30` (inclusive) only
  - associated line items for those orders

End with the following information:
1. tools/resources used (in order)  
2. approximate number of round-trips  
3. anything you intentionally avoided to reduce token use