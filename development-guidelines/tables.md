---
layout: docs
title: 'Development guidelines for Tables'
group: development-guidelines
subgroup: tables
redirect_from:
  - "/development-guidelines/"
toc: true
---




## Mandatory fields

- Each mandatory field should be displayed on first or second tab of the form. Usually, it belongs to _Overview_ or _General_ tab of the form.

- If target environment already has some data in the table, mandatory fields should be deployed into that environment with two steps:
  - Deploy field as non-mandatory into target environment. Run Job to fill all existing data.
  - Deploy field as mandatory.

- It is prohibited to add mandatory fields into standard tables. If needed, you should follow these steps:
  - Add field to table-extention and to have (or to add) the switch, enabling checking for filling the field value.
  - Add check for field validation on validateWrite() with mandatory switch, enabling additional validation.

Examples:

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
    
        if (VendGroup::find(this.VendGroup).CheckVendorReference_PRJ &&
            ! this.VendorReferenceTypeId_PRJ)
        {
            ok = checkFailed(strFmt("@SYS84378", fieldPName(PurchTable, VendorReferenceTypeId_PRJ)));
        }
    
        return ok;
}
```
