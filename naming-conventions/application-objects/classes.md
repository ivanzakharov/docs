---
layout: docs
title: 'Naming conventions for classes'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

# Naming conventions for classes
Extension of classes are named by adding the <b>_PRJ</b> and <b>_Extension</b> suffixes to the original class name.

Examples:

```
Classes\SalesFormLetter_PRJ_Extension
Classes\PurchReqWFExpendiParticipantProvider_PRJ_Extension
```
```
[ExtensionOf(classtr(PurchReqWFExpendiParticipantProvider))]
class PurchReqWFExpendiParticipantProvider_PRJ_Extension
{
	. . .
}
```

For implementing event handlers we should use <b>EventHandler_PRJ</b> suffix, accompanying table name:

```
class EcoResAttributeValueEventHandler_PRJ
{
    [DataEventHandler(tableStr(EcoResAttributeValue), DataEventType::Inserting)]
    public static void EcoResAttributeValue_onInserting(Common sender, DataEventArgs e)
    {
        EcoResAttributeValue ecoResAttributeValue = sender as EcoResAttributeValue;
        // Call the method as if it was defined directly on EcoResAttributeValue.
        ecoResAttributeValue.defaultCategoryGroupId_PRJ();
    }
}
```

For implementing event handlers on the forms, please use <b>FormEventHandler_PRJ</b> suffix, accompanying with form name:

```
class EcoResAttributeValueFormEventHandler_PRJ
{
    [FormEventHandler(formStr(EcoResAttributeValue), FormEventType::Closing)]
    public static void EcoResAttributeValue_OnClosing(xFormRun sender, FormEventArgs e)
    {
        FormDataSource ecoResProduct_ds = sender.dataSource(formDataSourceStr(EcoResAttributeValue, EcoResProductAttributeValue));
        EcoResProductAttributeValue ecoResAttributeValue = ecoResProduct_ds.cursor();
    }
}
```

_Important Notes:<br/>
After implementing of new _Pre_-/_Post_- event handler, you should rebuild your model (during this build the XML files with the list of handlers will be updated in the Bin folder of the model)._
