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
[ExtensionOf(formStr (PurchEditLines))]
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

### Extending the form datasources
To name a handler class that implements the extension of methods of an existing form datasource, use the following principle:

```Classes\<FormFullName>Form_<DatasourceFullName><b>DS_PRJ_Extension</b>```

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
final class EcoResProductCreateForm_CNL_Extension 
{
    void init()
    {
        next init();

        FormStringControl ctrlEcoResProductDivisionId_CNL = this.design().controlName(formcontrolstr(EcoResProductCreate, EcoResProductDivisionId_CNL));
        ctrlEcoResProductDivisionId_CNL.registerOverrideMethod(methodStr(FormStringControl, modified),
                                                               methodStr(EcoResProductCreateForm_CNL_Extension, EcoResProductDivisionId_CNL_modified), 
                                                               this);
        ctrlEcoResProductDivisionId_CNL.mandatory(EcoResProductParameters::find().ProductDivisionMandatory_CNL);

        FormReferenceGroupControl ctrlProductTypeCategoryId_CNL = this.design().controlName(formcontrolstr(EcoResProductCreate, EcoResProductTypeCategoryId_CNL));
        ctrlProductTypeCategoryId_CNL.registerOverrideMethod(methodStr(FormReferenceControl, resolveReference),
                                                             methodStr(EcoResProductCreateForm_CNL_Extension, EcoResProductTypeCategoryId_CNL_resolveReference),
                                                             this);
        ctrlProductTypeCategoryId_CNL.registerOverrideMethod(methodStr(FormReferenceControl, lookupReference),
                                                             methodStr(EcoResProductCreateForm_CNL_Extension, EcoResProductTypeCategoryId_CNL_lookupReference),
                                                             this);
        ctrlProductTypeCategoryId_CNL.registerOverrideMethod(methodStr(FormReferenceGroupControl, modified),
                                                             methodStr(EcoResProductCreateForm_CNL_Extension, EcoResProductTypeCategoryId_CNL_modified),
                                                             this);
        ctrlProductTypeCategoryId_CNL.mandatory(EcoResProductParameters::find().ProductTypeCategoryMandatory_CNL);

        FormReferenceGroupControl ctrlProductOriginCategoryId_CNL = this.design().controlName(formcontrolstr(EcoResProductCreate, EcoResProductOriginCategoryId_CNL));
        ctrlProductOriginCategoryId_CNL.registerOverrideMethod(methodStr(FormReferenceControl, resolveReference),
                                                               methodStr(EcoResProductCreateForm_CNL_Extension, EcoResProductOriginCategoryId_CNL_resolveReference),
                                                               this);
        ctrlProductOriginCategoryId_CNL.registerOverrideMethod(methodStr(FormReferenceControl, lookupReference),
                                                               methodStr(EcoResProductCreateForm_CNL_Extension, EcoResProductOriginCategoryId_CNL_lookupReference),
                                                               this);
        ctrlProductOriginCategoryId_CNL.registerOverrideMethod(methodStr(FormReferenceGroupControl, modified),
                                                               methodStr(EcoResProductCreateForm_CNL_Extension, EcoResProductOriginCategoryId_CNL_modified),
                                                               this);
        ctrlProductOriginCategoryId_CNL.mandatory(EcoResProductParameters::find().ProductOriginCategoryMandatory_CNL);
    }

    boolean EcoResProductDivisionId_CNL_modified(FormStringControl _sender)
    {
        boolean ret = _sender.modified();

        if (ret)
        {
            this.productData().identification_CNL().parmProductDivisionId_CNL(_sender.valueStr());
        }

        return ret;
    }

    public Common EcoResProductTypeCategoryId_CNL_resolveReference(FormReferenceControl _formReferenceControl)
    {
        return EcoResCategory::resolveCategoryHierarchyRole(
            _formReferenceControl,
            EcoResCategoryNamedHierarchyRole::ProductType_CNL);
    }

    public Common EcoResProductTypeCategoryId_CNL_lookupReference(FormReferenceControl _formReferenceControl)
    {
        return EcoResCategory::lookupCategoryHierarchyRole(
            _formReferenceControl,
            EcoResCategoryNamedHierarchyRole::ProductType_CNL,
            true);
    }

    boolean EcoResProductTypeCategoryId_CNL_modified(FormReferenceGroupControl _formReferenceGroupControl)
    {
        boolean ret = _formReferenceGroupControl.modified();
        if (ret)
        {
            this.productData().identification_CNL().parmProductTypeCategoryId_CNL(_formReferenceGroupControl.value());
        }
        return ret;
    }

    public Common EcoResProductOriginCategoryId_CNL_resolveReference(FormReferenceControl _formReferenceControl)
    {
        return EcoResCategory::resolveCategoryHierarchyRole(
            _formReferenceControl,
            EcoResCategoryNamedHierarchyRole::ProductOrigin_CNL);
    }

    public Common EcoResProductOriginCategoryId_CNL_lookupReference(FormReferenceControl _formReferenceControl)
    {
        return EcoResCategory::lookupCategoryHierarchyRole(
            _formReferenceControl,
            EcoResCategoryNamedHierarchyRole::ProductOrigin_CNL,
            true);
    }

    boolean EcoResProductOriginCategoryId_CNL_modified(FormReferenceGroupControl _formReferenceGroupControl)
    {
        boolean ret = _formReferenceGroupControl.modified();
        if (ret)
        {
            this.productData().identification_CNL().parmProductOriginCategoryId_CNL(_formReferenceGroupControl.value());
        }
        return ret;
    }

    public boolean validateWrite()
    {
        boolean ret = next validateWrite();

        ret = EcoResProductDivisionId_CNL.validate() && ret;

        ret = EcoResProductTypeCategoryId_CNL.validate() && ret;

        ret = EcoResProductOriginCategoryId_CNL.validate() && ret;

        return ret;
    }

}
```
