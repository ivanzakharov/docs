---
layout: docs
title: 'Naming conventions for methods'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/code-artifacts"
toc: true
---

# Naming conventions for methods

Methods on the new tables are created without suffix.<br/>
Methods on existing table are created with help of class extensions and without suffix.<br/>

Examples:

```
Tables\ItemCategoryList_PRJ\Methods\initItemCategoryListId()
Tables\EcoResProductDivision_PRJ\Methods\find()
```

Methods executing on existing table:
```
...
ecoResCategory.setCategoryGroupId_PRJ();
inventTable\validateItemConsumerGroup_PRJ();
...
```
