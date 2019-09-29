---
layout: docs
title: 'Naming conventions for Delegates and Event handlers'
group: naming-conventions
subgroup: delegates-and-event-handlers
redirect_from:
  - "/naming-conventions/"
toc: true
---

This topic provides the naming convention for delegates and event handlers when using X++.

## Delegate Naming Conventions

When you name a delegate, follow the general [Naming Conventions](/naming-conventions/overview.md) for X++ and the [Naming Conventions for Functions](/naming-conventions/code-artifacts/functions.md). The following list describes additional naming guidelines for delegates.

  - The two components of the name should be a noun (for example _invoice_) and a verb (for example _opening_ or _opened_). An example is _invoiceOpened_. When the class name is a noun, the noun can be omitted from the delegate name. For example, _Invoice\opened()_.
    
    Use present tense for logic that runs before an event occurs (end with _ing_)
    
    Use past tense for logic that runs after an event occurs (end with _ed_)

  - The following example illustrates definitions of two delegates creating and created in the _Invoice_ class that is a noun.
    
    ```
    class Invoice
    {
        …
        delegate void creating(object sender, InvoiceEventArgs args) {}
        delegate void created(object sender, InvoiceEventArgs args) {} 
    }
       
    ```

## Event Handler Naming Conventions

Event handlers must have a name with the suffix <b>EventHandler</b>. The following example illustrates names that consist of the delegate name and the <b>EventHandler</b> suffix.

```
    void createdEventHandler(object sender, InvoiceEventArgs args)
    void invoiceCreatedEventHandler(object sender, InvoiceEventArgs args)
```


