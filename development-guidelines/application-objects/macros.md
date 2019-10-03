---
layout: docs
title: 'Development guidelines for macros'
group: development-guidelines
subgroup: application-objects
redirect_from:
  - "/development-guidelines/application-objects/"
toc: true
---

Creating of macro is prohibited, use public variable with constant value.

Example:

```
class TutorialMacro
{
    public const str InfoString = 'This is the info string';
}


class PRJ00001_TutorialConstUse
{
    public static void main(Args _args)
    { 
        info(TutorialClass::InfoString);
    }
}

```
