# Incident 4: Order Not Processing

## Issue
Users report that orders are not being processed after submission.

## Impact
- Orders remain in "pending" state
- Business transactions are delayed
- Customer dissatisfaction

## Investigation
- Checked orders table for status
- Found multiple orders stuck in 'pending'
- Verified related user account status

## SQL Used
-- Find pending orders
SELECT * FROM orders WHERE status = 'pending';

-- Check related user accounts
SELECT u.username, u.status, o.status
FROM users u
JOIN orders o ON u.id = o.user_id
WHERE o.status = 'pending';

## Root Cause
Orders linked to inactive users were not being processed.

## Resolution
- Activated affected user accounts:
UPDATE users SET status = 'active' WHERE id = 2;

- Updated order status:
UPDATE orders SET status = 'completed' WHERE user_id = 2;

## Outcome
- Orders processed successfully
- System functionality restored

## ITIL Mapping
- Incident Type: Functional Failure
- Process: Incident Management
