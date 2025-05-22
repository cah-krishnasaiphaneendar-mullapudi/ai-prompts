# System Architecture Design Request: Order Allocation Planning with Historical Tracking

## Context
I'm developing an order allocation planning feature that needs to maintain historical snapshots and audit trails. The system integrates with SAP for allocation confirmations and shipping updates.

## Current System Flow
1. **Initial State**: Customer orders exist in the system
2. **Allocation Decision**: Business team allocates orders based on inventory
3. **Pending Allocation**: Units move to "Pending Allocation" column in database
4. **SAP Integration**: Application sends allocation request to SAP
5. **Allocation Confirmation**: SAP confirms allocation, units move to "Allocated" column
6. **Shipping Update**: SAP sends shipping confirmation, units move to "Shipped" column

## Database Schema (Current)
```
Orders Table:
- pending_allocation (units)
- allocated (units) 
- shipped (units)
```

## Requirements
- **Snapshot Capability**: When allocation planning feature is used, create snapshots instead of overwriting data
- **Historical Tracking**: Preserve transactional data to enable trend analysis
- **Audit Trail**: Users should be able to trace back through allocation decisions and see progression over time
- **Data Integrity**: Maintain consistency between planning snapshots and actual SAP integration

## Specific Questions
1. What design patterns are most suitable for this historical tracking requirement?
2. How should I structure the database to efficiently store snapshots while maintaining query performance?
3. What architectural patterns would best handle the dual nature of planning (snapshots) vs. actual execution (SAP integration)?
4. How can I ensure data consistency between planning scenarios and live allocation data?
5. Are there established patterns for versioning/temporal data in allocation/inventory systems?

## Constraints
- System must integrate with existing SAP workflow
- Performance should remain acceptable with historical data growth
- Business users need intuitive access to historical trends and comparisons

Please provide specific design patterns, database design recommendations, and architectural approaches that would solve this problem effectively.