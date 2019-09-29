---
layout: docs
title: 'Naming conventions for forms'
group: naming-conventions
subgroup: application-objects
redirect_from:
  - "/naming-conventions/application-objects"
toc: true
---

## Extending the forms 
To name a handler class that implements the extension of methods of an existing form, use the following principle:

Classes\<FormFullName><b>Form_PRJ_Extension</b>

Examples:
```
Forms\PurchTable - Classes\PurchTableForm_PRJ_Extension
Forms\LedgerJournalTransDaily – Classes\LedgerJournalTransDailyForm_PRJ_Extension
```

For creation of class-extension following attribute is used:
```
[ExtensionOf(formStr(PurchEditLines))]
```

## Datasources

### Datasources naming

Datasources name must match the name of the table used. 
In form extensions - with the <b>_PRJ</b> suffix. 

```
Tables\PurchTable_PRJ (new table)
Forms\PurchTable.Extension_PRJ (form extension)
Forms\PurchTable.Extension_PRJ\Datasources\VendTable_PRJ (new datasource on form extension)
Forms\VendInvoiceJour.Extension_PRJ\Datasources\PurchTable_PRJ (table PurchTable)
Forms\VendInvoiceJour.Extension_PRJ\Datasources\PurchTable_PRJ_PRJ (table PurchTable_PRJ)
```

Datasource name for temporary table should be same as table name.

```
Tables\TmpEcoResCategoryImport_PRJ
Forms\EcoResCategoryImportForm_PRJ\Datasources\TmpEcoResCategoryImport_PRJ
```

### Extending the form datasources
To name a handler class that implements the extension of methods of an existing form datasource, use the following principle:

```
Classes\<FormFullName>Form_<DatasourceFullName><b>DS_PRJ_Extension</b>
```

Examples:

```
Classes\PurchTableForm_PurchTableDS_PRJ_Extension
Classes\LedgerJournalTransDailyForm_LedgerJournalTransDS_PRJ_Extension
Classes\LedgerJournalTransDailyForm_LedgerJournalTrans_WDS_PRJ_Extension
```

For creation of class-extension following attribute is used:
```
[ExtensionOf(formDataSourceStr(PurchEditLines, PurchParmUpdate))]
```

### Extending the fields of form datasources
To name a handler class that implements the extension of the fields methods of an existing form datasource, use the following principle:

```Classes\<FormFullName>Form_<DatasourceFullName>DS_<FullDatasourceFieldName>Field_PRJ_Extension.```

Examples:

```
Classes\LedgerJournalTransDailyForm_LedgerJournalTransDS_AccountAgreementId_RUField_PRJ_Extension
Classes\LedgerJournalTransDailyForm_LedgerJournalTrans_WDS_CFDIFinancialSystem_MXField_PRJ_Extension
```

For creation of class-extension following attribute is used:
```
[ExtensionOf(formDataFieldStr(PurchEditLines, PurchParmUpdate,CheckCreditMax))]
```

## Form controls

### Form controls naming
All added from controls should have <b>_PRJ</b> suffix.

### Extending the form controls
To name a handler class that implements the extension of the form controls, use the following principle:

```Classes\\<FormFullName>Form_<ControlFullName>Ctrl<b>_PRJ_Extension</b>```

Examples:

```
Classes\LedgerJournalTransDailyForm_AccountAgreementId_RUCtrl_PRJ_Extension
Classes\LedgerJournalTransDailyForm_CFDIFinancialSystem_MXCtrl_PRJ_Extension
```

For creation of class-extension following attribute is used:
```
[ExtensionOf(formControlStr(PurchEditLines, CheckCreditMax))]
```

_Notes:
Since the class name is limited to 80 characters, you can shorten the name of the field or data source (but not the form!)._


