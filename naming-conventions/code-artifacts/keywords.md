---
layout: docs
title: 'Naming conventions for use of keywords'
group: naming-conventions
subgroup: code-artifacts
redirect_from:
  - "/naming-conventions/"
toc: true
---

Reserved words in the X++ language all begin with a lowercase letter.

Examples:

```
if (...)
{
    while (true)
    {
        for (int i=0; i < 10; i++)
        {
            ttsBegin;
            
            InventTable inventTable;
            select firstOnly pessimisticLock forUpdate inventTable;
            if (inventTable)
            {
                inventTable.update();
            }
            
            ttsCommit;
        }
    }
}
else
{
   ...
}
```
