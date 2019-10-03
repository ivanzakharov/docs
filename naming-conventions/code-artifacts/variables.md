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

Variable must be declared immediately before the variable is used. Thus code amendments will not break changes into two blocks of code - variables declaration and variables using.

Suffix with [model acronym](/naming-conventions/naming-basics/) should remain in variable name.

Example:

```

InventTable           inventTable;
InventTable           inventTableLocal;
EcoResProductCategory ecoResProductCategory;
EcoResProductType_PRJ ecoResProductType_PRJ;
```

## Variable type
Type of the variable should be used with same casing as defined.

_true_, _false_, and _null_ are all lowercase.

Primitive types (like _str_, _date_, _int_, _real_, _void_, _boolean_) have lowercase names.

Example:

```
ItemId  itemId;
int     i, k;
```


## Table-variable used for record updation
When using of table-variable especially for updating data record, use <b>Upd</b> suffix.

Example:

```
InventTable inventTable;
InventTable inventTableUpd;
```


## Temporary tables
Declaration of variable of temporary table type should be same, as table name.

Example:

```
TmpBankImport_RU tmpBankImport_RU;
TmpBudgetBalance tmpBudgetBalance;
```



## Temporary table from persistent table
Use suffix Tmp

Example:

```
InventTable inventTableTmp;
EcoResProductType_PRJ ecoResProductType_PRJ;

inventTableTmp.setTmp();
inventTableTmp.ItemId = itemId;

ecoResProductType_PRJTmp.setTmp();
ecoResProductType_PRJTmp.checkProductType();
```

## RunBase extensions

Use prefix <b>dialog</b> for naming variable of dialog form controls (using _DialogField_ class).<br/>
Use prefix <b>dialogGroup</b> for naming variable of dialog form controls (using _DialogGroup_ class)

Example:

```
ItemGroupId itemGroupId;
DialogField dialogItemGroupId;

DialogGroup itemGroup;
```


## Global variables
Variable declared in class declaration of parent class or form, should be used with exact cases as declared.


## See also
[lowCamelCase](https://ru.wikipedia.org/wiki/CamelCase)
