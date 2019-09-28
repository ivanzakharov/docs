---
layout: docs
title: 'Naming structure'
group: naming-conventions
subgroup: name-structure
redirect_from:
  - "/naming-conventions/"
toc: true
---

Where possible, application object names should be constructed hierarchically from four basic components.

For tables:

{business area name} + {business area description} + {type of contents} + {[acronim for model](model-naming.md)}

For classes:

{business area name} + {business area description} + {action performed} + {[acronim for model](model-naming.md)}


Examples:

```
Tables\PriceDiscAdmName_PRJ
Tables\PriceDiscAdmTrans_PRJ
Classes\PriceDiscAdmCopy_PRJ
Classes\PriceDiscAdmDelete_PRJ
Classes\PriceDiscAdmSearch_PRJ
Classes\CustInvoicePrintout_PRJ
```

## See also

[Naming basics](naming-basics.md)

[Model naming](model-naming.md)