## Alternate way to extending the forms 
For extending the forms, you may implement override-methods for form controls/datasources/fields.<br>
Benefits of this approach - to have single form extension class for all form customization:
```
[ExtensionOf(formStr(EcoResProductCreate))]
final class EcoResProductCreateForm_PRJ_Extension 
{
    void init()
    {
        next init();

        FormStringControl ctrlEcoResProductDivisionId_PRJ = this.design().controlName(formcontrolstr(EcoResProductCreate, EcoResProductDivisionId_PRJ));
        ctrlEcoResProductDivisionId_PRJ.registerOverrideMethod(methodStr(FormStringControl, modified),
                                                               methodStr(EcoResProductCreateForm_PRJ_Extension, EcoResProductDivisionId_PRJ_modified), 
                                                               this);
        ctrlEcoResProductDivisionId_PRJ.mandatory(EcoResProductParameters::find().ProductDivisionMandatory_PRJ);

        FormReferenceGroupControl ctrlProductTypeCategoryId_PRJ = this.design().controlName(formcontrolstr(EcoResProductCreate, EcoResProductTypeCategoryId_PRJ));
        ctrlProductTypeCategoryId_PRJ.registerOverrideMethod(methodStr(FormReferenceControl, resolveReference),
                                                             methodStr(EcoResProductCreateForm_PRJ_Extension, EcoResProductTypeCategoryId_PRJ_resolveReference),
                                                             this);
        ctrlProductTypeCategoryId_PRJ.registerOverrideMethod(methodStr(FormReferenceControl, lookupReference),
                                                             methodStr(EcoResProductCreateForm_PRJ_Extension, EcoResProductTypeCategoryId_PRJ_lookupReference),
                                                             this);
        ctrlProductTypeCategoryId_PRJ.registerOverrideMethod(methodStr(FormReferenceGroupControl, modified),
                                                             methodStr(EcoResProductCreateForm_PRJ_Extension, EcoResProductTypeCategoryId_PRJ_modified),
                                                             this);
        ctrlProductTypeCategoryId_PRJ.mandatory(EcoResProductParameters::find().ProductTypeCategoryMandatory_PRJ);

        FormReferenceGroupControl ctrlProductOriginCategoryId_PRJ = this.design().controlName(formcontrolstr(EcoResProductCreate, EcoResProductOriginCategoryId_PRJ));
        ctrlProductOriginCategoryId_PRJ.registerOverrideMethod(methodStr(FormReferenceControl, resolveReference),
                                                               methodStr(EcoResProductCreateForm_PRJ_Extension, EcoResProductOriginCategoryId_PRJ_resolveReference),
                                                               this);
        ctrlProductOriginCategoryId_PRJ.registerOverrideMethod(methodStr(FormReferenceControl, lookupReference),
                                                               methodStr(EcoResProductCreateForm_PRJ_Extension, EcoResProductOriginCategoryId_PRJ_lookupReference),
                                                               this);
        ctrlProductOriginCategoryId_PRJ.registerOverrideMethod(methodStr(FormReferenceGroupControl, modified),
                                                               methodStr(EcoResProductCreateForm_PRJ_Extension, EcoResProductOriginCategoryId_PRJ_modified),
                                                               this);
        ctrlProductOriginCategoryId_PRJ.mandatory(EcoResProductParameters::find().ProductOriginCategoryMandatory_PRJ);
    }

    boolean EcoResProductDivisionId_PRJ_modified(FormStringControl _sender)
    {
        boolean ret = _sender.modified();

        if (ret)
        {
            this.productData().identification_PRJ().parmProductDivisionId_PRJ(_sender.valueStr());
        }

        return ret;
    }

    public Common EcoResProductTypeCategoryId_PRJ_resolveReference(FormReferenceControl _formReferenceControl)
    {
        return EcoResCategory::resolveCategoryHierarchyRole(
            _formReferenceControl,
            EcoResCategoryNamedHierarchyRole::ProductType_PRJ);
    }

    public Common EcoResProductTypeCategoryId_PRJ_lookupReference(FormReferenceControl _formReferenceControl)
    {
        return EcoResCategory::lookupCategoryHierarchyRole(
            _formReferenceControl,
            EcoResCategoryNamedHierarchyRole::ProductType_PRJ,
            true);
    }

    boolean EcoResProductTypeCategoryId_PRJ_modified(FormReferenceGroupControl _formReferenceGroupControl)
    {
        boolean ret = _formReferenceGroupControl.modified();
        if (ret)
        {
            this.productData().identification_PRJ().parmProductTypeCategoryId_PRJ(_formReferenceGroupControl.value());
        }
        return ret;
    }

    public Common EcoResProductOriginCategoryId_PRJ_resolveReference(FormReferenceControl _formReferenceControl)
    {
        return EcoResCategory::resolveCategoryHierarchyRole(
            _formReferenceControl,
            EcoResCategoryNamedHierarchyRole::ProductOrigin_PRJ);
    }

    public Common EcoResProductOriginCategoryId_PRJ_lookupReference(FormReferenceControl _formReferenceControl)
    {
        return EcoResCategory::lookupCategoryHierarchyRole(
            _formReferenceControl,
            EcoResCategoryNamedHierarchyRole::ProductOrigin_PRJ,
            true);
    }

    boolean EcoResProductOriginCategoryId_PRJ_modified(FormReferenceGroupControl _formReferenceGroupControl)
    {
        boolean ret = _formReferenceGroupControl.modified();
        if (ret)
        {
            this.productData().identification_PRJ().parmProductOriginCategoryId_PRJ(_formReferenceGroupControl.value());
        }
        return ret;
    }

    public boolean validateWrite()
    {
        boolean ret = next validateWrite();

        ret = EcoResProductDivisionId_PRJ.validate() && ret;

        ret = EcoResProductTypeCategoryId_PRJ.validate() && ret;

        ret = EcoResProductOriginCategoryId_PRJ.validate() && ret;

        return ret;
    }

}
```
