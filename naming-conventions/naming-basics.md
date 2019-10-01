---
layout: docs
title: Naming basics
group: naming-conventions
subgroup: naming-basics
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

## Name structure

Application object names should be constructed hierarchically from four basic components.

For tables:

{business area name} + {business area description} + {type of contents} + _ +{[acronim for model](model-naming.md)}

For classes:

{business area name} + {business area description} + {action performed} + _ + {[acronim for model](model-naming.md)}

For forms:

{business area name} + {business area description} + {type of contents/usability} + _ + {[acronim for model](model-naming.md)}


Examples:

```
Tables\PriceDiscAdmName_PRJ
Tables\PriceDiscAdmTrans_PRJ
Classes\PriceDiscAdmCopy_PRJ
Classes\PriceDiscAdmDelete_PRJ
Classes\PriceDiscAdmSearch_PRJ
Classes\CustInvoicePrintout_PRJ
Forms\PriceDiscAdministration_PRJ
```

## General Rules

  - All names must be in U.S. English.

  - The default rule is to use logical and descriptive names if no other specialized rules apply.

  - Identifier names have a limit of 81 characters.

  - Names in the Application Object Tree (AOT) and in X++ code must correspond to the names in the U.S. English user interface.

  - Names must be spelled correctly.

  - Names must be used consistently.

  - Each path in the AOT must be unique; nodes must not have identical names.

  - All texts that appear in the user interface must be defined by using a label. (This rule applies only if you want your solution certified as an international solution.)

  - Do not begin a name with "DEL\_" unless it is a table, extended data type or enum, and it is needed for data upgrade purposes. 

  - EDT cannot be with the same name as a Table, Base Enum, or Class.
  
