---
layout: docs
title: 'Naming conventions for variables'
group: naming-conventions
subgroup: code-artifacts
redirect_from:
  - "/naming-conventions/code-artifacts/"
toc: true
---

Variables have mixed-case names with a lowercase first letter. The first letter of each internal word is capitalized. 

Suffix with [model acronim](/naming-conventions/model-naming.md) remains in variable.

Examples

```

InventTable           inventTable;
InventTable           inventTableLocal;
EcoResProductCategory ecoResProductCategory;
EcoResProductType_PRJ ecoResProductType_PRJ;
```


## Table-variable used for record updation
When using of table-variable especially for updating data record, use <b>Upd</b> suffix.

Examples:

```
InventTable inventTable;
InventTable inventTableUpd;
```


## Temporary tables
Declaration of variable of temporary table type should be same, as table name.

Examples:

```
TmpBankImport_RU tmpBankImport_RU;
TmpBudgetBalance tmpBudgetBalance;
```



## Temporary table from persistent table
Use suffix Tmp

Examples:

```
InventTable inventTableTmp;
EcoResProductType_PRJ ecoResProductType_PRJ;

inventTableTmp.setTmp();
inventTableTmp.ItemId = itemId;

ecoResProductType_PRJTmp.setTmp();
ecoResProductType_PRJTmp.checkProductType();
```


## Existing variable
Variable declared in class declaration of parent class or form, should be used with exact cases as declared.


## See also
[lowCamelCase](https://ru.wikipedia.org/wiki/CamelCase)
