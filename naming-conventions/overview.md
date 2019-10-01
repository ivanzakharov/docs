---
layout: docs
title: 'Naming conventions: Overview'
group: naming-conventions
subgroup: naming-overview
redirect_from:
  - "/naming-conventions/"
toc: true
---

For many years in the world of Dynamics AX, prefixes have been used to name objects.

Modern D365FO requires a new way of naming objects, which will be fully combined with features and existing limitations.

Present naming conventions contribute to consistency and to making the application easier to understand.

## Suffixes instead of prefixes

We use [model acronim](/naming-conventions/model-naming/) as suffix with implementing any needed customizations. 

Also, we use following naming convention for: [New objects](/naming-conventions/application-objects/new-objects/) and [Extended objects](/naming-conventions/application-objects/extended-objects/) 


### Benefits

- According to the [Development guidelines](/development-guidelines/overview/) (to have only one extension for object per model), proposed naming will help the developer easily find the existing extensions or customizations for the object.<br/>Thus class-extentions will be aligned with extended class as well as inherited-classes.

Examples:

```
Tables\EcoResProduct
Tables\EcoResProductType_PRJ
Table Extensions\EcoResProduct.Extension_PRJ

Classes\SalesFormLetter
Classes\SalesFormLetter_PRJ_Extension
...
Classes\SalesFormLetter_Invoice
Classes\SalesFormLetter_Invoice_PRJ_Extension
```

- Code extentions well-aligned with standard methods

Examples:

```
[ExtensionOf(tableStr(EcoResCategory))]
final class EcoResCategory_PRJ_Extension
{
    public static EcoResCategory findByCode_PRJ(EcoResCategoryCommodityCode _ecoResCategoryCommodityCode,
                                                EcoResCategoryHierarchyId   _ecoResCategoryHierarchyId,
                                                boolean                     _forUpdate = false)
    {
    }
}


// example of using

class PRJ0001_TutorialJob
{
   EcoResCategory ecoResCategory = EcoResCategory::findByCode_PRJ(...);
}

```

- VisualStudio IntelliSense helps to the developer to code with looking up of standard and new objects, alphabetically ordered.
Naming conventions contribute to consistency and to making the application easier to understand.

## Naming conventions

This topic provides naming rules:

[Naming basics](/naming-conventions/naming-basics)

[Model naming](/naming-conventions/model-naming)

[Application objects](/naming-conventions/application-objects/overview)

[Code artifacts](/naming-conventions/code-artifacts/overview)

[UI artifacts](/naming-conventions/ui-artifacts/overview)

[Underscores](/naming-conventions/underscores)

[Development project](/naming-conventions/development-project)
