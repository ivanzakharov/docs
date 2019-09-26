---
layout: docs
title: 'Naming conventions for data entities'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

# Naming conventions for data entities

## Data entities for new objects
For new data entities and new related objects (staging table, privileges) it is necessary to adhere to the following rules.

For the original table InventJournalTable_<b>PRJ</b>:<br/>
DataEntities\InventJournalTableEntity_<b>PRJ</b><br/>
Tables\InventJournalTableStaging<b>PRJ</b><br/>
SecurityPrivileges\InventJournalTableEntityMaintain_<b>PRJ</b><br/>
SecurityPrivileges\InventJournalTableEntityView_<b>PRJ</b><br/>

## Modifying existing data model

With adding new fields/tables you should also update existing data entities in which data fields/tables is used.
