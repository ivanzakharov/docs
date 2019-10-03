---
layout: docs
title: 'Naming conventions for methods'
group: naming-conventions
subgroup: code-artifacts
redirect_from:
  - "/naming-conventions/code-artifacts/"
toc: true
---

## Method naming

Write a clear, descriptive name for your method or function. If one cannot be found, consider splitting it up.

Use the following preferred names for methods:
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>check*</p></td>
<td><p>A Boolean method that checks a condition. If the condition is not fulfilled, it must put a warning on the Infolog, and return false.</p></td>
</tr>
<tr class="even">
<td><p>exist</p></td>
<td><p>Returns a Boolean that is true if a record with the supplied key exists.</p>
<p>Typical use: Table static method.</p></td>
</tr>
<tr class="odd">
<td><p>find</p></td>
<td><p>Returns a record indicated by the supplied key.</p>
<p>Typical use: Table static method.</p></td>
</tr>
<tr class="even">
<td><p>find*</p></td>
<td><p>Finds a record in the table (where the method is declared). The postfix is the name of the field which is used for accessing the table, or a logical name for more fields.</p>
<p>Typical use: Table static method.</p></td>
</tr>
<tr class="odd">
<td><p>initFromTableName</p></td>
<td><p>This buffer is initialized with values from the buffer supplied.</p>
<p>One argument, which is a buffer of the same type as that named in the method.</p>
<p>Typical use: Table instance method.</p></td>
</tr>
<tr class="even">
<td><p>initParm</p></td>
<td><p>Used for methods that set member variables. If the method only sets some of the variables, indicate this in a prefix to the name, for example initParmVersDate.</p></td>
</tr>
<tr class="odd">
<td><p>is*</p></td>
<td><p>A Boolean method that will check some condition. If the condition is not fulfilled, it must return false. is* cannot change the method. Information must not be sent to the Infolog.</p></td>
</tr>
<tr class="even">
<td><p>parmMemberVariableName</p></td>
<td><p>Methods used for setting and getting the value of a member variable as a part of an object initialization. The method should have the same name as the variable, prefixed with parm.</p></td>
</tr>
<tr class="odd">
<td><p>set*</p></td>
<td><p>Used for methods that set value(s) in the object. The name must make it clear that the method also sets the state of some other global members. set* methods should be void or Boolean, signaling the result of the set.</p></td>
</tr>
<tr class="even">
<td><p>updateFieldName</p>
<p>createFieldName</p></td>
<td><p>If a method updates or creates a record, reflect that in the name, rather than calling the method set FieldName.</p></td>
</tr>
<tr class="odd">
<td><p>validate*</p></td>
<td><p>Same as check*.</p></td>
</tr>
</tbody>
</table>

Methods that have the names listed in the preceding table must carry out the tasks described, and must not have any additional functionality. For example, there must be no assignments in a _validate_, _check*_, or _is*_ method.

## Use of suffixes

Methods on the new tables are created without suffix (as table should has it).<br/>

Examples:

```
Tables\ItemCategoryList_PRJ\Methods\initItemCategoryListId()
Tables\EcoResProductDivision_PRJ\Methods\find()
```


Methods on the existing tables are created with help of class extensions also with suffix.<br/>
See also [Extending tables](/naming-conventions/application-objects/tables/#extending-the-tables).

Examples for how they could be called:

```
ecoResCategory.setCategoryGroupId_PRJ();
inventTable\validateItemConsumerGroup_PRJ();
```

## Existing methods calling
Calling of existing methods (including system functions) should use same casing as method defined.

Follow IntelliSence suggestions in case of doubts.

Example (incorrect):

```
INFO(Enum2Str(NoYes::NO));
```

Example (correct):

```
info(strLTrim(strRTrim(strFmt("Hello, World"))));
salesTable.DeliveryDate = dateNull();
info(enum2Str(NoYes::No))
```



## Use of Uppercase and Lowercase 

Methods have mixed-case names with a lowercase first letter. The first letter of each internal word is capitalized. 

Examples:

```
classDeclaration TutorialExampleClass_PRJ
{
    public void nameThisMethodCorrectly()
    {
    }


}
```

## RunBase extensions

Mutator method must be implemented for each public parameter in class extension of RunBase*. Use prefix <b>parm</b> followed by full name of variable, as method-name:

Examples:

```
class InventABCUpdate extends RunBaseBatch
{
    FromDate fromDate;
    DialogField dialogFromDate;
    
    ToDate toDate;
    DialogField dialogToDate;
 
    public FromDate parmFromDate(FromDate _fromDate = fromDate)
    {
        fromDate = _fromDate;
        return fromDate;
    }
    
    public ToDate parmToDate(ToDate _toDate = toDate)
    {
        toDate = _toDate;
        return toDate;
    }
 
}
```
