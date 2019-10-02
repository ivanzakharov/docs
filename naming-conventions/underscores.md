---
layout: docs
title: 'Naming conventions for using Underscores'
group: naming-conventions
subgroup: underscores
redirect_from:
  - "/naming-conventions/"
toc: true
---

The underscore character ('\_') can be used in the following situations.

  - When naming formal parameters, it should be used as the first character. 

  - In the [DEL\_ prefix](prefixes.md).

  - Subclasses can have the same name as their parent class, postfixed with a logical name that describes the subclass specialization. The name of the parent class might have to be shortened. In this case, use an underscore between the shortened parent class name, and the rest of the name. For example: InventUpd\_Financial, InventUpd\_Physical.

  - In an application object that is created within the specific model using [model acronim](naming-conventions/naming-basics/#model-naming). For example: TaxReport\_BE, LedgerJournalizeTrans\_ES.

Do not use an underscore in the following situations:

  - Beginning of an application object name.

  - First character of a variable name in class declarations or methods.

  - End of a variable name in class declarations or methods.
