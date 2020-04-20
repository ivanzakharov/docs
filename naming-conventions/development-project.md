---
layout: docs
title: 'Naming conventions for Development projects'
group: naming-conventions
subgroup: naming-basics
redirect_from:
  - "/naming-conventions/"
toc: true
---

Every single feature/functionality should be developed using Visual Studio and each development task should be linked with related task in Azure DevOps with further delivery to production.

_Notes:<br/>
It is not necessary to create separate project for bug fixing during functional and acceptance testing – task is developing with single solution._

Naming of development project (and solution) in Visual Studio should follow this rule:

_PRJAAAAA_BBBBBBBBB_UUU_, where<br/>

_PRJ_ - acronym for current model (see [Model naming](/naming-conventions/model-naming/))<br/>

_AAAAA_ - task id / work item Id, padded with zeros to the left of 5 characters<br/>

_BBBBBBBBB_ - short name of the developing feature in [UpperCamelCase](https://techterms.com/definition/camelcase)<br/>

_UUU_ – developer’s nickname\alias in UPPERCASE

Examples:

```
CNL00153_PurchWorkflowParticipants_IZA
CNL02001_SalesInvoicePrintToExcel_SAO
VG00021_ImportPurchLineFromExcel_RDO
```
