---
layout: docs
title: Naming conventions
description: Following naming conventions for application objects contain naming rules which are mandatory for developer.
group: development-guidelines
redirect_from:
  - "/"
  - "/development-guidelines/"
  - "/naming-conventions/"
toc: true
---

# Naming essentials

- All customizations should consist project suffix (hereinafter referred as <b>_PRJ</b>).   
- All customizations should be implemented in the single unified model (hereinafter referred as <i><b>Project</b> model</i>).
- Present naming conventions guarantee to have only one extension for the object.

## New objects

New objects with following types are created with <b>_PRJ</b> postfix:
- Base Enums
- Extended Data Types
- [Tables](#tables)
- Views
- Queries
- [Data Entities](#data-entities)
- Composite Data Entities
- Aggregate Data Entities
- Maps
- Table Collections
- Classes
- Macros
- Forms
- Tiles
- Menus
- Menu Items
- Analytics (and all its descendants)
- Reports (and all its descendants)
- Business Process and Workflow
- Resources
- Configuration (and all its descendants)
- Security Roles
- Security Duties
- Security Privileges
- Security Policies
- Services
- Service Groups

Examples:

```
BaseEnums\BankClientStreamType_PRJ
BaseEnums\DayNight_PRJ
BaseEnums\GanttBorderType_PRJ
ExtendedDataTypes\DirOrganizationRoles_PRJ
ExtendedDataTypes\ProjCategoryItemId_PRJ
ExtendedDataTypes\EcoResProductTypeCategoryId_PRJ
Tables\EcoResCategoryGroupsTable_PRJ
Tables\CustomerEntityStaging_PRJ
Tables\DispatchBoardProfile_PRJ
Views\WorkflowCommentList_PRJ
Views\PurchTableLastReqView_PRJ
Queries\ActivityListOpen_PRJ
Queries\AssetRecordList_PRJ
```

## Extended objects

Following extensions are created with <b>.Extension_PRJ</b> postfix:
- Base Enum Extensions
- Extended Data Types Extensions
- Table Extensions
- View Extensions
- Query Extensions
- Data Entity Extensions
- Form Extensions
- Menu Extensions
- Menu Item Extensions
- Security Role Extensions
- Security Duty Extensions

Examples:

```
BaseEnumExtensions\CaseCategoryGroupType.Extension_PRJ
BaseEnumExtensions\NumberSeqModule.Extension_PRJ
ExtendedDataTypesExtensions\CalendarId.Extension_PRJ
ExtendedDataTypesExtensions\Description.Extension_PRJ
ExtendedDataTypesExtensions\Name.Extension_PRJ
TableExtensions\EcoResCategory.Extension_PRJ
ViewsExtensions\CaseCategoryGroupType.Extension_PRJ
ViewsExtensions\NumberSeqModule.Extension_PRJ
QueryExtensions\smmActivities.Extension_PRJ
FormExtensions\RetailStoreTable.Extension_PRJ
FormExtensions\SalesAgreement.Extension_PRJ
```



# Tables

## Fields
Fields on table extensions should be named with postfix <b>_PRJ</b><br/>
Fields on new tables are created without postfix.

Examples:

```
TableExtensions\CategoryTable.Extension_PRJ\FIelds\CategoryGroupId_PRJ
TableExtensions\InventTable.Extension_PRJ\FIelds\ItemConsumerGroup_PRJ
Tables\ItemCategoryList_PRJ\Fields\ItemCategoryListId
```

## Methods 
Methods on the new tables are created without postfix.<br/>
Methods on existing table are created with help of class extensions and without postfix.<br/>

Examples:

````
Tables\ItemCategoryList_PRJ\Methods\initItemCategoryListId()
Tables\EcoResProductDivision_PRJ\Methods\find()
````

Methods executing on existing table:
````
...
ecoResCategory.setCategoryGroupId_PRJ();
inventTable\validateItemConsumerGroup_PRJ();
...
````

## Extending tables 

For extending/changing of behavior of methods on existing _standard_ tables new class-handlers are created, named with name of the origin table and postfix <b>_PRJ_Extension</b>.

You should follow these guides with that:<br/>


[Class extension via method wrapping and Chain of Command (CoC)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/method-wrapping-coc)

[Add methods to tables through extension](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/add-method-table)


Using of CoC (Chain of Commands) is more reasonable. If not possible, it is allowed to use EventHandlers.

See also [Code execution sequence using Chain-of-Commands and EventHandlers](/development-guidlines/code-execution-sequence-using-chain-of-commands-and-eventhandlers/)

Examples:

```
Classes\SMAServiceOrderTable_PRJ_Extension
Classes\PurchTable_RU_PRJ_Extension
```
Для создания класса-обработчика используется атрибут _ExtensionOf_: 
```
[ExtensionOf(tableStr(PurchParmTable))] 
```

# Data Entities

## Data entities for new objects
For new data entities and new related objects (staging table, privileges) it is necessary to adhere to the following rules.

For the original table InventJournalTable_<b>PRJ</b>:<br/>
DataEntities\InventJournalTableEntity_<b>PRJ</b><br/>
Tables\InventJournalTableStaging<b>PRJ</b><br/>
SecurityPrivileges\InventJournalTableEntityMaintain_<b>PRJ</b><br/>
SecurityPrivileges\InventJournalTableEntityView_<b>PRJ</b><br/>

## Modifying existing data model

With adding new fields/tables you should also update existing data entities in which data fields/tables is used.

# Classes
Extension of classes are named by adding the <b>_PRJ</b> and <b>_Extension</b> postfixes to the original class name.

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

For implementing event handlers we should use <b>EventHandler_PRJ</b> postfix, accompanying table name:

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

For implementing event handlers on the forms, please use <b>FormEventHandler_PRJ</b> postfix, accompanying with form name:

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
  
# Forms

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
In form extensions - with the <b>_PRJ</b> postfix. 

```
Tables\PurchTable_PRJ (new table)
Forms\PurchTable.Extension_PRJ (form extension)
Forms\PurchTable.Extension_PRJ\Datasources\VendTable_PRJ (new datasource on form extension)
Forms\VendInvoiceJour.Extension_PRJ\Datasources\PurchTable_PRJ (table PurchTable)
Forms\VendInvoiceJour.Extension_PRJ\Datasources\PurchTable_PRJ_PRJ (table PurchTable_PRJ)
```

### Extending the form datasources
To name a handler class that implements the extension of methods of an existing form datasource, use the following principle:

Classes\<FormFullName>Form_<DatasourceFullName><b>DS_PRJ_Extension</b>

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

Classes\<FormFullName>Form_<DatasourceFullName>DS_<FullDatasourceFieldName>Field_PRJ_Extension.

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
All added from controls should have <b>_PRJ</b> postfix.

### Extending the form controls
To name a handler class that implements the extension of the form controls, use the following principle:

Classes\\<FormFullName>Form_<ControlFullName>Ctrl<b>_PRJ_Extension</b>

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


# Jobs (Runnable class)
Standalone executed runnable classes (Jobs) are named as follows:<br/>
_PRJAAAAA_BBBBBBBBB_, where<br/>
_AAAAA_ - work item Id, padded with zeros to the left of 5 characters<br/>
_BBBBBBBBB_ - short title for Job in [UpperCamelCase](https://techterms.com/definition/camelcase)

Examples:

```
PRJ00153_PurchWorkflowParticipantsUpdate
PRJ00087_SalesAgreementUpdate_Customers
PRJ00087_SalesAgreementUpdate_Agreements
PRJ00087_SalesAgreementUpdate_SalesOrders
````

# Development projects
Every single feature/functionality should be developed using Visual Studio and each development task should be linked with related task in Azure DevOps with further delivery to production.

_Notes:<br/>
It is not necessary to create separate project for bug fixing during functional and acceptance testing – task is developing with single solution._

Naming of development project (and solution) in Visual Studio should follow this rule:
_PRJAAAAA_BBBBBBBBB_UUU_, where<br/>
_AAAAA_ - task id / work item Id, padded with zeros to the left of 5 characters<br/>
_BBBBBBBBB_ - hort name of the developing feature in [UpperCamelCase](https://techterms.com/definition/camelcase)<br/>
_UUU_ – developer’s nickname\alias in UPPERCASE

Examples:

```
CNL00153_PurchWorkflowParticipants_IZA
CNL02001_SalesInvoicePrintToExcel_SAO
VG00021_ImportPurchLineFromExcel_RDO
```


# Benefits
- Objects are well-organized with natual naming
- No more parm methods doubts:
a) implement as parmprjInventTable()<br/>
b) implement as parmPRJInventTable()<br/>
c) implement as prjParmInventTable()<br/>
d) implement as prjparmInventTable()<br/>
Answer: implement as parmInventTable_PRJ()<br/>
- variables could start with natural language, ending with postfix:<br/>
```
PurchTable_PRJ purchTable_PRJ = PurchTable::find(purchId).purchTable_PRJ();
VendTableClassId_PRJ vendTableClassId_PRJ = purchTable_PRJ.vendTableClassId_PRJ();
```

Same logic implements with set/get methods
 
