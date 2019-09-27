---
layout: docs
title: 'Naming conventions for methods'
group: naming-conventions
subgroup: code-artifacts
redirect_from:
  - "/naming-conventions/code-artifacts/"
toc: true
---

Methods on the new tables are created without suffix (as table should has it).<br/>

Examples:

```
Tables\ItemCategoryList_PRJ\Methods\initItemCategoryListId()
Tables\EcoResProductDivision_PRJ\Methods\find()
```


Methods on the existing tables are created with help of class extensions also with suffix.<br/>
See also [Extending tables](/application-objects/tables.md#extending-tables).

Examples for how they could be called:

```
ecoResCategory.setCategoryGroupId_PRJ();
inventTable\validateItemConsumerGroup_PRJ();
```
