---
layout: docs
title: 'Naming conventions for tables'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

## Fields
Fields on table extensions should be named with suffix <b>_PRJ</b><br/>
Fields on new tables are created without suffix.

Examples:

```
TableExtensions\CategoryTable.Extension_PRJ\FIelds\CategoryGroupId_PRJ
TableExtensions\InventTable.Extension_PRJ\FIelds\ItemConsumerGroup_PRJ
Tables\ItemCategoryList_PRJ\Fields\ItemCategoryListId
```

## Methods 
See [Naming conventions for methods](/naming-conventions/code-artifacts/methods/)

## Extending the tables 

For extending/changing of behavior of methods on existing _standard_ tables new class-handlers are created, named with name of the origin table and suffix <b>_PRJ_Extension</b>.

You should follow these guides with that:<br/>


[Class extension via method wrapping and Chain of Command (CoC)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/method-wrapping-coc)

[Add methods to tables through extension](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/add-method-table)


Using of CoC (Chain of Commands) is more reasonable. If not possible, it is allowed to use EventHandlers.

See also [Code execution sequence using Chain-of-Commands and EventHandlers](/examples/code-execution-sequence/)

Examples:


```
Classes\SMAServiceOrderTable_PRJ_Extension
Classes\PurchTable_RU_PRJ_Extension
```

Для создания класса-обработчика используется атрибут _ExtensionOf_: 
```
[ExtensionOf(tableStr(PurchParmTable))] 
```

## Temporary tables

Temporary tables, either InMemory or TempDB, should be named with prefix <b>Tmp</b>.

Examples:

```
TmpEcoResCategoryImport_PRJ
TmpMarkReportTable_PRJ
```
