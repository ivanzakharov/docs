---
layout: docs
title: 'Dead code examples'
group: examples
subgroup: dead-code
redirect_from:
  - "/examples/"
toc: true
---

Avoid writing redundant code.

Example 1

In the following example, b++ is never reached:

```
a++;
return a;
b++;
return b;
```

Example 2

In the following example, the break statement is never reached:

```
switch (type)
{
    case UtilElementType::Job:
         return false;
         break;
    ...    
}
```

Example 3

In the following example, return a is never reached:

```
if (!a)
{
    throw error("@SYS21628");
    return a;
}
b++;
return b;
```

Example 4

In the following example, the else statement is never used, because execution has already ended at the return statement:

```
if (a)
{
    return a;
}
else
{
    b++;
    return b;
}
```

Use this format instead:

```
if (a)
{
    return a;
}
b++;
return b;
```
