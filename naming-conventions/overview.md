---
layout: docs
title: 'Naming conventions: Overview'
group: naming-conventions
subgroup: naming-overview
redirect_from:
  - "/naming-conventions/"
toc: true
---

For many years in the world of Dynamics AX, prefixes have been used to name objects.

Modern D365FO requires a new way of naming objects, which will be fully combined with features and existing limitations.

Present naming conventions contribute to consistency and to making the application easier to understand.

## Simple naming rule

The naming rule is quite simple and straighforward - to use suffixes instead of prefixes:

- Use suffix <b>_PRJ_Extension</b> (where <b>_PRJ</b> is [model acronym](/naming-conventions/naming-basics)) to name the class extension.

  Example:
  ```
  Classes\InventJournalTrans_PRJ_Extension  
  Classes\PurchTableForm_PurchTableDS_PRJ_Extension
  Classes\SalesFormLetter_PRJ_Extension
  ```

- Use suffix <b>_PRJ</b> to name any other application object/element.

  Example:
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
  DataEntities\InventJournalTableEntity_PRJ
  Tables\InventJournalTableStaging_PRJ
  SecurityPrivileges\InventJournalTableEntityMaintain_PRJ
  SecurityPrivileges\InventJournalTableEntityView_PRJ
  ```

Detailed naming conventions for [New objects](/naming-conventions/application-objects/new-objects/) and [Extended objects](/naming-conventions/application-objects/extended-objects/). 

### Benefits

- According to the [Development guidelines](/development-guidelines/overview/) (to have only one extension for object per model), proposed naming will help the developer easily find the existing extensions or customizations for the object.<br/>Thus class-extentions will be aligned with extended class as well as inherited-classes.

  Example:

  ```
  Tables\EcoResProduct
  Tables\EcoResProductType_PRJ
  Table Extensions\EcoResProduct.Extension_PRJ
  ...
  Classes\SalesFormLetter
  Classes\SalesFormLetter_PRJ_Extension
  ...
  Classes\SalesFormLetter_Invoice  
  Classes\SalesFormLetter_Invoice_PRJ_Extension
  ```

- Code extentions well-aligned with standard methods

  Example:

  ```
  [ExtensionOf(tableStr(EcoResCategory))]
  final class EcoResCategory_PRJ_Extension
  {
      public static EcoResCategory findByCode_PRJ(EcoResCategoryCommodityCode _ecoResCategoryCommodityCode,
                                                  EcoResCategoryHierarchyId   _ecoResCategoryHierarchyId,
                                                  boolean                     _forUpdate = false)
      {
        ...
      }
  }


  // example of using

  class PRJ0001_TutorialJob
  {
     EcoResCategory ecoResCategory = EcoResCategory::findByCode_PRJ(...);
  }

  ```

- VisualStudio IntelliSense helps to the developer to code with looking up of standard and new objects, alphabetically ordered.
Naming conventions contribute to consistency and to making the application easier to understand.

- The naming rule is well-determined leaving the developer from doubts in naming. 

- Present naming convention is fully align with having several models used in implementation projects.

  Example (with single _global_ model with models by countries\regions):

  ```
  Table Extensions\PurchTable\Fields\PaymClassId_PRJ (sample model 'Project' with arconym 'PRJ')
  Table Extensions\PurchTable\Fields\IntrastatCode_PRJEU
  Table Extensions\PurchTable\Fields\PaymClassId_PRJAPAC
  Table Extensions\PurchTable\Fields\PaymClassId_PRJUS
  ```
  
## Naming conventions

This topic provides naming rules:

[Naming basics](/naming-conventions/naming-basics)

[Model naming](/naming-conventions/model-naming)

[Application objects](/naming-conventions/application-objects/overview)

[Code artifacts](/naming-conventions/code-artifacts/overview)

[UI artifacts](/naming-conventions/ui-artifacts/overview)

[Underscores](/naming-conventions/underscores)

[Development project](/naming-conventions/development-project)
