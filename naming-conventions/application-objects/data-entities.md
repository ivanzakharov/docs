---
layout: docs
title: 'Naming conventions for data entities'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

## Data entities for new objects
For new data entities and new related objects (staging table, privileges) it is necessary to adhere to the following rules.

For the original table InventJournalTable<b>_PRJ</b>:<br/>
DataEntities\InventJournalTableEntity<b>_PRJ</b><br/>
Tables\InventJournalTableStaging<b>_PRJ</b><br/>
SecurityPrivileges\InventJournalTableEntityMaintain<b>_PRJ</b><br/>
SecurityPrivileges\InventJournalTableEntityView<b>_PRJ</b><br/>

## Modifying existing data model

With adding new fields/tables you should also update existing data entities in which data fields/tables is used.
