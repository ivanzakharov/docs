---
layout: docs
title: 'Naming conventions for Jobs (Runnable classes)'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

Standalone executed runnable classes (Jobs) are named as follows:<br/>
_PRJAAAAA_BBBBBBBBB_, where<br/>
_PRJ_ - acronym for current model (see [Model naming](/naming-conventions/naming-basics/#model-naming))<br/>
_AAAAA_ - work item Id, padded with zeros to the left of 5 characters<br/>
_BBBBBBBBB_ - short title for Job in [UpperCamelCase](https://techterms.com/definition/camelcase)

Examples:

```
PRJ00153_PurchWorkflowParticipantsUpdate
PRJ00087_SalesAgreementUpdate_Customers
PRJ00087_SalesAgreementUpdate_Agreements
PRJ00087_SalesAgreementUpdate_SalesOrders
```
