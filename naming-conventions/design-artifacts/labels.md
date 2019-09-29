---
layout: docs
title: 'Naming conventions for Labels'
group: naming-conventions
subgroup: design-artifacts
redirect_from:
  - "/naming-conventions/"
toc: true
---

Every user interface text must be defined by using a label.

A new label must be created for each new semantic use.

Existing labels must be reused. Always try to find a label that expresses the same semantics as the semantics you want to express.

A label should have an uppercase first letter and all the other internal words should begins with uowercase. Labels should not end with a period unless they end with three periods, for example: "New…", "Add…". 

You should not use text constants (for example "%1 - %2") to format labels.

## Languages

Labels should be created for at least US-English language, accompaying with language of feature use.

Describe the use of the text that is used in the label in US-English in the **Description** field on the **Label editor** form. 
This is particularly important for shorter labels where the context is not completely clear.
The comment is used when the label is translated to other languages.

## Inherit Labels from Underlying Data Types

The contents of label-type properties are usually automatically taken from the underlying definitions. For example, the label used for a field HelpText is often inherited from the HelpText of the underlying extended data type. It is an error to insert the same label as that used in the underlying definition (inherit it, do not duplicate it). ![Error icon](images/Aa872655.ErrorIcon(AX.60).gif "Error icon")

However, the label should be changed, if a different description is needed for the item. The following illustration shows a typical situation:

Inheritance of labels:

  - A label is defined on an extended data type.

  - The extended data type is extended by another extended data type, but as long as the label is not changed, it is inherited and reused.

  - That other extended data type is used on a field, and as long as the label is not changed on the field, it is reused again.

  - The field is shown using a control on a form, but as long as the label is not changed on the control, it is reused again.

When possible, a label should be created on an extended data type rather than on a field. If an existing extended data type can be reused, but the existing label is considered unsuitable, create a new extended data type based on the former one and change only the label.

## See also

[HelpText](helptext.md)

