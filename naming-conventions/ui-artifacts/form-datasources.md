---
layout: docs
title: 'Naming conventions for Form datasources'
group: naming-conventions
subgroup: ui-artifacts
redirect_from:
  - "/naming-conventions/"
toc: true
---

Datasources name must match the name of the table used. 
In form extensions - with the <b>_PRJ</b> suffix. 

```
Tables\PurchTable_PRJ (new table)
Forms\PurchTable.Extension_PRJ (form extension)
Forms\PurchTable.Extension_PRJ\Datasources\VendTable_PRJ (new datasource on form extension)
Forms\VendInvoiceJour.Extension_PRJ\Datasources\PurchTable_PRJ (table PurchTable)
Forms\VendInvoiceJour.Extension_PRJ\Datasources\PurchTable_PRJ_PRJ (table PurchTable_PRJ)
```

Datasource name for temporary table should be same as table name.

```
Tables\TmpEcoResCategoryImport_PRJ
Forms\EcoResCategoryImportForm_PRJ\Datasources\TmpEcoResCategoryImport_PRJ
```

## Form controls naming

All added form controls should have <b>_PRJ</b> suffix.
