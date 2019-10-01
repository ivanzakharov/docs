---
layout: docs
title: Naming basics
group: naming-conventions
subgroup: naming-basics
toc: true
---

## Model naming

Customizations should have suffix (referred as <b>_PRJ</b>, or _model acronim_) related with current application model.

It is recommended to have one single model per implementation project.

## Name structure

Application object names should be constructed hierarchically from four basic components.

For tables:

{business area name} + {business area description} + {type of contents} + _ + {_model acronim_}

For classes:

{business area name} + {business area description} + {action performed} + _ + {_model acronim_}

For forms:

{business area name} + {business area description} + {type of contents/usability} + _ + {_model acronim_}


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
  
## Prefixes

### Subject area object prefix

A subject area specific application object is prefixed with the name of the subject area the object belongs to.

Following prefixes should be used in different subject areas:

| Subject area | Prefix | Examples |
---------------|--------|-----------
| Inventory | Invent* | <b>Invent</b>AccountType_PRJ |
| Products | EcoResProduct* | <b>EcoResProduct</b>Type_PRJ |
| Product categories | EcoResCategory* | <b>EcoResCategory</b>Class_PRJ |
| Customers | Cust* | <b>Cust</b>BankAccount<br/> <b>Cust</b>BalanceCurrency |
| Vendors | Vend* | |
| Ledger | Ledger* | |
| Project | Proj* | | 
| Production | Prod* | |
| Warehouse management | WMS*<br/>WHS* | <b>WMS</b>OrderSplit |

### Application area object prefix

An application area object is prefixed with the name of the application area the object belongs to.

| Subject area | Prefix | Examples |
---------------|--------|-----------
| System wide feature | Sys*<br/>System* | <b>Sys</b>Environments_PRJ |
| Workflow | Workflow* | |
| Data Management Framework | DMF* | | 


### The DEL\_ prefix

DEL\_ is a special prefix. It is an abbreviation for Deleted and is used for application objects that will be deleted. After an object is prefixed with DEL\_, it will be supported for a release and then deleted in the next version of the product.

DEL\_ tables and fields are necessary to allow data update. Such objects allow access to old data that must be migrated to a new location.

When an object with a DEL\_ prefix is introduced, the update mechanisms handle changes in the standard application, for example by moving fields and X++ code to the table that replaces the one with the DEL\_ prefix. But, if you have written X++ code that references an application object that has been given a DEL\_ prefix, you have to update these references yourself.
