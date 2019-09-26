---
layout: docs
title: 'Naming conventions for forms'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

# Naming conventions for Jobs (Runnable classes)

Standalone executed runnable classes (Jobs) are named as follows:<br/>
_PRJAAAAA_BBBBBBBBB_, where<br/>
_PRJ_ - acronim for current model (see [Model naming](/./model-naming.md))<br/>
_AAAAA_ - work item Id, padded with zeros to the left of 5 characters<br/>
_BBBBBBBBB_ - short title for Job in [UpperCamelCase](https://techterms.com/definition/camelcase)

Examples:

```
PRJ00153_PurchWorkflowParticipantsUpdate
PRJ00087_SalesAgreementUpdate_Customers
PRJ00087_SalesAgreementUpdate_Agreements
PRJ00087_SalesAgreementUpdate_SalesOrders
```
