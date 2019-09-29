---
layout: docs
title: 'Naming conventions for functions'
group: naming-conventions
subgroup: code-artifacts
redirect_from:
  - "/naming-conventions/code-artifacts/"
toc: true
---

## Use of suffixes

Methods on the new tables are created without suffix (as table should has it).<br/>

Examples:

```
Tables\ItemCategoryList_PRJ\Methods\initItemCategoryListId()
Tables\EcoResProductDivision_PRJ\Methods\find()
```


Methods on the existing tables are created with help of class extensions also with suffix.<br/>
See also [Extending tables](/naming-conventions/application-objects/tables/#extending-the-tables).

Examples for how they could be called:

```
ecoResCategory.setCategoryGroupId_PRJ();
inventTable\validateItemConsumerGroup_PRJ();
```


## Use of Uppercase and Lowercase 

Methods have mixed-case names with a lowercase first letter. The first letter of each internal word is capitalized. 

Examples:

```
classDeclaration TutorialExampleClass_PRJ
{
    public void nameThisMethodCorrectly()
    {
    }


}
```
