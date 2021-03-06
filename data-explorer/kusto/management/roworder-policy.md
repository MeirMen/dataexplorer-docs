---
title: RowOrder policy - Azure Data Explorer
description: This article describes RowOrder policy in Azure Data Explorer.
services: data-explorer
author: orspod
ms.author: orspodek
ms.reviewer: rkarlin
ms.service: data-explorer
ms.topic: reference
ms.date: 02/24/2020
---
# roworder policy command

This article describes control commands used for creating and altering [row order policy](../management/roworderpolicy.md).

## Show RowOrder policy

```kusto
.show table <table_name> policy roworder

.show table * policy roworder
```

## Delete RowOrder policy

```kusto
.delete table <table_name> policy roworder
```

## Alter RowOrder policy

```kusto
.alter table <table_name> policy roworder (<row_order_policy>)

.alter tables (<table_name> [, ...]) policy roworder (<row_order_policy>)

.alter-merge table <table_name> policy roworder (<row_order_policy>)
```

**Examples** 

The following example sets the row order policy on the `TenantId` column (ascending) as a primary key, 
and on the `Timestamp` column (ascending) as the secondary key. The policy is then queried.

```kusto
.alter table events policy roworder (TenantId asc, Timestamp desc)

.alter tables (events1, events2, events3) policy roworder (TenantId asc, Timestamp desc)

.show table events policy roworder 
```

|TableName|RowOrderPolicy| 
|---|---|
|events|(TenantId asc, Timestamp desc)|
