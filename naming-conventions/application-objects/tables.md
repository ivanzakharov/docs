---
layout: docs
title: 'Naming conventions for tables'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

# Naming conventions for tables

## Fields
Fields on table extensions should be named with postfix <b>_PRJ</b><br/>
Fields on new tables are created without postfix.

Examples:

{% highlight cpp %}
TableExtensions\CategoryTable.Extension_PRJ\FIelds\CategoryGroupId_PRJ
TableExtensions\InventTable.Extension_PRJ\FIelds\ItemConsumerGroup_PRJ
Tables\ItemCategoryList_PRJ\Fields\ItemCategoryListId
{% endhighlight %}

## Methods 
Methods on the new tables are created without postfix.<br/>
Methods on existing table are created with help of class extensions and without postfix.<br/>

Examples:

{% highlight cpp %}
Tables\ItemCategoryList_PRJ\Methods\initItemCategoryListId()
Tables\EcoResProductDivision_PRJ\Methods\find()
{% endhighlight %}

Methods executing on existing table:
{% highlight cpp %}
...
ecoResCategory.setCategoryGroupId_PRJ();
inventTable\validateItemConsumerGroup_PRJ();
...
{% endhighlight %}

## Extending tables 

For extending/changing of behavior of methods on existing _standard_ tables new class-handlers are created, named with name of the origin table and postfix <b>_PRJ_Extension</b>.

You should follow these guides with that:<br/>


[Class extension via method wrapping and Chain of Command (CoC)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/method-wrapping-coc)

[Add methods to tables through extension](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/add-method-table)


Using of CoC (Chain of Commands) is more reasonable. If not possible, it is allowed to use EventHandlers.

See also [Code execution sequence using Chain-of-Commands and EventHandlers](/development-guidlines/code-execution-sequence-using-chain-of-commands-and-eventhandlers/)

Examples:


{% highlight cpp %}
Classes\SMAServiceOrderTable_PRJ_Extension
Classes\PurchTable_RU_PRJ_Extension
{% endhighlight %}
Для создания класса-обработчика используется атрибут _ExtensionOf_: 
{% highlight cpp %}
[ExtensionOf(tableStr(PurchParmTable))] 
{% endhighlight %}

