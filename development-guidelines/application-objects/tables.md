---
layout: docs
title: 'Development guidelines for Tables'
group: development-guidelines
subgroup: tables
redirect_from:
  - "/development-guidelines/"
toc: true
---

## Table properties

- Always define Primary and Cluster indexes.

- Always define _Table group_ property based on table contents.

## Fields

- Visible field should always be the part of field group (at least one)

### Field data type

- Always set field data type as EDT or Base enum.

- For field which is Foreing Key, use same data type, as used in Primary key of related table.

- For _RecId_ and _TableId_ data stored in the field, use Extended Data Types _RefRecId_ and _RefTableId_ respectively. 

## Renaming the keys

- New customization should not affect to standard renaming primary key functionality. With adding new fields, that are Foreign Keys, neet to make sure that there is proper relation with Primary Key. 

## Relations


## Indexes

- Maximum column count in customized index is limited to 3 (three). If more needed, BP Rule exception should be introduced anc checked by Code Reviewer or Technical Architect afterwards. 
[TODO - Make BP with limiting index field count](todo.md)

## Mandatory fields

- Each mandatory field should be displayed on first or second tab of the form. Usually, it belongs to _Overview_ or _General_ tab of the form.

- If target environment already has some data in the table, mandatory fields should be deployed into that environment with two steps:
  - Deploy field as non-mandatory into target environment. Run Job to fill all existing data.
  - Deploy field as mandatory.

- It is prohibited to add mandatory fields into standard tables. If needed, you should follow these steps:
  - Add field to table-extention and to have (or to add) the switch, enabling checking for filling the field value.
  - Add check for field validation on validateWrite() with mandatory switch, enabling additional validation.

Example:

```
Table Extensions\PurchTable.Extension_PRJ\Fields\VendorReferenceTypeId_PRJ (added)
Table Extensions\VendGroup.Extension_PRJ\Fields\CheckVendorReference_PRJ (added)

...

[ExtensionOf(tableStr(PurchTable))]
final class PurchTable_PRJ_Extension (added)
{
    public boolean validateWrite()
    {
        boolean ok = next validateWrite();
    
        if (! this.VendorReferenceTypeId_PRJ &&
            VendGroup::find(this.VendGroup).CheckVendorReference_PRJ)
        {
            ok = checkFailed(strFmt("@SYS84378", fieldPName(PurchTable, VendorReferenceTypeId_PRJ)));
        }
    
        return ok;
}
```

## Mandatory data entities

For tables with following table groups it is mandatory to create flat data entity with all table fields:

- Group
- Main
- Miscellaneous
- Reference
- Worksheet
- Worksheet header
- Worksheet line

Such data entity should be named with suffix <b>FlatEntity_PRJ</b> 
