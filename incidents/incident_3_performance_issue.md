# Incident 3: Slow Application Performance

## Issue
Users report that the application is slow when loading order data.

## Impact
- Increased response time
- Poor user experience
- Delay in accessing order information

## Investigation
- Checked database query performance
- Identified that queries on the orders table were taking too long
- Observed missing indexing on frequently queried columns

## SQL Used
-- Check execution on orders table
SELECT * FROM orders WHERE user_id = 1;

-- Analyze query performance (conceptual)
EXPLAIN SELECT * FROM orders WHERE user_id = 1;

## Root Cause
No index on user_id column in orders table, causing full table scan.

## Resolution
Created index to optimize query performance:

CREATE INDEX idx_user_id ON orders(user_id);

## Outcome
- Query execution time improved significantly
- Application performance stabilized

## ITIL Mapping
- Incident Type: Performance Issue
- Process: Incident Management → Problem Management
